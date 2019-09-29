These FAQs (Frequent Asked Questions) are compiled from Telegram chatgroup NEM::Helpdesk and NEM::Projects, Slack and questions I received when I was conducting trainings for public, colleges and universities. The FAQs will be updated from time to time.  
Appreciations go to the contributors to the answers in the group chats.   
Collaboration is welcomed.  
As the development progresses (especially for NEM2), answers may vary.  

# General Questions

## Mosaic
**Q:** Does Mosaic only represent coin or tokens or cryptocurrency?  
**A:** No. A mosaic can represent anything you set it to be. It can be representing units of cryptocurrency or any asset (Security token). 

## Multisignature Account
**Q:** Is that possible to revert a multisignature account back to uni-sighnature account?  
**A:** Yes, this must be initialized from the cosigner. First, login to cosigner, go to `Services -> Multisignature and Multi-User Accounts -> Edit an existing contract.`
Check out this [tutorial.](https://blog.nem.io/how-to-use-multi-signature-contracts-with-nanowallet/)

## Non-fungible token
**Q:** Is there a standard procedure to develop collectibel tokens/mosaics (non-fungible)?  
**A:** There is no project in NEM1 for this, but there is a first draft (with a few issues) for NEM2: https://github.com/aleixmorgadas/nem2-nonfungible-asset. For NEM1,mosaic is fungile. Non-fungible asset can be created using `account`.

**Q:** What is fungibility?  
**A:** [`In economics, fungibility is the property of a good or a commodity whose individual units are essentially interchangeable, and each of its parts is indistinguishable from another part.`](https://en.wikipedia.org/wiki/Fungibility) - Wikipedia. 

## Offline
**Q:** Can an application interact with NEM Blockchain with or without internet ?  
**A:** To unitilise the public NEM Blockchain, the applicaton has to be connected to the internet. If the application is running on local network for a private blockchain, that works too.

**Q:** Can we run the application without internet?  
**A:** You may run application without internet until the signing of the transaction. However, you will need internet or local network in order to interact with the Blockchain.  

## On-chain Smart Contract
**Q:** Is it possible to create smart contract rules on-chain in NEM Blockchain?  
**A:** NEM uses Smart Assets approach. All business logics are to be done at the application leyer. Smart Assets approach is more secure, in the sense that its bulletproof against onchain bugs caused by bad smart contracts developers. 

## Private chain
**Q:** How can I set the user privilege as to who can read and write to the blockchain?  
**A:** A private chain could be your solution for this.

**Q:** Can I fork NEM and modify certain configurations for us to create our own Blockchain?   
**A:** Yes. NEM2 Catapult is open source. Refer to https://github.com/nemtech/catapult-server.

**Q:** Can we create our own blockchain? Or can we fork NEM and modify certain configurations for us to create our own NEM? And still integrated with NEM?  
**A:** Yes. NEM2 Catapult is open source. You can deploy your own private chain and still integrated with other chains. Go to https://github.com/nemtech for more information. 

**Q:** Can anyone participate in the Blockchain?  
**A:** Yes, for public chain. For private or hybrid chain, you may need permission to participate. To participate, you will need an account. 

## Programming language
**Q:** What Progamming language can be used to build application for NEM?  
**A:** NEM Blockchain is API-driven. You may use any langugage you wish and utilise the SDKs available or build your own SDKs.  
`SDKs for NIS1 https://nem.io/developers/`  
`SDKs for Catapult https://nemtech.github.io/sdk/languages.html`

## Sending transaction
**Q:** Is it possible to send a payment request transaction to an address on the NEM Network or run a debit order against an account for a monthly services?   
**A:** This feature is not available in NEM1. However, in the Catapult release, it will be possible to initialize transaction from receiver side but the sender is still required to sign and send the transaction.

**Q:** I made a transfer to my NEM account. However, I lost my private key. Is there any way to reverse the transaction?  
**A:**  No, it’s not possible. You need access to wallet to move coins, which means having your private key. If you lose access and you don’t have backup, the coins are considered lost.

## Transaction fee
**Q:** I’d like to to create a coin where there are no transaction fees and the admin (being a 3rd party) automatically pays all the fees for everyone. Also, it can be instantly used without using NEM to pay for transaction fees. There would be a 2% hit on each transaction that would go towards admin’s account, which covers transaction fees and any overhead fees.Is that doable?  
**A:** While it’s not possible with the current NEM1 public blockchain, it will be possible with the upcoming release of Catapult, where you can pay fees for senders. All transacton fees will still be in XEM for the public chain. 

**Q:** If I create a mosaic, can I create my own coin to use as transaction fees, or the fee must always be in XEM?  
**A:** Transaction fee is always in XEM for public chain.

**Q:** How does NEM calculate the mosaic transaction fee? I’ve created 5 difference namespaces and mosaics. When I sent each mosaic in quantity of 100, their transaction fees appeared to be different.  
**A:** It’s based on Mosaic supply, divisibiltiy and the amount you spent. Please refer to https://nemproject.github.io/#transaction-fees.

**Q:** Are there fees for every transaction?  
**A:** Yes. For the public chain, every transaction will have transaction fee to be paid in XEM. 

# NEM2

## API
**Q:** Does Catapult has API Key feature to secure REST API?  
**A:** No, it works the same as NIS1 in which you just call the endpoints. No API Key needed.

**Q:** How to manage Access Control List (ACL) offchain?  
**A:** Currently there is no mechanism for this. Generally, frontend interacts with the SDK, SDK interacts with Catapult. Getting information does not require any permission or special parameters.

## Catapult-service-bootstrap
**Q:** I have set up nodes from Catapult-service-bootstrap. It was running fine and how I could not send any transaction to the network via nem2-sdk or CLI. How to fix this?  
**A:** If you had a running network and then it stopped working even if you restarted it repeatedly, this could mean the chain file store and MongoDB are out of sync due to dirty shut down. Perform `./clean-data` and `./clean-all` and start afresh. https://github.com/tech-bureau/catapult-service-bootstrap#known-issues.  

**Q:** I'm trying to install Docker for Windows but the installation failed because it requires Windows 10 Pro or Enterprise 14393 to run. Is it possible to install Docker without Windows 10 Pro or Enterprise?  
**A:** There is a version of Docker where you can run it in Virtualbox with a Ubuntu Distro. Try to install them and read through [Docker’s official guide.](https://docs.docker.com/machine/get-started/ https://docs.docker.com/toolbox/toolbox_install_windows/)
If you’re using Windows 10 Home Edition, you can check out [this guide.](https://medium.freecodecamp.org/how-to-set-up-docker-and-windows-subsystem-for-linux-a-love-story-35c856968991)  

**Q:** I've done `docker-compose up` & when I typed in the terminal `curl localhost:3000/block/1` it gives this error `curl: (7) Failed to connect to localhost port 3000: Connection refused`. How do I fix this error?  
**A:** Connection refused usually means there is no server running. Try `netstat -an | grep -i`. You will get a list. Try `netstat -an`, if there is no row matching the number 3000 then you have to start the server using Docker Compose. Remove the `/data/mongo` lines in the `docker-compose.yml` file. There are two lines that have the `/data/mongo`. Delete both and run docker-compose up again. If the containers are not built properly, run docker-compose with the following flags `docker-compose up --force-recreate --build`.  

**Q:** Error `does not match calculated receipts hash` appears when setting up Catapult-server. What could have caused this?
**A:** This means your network settings vs settings used when running `nemgen` are different.

**Q:** Does `clientPrivateKey` in catapult-rest `userconfig/rest.json` need to be an address with funds? 
**A:** It does not need to be an address with fund. The address is used to uniquely identify a client with the api node.

## Cross-chain Swap
**Q:** How many attempts can be made until the secret proofs and secret lock match?  
**A:** You may attempt as many time as possible before the stipulated time is up. However, if you have the correct secret proof, they shall match at the first attempt.

## Formatting
**Q** Why REST formatting some UInt64 as hex but others as string?
**A** Identifiers do not have a meaning on their own when not encoded. For that reason, we can show them nicely in a shorter form (hex). Doing so, we achieve compatibility with the current endpoint parameters (e.g. /mosaic/<mosaicId (hexa)>).Other values such as supply are easier to read if not encoded (e.g. an amount, a duration). The rule right now is:  
  • quantitative: string  
  • identifier: hex  

## Mosaic
**Q:** Is it possible that the duration of the mosaic is infinite?   
**A:** Yes. `Eternal_Artifact_Duration (0 duration)` is default for mosaic and should not be specified  in the mosaic definition transaction.

## Namespace
**Q:** In a Catapult private deployment, how can we set the Namespace renting price to zero?
**A:** You can try changing the network specific configuration properties. It’s located in `config-network.properties` `rootNamespaceRentalFeePerBlock`, `childNamespaceRentalFee`, `mosaicRentalFee`. You will need to rebuild the server. 

## NEM2-CLI
**Q:** `Failed at the bufferutil@3.0.5 install script` This errors appeared when *npm install --global nem2-cli* was ran. What could be the cause?  
**A:** Install Python version 2.7. Restart the PC to get the system paths updated. 
Download link here: https://www.python.org/downloads/windows/

## Voting System
**Q:** I am using AggreateTransaction function for my voting system so that the transactions of votes to the candidates and the registration of the user's identifier are annouced at the same time. In tnis case, the identifiers and the votes to the candidate can be seen. How to separate these information?  
**A:** You may have a transaction to confirm the registration of the user first with the UI making the user wait for the confirmation of the registration. Create mosaic to be distributed to registered user/voter to only vote once by sending the mosaic to address of the candidate the user/voter wishes to vote for. 

**Q:** Does the user/voter has to use a wallet to vote?  
**A:** No, a wallet is not necessary.

# NEM1

## Running NIS
**Q:** Do you need 10k XEM to run a node?  
**A:** No, you do not need any XEM to run a node. 

**Q:** How to enable the number of hours to keep the hashes of transactions in memory?  
**A:** For your own node, you have to enable TRANSACTION_HASH_LOOKUP and nis.transactionHashRetentionTime = -1 (To keep all the hashes). It should have over 8GB RAM for this setup. Running a node with HISTORICAL_ACCOUNT_DATA at 4GB-8GB could be unstable and get stucked before full synchronization. Historical-data allows you to fetch account state in any point of time. That’s why it requires so much resources. To keep all hashes in memory, it takes a couple hundred MB RAM memory.

**Q:** Does the node synchronise from 0 every time it restarts?  
**A:** The node load from your hard drive when it restarts. Synchronization with the network is done only once. It might take hours for the first time it syncs with the network. You may download database dump `nis5_mainnet.h2-2015k.db.zip` from http://bob.nem.ninja/. After that the next time you restart the node, the synchronization will be relatively faster as it will "loadBlock" into the memory.

**Q:** My NEM node occasionally stops syncing. It then restarts, loads the local data, and resumes synchronization. What is causing this issue and how to solve it?  
**A:** Check the amount of RAM the NIS is given, it might not be sufficient. The minimum amount should be 4GB. Ideally 8GB.   

## Supernodes
**Q:** Is there a record showing the number of supernodes online for the past 12 months?  
**A:** There is not. You may refer to https://supernodes.nem.io/history for the monthly reward pay-out though. 

**Q:** There are months where the reward pay-out for supernodes has increased. Would the reason be lesser nodes are online?  
**A:** Not necessary. There could also be supernodes that were online but yet to upgrade to the new requirements. 

**Q:** What are the technical requirements for running a supernode?  
**A:** If you have 3 million XEMs, a server with 8GB of RAM and an average CPU should suffice. For storage, 20GB should be enough.

## Timestamp
**Q:** I got an error saying the timestamp is too far in the future. How to fix it?  
**A:** Your system time is not synchronised with the network time. You may synchronised it using SDK. 

**Q:** How do we synchronize the time of the transaction?  
**A:** You may synchronised it using SDK. 

**Q:** Should I use NEM Network time for transaction timestamp, even though I’m hosting my own node?  
**A:** Even if you host your own node, you should use NEM network time for the transaction timestamp. The NEM network time is not guaranteed to be in sync with UTC time, it is only guaranteed that all other nodes use that time to validate the timestamps.

**Q:** What goes into the timestamp and deadline?   
**A:** `Timestamp` is the number of seconds passed from the beginning of NEM epoch. `Deadline` is the time when transaction will be gone from unconfirmed, if it is not confirm. 

## Version
**Q:** What are transaction type and version fields?  
**A:** `Version` is just version of transaction structure. `Type` is the code which tells us how transaction fields should be interpreted: simple transfers, multi sig, importance transfer etc.

## Blocksize
**Q:** What is NEM’s current blockchain size?  
**A:** As of 28 February 2019, it's 2.8GB.

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
`1. Check if the deposit transaction is a multisig transaction.`  
`2. If it is, extract the inner trasaction.`    
`3. Within the transaction (if is not a multisig transaction) or inner transaction, check if there is a "mosaic" array or if the "mosaic" array is empty.`    
`4. If there isn't a "mosaic" array or if the "mosaic" array is emp ty, the deposit is XEM and the "amount" field equals to the amount of XEM deposited in term of micro-XEM (6 divisibles).`   
`5. Else, the "amount" equals to a multiplier for the mosaic "quantity".`

## Multisignature Transactions
**Q:** For multisig transaction, which hash should I use to retrieve information from NEM explorer?    
**A:** There are 3 types of hash in a multisig transaction. "innerHash" is for the inner transaction and only available in multisig transaction. "hash" is the transaction hash. "otherHash" is for the corresponding multisig transaction that related to the inner transaction. Use "hash" to look up for information from NEM explorer. 

**Q:** Could there be instances where M will be equal to N in the Multisig account?  
**A:** Yes. That could be set. However, N will always be <= to M. In the instance where M=N, to delete a cosignatory, `M=N-1` applies.

## Query of transaction history
**Q:** Why I can't retrieve history of transactions from local node?  
**A:** Default for hash retention is 36 hours `nis.transactionHashRetentionTime = 36`. To retain all history of transactions, change the configuration to `-1` in `config.properties`. nis.transactionHashRetentionTime for supernode is set to -1. 

**Q:** Is it possible to get JSON data of a transaction hash?  
**A:** : Yes, using this API endpoint:
`/transaction/get?hash=<insert you hash here>`

**Q:** How to get all transactions in a block?  
**A:** Refer to https://nemproject.github.io/#getting-part-of-a-chain 4.2.2, use the API path `/local/chain/blocks-after` to do that. This API will only works in localhost. 

**Q:** Is there any testnet node where search by hash is working?  
**A:** Try 95.216.73.245. The full list is available [here.](http://bob.nem.ninja:8765/#/nodes/)

## SSL_PROTOCOL_ERROR/ https
**Q:** Transactions I made on localhost worked well. However, I hit  https://23.228.67.85:7890/transaction/announce `ERR_SSL_PROTOCOL_ERROR` when it is hosted online.  
**A:** Majority of the nodes listen on http ports while you are calling with https. However, you can have SSL in your site and call http nodes in backend. Only a handful NEM nodes listen to https. It’s usually on 7891 instead of 7890.  
You can use this https://nistest.opening-line.jp:7891

**Q:** Is there a way to make a rquest to the Catapult node with https?  
**A:** There are no https nodes available. You may use a proxy. 

## Transaction anncouncement 
**Q:** How to make sure 2 transactions that are broadcasted together are included in the block or if one transaction fails, the other would be dropped?  
**A:** Announcing transaction doesn't guarantee it will be included in a block. Once annouced, it cannot be called back. Transaction will be either be included in a block or dropped. However, in NEM2, aggregate transacton will have all the transactions aggregated included in a block or dropped altogether. Simply add a handler for https, proxying to the said node. 

**Q:** The following result was returned after a transaction was annouced. What does it mean?  
`{ `  
       `"type": 1, `  
       `"code": 0,`   
       `"message": "neutral" `  
`}`    
**A:** Referring to https://nemproject.github.io/#nemRequestResult 9.30, neutral result. A typical example would be that a node validates an incoming transaction and realizes that it already knows about the transaction. In this case it is neither a success (meaning the node has a new transaction) nor a failure (because the transaction itself is valid). However, this doesn't mean the transaction will definately be included in a block. 

**Q:** Are transaction hashes always in SHA3-256 and 64-characters?  
**A:** Yes.

## FAILUTRE_INSUFFICIENT-BALANCE
**Q:** I have a testnet address with verified balance of 1000 XEM. My Mosaic levy is absolute of 5 XEM. I tried to send 1 mosaic to another address but got this error: FAILURE_INSUFFICIENT_BALANCE. What could have happened?   
**A:** There could be only 0.001 XEM in your testnet address. When you get the account balance from an endpoint, it always show in microbalances. As XEM has divisibility of 6, 1000 microXEM means 0.001 XEM. Same goes to mosaic. It will always show in micro-mosaic (depends on its divisibility).

## Vested XEM
**Q:** Can the vested XEM be transferred?  
**A:** Everytime when XEM are being transferred, it will be a combination of vested and unvested XEM. However, it will be all unvested to the recipient. 

**Q:** How long it takes for me to have 10k vested XEM, if I have 20k XEM in total?  
**A:** You use this calculator https://nem-tools.com/#/harvesting/calculator.

## Mosaic
**Q:** What would happen to the Mosaics if the Namespace it ties to didn't get renewed?  
**A:** After the Namespace on its 12th month of rental, the account owns the Namespace can renew it and continue with another year of rental, together with the Mosaics attached to it.   After the 12th month, the Namespace and Mosaics will not be shown, however, the creator of the Namespace can still rent back the Namespace, before the 13th month ends, together with the Mosaics attached to it. When the creator account rent back the Namespace, the Namespace and the Mosaics will be shown again. Only the creator of the Namespace can rent back that particuar Namespace during the 13th month.    
After the 13th month, the Namespace will be available for any account to rent. The mosaics, however, will be gone forever. 

**Q:** How to pay the fee for an expiring mosaic that I don’t own?  
**A:** Only creator can pay for expiring namespace and mosaic.

## API
**Q:** How to query for transactions of an account for more than 25 transactions per page?  
**A:** E.g. http://18.224.152.252:7890/account/transfers/incoming?address=TAR4ZUESJDG2IWJUVVV3UUEECSB2CV5B6UIO3GEM&pageSize=1000  

**Q:** How many API is needed to transfer a coin?  
**A:** You only need just one call i.e. [`requestAnnounce`](https://nemproject.github.io/#requestAnnounce) to do so. Before you can send a transaction, you must serialize it and you may use the SDK for that. Then sign the transaction with the private kay, and send the transaction payload to any node.

**Q:** Is there any API available to get the current USD/XEM price?  
**A:** The Coinmarketcap API offers such feature. Alternatively, you can try using the Java NEM-SDK via nem.com.requests.market.xem.

**Q:** How to get address from public key, e.g. in `transaction.signer.address.plain() == [public address here]`?  
**A:** If you are using some wrapper, it should be available in it because address can be calculated from public key. Alternatively, you can also use an API call for the `/account/get/from-public-key`. You can refer to the documentation at https://nemproject.github.io.
Example:
http://hugealice.nem.ninja:7890/account/get/from-public-key?publicKey=f9bd190dd0c364261f5c8a74870cc7f7374e631352293c62ecc437657e5de2cd

## Harvesting XEM
**Q:** Is it possible to mine XEM?  
**A:** XEM can't be minded. All `8,999,999,999` XEMs were created and distributed on the Nemesis block (first block). What you can do is to `harvest` XEM. You need minimum `10k XEM vested` and `importance score > 0` to start harvesting and it will let you receive fees in case you hit a block.  

**Q:** How long does it take for remote status to activate after sending the importance transaction?  
**A:** Around 6 hours.

## CLI
**Q:** How to create a new address/keys via command line by Python or Javascript?  
**A:** You can check out [QuantumMechanics' NEM-SDK](https://github.com/QuantumMechanics/NEM-sdk), you can generate an account using Javascript. 

## Levy
**Q:** Someone sent me a mosaic with a constant 10 XEM levy on it. How do I remove this?  
**A:** You can remove it without paying 10xem levy using [this tool.](http://46.101.212.139:8088/spam/remover.html)  
1. First provide your address and this faucet will send you another mosaic which has levy in pontifier mosaic.   
2. Next send back to address in instruction received from faucet mosaic (please refer to screenshot in the instuction).   
Of course you can leave this mosaic as is in your account.

## Websocket
**Q:** When using the Javascript NEM-SDK, after creating a connection with `nem.com.websockets.connector.create`, how to close the connection?  
**A:** Use `nem.com.web.sockets.connector.close`.
            
## NEM Wallet
**Q:** Can NEM-based tokens (mosaics) be withdrawn from NEM Wallet?  
**A:** Not from NEM mobile wallet. You can do that from NEM desktop wallet. Download desktop NEM Wallet from nem.io/downloads, open the "start.html" files in the folder, select "SIGN UP" on the top right, choose "Private key wallet", follow instruction and input the private key from your mobile wallet. You should be able to see the mosaics available in your account and manage them from there.

**Q:** How to generate a new account other than generating through a NEM Wallet?  
**A:** If you are running your own local NIS (NEM Infrastructure Server) node, you can generate new account using the endpoint: http://localhost:7890/account/generate. Else you may use the NEM SDK (example for Testnet):  
`var nem = require('nem-sdk').default;`  
`var rBytes = nem.crypto.nacl.randomBytes(32);`  
`var privateKey = nem.utils.convert.ua2hex(rBytes);`  
`var keyPair = nem.crypto.keyPair.create(privateKey);`  
`var publicKey = keyPair.publicKey.toString();`  
`var address = nem.model.address.toAddress(publicKey, -104);`  

**Q:** How to update the NEM Wallet from version 2.1 to 2.4?  
**A:** First export `.wlt` file from the old version. Next download and extract new wallet and import `.wlt` file (from old wallet) using Import option. The export option is visible when you click Account in top right corner.  

**Q:** Is it possible for the Apostille certificate to include our own company logo and other details, or is it allowable to edit the certificate and put our company logo and details without having any legal/copyright issue?  
**A:** It's open source so you can modify. To modify logo and description will require some small modifications in code, as it's not editable via interface right now.
Here are the [license conditions](https://github.com/NemProject/NanoWallet/blob/2.0/LICENSE) for NEM Wallet. 

**Q:** I still could not connect to a node even if I have switched to another node, multiple times. What could be the reason?  
**A:** You could be in an office building or a university campus where the internet provider has blocked the port (7890) NEM is using. Check your firewall settings or use a VPN which will allow you to use the NEM Wallet.

**Q:** What should I do if harvesting of my NEM Wallet becomes ``INACTIVE``?   
**A:** After login to your NEM Wallet, selet `Service` --> Under "Delegated Harvesting", select `Manage delegated account` --> Select `Start/Stop delegated harvesting` --> Select a node with free slot --> type your password.

**Q:** I’ve downloaded the NEM wallet with Trezor support 2.4.2 but it just shows a blank page in the browser.  
**A:** Check if you have enabled third party cookies in browser. Click here for [instructions for Chrome.](https://support.cloudhq.net/how-to-enable-3rd-party-cookies-in-google-chrome-browser/)  

**Q:** Is there a way to detect the IP Address where a certain wallet was logged in?  
**A:** No, if you have control over the node used, it should be possible but this is not data logged in any way.

**Q:** When depositing XEM to NEM Wallet from exchanges, is a message required?  
**A:** No, when you are sending transaction to NEM Wallet, message is not required.  

**Q:** Is there a way to create sub accounts?  
**A:** Yes. In NEM Wallet, click `Account` on top right corner. 

**Q:** Do the main and sub wallet hold different private keys?  
**A:** Yes. All have different private keys. Private key for subwallet is derived from primary account private key and password.

**Q:** Is NCC still usable?  
**A:** NCC is still working but it’s not maintained. For example, in NCC you will have hardcoded old fees structure. It is better to use [NEM Wallet.](https://nem.io/downloads/)
