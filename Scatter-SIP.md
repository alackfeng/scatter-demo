


###### connnect
`````
42/scatter,["pair",{"data":{"appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","origin":"192.168.0.238","passthrough":false},"plugin":"scatter-demo"}]

42/scatter,["paired",true]


`````

###### getIdentity allows your application to request permission to interact with a user's Scatter and be provided with an Identity of the user's choosing. You can equate requesting an Identity to signing in with Google or Facebook without a centralized server.

`````

42/scatter,["api",{"data":{"type":"getOrRequestIdentity","payload":{"fields":{"accounts":[{"blockchain":"eos","host":"mainnet.eoscanada.com","port":443,"protocol":"https","chainId":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906"}]},"origin":"192.168.0.238"},"id":"149242221224461971781276319441872222142281751471331287319886140","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"587692414110791106918217622421725420224122216267163114194230222","nextNonce":"567c6b126c64c51a512da1b9a9cc623d04cd884faf75c0f06fa1e2de8e9704fb"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"149242221224461971781276319441872222142281751471331287319886140","result":{"hash":"2f6c45d4f67354c8a4896f04b0651ceafa08b2c86658b54a0fc095f9662691f1","publicKey":"EOS8S3tdsSeTyCe2NBgkKcHgv9KYw2xVwLFDGxH1ebVhLwMnGkDxY","name":"MyFirstIdentity","kyc":false,"accounts":[{"name":"coinfid55555","authority":"active","publicKey":"EOS7cZMPEEo3EMHWkRJ7zHv3dQNvZDUHi71tHitNPqht8zwppdFXZ","blockchain":"eos","chainId":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906","isHardware":false}]}}]



42/scatter,["api",{"data":{"type":"identityFromPermissions","payload":{"origin":"192.168.1.103"},"id":"1541992211131891564222017190227485785122234108252193239231123200102","appkey":"b0b862450f463099e98e39afae11e44919b9015cdafc7d2b09d51ba142646f51","nonce":"1974562248039159934512854106191144616925477821681491804442","nextNonce":"28cd6fd5b4f1c512da10390250bd158c15dc57dee2a7596c1067384a1c071dfd"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"1541992211131891564222017190227485785122234108252193239231123200102","result":{"hash":"2f6c45d4f67354c8a4896f04b0651ceafa08b2c86658b54a0fc095f9662691f1","publicKey":"EOS8S3tdsSeTyCe2NBgkKcHgv9KYw2xVwLFDGxH1ebVhLwMnGkDxY","name":"MyFirstIdentity","kyc":false,"accounts":[{"name":"coinfid55555","authority":"active","publicKey":"EOS7cZMPEEo3EMHWkRJ7zHv3dQNvZDUHi71tHitNPqht8zwppdFXZ","blockchain":"eos","chainId":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906","isHardware":false}]}}]


`````


###### forgetIdentity let you sign your user out of your application. They can then sign in with another Identity if they choose to.

`````
42/scatter,["api",{"data":{"type":"forgetIdentity","payload":{"origin":"192.168.0.238"},"id":"13394185987921327127213255132144105717327159158223190205225195166","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"244160219234247651781865518606873239250641861821517020918213998","nextNonce":"7e691a400d7bba508c18278185f8883ce801060a911d145b9f4e20f72e87393c"},"plugin":"scatter-demo"}]


42/scatter,["api",{"id":"13394185987921327127213255132144105717327159158223190205225195166","result":true}]

`````


###### suggestNetwork can be useful if you are using a network that isn't a Mainnet for your application, such as a test network, a side chain or a fork.

`````
42/scatter,["api",{"data":{"type":"requestAddNetwork","payload":{"network":{"blockchain":"eos","host":"mainnet.eoscanada.com","port":443,"protocol":"https","chainId":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906"},"origin":"192.168.0.238"},"id":"1321641707920025547179238194104108253968622710123813624225411971176","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"61831962212291421521014359915312395240615614018918711218022992","nextNonce":"4042cdf2b489cac43187ce2a77ccb943c2a50ad48bea00952c864d67b9438a94"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"1321641707920025547179238194104108253968622710123813624225411971176","result":true}]

`````

###### getPublicKey is part of the onboarding tools provided by Scatter. By requesting a public key from a user they are given the chance to either give you an existing public key, or create one on the fly which is then store within their Scatter.

