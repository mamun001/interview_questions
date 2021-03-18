
# .......... 151 Vault Interview Questions  .........

##### *Vault is a Hashicorp Product widely used in DevOps.

## By  Mamun Rashid :: https://www.linkedin.com/in/mamunrashid/ :: Please connect with me.

### Last Updated: 2021.03.18

##


#### 1. What have you done with Vault?

   Answer: 

   Of course, the answer will depend on your unique experiences. 
   
   However, a prepared and practiced answer goes a long way to convince the interviwer that you are well-versed in Vault. Here are some of possible items:

   a. Install and Setup Non-prod and prod cluster.

   b. Added users, groups and policies OR

   c. Incorporated federated logins to Vault clusters.

   d. Incorporated Vault Token into Gitlab Pipelines such that gitlab pipelines can run based on automated triggers

   e. Tested backup and recovery of Vault Clusters

   f. Migrated GCP secrets to Vault from various other places

##

#### 2. What problem does Vault solve? What value does Vault add?

   Answer:
 
     All companies have secrets (passwords, SSL certs, keys etc.). Often, these are needed in code to deploy stuff. That is a significant risk, because traces of these secrets linger on in various places (like repos and logs). Vault among other things, provides 3 major values:

     a. Secrets can be stored securely in one place and retrieved in an encrypted form to be used once.

     b. You can change these secrets dynamically and automatically so that even if a secret is leaked, it has no value after one use.

     c. Vault can handle many types of secrets natively (Database, AWS, Key-Value etc.)

##

#### 3. If you have no access to internet, how to do you get help on CLI?

##
   Answer:

     Vault's help is actually very good quality. Here are 3 examples:

     a. vault -h   (gets help on vault and list subcommands)

     b. vault kv -h (gets help on vault kv and lists subcommands)

     c. vault kv get -h (gets help on vault kv get)  (testmized)

##

#### 4. Why can't one secrets engine access data from another secrets engine? 

    Answer: 

      Beacuse the mechanisms are completely unique for each secret engine. 

      Example: GCP engine and AWS engine and Gitlab engine.

      Another example: kv engine works completely different than database engine. They are also kept in different PATHs.

##

#### 5. Can you have "versions" of secrets?

   Answer:

    First of all when you do "vault read secret", it tells you version number, as long as versioning is turned on.

    Example of retrieving a specific version of a secret: vault kv get -version=1 secret/foo/bar  

    (get version 1 of this secret)

   
##

#### 6. Can you un-delete a secret?

     Answer:

       Yes. vault kv undelete -version=3 secret/foo/bar 

##

#### 7. Can you get a docker image of vault server and run it on your Mac?

     Answer:
 
       docker run --cap-add=IPC_LOCK -e 'VAULT_DEV_ROOT_TOKEN_ID=myroot' -e 'VAULT_DEV_LISTEN_ADDRESS=0.0.0.0:1234' -p 8200:1234 vault
       (here the last word "vault" is the image name and we are setting parameter values on the fly)
       (tested successfully)

##

#### 8. How many keys are used in Vaults encryption process? 

    Answer:	
      Master key and 
      key for storing secrets at rest

##

#### 9. What are the three main duties of response wrapping?

   Answer: 
        A. provides cover so that actual data transmitted is not the secret in plain text format, but encrypted. 

        B. Ensure one party can unwrap the secret and 

        C. The secret has a predefined life-time (like a token).

##

#### 10. What is dev mode?

    Answer:
      It is kind of like "open and easy" mode.
      When Vault is started in dev mode, no further set up is required AND you local vault CLI has automatic access.
      This is meant for playing with vault.

##

#### 11. What does "list" command do?

    Answer: 
      This one is confusing. "list" does what it should do. e.g. list keys in a path, lists auths enabled.
      BUT , format is different for different commands (way to go Hashicorp :-) ):
      Examples:
      vault auth list (lists auths enabled) 
      vault list just-a-test/  (lists keys in that path)

##

#### 12. You have a dynamic secret set up for a database. Lease Time is 24 hours. Developer A does a "vault read" on the correct path. That generates a username and password. Developer A uses that pair to succesfully login to the database. After 1 hour, Developer B (who also has access) does "vault read". Will she get a new pair of username/password or the same one that Developer got?

     Answer:

       Same as Developer A

##

