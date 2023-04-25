# Automatic CSFLE using AWS KMS for Node.js

### CSFLE 

- [Mongo CSFLE](https://www.mongodb.com/docs/manual/core/csfle/)

### Prerequesites for Automatic CSFLE

- [mongocryptd](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-enterprise-on-os-x/#install-mongodb-enterprise-on-macos) : On Client where application will connect, install the MongoDB enterprise version.

- [libmongocrypt](https://www.mongodb.com/docs/manual/core/csfle/reference/libmongocrypt/): is required for automatic field level encryption, as it is the component that is responsible for performing the encryption or decryption of the data on the client

### Steps to Execute

- After cloning the code create an .env file 
    - MONGODB_URI: 
    - AWS_ACCESS_KEY_ID: 
    - AWS_SECRET_ACCESS_KEY: 
    - AWS_KEY_REGION: 
    - AWS_KEY_ARN: 

- Create a Data Key in encryption.__keyVault collection
    - node make_data_key.js

- Test Automatic Encryption/Descryption
    - node insert_encrypted_document.js 
 

### Few Notes : 

- The mongocryptd can only bind to localhost and cannot be accessed "over the network"
- the mongocryptd process does not run on database cluster, but rather should be run within your own environment. 
- The mongocryptd daemon should be installed and run on the same server hosting the application so that the MongoDB client (driver) can automatically start and connect to the process

### Architecture Diagrams

- [Write Mongo CSFLE Encryption]

![alt text](https://www.mongodb.com/docs/manual/images/CSFLE_Write_Encrypted_Data.png)

- [Read Mongo CSFLE Decryption]

![alt text](https://www.mongodb.com/docs/manual/images/CSFLE_Read_Encrypted_Data.png)




### Good Reads

- Client Side Field Level Encryption
  - [BLOG](https://www.mongodb.com/developer/languages/javascript/client-side-field-level-encryption-csfle-mongodb-node/)
  - [How Encrypted Writes and Reads Work](https://www.mongodb.com/docs/manual/core/csfle/fundamentals/automatic-encryption/#how-encrypted-writes-and-reads-work)
- [Keys and Key Vaults](https://www.mongodb.com/docs/manual/core/csfle/fundamentals/keys-key-vaults/#keys-and-key-vaults)
- [Use Automatic Client-Side Field Level Encryption with AWS](https://www.mongodb.com/docs/manual/core/csfle/tutorials/aws/aws-automatic/#std-label-csfle-tutorial-automatic-aws)
- [Tutorials](https://www.mongodb.com/docs/manual/core/csfle/tutorials/#tutorials)