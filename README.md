These FAQs (Frequent Asked Questions) are compiled from Telegram chatgroup NEM::Helpdesk and NEM::Projects, and questions I received when I was conducting trainings for public, colleges and universities. The FAQs will be updated from time to time.

# General Questions
## On-chain Smart Contract
**Q:** Is it possible to create smart contract rules on-chain in NEM Blockchain?  
**A:** NEM uses Smart Assets approach. All business logics are to be done at the application leyer. Smart Assets approach is more secure, in the sense that its bulletproof against onchain bugs caused by bad smart contracts developers. 

## Permission
**Q:** How can I set the user privilege as to who can read and write to the blockchain?  
**A:** A private chain could be your solution for this.

## Non-fungible token
**Q:** Is there a standard procedure to develop collectibel tokens/mosaics (non-fungible)?  
**A:** There is no project in NEM1 for this, but there is a first draft (with a few issues) for NEM2: https://github.com/aleixmorgadas/nem2-nonfungible-asset. For NEM1,mosaic is fungile. Non-fungible asset can be created using `account`.

# NEM2

## API
**Q:** Does Catapult has API Key feature to secure REST API?  
**A:** No, it works the same as NIS1 in which you just call the endpoints. No API Key needed.

**Q:** How to manage Access Control List (ACL) offchain?  
**A:** Currently there is no mechanism for this. Generally, frontend interacts with the SDK, SDK interacts with Catapult. Getting information does not require any permission or special parameters.

## Voting System
**Q:** I am using AggreateTransaction function for my voting system so that the transactions of votes to the candidates and the registration of the user's identifier are annouced at the same time. In tnis case, the identifiers and the votes to the candidate can be seen. How to separate these information?  
**A:** You may have a transaction to confirm the registration of the user first with the UI making the user wait for the confirmation of the registration. Create mosaic to be distributed to registered user/voter to only vote once by sending the mosaic to address of the candidate the user/voter wishes to vote for. 

**Q:** Does the user/voter has to use a wallet to vote?  
**A:** No, a wallet is not necessary.

## Catapult-service-bootstrap
**Q:** I have set up nodes from Catapult-service-bootstrap. It was running fine and how I could not send any transaction to the network via nem2-sdk or CLI. How to fix this?  
**A:** If you had a running network and then it stopped working even if you restarted it repeatedly, this could mean the chain file store and MongoDB are out of sync due to dirty shut down. Perform `./clean-data` and `./clean-all` and start afresh. https://github.com/tech-bureau/catapult-service-bootstrap#known-issues. 

# NEM1

## Supernodes
**Q:** Is there a record showing the number of supernodes online for the past 12 months?  
**A:** There is not. You may refer to https://supernodes.nem.io/history for the monthly reward pay-out though. 

**Q:** There are months where the reward pay-out for supernodes has increased. Would the reason be lesser nodes are online?  
**A:** Not necessary. There could also be supernodes that were online but yet to upgrade to the new requirements. 

## NEM Wallet
**Q:** Can NEM-based tokens (mosaics) be withdrawn from NEM Wallet?  
**A:** Not from NEM mobile wallet. You can do that from NEM desktop wallet. Download desktop NEM Wallet from nem.io/downloads, open the "start.html" files in the folder, select "SIGN UP" on the top right, choose "Private key wallet", follow instruction and input the private key from your mobile wallet. You should be able to see the mosaics available in your account and manage them from there.

**Q:** How to generate a new account other than generating through a NEM Wallet?  
**A:** If you are running your own local NIS (NEM Infrastructure Server) node, you can generate new account using the endpoint: http://localhost:7890/account/generate. Else you may use the NEM SDK (example for Testnet):

<<<<<<< HEAD
<<<<<<< HEAD
`var nem = require('nem-sdk').default;`
`var rBytes = nem.crypto.nacl.randomBytes(32);`
`var privateKey = nem.utils.convert.ua2hex(rBytes);`
`var keyPair = nem.crypto.keyPair.create(privateKey);`
`var publicKey = keyPair.publicKey.toString();`
`var address = nem.model.address.toAddress(publicKey, -104);`
=======
=======
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378
`var nem = require('nem-sdk').default;  
var rBytes = nem.crypto.nacl.randomBytes(32);  
var privateKey = nem.utils.convert.ua2hex(rBytes);  
var keyPair = nem.crypto.keyPair.create(privateKey);  
var publicKey = keyPair.publicKey.toString();  
var address = nem.model.address.toAddress(publicKey, -104);`
<<<<<<< HEAD
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378
=======
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378

## Timestamp
**Q:** I got an error saying the timestamp is too far in the future. How to fix it?  
**A:** Your system time is not synchronised with the network time. You may synchronised it using SDK. 

**Q:** Should I use NEM Network time for transaction timestamp, even though I’m hosting my own node?  
**A:** Even if you host your own node, you should use NEM network time for the transaction timestamp. The NEM network time is not guaranteed to be in sync with UTC time, it is only guaranteed that all other nodes use that time to validate the timestamps.

## Exchanges
**Q:** How many types of transaction are support by exchanges?  
**A:** There are 8 types of transactions in NEM1. However, exchanges are not concern about all of those, like ImportantTransfer and MultisigAggregateModification etc. It is the transferTransaction type 257 that the exchanges would concern. the However, there are 2 versions of transaction: 
' Version 1 for transfer of "XEM".
Version 2 for transfer of "Mosaic".
As XEM is also a mosaic, it can be transferred by using both versions.'

**Q:** Do exchanges support multisig transactions?  
**A:** A lot of exchanges do support multisig transactions, but not all. 