`````
42/scatter,["api",{"data":{"type":"getPublicKey","payload":{"blockchain":"eos","origin":"192.168.0.238"},"id":"292347240106194137402157913217711441772291261462455321267120","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"221521922161661663832221196427821362101881019810123421522024393","nextNonce":"fbc41633acdd1ef6582e9e71ed82afeb5dc963f862243735407fa1add37c8411"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"292347240106194137402157913217711441772291261462455321267120","result":"EOS5zwpo5uNUGsjbGHDM7vGJstgo357WDhn5cL1CxXtDWpLHEetce"}]

`````

###### linkAccount is part of the onboarding tools provided by Scatter and in most cases goes hand-in-hand with getPublicKey. Your application can prompt the user to bind an account and network to a public key which allows them to use it to interact with your application when using getIdentity

`````
42/scatter,["api",{"data":{"type":"linkAccount","payload":{"account":{"name":"coinfid55555","authority":"active","publicKey":"EOS7cZMPEEo3EMHWkRJ7zHv3dQNvZDUHi71tHitNPqht8zwppdFXZ"},"network":{"blockchain":"eos","host":"mainnet.eoscanada.com","port":443,"protocol":"https","chainId":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906"},"origin":"192.168.0.238"},"id":"661532414374918821256163156292314616713816123671372194137197","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"539147551782031451429614626208120735223719014916610817115920711","nextNonce":"67e14e802e74e691e1b1978ce7e51641e32bd60062b5f3a19a46075f784f7721"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"661532414374918821256163156292314616713816123671372194137197","result":true}]

`````

###### getArbitrarySignature lets you sign arbitrary data with a given public key's private key.

`````

42/scatter,["api",{"data":{"type":"requestArbitrarySignature","payload":{"publicKey":"EOS8S3tdsSeTyCe2NBgkKcHgv9KYw2xVwLFDGxH1ebVhLwMnGkDxY","data":"tokenpocket","origin":"192.168.0.238"},"id":"252642074423518120919877238852421141311510524716818123493243856","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"106193231199124378162401252172351709919233109863136102253114226","nextNonce":"b0a4be0a637679dd7a954c848d26a528a20cf16016507b1a1f47354310d5889b"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"252642074423518120919877238852421141311510524716818123493243856","result":"SIG_K1_KUtE54b88SQppgSGvyQM44ejjXyY6HjJM7i1uEDGFJU4WyJTCEht4bMW79Nw9jiEpXyeMnqruWnWcp2bnuEwCoDzkTv4Dg"}]

`````



###### Request Transfer
This API route sends a transfer request to the user. It functions as a type of "Donate" button which bypasses the need for Login Authentication due to it never returning results. 

If the amount is set to 0, the user will be able to select the amount. If it is greater than 0 then it is a fixed amount the user must pay.