#### 13. Which command would bring out master key?

    Answer: 

      unseal

##

#### 14. Why do you need to get the "master key" with the unseal command?

    Answer:

       Master key is used the decrypt the encryptions keys sitting next to the secrets.

##

#### 15. What is Shamir Sealing and how does Vault use this concept?

   Answer: 

     This is basically an algorithm to safeguard the master key. A certain threshold of shards is required to reconstruct the unseal key, which is then used to decrypt the master key.    

##

#### 16. How does the unseal process work?

    Answer:
      The shards are added one at a time (in any order) until enough shards are present to reconstruct the key and decrypt the master key.

##

#### 17. Once a Vault node is unsealed, it remains unsealed until one of what needs to happen for it to be sealed again?

    Answer:	
      It is sealed again once "operator seal" command is run

##

#### 18. When you are writing policies, difference between + AND * ?

     Answer:
       + is single directory wildcard
       * true wild card : recursive all the way down

##

#### 19. What does that general encryption process look like in Vault?

    Answer: 
      Operator sends a secret AFTER encrypting it using base64 (to ensure safe transit).  Vault then encrypts it again using its internal key before storing it at rest.

##

#### 20. What is this "cubbyhole" thing in Vault?

     Answer:
       When Vault is running for the first time, it gives everyone a PATH where,  by defauly, anyone can save secrets. That is "cubbyhole". Without this, one would have to create a path and change its policy just to test out the function of writing and reading secrets.

##

#### 21. When you configure Vault using a configuration file, which 3 parameters must your provide?

     Answer:
       A. Cluster Name
       B. Storage Backend
       C. Seal type

##

#### 22. Name some of the advantages of using PKI:

     Answer:
       A. Reducing or eliminating certifcate revocations
       B. Reduces time to get certificates by eliminating the need to generte a private key and CSR
       C. Vault can act as an intermediate CA

##

#### 23. What is response wrapping?

    Answer: A secret , when retrived, is "wrapped" with ANOTHER token , which can be used ONLY once. This way, the real token cannot be stolen in transit.
            (You can send secret in email if you want, because token can be used only once)

##

#### 24. What default policies do an Empty Policy grant in Vault?

    Answer: 
      Grants no permission at all.

##

#### 25. Can a service token be used to handle a raw request when Vault is in recovery mode? Why or why not?

    Answer:
      No. Because , while in recovery mode, only recovery tokens can be used (by rule of vault operations)

##

#### 26. What are two ways you can join a node to an existing Vault cluster?

    Answer: 
      A. using root certificate and API calls 
      B. Using consul agents running on the new vault nodes

##

#### 27. What is the function of a Google Cloud Storage Bucket when setting up Vault via GCP?

    Answer:
      It stores all the "data" of vault. (e.g. secrets).

##

#### 28. When using Google Cloud Storage, can multiple vault nodes can have access to this data from the bucket?

    Answer: 
      Yes (same idea as NAS)

##

#### 29. Should your vault cluster be able to run other workloads? Why or why not?

    Answer: 
      It can, but it should not. Running other workloads opens up variety of security concerns.

##

#### 30. Does Transit Secret Engine encrypt?
 
    Answer: 
      NO

##

#### 31. True/False: Vault Policies and Roles (Roles have policies) just like AWS.

    Answer: True   (same concept)

    user/entity ----- gets role --- role is attached to policy -- that policy gives specific permissions

##

#### 32. Can you list some of the capabilities alloted in Vault regarding policies?

    Answer: 
      create, read, update, delete, list, sudo, deny (6)

##

#### 33. Which capability takes precedence above all else?

    Answer: 
      Deny

##

#### 34. What is cubbyhole?

    Answer: 
      It is an equivalent of "safe place" at home. It is a predefined PATH. All secrets are kept there namespaced under token.
      If the token expires, secret also expires.

##

#### 37. Command to list all enabled AUTHs:

    Answer: 
      vault auth list -detailed

##

#### 38. Command to list policies?

    Answer: 
      vault policy list   (thanks to hashicorp for being counter-intuitive!) (noun + VERB)

##

#### 39. Let's say you run this command: vault list foo, what will vault server do? (Notice VERB before noun)

    Answer: 
      In this case, you put VERB ahead of noun, it will think that "foo" is a path, so, it will try do see if foo/ (even though you did not put / in the end) is enabled and if so, it will give you list of keys in that path.

