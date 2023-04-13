# Create a transaction in Solana with an EVM keypair

![alt text](flow.png)

## Steps:
* Connect to your `MetaMask` wallet. 
* Sign a transaction using `MetaMas`k and package it as a message. (Verify it first by use `ethers.utils.verifyMessage`)
* Transmit the message to the server.
* The server generates two instructions, one for the `Secp256k1 Program` and another for your custom program.
* The `Secp2561 Program` validates the signature, public key, and message in the instruction data. If invalid, the transaction is rejected; otherwise, it is accepted.
* Return the transaction's signature to the client.
  
## Discover:
* Your program does not need to verify the Ethereum signature. Simply pass it to the `Secp256k1 Program`, which can validate the signature and public key.
  
## Updates:
* Slight modifications were made on the client side. A Solana `Keypair` is now used to sign the transaction, which is serialized and sent to the server.
* To accommodate multiple signers, use `transaction.partialSign(signer)` to sign the transaction. Using `transaction.sign`(signer) would nullify the signatures of previous signers, preventing confirmation of transactions with multiple signers.
* If you serialize the same transaction multiple times, set `skipPreflight:true` to avoid issues.

# In user role

## Install all dependencies

```bash
yarn install
```

## Run
```bash
yarn start
```

# In server role

## Install all dependencies
```bash
yarn install
```
## Run
```bash
node server.js
```