**Q:** What are the steps for an exchange to determine if the user is depositing XEM or other mosaic?  
**A:** Here are simple step for an exchange to consider:
<<<<<<< HEAD
<<<<<<< HEAD
`1. Check if the deposit transaction is a multisig transaction.`  
`2. If it is, extract the inner trasaction.`    
`3. Within the transaction (if is not a multisig transaction) or inner transaction, check if there is a "mosaic" array or if the "mosaic" array is empty.`    
`4. If there isn't a "mosaic" array or if the "mosaic" array is emp ty, the deposit is XEM and the "amount" field equals to the amount of XEM deposited in term of micro-XEM (6 divisibles).`   
`5. Else, the "amount" equals to a multiplier for the mosaic "quantity".`
=======
=======
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378

` 1. Check if the deposit transaction is a multisig transaction.
2. If it is, extract the inner trasaction.
3. Within the transaction (if is not a multisig transaction) or inner transaction, check if there is a "mosaic" array or if the "mosaic" array is empty.  
4. If there isn't a "mosaic" array or if the "mosaic" array is empty, the deposit is XEM and the "amount" field equals to the amount of XEM deposited in term of micro-XEM (6 divisibles).  
5. Else, the "amount" equals to a multiplier for the mosaic "quantity".`
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378

## Multisignature Transactions
**Q:** For multisig transaction, which hash should I use to retrieve information from NEM explorer?    
**A:** There are 3 types of hash in a multisig transaction. "innerHash" is for the inner transaction and only available in multisig transaction. "hash" is the transaction hash. "otherHash" is for the corresponding multisig transaction that related to the inner transaction. Use "hash" to look up for information from NEM explorer. 

## Query of transaction history
**Q:** Why I can't retrieve history of transactions from local node?  
**A:** Default for hash retention is 36 hours `nis.transactionHashRetentionTime = 36`. To retain all history of transactions, change the configuration to `-1` in `config.properties`. nis.transactionHashRetentionTime for supernode is set to -1. 

**Q:** Is it possible to get JSON data of a transaction hash?  
**A:** : Yes, using this API endpoint:
`/transaction/get?hash=<insert you hash here>`

**Q:** How to get all transactions in a block?  
**A:** Refer to https://nemproject.github.io/#getting-part-of-a-chain 4.2.2, use the API path `/local/chain/blocks-after` to do that. This API will only works in localhost. 

## Synchronising with Network
**Q:** Does the node synchronise from 0 every time it restarts?  
**A:** The node load from your hard drive when it restarts. Synchronization with the network is done only once. It might take hours for the first time it syncs with the network. You may download database dump `nis5_mainnet.h2-2015k.db.zip` from http://bob.nem.ninja/. After that, the next time you restart the node, the synchronization will be relatively faster as it will "loadBlock" into the memory.

<<<<<<< HEAD
## SSL_PROTOCOL_ERROR/ https
=======
## SSL_PROTOCOL_ERROR
<<<<<<< HEAD
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378
=======
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378
**Q:** Transactions I made on localhost worked well. However, I hit  https://23.228.67.85:7890/transaction/announce `ERR_SSL_PROTOCOL_ERROR` when it is hosted online.  
**A:** Majority of the nodes listen on http ports while you are calling with https. However, you can have SSL in your site and call http nodes in backend. Only a handful NEM nodes listen to https. It’s usually on 7891 instead of 7890.

**Q:** Is there a way to make a rquest to the Catapult node with https?  
**A:** There are no https nodes available. You may use a proxy. 

## Transaction confirmation 
**Q:** How to make sure 2 transactions that are broadcasted together are included in the block or if one transaction fails, the other would be dropped?  
**A:** Announcing transaction doesn't guarantee it will be included in a block. Once annouced, it cannot be called back. Transaction will be either be included in a block or dropped. However, in NEM2, aggregate transacton will have all the transactions aggregated included in a block or dropped altogether. Simply add a handler for https, proxying to the said node. 

**Q:** The following result was returned after a transaction was annouced. What does it mean?
``{ 
       "type": 1, 
       "code": 0, 
       "message": "neutral" 
}``  
**A:** Referring to https://nemproject.github.io/#nemRequestResult 9.30, neutral result. A typical example would be that a node validates an incoming transaction and realizes that it already knows about the transaction. In this case it is neither a success (meaning the node has a new transaction) nor a failure (because the transaction itself is valid). However, this doesn't mean the transaction will definately be included in a block. 

## FAILUTRE_INSUFFICIENT-BALANCE
**Q:** I have a testnet address with verified balance of 1000 XEM. My Mosaic levy is absolute of 5 XEM. I tried to send 1 mosaic to another address but got this error: FAILURE_INSUFFICIENT_BALANCE. What could have happened?   
**A:** There could be only 0.001 XEM in your testnet address. When you get the account balance from an endpoint, it always show in microbalances. As XEM has divisibility of 6, 1000 microXEM means 0.001 XEM. Same goes to mosaic. It will always show in micro-mosaic (depends on its divisibility).

<<<<<<< HEAD
<<<<<<< HEAD
##N NEM Wallet
=======
## NEM Wallet
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378
=======
## NEM Wallet
>>>>>>> 560e7e5cab4233f4b9eb7dfcbaf65bdef1f7d378
**Q:** I still could not connect to a node even if I have switched to another node, multiple times. What could be the reason?  
**A:** You could be in an office building or a university campus where the internet provider has blocked the port (7890) NEM is using. Check your firewall settings or use a VPN which will allow you to use the NEM Wallet.

## Vested XEM
**Q:** Can the vested XEM be transferred?  
**A:** Everytime when XEM are being transferred, it will be a combination of vested and unvested XEM. However, it will be all unvested to the recipient. 

**Q:** How long it takes for me to have 10k vested XEM, if I have 20k XEM in total?  
**A:** You use this calculator https://nem-tools.com/#/harvesting/calculator.