##

#### 40. Command to write a secret to the path: secret/teams/
       with key=test1 value=junk1

    Answer:
      vault write secret/teams test1=junk1

##

#### 41. Environment variable that points to vault server:

    Answer:
      VAULT_ADDR="https://vault.example.com"

##


#### 42. Will vault use ENV variable to find your token?

    Answer:
      Yes. VAULT_TOKEN

##

#### 43. Which command will show YOUR TOKEN ID and policies it is attached to: (kind of like whoami and more in linux)

    Answer:
      vault token lookup

##

#### 44. What is Token Accessor?

    Answer:
      It is like a "pointer" or metadata about a token (e.g. TTL etc.)

##

#### 45. Can you make API calls against Vault Server?

    Answer: 
      Yes. Vault has API server that you can reach usig curl command:

##

#### 46. curl command to get system health of the vault server:

    Answer:
      curl -kv $VAULT_ADDR/v1/sys/health

##

#### 47. Which command is basically same as token look up?

    Answer:
      vault read auth/token/lookup-self
      (The point is that token lookup command is just reading from a PATH)

##

#### 48. In vault: "users" are called what?

    Answer: 
      Entity Ids
##

#### 49. Command to list all entity IDs?

    Answer:
      vault list identity/entity/id/ 
     (All it is really it is listing a predefined "path")

##

#### 50. You want auth backend things like GCP/AWS/KV etc. What are these officially called?

    Answers:
      "SECRET ENGINES"

##

#### 51. Storage Backend is for what ?

    Answer: vault "data" (e.g. secrets, entities, policies etc?)

##

#### 52. How can "users" authneticate with vault? Name a few ways.

    Answer:
     a. tokens
     b. TLS certs
     c.  username/password
      AND MORE
##

#### 53. What is you wanted to generate a fresh Token for root. Which command do you run?

    Answer:
      vault operator generate-root
##


#### 54. When vault stores data (eg. secrets), what does it store with it?

    Answer: 
      Data Encryption Key
##

#### 55. What does vault use to decrypt Data Encryption Key:

    Answer: Master Key

##

56. Where does the Master key reside ?

    Answer: 
      In memory (never on persistent disk)

57. How to start vault in dev mode locally:

    Answer:
      vault server -dev

58. Local vault server runs on port:

    Answer: 8200 


59. Command to write a KV secret in path path1/kvsecret1 with key and value of foo=bar:

    Answer:
      vault kv put path1/kvsecret1 foo=bar


60. Command to "read" a kv secret in path path1/secret1 :

    Answer:
      vault kv get path1/secret1

65. Command to delete a secret in path path1/secret1 ?

    Answer: 
      vault kv delete path1/secret1


66. Can Vault tackle dynamic cloud secrets?

      Answer:
        Yes. In fact, this is one the best features of vault.

67. Can Vault tackle PKI Certificates?

      Answer:
        Yes

68. Can Vault tackle Consul and Nomad ACL tokens?

      Answer:
        Yes


