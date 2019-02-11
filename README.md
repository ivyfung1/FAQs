This FAQs (Frequent Asked Questions) are compiled from Telegram chatgroup NEM::Helpdesk and NEM::Projects, and questions I received when I was conducting trainins for public, colleges and universities. The FAQs will be updated from time to time.

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

'var nem = require('nem-sdk').default;
var rBytes = nem.crypto.nacl.randomBytes(32);
var privateKey = nem.utils.convert.ua2hex(rBytes);
var keyPair = nem.crypto.keyPair.create(privateKey);
var publicKey = keyPair.publicKey.toString();
var address = nem.model.address.toAddress(publicKey, -104);'


## Timestamp
**Q:** I got an error saying the timestamp is too far in the future. How to fix it?
**A:** Your system time is not synchronised with the network time. You may synchronised it using SDK. 

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
' 1. Check if the deposit transaction is a multisig transaction.
2. If it is, extract the inner trasaction. 
3. Within the transaction (if is not a multisig transaction) or inner transaction, check if there is a "mosaic" array or if the "mosaic" array is empty.
4. If there isn't a "mosaic" array or if the "mosaic" array is empty, the deposit is XEM and the "amount" field equals to the amount of XEM deposited in term of micro-XEM (6 divisibles).
5. Else, the "amount" equals to a multiplier for the mosaic "quantity".'