`````

42/scatter,["api",{"data":{"type":"requestTransfer","payload":{"network":{"blockchain":"eos","host":"mainnet.eoscanada.com","port":443,"protocol":"https","chainId":"aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906"},"to":"whatsupto123","amount":"0.0001","options":{"contract":"eosio.token","symbol":"EOS","memo":"","decimals":4},"origin":"192.168.0.238"},"id":"197219128145249224175184942056966173391481461156861146253212195158","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"7262218168199201197672521831842291612419818580237235986535438","nextNonce":"196bd01dc0ab10a39e93469787b30d174494d658ff0b4e249ae9e4edfd84c4c3"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"197219128145249224175184942056966173391481461156861146253212195158","result":{"broadcast":true,"transaction":{"compression":"none","transaction":{"expiration":"2019-02-11T07:13:40","ref_block_num":37666,"ref_block_prefix":3487995166,"max_net_usage_words":0,"max_cpu_usage_ms":0,"delay_sec":0,"context_free_actions":[],"actions":[{"account":"eosio.token","name":"transfer","authorization":[{"actor":"coinfid55555","permission":"active"}],"data":"504a2925b9351d453044a0b96a9c4de3010000000000000004454f530000000000"}],"transaction_extensions":[]},"signatures":["SIG_K1_KA4BnexkQXaAfkHYGYppt7kRhsaeS4JjFTxnFxZhTXXbmu2WWebS8P9uhL7SZUVsXyDE6tUZB2En4JSXJjPzLQVzH4QZiV"]},"transaction_id":"1537c72aa97780003420630169fa305bca1785f6440cd99b35c9c86a9ead7113","processed":{"id":"1537c72aa97780003420630169fa305bca1785f6440cd99b35c9c86a9ead7113","block_num":42177656,"block_time":"2019-02-11T07:12:44.500","producer_block_id":null,"receipt":{"status":"executed","cpu_usage_us":297,"net_usage_words":16},"elapsed":297,"net_usage":128,"scheduled":false,"action_traces":[{"receipt":{"receiver":"eosio.token","act_digest":"5fa181a78ea9974d779e77c9e29bcd6038b004325daf01c3eef32c1b3b2c50ad","global_sequence":"4947401029","recv_sequence":813803224,"auth_sequence":[["coinfid55555",130]],"code_sequence":2,"abi_sequence":2},"act":{"account":"eosio.token","name":"transfer","authorization":[{"actor":"coinfid55555","permission":"active"}],"data":{"from":"coinfid55555","to":"whatsupto123","quantity":"0.0001 EOS","memo":""},"hex_data":"504a2925b9351d453044a0b96a9c4de3010000000000000004454f530000000000"},"context_free":false,"elapsed":109,"console":"","trx_id":"1537c72aa97780003420630169fa305bca1785f6440cd99b35c9c86a9ead7113","block_num":42177656,"block_time":"2019-02-11T07:12:44.500","producer_block_id":null,"account_ram_deltas":[],"except":null,"inline_traces":[{"receipt":{"receiver":"coinfid55555","act_digest":"5fa181a78ea9974d779e77c9e29bcd6038b004325daf01c3eef32c1b3b2c50ad","global_sequence":"4947401030","recv_sequence":175,"auth_sequence":[["coinfid55555",131]],"code_sequence":2,"abi_sequence":2},"act":{"account":"eosio.token","name":"transfer","authorization":[{"actor":"coinfid55555","permission":"active"}],"data":{"from":"coinfid55555","to":"whatsupto123","quantity":"0.0001 EOS","memo":""},"hex_data":"504a2925b9351d453044a0b96a9c4de3010000000000000004454f530000000000"},"context_free":false,"elapsed":3,"console":"","trx_id":"1537c72aa97780003420630169fa305bca1785f6440cd99b35c9c86a9ead7113","block_num":42177656,"block_time":"2019-02-11T07:12:44.500","producer_block_id":null,"account_ram_deltas":[],"except":null,"inline_traces":[]},{"receipt":{"receiver":"whatsupto123","act_digest":"5fa181a78ea9974d779e77c9e29bcd6038b004325daf01c3eef32c1b3b2c50ad","global_sequence":"4947401031","recv_sequence":19,"auth_sequence":[["coinfid55555",132]],"code_sequence":2,"abi_sequence":2},"act":{"account":"eosio.token","name":"transfer","authorization":[{"actor":"coinfid55555","permission":"active"}],"data":{"from":"coinfid55555","to":"whatsupto123","quantity":"0.0001 EOS","memo":""},"hex_data":"504a2925b9351d453044a0b96a9c4de3010000000000000004454f530000000000"},"context_free":false,"elapsed":5,"console":"","trx_id":"1537c72aa97780003420630169fa305bca1785f6440cd99b35c9c86a9ead7113","block_num":42177656,"block_time":"2019-02-11T07:12:44.500","producer_block_id":null,"account_ram_deltas":[],"except":null,"inline_traces":[]}]}],"except":null}}}]

`````



###### getVersion This API route just fetches the version of Scatter the user is using.

`````
42/scatter,["api",{"data":{"type":"getVersion","payload":{"origin":"192.168.0.238"},"id":"129828211333125165148183204994522381088021410210525020013023344","appkey":"1efa5c9df8cba637fd543d0389aba98d3cca7be4fb7fb4fff2c06dfb08395e46","nonce":"1843862421615115422712616810849572557412851719187112212145221","nextNonce":"4d759e91fafa82dcf0120fcedcc9e642527f26a92a0a51715759ee97a9144f85"},"plugin":"scatter-demo"}]

42/scatter,["api",{"id":"129828211333125165148183204994522381088021410210525020013023344","result":"10.1.2"}]
`````