69. In a KV V1 policy, can you * in a path?

    Answer:
      Yes.
      For example: path "secret1/data/*"
      (I don't think it works recursively , though)


70. Is "deny" a capability (in a policy) ?

    Answer:
      Yes.


71. Most authentication methods have something  that you can tie policies to. What is that called?

    Answer:
      Roles 


72. One of problem with writing policies is that you have repeat yourself often for various similar policies. Managing those policies become a nightmare pretty fast. How can we make this problem a bit more managable?

    Answer:
      Use templates and variables


73. A few examples of auto-auth functions:

    Answer:
      AWS, Kubernetes, Azure


74. Can Vault Agent create new tokens?

    Answer: 
      Yes

75. Can Vault Agent renew tokens?

    Answer:
      Yes.

76. Which component caches leased secrets like dynamoDB credetentials and PKI certificates?

    Answer:
      Vault Agent



77. Example command to enable kv engine on your vault server?

    Answer: 
      vault secrets enable -path=kv-foo -version =2 kv


78. Name 3 "storage" vault can use:

    Answer: 
      S3, Consul, Generic File Storage


79. Name some of Authentication mechanisms:

    Answer: 
      EC2 (believe it or not), LDAP, Github, Tokens, Username/Password


80. What does "vault init" command do?

    Answer:
      Will initialize tokens and generate root access token



81. How many unseal tokens does vault init command create?

    Answer:
      5

82. Can you access the vault secrets when it is sealed?

    Answer:
      No. (You can read it, but you can't encrypt it, so it is useless)


83. Command to initialize vault:

    Answer:
      vault operator init


84. How many times can you initialize vault?

    Answer: 
      Only Once


85. If you restart vault server after unsealing it, which state does it start up in?

    Answer:
      Sealed State again.


86. In sealed state, why can't vault encrypt the secrets?

    Answer: 
      It has no master key at that point.


87. What can you use instead of Shamir?

    Answer: 
      AWS KMS


88. How do you use AWS KMS instead of Shamir?

    Answer: Add a new seal block under the configuration file for KMS. Then, start up Vault with that configuration file.


89. How many keys do you need to unseal using Shamir (by default)?

    Answer: 
      3


90. Name an engine supports dynamic secrets:

    Answer:
      Google Cloud


91. What is "dynamic" secret? 

    Answer:  
      A secret that is generated on demand and has a lease that expires. For example a database password that is generated on the fly and will automatically expire after the lease expires. So, an entity with the right policy gets this password when it needs and uses to login, but after a while (e.g. 24 hours), password is no longer valid.


92. If you want read replicas for low latency, what do you need?

    Answer: 
      Performance Replica


93. What kind of replication do you need to prevent against data loss?

    Answer: 
      Diaster Recovery Replication


94. How can you get secrets without storing any logic to store tokens and also not making requests with tokens?

    Answer: Vault Agent Caching


95. What is Vault Agent?

    Answer: 
      Vault agent automatically handles renewal and re-authentication and thus you do not have to implement potentially complicated renewal logic yourself.


96. Do you have to be root to unseal Vault?

    Answer:
      NO!


97. Do you have to root to enable audit?

    Answer:
      Yes.


98. How do you revoke ALL all the leases for secrets on a specific path?

    Answer: 
      vault lease revoke -prefix PATH


99. Command to renew a token:

    Answer: 
      vault token renew   


100. Command to enable aws engine:

     Answer:
       vault secrets enable aws  


101. If you revoke a parent token, what happens to its child token?

     Answer:
       Child token is also revoked


102. If you disbale a Secret Engine, what happens to all secrets that belong to that Secret Engine?

     Answer: 
       All secrets will be revoked and
      (data will not be archived for later "enabling")


103. Name some of the "backends" supported by Vault:

     Answer:
       A. Consul
       B. Filesystem
       C. Inmemory
       D. Raft



104. Which permission do you need to do stuff in UI?

     Answer: 
       List


105. Which type of tokens are recommended for encrypting data within Vault?

     Answer:
       Batch Tokens


106. Name some of the actions Secret Engines can do?

     Answer:
       A. STORE
       B. ENCRYPT
       C. Generate


107. Can "Transit Engine" encrypt data?

     Answer:
       Yes. This makes sense because , otherwise, secrets will be readable while in transit.

108. Is encoding same as encrypting?

     Answer:
       No! Anyone can encode and decode with base64 command.



109. Can you have a replication set up on different cloud provider than the primary?

     Answer:
       Yes. 


110. What can you do if a lease  of a Dynamic Secret expires ?

     Answer:
       You have to  generate a new secret because the old secret is gone and so, extending the lease of the old secret doesn't help.


111. Name couple of benefits of Vault Agents?

     Answer:
       1. Caching and 
       2. Renewing


112. Can Vault Agents encrypt secrets?

     Answer:
       NO.


113. Name couple of advantages of DEV mode:
     
     Answer:
       Encryption with TLS
       Persistent backend storage


114. When you are writing policies, which two characters can you use as wild-card characters?

     Answer:
       * AND
       +


115. Can the Transit Secret Engine update a secret?

     Answer:
       NO! Transit Engine has no business modifying a secret. It's job is take a secret from once place to another (from at rest to an entity who has permission to seet i).

116. Can the Transit Secret Engine decrypt a secret?

     Answer:
       Yes. 


117. What are the 3 ways to interact with Vault?

     Answer:
      CLI+ UI + API  (This is true of almost any product these days)

118. Can Vault have plugins?

     Answer:
       Yes.

119.  How can delete a secret?

    Answer: 
      vault delete secret/foo/bar    (Path and Secret Name)

120. Assuming you have the right variable defined, what is quick way to connect to vault server (you are connecting, you are not authenticating) 

   Answer:
     vault status



121. Can vault use github and AD for authentican ?

     Answer:
       Yes, Both



122. Name some of the ways unseal can happen automatcally:

     Answer:
       TRANSIT, AZURE KMS, AWS KMS, HSM


123. Name some of the advantages of batch token over service token:

     Answer:
       A. No storage cost for token creation
       B. Used for ephemeral, high-performance workload
       C. lighteight and scalable



124. Name some of the ways you can unseal when vault is on-prem:

     Answer:

      A. HSM PKCS11
      B. Key shards
      C. AWS KMS
      D. Transit


125. What should you do with root token so that it does not get compromised?

     Answer:
       You should revoke it and generate it again when needed.
       This is kind of like AWS root account keys. You should make other admin accounts and basically keep root account out of reach. You can always re-generate root token when you need it.


126. Does Transit Engine STORE any data ?

     Answer:
       NO


127. Does TSE (Transit Secret Engine) generate Hash ?

     Answer:
       Yes.



128. What is HMAC?

     Answer:
       From wikipedia:  In cryptography, an HMAC is a specific type of message authentication code involving a cryptographic hash function and a secret cryptographic key. As with any MAC, it may be used to simultaneously verify both the data integrity and the authenticity of a message.



129. Does TSE (Transit Secret Engine) generate HMACs?

     Answer:
       Yes

130. Can one secrets engine access data from another secrets engine? 

    Answer: 
      No.



131. If you have an application, but you don't want to implement any logic to store tokens or renew token leases, what can you do?

     Answer:
       Use Vault Agent Caching

132. Which functionality of Vault Agent allows for easy authentication in a wide variety of environments?

     Answer:
       Auto-Auth functionality 



133. When Vault is first initialized, which auth method is availble: (only one) ?

     Answer: Tokens  (Makes sense ,e.g. like root token)



134. Unsealing does exactly what?

     Answer:

     Gets the master key (plaintext)


135. When you are using * as wildcard, can you also use * as part of path's name (e.g. foo_* to mean foo_abc foo_def etc)?

     Answer:
       Yes


136. When you are writing a policy and you want to basiclaly say "enter entity's name here", how do you do that?

     Answer:
       {{identity.entity.name}}



137. Using curl, how to get secret stored at foo/bar   (IP Address of the Vault Server is 1.2.3.4)

     Answer: 
       curl --header "X-Vault-Token:insert_token_her" https://1.2.3.4:8200/v1/foo/bar



138. Joanne logged in to Vault via CLI. He is now sending API calls vi curl, what does he get back?

     Answer: Token Polcies (i.e. Her permissions)


139. Easiest to way to install Vault on your Mac?

      Answer:
        brew install vault


140. Can TSE (Transit Secret Engine) "rewrap" ?

     Answer:
       Yes


141. Can you use memory store as backend?

     Answer:
       Yes


142. Does Vault Support authentication via TLS certificates?

     Answer:
       Yes


143. Command to generate root token again:

     Answer:
       vault operator generate-root


144. According to best practice, what should you do with root tokens in production?

     Answer:
       revoke them! It is like a having a superuser password just hanging around.


145. How do you configure where the plugins are located?

     Answer:
       vault configuration file: plugin_directory=<path>

146. Shamir seal protecs what?

    Answer:
      The Master key 

147. What is PKCS 11?

     Answer: 
       In cryptography, PKCS #11 is one of the Public-Key Cryptography Standards (source: wikipedia)


148. Can you disable tokens auth method?

     Answer:
       NO

149. What does "vault kv destroy" do? Does it destroy a single version or all versions of the secret?

     Answer:
       Permanently deletes a SINGLE version of a secret. NOT all versions.

150. What does the following command do?

     vault write identity/group name="foo_group" policies="default" ....................... (more options)

     Answer: 
       Create a group! The thing to note here is that even creating a group is just writing to a PATH.

151. How to do see what is inside a policy named "foo" ?

     Answer:
       vault policy read foo

152. How to see if your vault has HA enabled or not?

    Answer:
      vault status


153. How to read a secret from a path:

    Answer:
      vault read secret/path1/foo_secret    



