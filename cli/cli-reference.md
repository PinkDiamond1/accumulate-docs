---
description: All the commands available via the Command Line Tool are documented below
---

# CLI reference

## **Lite Token Account/Lite Identity Creation**

This command will generate a new account URL for you.

**Syntax**

```
./accumulate account generate
```

**Command**

```
./accumulate account generate
```

**The above command will return an output similar to the following:**

```shell-session
lite identity        :       0143b52490530b90eef9b1a2405e322c6badc1e90e200c56
lite token account    :       acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
public key      :       03c633851507f63ef8517dc934075f2abe2f8c3b3053b5a49a477e8513e01955
key type        :       ed25519
```

### **Account List**

This command will get the list of accounts.

**Command**

```
./accumulate account list
```

**The above command will return an output similar to the following:**

```
key name : 001846c0a1590675fd0ad816ab4873387ef127cd9b307c24 
lite account : acc://001846c0a1590675fd0ad816ab4873387ef127cd9b307c24/ACME 
public key : 3615e429b89fa3d6b636412d7a17b13cc321c14b2f2e5bf520868c9617401845 
key type : legacyED25519 
key name : 003df7b8b865b3eda520dbb224eaf7536ee98cc25874ce54 
lite account : acc://003df7b8b865b3eda520dbb224eaf7536ee98cc25874ce54/ACME 
public key : 45090e7cfa0edd52db7181fa0a30f1da8d2c0b1bdc6b4847de75fe922ad9e755 
key type : ed25519
```

### **Faucet Transaction**

The Test Faucet can be used to add test ACME tokens to a Lite Token Account. The Sponsor of the transaction is the Test Faucet address that holds Test ACME. ([acc://7117c50f04f1254d56b704dc05298912deeb25dbc1d26ef6/ACME](https://beta.explorer.accumulatenetwork.io/acc/7117c50f04f1254d56b704dc05298912deeb25dbc1d26ef6/ACME)):

**Syntax**

```
accumulate faucet [url] Get tokens from faucet to address
```

**Command**

```
./accumulate faucet acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
```

The above command will return an output similar to the following:

```shell-session
Transaction Hash        : a0018d18c558c36f3f639fa1a64e2e9c47cc705fdf0d3f65a8ec8f0e0bd0f328
Signature 0 Hash        : 78d521b36691c46216a66d6648dd620a9f6ec312a24b3b0f29a9889887f4953d
Simple Hash             : ab039db9714e8a30b0443054dea78a36e754ead8ca50a6ab6e50adc62ef3d801
Error code              : ok
Result                  : 
```

_**The Transaction Hash is a hash of the transaction without signatures and the Signature Hash is the Transaction Hash with the Signature appended to it and hashed.**_

### **TX Get Transaction Hash (TXID)**

To query a transaction by the transaction ID a tx get command is required

**Syntax**

```
accumulate tx get [txid] Get token transaction by txid
```

**Command**

```
accumulate tx get a0018d18c558c36f3f639fa1a64e2e9c47cc705fdf0d3f65a8ec8f0e0bd0f328
```

The above command will return an output similar to the following:

```
(type): Acme Faucet
Transaction Type: acme Faucet
Url: acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
- Synthetic Transaction 0 : 8eb0088ec37e2fca37fd915aa2348e03b30c77e2b2abdcbc4ee7b94e6c532f2f
```

### **TX Get Signature Hash**

To query the transaction hash from the Faucet account transaction:

**Syntax**

```
accumulate tx get [txid] Get token transaction by txid
```

**Command**

```
./accumulate tx get 78d521b36691c46216a66d6648dd620a9f6ec312a24b3b0f29a9889887f4953d
```

The above command will return an output similar to the following:

```
(type): Acme Faucet
Transaction Type: acme Faucet
Url: acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
- Synthetic Transaction 0 : 8eb0088ec37e2fca37fd915aa2348e03b30c77e2b2abdcbc4ee7b
94e6c532f2f
```

### **Synthetic TX Get**

To query the synthetic transaction from the Faucet Account transaction

**Syntax**

```
accumulate tx get [txid] Get token transaction by txid
```

**Command**

```
./accumulate tx get 8eb0088ec37e2fca37fd915aa2348e03b30c77e2b2abdcbc4ee7b94e6c532f2f
```

The above command will return an output similar to the following:

```
Receive 2000000.00000000 ACME to acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME (cause: A0018D18C558C36F3F639FA1A64E2E9C47CC705FDF0D3F65A8EC8F0E0BD0F328)
---
- Transaction : 8eb0088ec37e2fca37fd915aa2348e03b30c77e2b2abdcbc4ee7b94e6c532f2f
- Signer Url : acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
- Signatures :
- Signer : acc://bvn-BVN0/validators/1 (keyPage)
- : synthetic
- : 739d02db90d8f4a979241d37aab8de104f7d967cfc29611e8664afb70006aa4e0b6d728c9d01a8481704e7a3a0b17ce15de6c7744d82508e9102ac3572cbdf0e (sig)
- : b4449beb71f752736e8223fae4a407037e3016e7e91d5b2dc60e87f5b2978cc4 (key hash)
- : receipt
- Signatures :
- Signer : acc://dn/validators/1 (unknownSigner)
- : receipt
```

### **Get Token Balance**

The get token command will query the balance to check the token balance of a Lite Token Account. The Token URL in the output specifies the type of Token.

**Syntax**

```
accumulate get [url] Get data by Accumulate URL
```

**Command**

```
./accumulate get acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
```

The above command will return an output similar to the following:

```
Account Url : acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME
Token Url : acc://ACME
Balance : 2000000.00000000 ACME
```

### **Key**

A named key can be generated using the key generating function. This will also output the public key's name and key type. Unless specified otherwise, this will create an ed25519 key. If you are creating an ADI DO NOT use a key other than an ed25519 key. Support for this will be added in the future.

**Syntax**

```
./accumulate key generate [key name]
```

**Command**

```
./accumulate key generate keytest
```

The above command will return an output similar to the following:

```
name : keytest
lite account : acc://601b40a84a69f216173a457c44de5b942bf5aec62a7003ce/ACME
public key : 1ac021a5d6a1e457102019d5fd00cc04d3e9783a745905761d3fab96e9598c57
key type : ed25519
```

### **Bitcoin**

This command will sign an Accumulate transaction using the `Bitcoin` signature algorithm

**Syntax**

```
./accumulate key generate --sigtype btc [keyname]
```

**Command**

```
./accumulate key generate --sigtype btc testbtc
```

The above command will return an output similar to the following:

```
name : testbtc
lite account : acc://321ec96337292b2a34b6b5c8c62f54f1d198465b0a00f35a/ACME
public key : 0396adeb7869b780606a8fe1218ebfb9c71e7e91ca72b1d95210717c3ed5f4dfd8
key type : btc
```

### **Bitcoin Legacy**

This command will sign an Accumulate transaction using the `Bitcoin` signature algorithm

**Syntax**

```
./accumulate key generate --sigtype btclegacy [keyname]
```

**Command**

```
./accumulate key generate --sigtype btclegacy testbtclegacy
```

The above command will return an output similar to the following:

```
name : testbtclegacy
lite account : acc://95b9e649f8853e40c59aea635ef883100f014b85d57b75a6/ACME
public key : 040ea7496cd6f50c77230d89b9c9ca60bca1d078b06e0efba9c5f3068f8668d229a38fdb71105cb4beffe66958c9b46bec940296346c494a65263f1330c4340755
key type : btclegacy
```

### **Ethereum**

This command will sign an Accumulate transaction using the `Ethereum` signature algorithm

**Syntax**

```
/accumulate key generate --sigtype eth [keyname]
```

**Command**

```
./accumulate key generate --sigtype eth testeth
```

The above command will return an output similar to the following:

```
name : testeth
lite account : acc://388acd64ebbabbf89f0c2b250fb181ef5dff5122b1448c87/ACME
public key : 041901c4486b91f82d16281d84031bd25baf2d61703a3c4caade2f5a844a6f73f2f1e2f80f995fa9db6ed794234eb5efdd44efad81a4b2bf6e14319bd74b55d588
key type : eth
```

### **Factom (RCD1)**

This command will sign an Accumulate transaction using the `Factom` signature algorithm

**Syntax**

```
./accumulate key generate --sigtype RCD1 [keyname]
```

**Command**

```
./accumulate key generate --sigtype RCD1 testRCD1
```

The above command will return an output similar to the following:

```
name : testRCD1
lite account : acc://6a3956d856638d58757e0a47f24fa112876e664ffa322fa2/ACME
public key : 9f3d2d2604d8e50453f59d379c25c0fc5220d512a786f3c419947e6050e758a6
key type : rcd1
```

### **Key Import Mnemonic**

This command imports the key using the mnemonic phrase

**Syntax**

```
accumulate key import mnemonic [mnemonic phrase...] Import the mnemonic phrase used to generate keys in the wallet
```

**Command**

```
./accumulate key import mnemonic decide trap aisle raise above wool excite funny tuna body choice stereo
```

The above command will return an output similar to the following:

```
mnemonic import successful
```

### **Key Import Factoid**

This command imports the key using the mnemonic

**Syntax**

```
accumulate key import factoid [factoid private address] Import a factoid private address
```

**Command**

```
./accumulate key import factoid Fs23yok1z8ZsHtoMsWc1oMy76sKRgHF3jN6HLjoMQ9iMxYrnnkiL
```

The above command will return an output similar to the following:

```
name : FA2MSMBiyHmBLP1LDYAVWGRkkLpr64mMMi7N11hKchT6bAi926XW
lite account : acc://32c484ebfd344810353cb273d538166f3b4a9391486343d5/ACME
public key : aba7ecaa24874d13f272b87b7924bc4613a82904a98ef399f4b6d9a29e46a381
key type : rcd1
```

### **Key Import Lite**

***

**Syntax**

```
accumulate key import lite [private key hex] Import a key as an anonymous address
```

**Command**

```
./accumulate key import lite ****************************
```

The above command will return an output similar to the following:

```
name : 4111d56848824a2d74ee93e2c42091f7019a87c7649b48fe
lite account : acc://4111d56848824a2d74ee93e2c42091f7019a87c7649b48fe/ACME
public key : 76324e43a382e6ff6a9724f8dae137b93f5d5a61a3eb9d6e5213739b656c5d44
key type : ed25519
```

### **Key Export All**

**Syntax**

```
accumulate key export all  
```

**Command**

```
./accumulate key export all  
```

The above command will return an output similar to the following:

```
{
  keys: [
    {
      name: 'f194af0eeb01ca0ffcf05918aa2328bb11c44b9d27d80ff4',
      privateKey: '9272c3f03a182281efa8baf743fe4172216fd90e60c47c1cbe47bd36b51b08d90026e3420379dcc7f7eeeb1c61132ac4a1ecad95843bd255eb1b762e8c5e84b4',
      publicKey: '0026e3420379dcc7f7eeeb1c61132ac4a1ecad95843bd255eb1b762e8c5e84b4',
      keyInfo: [Object],
      keyHash: 'f194af0eeb01ca0ffcf05918aa2328bb11c44b9d434887c9f1319c562af0d57e'
    },
    {
      name: 'e4df9ccaab3e644788eac7361a8cc93caff5e9c2021eda10',
      privateKey: '23834430ffa16cfe52ed79448259e058e21728c700695e6b4583f6843adbf614007486895d9cf3b5a9d945f615d1922bbd2e696a1b5dedcdeaa04e6aa2bdab14',
      publicKey: '007486895d9cf3b5a9d945f615d1922bbd2e696a1b5dedcdeaa04e6aa2bdab14',
      keyInfo: [Object],
      keyHash: 'e4df9ccaab3e644788eac7361a8cc93caff5e9c2c28ac65ee5340f8f34af8787'
    },
    ... 1158 more items
  ]
}
```

### **Key Export Private**

**Syntax**

```
accumulate key export private [key name] export the private key by key name
```

**Command**

```
./accumulate key export private [key/label name]
```

The above command will return an output similar to the following:

```
./accumulate key export private dnkey
Password: ********
 Name        | dnkey
 Private Key | 9a94cb8f45f6cbd4d421c07b491d9067dee6c9a72c73f923f90ff188c1d37030c1b5e95298e6817ac62cfbe792240025e9ce9c9644913a5e3c27c10516961721
 Public Key  | c1b5e95298e6817ac62cfbe792240025e9ce9c9644913a5e3c27c10516961721
 Key Hash    | 4b3684fb8fa25fa279d4b6fb6c4681999b92446eb5fca4a508f3a12a9c430f2e
 Key Type    | ed25519
 Derivation  | m/44'/281'/0'/0'/0'
```

### **Key Export Mnemonic**

**Syntax**

```
accumulate key export mnemonic (export the mnemonic phrase if one was entered)
```

**Command**

```
./accumulate key export mnemonic
Password: ********
mnemonic phrase: cat laugh aunt question rib scrap picture axis cushion deposit door taste
```



### **Key Export Seed**

**Syntax**

<pre><code><strong>accumulate key export seed (export the seed generated from the mnemonic phrase)</strong></code></pre>

**Command**

```
./accumulate key export seed
Password: ********
```

The above command will return an output similar to the following:

```
seed: ed542528af5bf865161314165b25bd106d98d7b57b372e7ac61bba767433bb6046c09f02c705b42153e2f95eef54b62981f2022dd8864b53b790d444cfd92756
```

### **Key Label**

**Syntax**

```
accumulate key label [command]
Available Commands:
  assign      assign public key of existing label to a new label.      
  remove      remove a key label
  rename      rename a key label to new label, note: the old key name will be replaced with the new key 
name
```

**Command (assign)**

```
./accumulate key label assign test501 test505
Password: ********
```

The above command will return an output similar to the follow

```
 Label(s)   | test501
            | test505
 Lite Label | 612d6cd0ff886f95c9385c828cd8c3006de84d06617f20fa
 Public Key | 936dc073a2694118a4e1d8b344b033d7a7fac0bdc981ef16f122e65be4967c16
 Key Hash   | 612d6cd0ff886f95c9385c828cd8c3006de84d06a2fd5474fed97f0d954a6215
 Key Type   | rcd1
 Derivation | m/44'/131'/0'/0/3
```

**Command (rename)**

```
/accumulate key label rename test501 test599
Password: ********
```

The above command will return an output similar to the follow

```
 Label(s)   | test505
            | test599
 Lite Label | 612d6cd0ff886f95c9385c828cd8c3006de84d06617f20fa
 Public Key | 936dc073a2694118a4e1d8b344b033d7a7fac0bdc981ef16f122e65be4967c16
 Key Hash   | 612d6cd0ff886f95c9385c828cd8c3006de84d06a2fd5474fed97f0d954a6215
 Key Type   | rcd1
 Derivation | m/44'/131'/0'/0/3
```

**Command (remove)**

```
/accumulate key label remove test599
Password: ********
```

The above command will return an output similar to the follow

```
 Label(s)   | test505
 Lite Label | 612d6cd0ff886f95c9385c828cd8c3006de84d06617f20fa
 Public Key | 936dc073a2694118a4e1d8b344b033d7a7fac0bdc981ef16f122e65be4967c16
 Key Hash   | 612d6cd0ff886f95c9385c828cd8c3006de84d06a2fd5474fed97f0d954a6215
 Key Type   | rcd1
 Derivation | m/44'/131'/0'/0
```

### **Wallet**&#x20;

**Export -** Export Wallet Details\
./accumulate export "C:\filepath\myaccounts.json"\
\
Check the file path and open the json file to view its contents\
\
**Init** - Import secret factoid key from terminal input \
./accumulate wallet init create\
\
./accumulate wallet init import \
Enter mnemonic :\
\
**Serve -** run wallet service daemon

./accumulate wallet serve

### **Credits**

To send ACME tokens to another account, you need to purchase credits with ACME and send them to a recipient.

Check this [link](https://docs.accumulatenetwork.io/accumulate/getting-started/fees) to view the Base Fees for different transactions.

To send credits to your lite account or Key Page, run the example command in your terminal

### **Adding Credits to a Lite Token Account/Lite Identity.**

This command adds credit to your lite token account/lite identity.&#x20;

**Syntax**

```
accumulate credits [origin token account] [key page or lite identity url] [number of credits wanted] [max acme to spend] [percent slippage (optional)] [flags][BS2]
```

**Command**

```
./accumulate credits acc://f338762f7013acb0fd5e1480c20df47ff836862adbd6e0f1/ACME acc://f338762f7013acb0fd5e1480c20df47ff836862adbd6e0f1/ACME 10000
```

The above command will return an output similar to the following:

```
Transaction Hash : a743ab4412cc4ca8b08761e21d7bae7ddb2ed84e7e82a514a32e538eb5d79f08
Simple Hash : 7e43cfcdb1acbc1f1f43d266013b2d48463fd2e5263f3cac3b89e4b08a52d9aa
Error code : ok
Result : Oracle $0.05 / ACME
Credits 10000.00
Amount 2000.00000000 ACME
```

**Use the TX History command to see prior transactions**

This command gets the list of your transactions using a range of numbers.

**Syntax**

```
accumulate tx history [url] [starting transaction number] [ending transaction number] Get transaction history
```

**Command**

```
accumulate tx history acc://ec53ee9f68b7f712da6ef3a0c96583af547c8e2964684733/ACME 0 10
```

The above command will return an output similar to the following:

```
Transaction History Start: 0 Count: 1 Total: 28
```

### **Oracle**

To explicitly query the oracle to see the current price of ACME and the number of credits per ACME:

**Syntax**

```
./accumulate oracle
```

**Command**

```
./accumulate oracle
```

The above command will return an output similar to the following:

```
USD per ACME : $0.0500
Credits per ACME : 5.00
```

### **Lite Data Accounts**

Lite Data Accounts are an extension of the Factom Protocol, which will be used to transition data from Factom to Accumulate.

### **Lite Data Account Creation from Lite Token Account/Lite Identity**

This command creates a new lite data account from a lite token account.

**Syntax**

```
account create data --lite [lite token account URL] [data (chain name)]
```

**Command**

```
./accumulate account create data --lite acc://f338762f7013acb0fd5e1480c20df47ff836862adbd6e0f1/ACME "Ben"
```

The above command will return an output similar to the following:

```
Account Url :acc://c26fd6ed6beafd197086c420bbc334f0cd4f05802b550e5d
Account Id :c26fd6ed6beafd197086c420bbc334f0cd4f0580a44dc689452b57b150d10e46
Entry Hash :cda19cfa7cc15bcf1ce2dea451c13a0f8a77e15fee6289c0839f4f176d357bce
Transaction Hash : 62f4c555e8d95b00a775337c54cac80ab6222d6bdf7c4f8eadc013830b9b1fc4
Signature 0 Hash : 89bfdd4619147eb32590cb83f8d05d73697f6f8a31a6961df3e0a8feaaa41b1e
Simple Hash : 05ea5c5b406964af4f4a5adc52d5c8ef6e5565ec9de21415847310e5e5980a40
Error code : ok
Result :
```

### **Lite Data Account Creation from ADI**

This command creates a new lite data account from an ADI

**Syntax**

```
Account create data --lite [origin token account][signing key][extID]
```

**Command**

```
./accumulate account create data --lite acc://DefiDevs.acme Key2 "Marian"
```

The above command will return an output similar to the following:

```
Account Url :acc://7d27485702b1f756a7c0f6ac39931e77959f58d475ee3898
Account Id :7d27485702b1f756a7c0f6ac39931e77959f58d4598949d4fd9dfd8f98358c04
Entry Hash :071b9662b4c3512d4c0b3dbdd73fc092e155abe805aad3ec14a1183fb732b960
Transaction Hash : eac6868a7e756faca5e00e999efadec6967eab5c9b7b434b4c6160bda6e7a283
Signature 0 Hash : 31c2b9d9e9457dc484a3dc2260b20bc6d34f2876196fabc531279c6100145a1f
Simple Hash : d28c28d27ec764bcf3218c10abcdf69e23024461c102331e35cd221c0663580a
Error code : ok
Result :
```

### **Writing to a Lite Data Account**

This command writes to an Accumulate lite data account

**Syntax**

```
accumulate data write-to [account url] [signing key][BS3] [lite data account] [extid_0 (optional)] ... [extid_n (optional)] [data]
```

**Command**

```
data write-to acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME acc://7d27485702b1f756a7c0f6ac39931e77959f58d475ee3898 "Key6"
```

The above command will return an output similar to the following:

```
Account Url :acc://7d27485702b1f756a7c0f6ac39931e77959f58d475ee3898
Account Id :7d27485702b1f756a7c0f6ac39931e77959f58d4598949d4fd9dfd8f98358c04
Entry Hash :185f8db32271fe25f561a6fc938b2e264306ec304eda518007d1764826381969
Transaction Hash : f27277b07e66883c836a72020d50e57cc8c1e86f24307ac99e2a4c035f6f8973
Signature 0 Hash : 0b4fbe4878374e5dd7aafb10dbe23f141998dd3603ee35dd930102f80cc256cf
Simple Hash : e8b203831aa0de000a9e26e60c44d8167c272d2e53dcb99c0785dfd7bd6ede15
Error code : ok
Result :
```

### **Querying a Lite Data Account by URL**

This command \*\*\*\* returns a lite data account by url.

**Syntax**

```
accumulate data get [DataAccountURL] Get most current data entry by URL
```

**Command**

```
./accumulate data get acc://7d27485702b1f756a7c0f6ac39931e77959f58d475ee3898
```

The above command will return an output similar to the following:

```
{"type":"dataEntry","mainChain":{"height":2,"count":2,"roots":["04b097c244655110e76f77dfeaf39910af96d4c651037c05cdc841872f53d11a","8e70b62e509e6f037b69f205a8355c0586ce7e26457411d781dfe8de0eecedc7"]},"data":{"entry":{"data":["48656c6c6f"]},"entryHash":"f522210a71e681a1f7f40d005322dc36fb6bcbe915889dd9f1aa78147703ee38"},"chainId":"a2bd8fbd9b14eef22f157079cb3a99067d87fd3b9923e423fdf051e55d116a01"}
```

### **Querying a Lite Data Account by URL and a Specific Entry Hash**

This command returns a lite data account by using the url and entryhash.

**Syntax**

```
accumulate data get [DataAccountURL] [EntryHash] Get data entry by entryHash in hex
```

**Command**

```
./accumulate data get acc://7d27485702b1f756a7c0f6ac39931e77959f58d475ee3898 071b9662b4c3512d4c0b3dbdd73fc092e155abe805aad3ec14a1183fb732b960
```

The above command will return an output similar to the following:

```
{"type":"dataEntry","mainChain":{"height":2,"count":2,"roots":["04b097c244655110e76f77dfeaf39910af96d4c651037c05cdc841872f53d11a","8e70b62e509e6f037b69f205a8355c0586ce7e26457411d781dfe8de0eecedc7"]},"data":{"entry":{"data":["","4d617269616e"]},"entryHash":"071b9662b4c3512d4c0b3dbdd73fc092e155abe805aad3ec14a1183fb732b960"},"chainId":"a2bd8fbd9b14eef22f157079cb3a99067d87fd3b9923e423fdf051e55d116a01"}
```

### **Querying a Lite Data Account by URL and Index**

This command returns a lite data account by using the url and index.

**Syntax**

```
accumulate data get [DataAccountURL] [start index] [count] expand(optional) Get a set of data entries starting from start and going to start+count, if "expand" is specified, data entries will also be provided
```

**Command**

```
./accumulate data get acc://7d27485702b1f756a7c0f6ac39931e77959f58d475ee3898 0 2
```

The above command will return an output similar to the following:

```
{"type":"dataSet","items":[{"entry":{},"entryHash":"071b9662b4c3512d4c0b3dbdd73fc092e155abe805aad3ec14a1183fb732b960"},{"entry":{},"entryHash":"f522210a71e681a1f7f40d005322dc36fb6bcbe915889dd9f1aa78147703ee38"}],"start":0,"count":2,"total":2}
```

### **ADI Creation from a Lite Token Account:**

This command creates an ADI from a lite token account.

**Syntax**

```
accumulate adi create [origin-lite-account] [adi url to create] [public-key or key name] [key-book-name (optional)] [public key page 1 (optional)] Create new ADI from lite token account.
```

When public-key one is specified, it will be assigned to the first page. Otherwise, the origin key is used.

**Command**

```
./accumulate adi create acc://f338762f7013acb0fd5e1480c20df47ff836862adbd6e0f1/ACME acc://DefiDevs.acme Key1 acc://DefiDevs.acme/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : 1139db355819257a618129641464b145e8a4d0fdab301507f7c0ebbcd9185105
Signature 0 Hash : cf3dbe8c63b9f31b5a506de03cf758393e1db6c71e039b7c528d7651b9128b8c
Simple Hash : a08ab66047f800ce11e0654bae6b584d085fd594c70c225a3aa87cbd9e0bc597
Error code : ok
Result :
```

### **ADI Creation from an ADI**

This command creates ADI from another ADI.

**Syntax**

```
accumulate adi create [origin-adi-url] [wallet signing key name] [key index (optional)] [key height (optional)] [adi url to create] [public key or wallet key name] [key book url (optional)] [public key page 1 (optional)] Create new ADI for another ADI
```

**Command**

```
./accumulate adi create acc://DefiDevs.acme Key2 acc://Toyota Key2 acc://Toyota/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : 00038a5fd818006ac01089f8aea782b846722bec150a333dfc77356a277e60bf
Signature 0 Hash : 5c64193d64950c2bee4873feb557d477ca0590fd37e4b0b4ad817a5fdd1fcdb4
Simple Hash : 032d354fc6b03036f00cb5cfdf2674705a2e5f0f2f99896b9ceea48e77feaad9
Error code : ok
Result :
```

{% hint style="info" %}
ADIs can also be created using the following accounts as principals for the transaction: ADI Data Account, ADI Token Account, ADI Token Issuance, and a Sub-ADI and its Accounts.
{% endhint %}

### **ADI Creation from a Sub-ADI**

This command creates ADI from a sub-ADI.

**Syntax**

```
accumulate adi create [origin-adi-url] [wallet signing key name] [key index (optional)] [key height (optional)] [adi url to create] [public key or wallet key name] [key book url (optional)] [public key page 1 (optional)] Create new ADI for another ADI
```

**Command**

```
./accumulate adi create acc://DefiDevs.acme/Robot Key2 acc://Ford.acme Key2 acc://Ford.acme/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : e3fa9f05a4eb736dbaac58594fdcfb1478098555d7c27c315a4595a38aabdd5e
Signature 0 Hash : c00282900903ddf18f7ca2fcbe09bd2971d48d8364516e45d9f7069ecb1db7b7
Simple Hash : 23c66ccbe1bba178b553c87582595d2710e7e97d85528c96c37d5ae07ebfebe3
Error code : ok
Result :
```

### **ADI Creation from a Sub-Sub-ADI**

This command creates ADI from a sub-sub-ADI.

**Syntax**

```
accumulate adi create [origin-adi-url] [wallet signing key name] [key index (optional)] [key height (optional)] [adi url to create] [public key or wallet key name] [key book url (optional)] [public key page 1 (optional)] Create new ADI for another ADI
```

**Command**

```
./accumulate adi create acc://DefiDevs.acme/Robot/MrRoboto Key2 acc://Ferrari Key2 acc://Ferrari/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : a203c790287deb440c2fb1abeaab92131ea0ce4deaeb1d2c448bf2ba92b9dac6
Signature 0 Hash : e095e22c1e20d89f0b741332200d647febc86369826f3c65000e842f99cbef35
Simple Hash : f4509afb159a11ece81f89395f512e9f0bf40b16c0a007140b8606dd6ba23f93
Error code : ok
Result :
```

### **ADI Directory**

This command returns the list of your ADI directory.

**Syntax**

```
accumulate adi directory [url] [from] [to] [flags]
```

**Command**

```
./accumulate adi directory acc://DefiDevs.acme 0 20
```

The above command will return an output similar to the following:

```
ADI Entries: start = 0, count = 20, total = 11
acc://DefiDevs.acme/Keybook (Key Book)
acc://DefiDevs.acme/Tokens (ADI Token Account)
acc://DefiDevs.acme/Data (Data Chain)
acc://DefiDevs.acme/ScratchData (Data Chain)
acc://DefiDevs.acme/Keybook2 (Key Book)
acc://DefiDevs.acme/Car (ADI)
acc://DefiDevs.acme/Robot (Sub-ADI)
acc://DefiDevs.acme/Cybertruck (Sub-ADI)
acc://DefiDevs.acme/AI (tokenIssuer)
acc://DefiDevs.acme/AITokens (ADI Token Account)
```

### **ADI List**

To see a list of ADIs created and the initial Key specified for Key Page 1

### **ADI Get**

An ADI get returns the ADI URL, as well as the Key Book, generated during the creation of the ADI.

**Syntax**

```
accumulate adi get [url] [flags]
```

**Command**

```
./accumulate adi get acc://DefiDevs.acme
```

The above command will return an output similar to the following:

```
ADI url : acc://DefiDevs.acme
Key Book Url : acc://DefiDevs.acme/Keybook
```

### **Key Books**

The Key Books store an ADI's Hierarchical Key Management Structure using Key Pages and Keys within those pages.

### **Get Key Book**

This command **returns the list of keybook**

**Syntax**

```
accumulate get [url] Get data by Accumulate URL
```

**Command**

```
./accumulate get acc://DefiDevs.acme/Keybook/
```

The above command will return an output similar to the following:

```
Page Count
2
```

get Deprecated - use \`accumulate get ...\` fix in CLI

### **Create an Additional Key Book**

An ADI can have multiple Key Books. To create an additional Key Book, a Public Key Hash or Key Book URL must be specified for the purpose of signing the transaction. A new public key or key name should be added to the new book.

**Syntax**

```
accumulate book create [origin adi url] [signing key name] [key index (optional)] [key height (optional)] [new key book url] [public key 1 (optional)] ... [public key hex or name n + 1 [flags]
```

**Command**

```
./accumulate book create acc://DefiDevs.acme Key1 acc://DefiDevs.acme/Keybook2 Key3
```

The above command will return an output similar to the following:

```
Transaction Hash : c168ecfb3985a88f694666b0ed19f8e24b6451eb412da788f1068694a24e4a24
Signature 0 Hash : 0c023834a44520f396470c0db58404db94330aee7189a78073463d017d2736a1
Simple Hash : 48f0c4a86d6c1d45e8de4d718370aa6481da9f09c853f53135b5858de85d976c
Error code : ok
Result :
```

### **Key Pages**

A Key Page has entries that define the parties required to sign a transaction. If you have the same Key in multiple Key Pages you must explicitly specify the page using keyname@adi.acme/book/(page number).

### **Get Key Page**

This command returns the list of key pages.

**Syntax**

```
accumulate get [url] Get data by Accumulate URL
```

**Command**

```
./accumulate get acc://DefiDevs.acme/Keybook/1
```

The above command will return an output similar to the following:

```
Credit Balance : 0.00
Index Nonce Public Key Key Name(s)
0 1969-12-31 19:00:00 -0500 EST fa9ae1e76b6936583546d495c98f34a9f0d57b52f759b4ebf1f04e6db0111381 Key3
1 1969-12-31 19:00:00 -0500 EST c3781e20dd3dbaade511587e4b153efc86e2194111a07091a0e6159d7699c513 Key4
2 1969-12-31 19:00:00 -0500 EST 0d83eababd1ba323f69470576f8c9eb563821a07cca55f5ac30f276cf62bebc4 Key1
```

### **Adding Credits to a Key Page**

An ACME token account must be referenced when adding credits to a Key Page. This can either be a Lite Token Account or an ADI Token Account.

**Syntax**

```
accumulate credits [origin token account] [key page or lite identity url] [number of credits wanted] [max acme to spend] [percent slippage (optional)] [flags]
```

**Command**

```
./accumulate credits acc://f338762f7013acb0fd5e1480c20df47ff836862adbd6e0f1/ACME acc://DefiDevs.acme/Keybook/1 10000
```

The above command will return an output similar to the following:

```
Transaction Hash : 7bba5f1178d71193a91641ad627d8d232b88f4f0a37cb855bef5afa1b741aa1a
Simple Hash : 00da35f2201a5a6143375d9225188ac49f1129c7c748bd7f6c0f2d218eb85b2a
Result : Oracle $0.05 / ACME
Credits 10000.00
Amount 2000.00000000 ACME
```

### **Adding Additional Key Pages to a Key Book**

A new Key Page can be added to a Key Book where public keys or key names can be specified. In the example below 3 keys were added to the new Key Page (Key1, Key3, and Key4. Due to this being the 2nd Key Page, the Key Page URL would be acc:/DefiDevs.acme/Keybook/2.&#x20;

**Syntax**

```
accumulate page create [origin key book url] [key name[@key book or page]] [public key 1] ... [public key hex or name n + 1] [flags]
```

**Command**

```
./accumulate page create acc://DefiDevs.acme/Keybook Key1 Key3 Key4
```

The above command will return an output similar to the following:

```
Signature 0 Hash : dee40ebb838385eb43c78edd325cf4ad1c54c4e68dd73e8b4454348aea8a849b
Simple Hash : cb61cd5f34b2785da2763ac8ca773c2c19a60410f734bb7cb230fd8bc4fc009f
Error code : ok
Result :
```

### **Adding a Key**

**Syntax**

```
accumulate page key add [key page url] [signing key name] [key index (optional)] [key height (optional)] [new key name] [flags]
```

**Command**

```
./accumulate page key add acc://DefiDevs.acme/Keybook/1 Key1 Key2
```

The above command will return an output similar to the following:

```
Transaction Hash : 9fbcbe49b4dbbf861be63eeae41576f1da7b7ca3b31e1c3968adff766b0445c2
Signature 0 Hash : 99f87aa951585592d66a56e670b083c8a4f10de0fd014a72b2d05fa901546dde
Simple Hash : f4f7e5e0d8b5599aad214412939f954b4bf012b8f5ac9a56d24d54983f185d3d
Error code : ok
Result :
```

### **Query Page**

A get command will query the Key Page to show the new key that has been added.

**Syntax**

```
accumulate get [url] Get data by Accumulate URL
```

**Command**

```
./accumulate get acc://DefiDevs.acme/Keybook/1
```

The above command will return an output similar to the following:

```
Credit Balance : 9997.00
Index Nonce Public Key Key Name(s)
0 1969-12-31 19:00:00 -0500 EST 272b7a64c2caf76ffe6cf0adf37a144aff60920bdc269803982f150802053afb Key1
1 1969-12-31 19:00:00 -0500 EST f619aa889a2532d2d331d8a1287895b87605d7a5a1c75ad671f9bb6a7628940c Key2
```

### **Removing a Key**

This command removes a key from a keypage.

**Syntax**

```
accumulate page key remove [key page url] [signing key name] [key index (optional)] [key height (optional)] [old key name] [flags]
```

**Command**

```
./accumulate page key remove acc://DefiDevs.acme/Keybook/1 Key2 Key2
```

The above command will return an output similar to the following:

```
Transaction Hash : c237853496f3348e8dd9fc847bb692608a1d9ed95236d351908203691951b749
Signature 0 Hash : ecb1aa735f8473d8d0b0194549d9ec94be520b1ee6c24e4846b0b7b122ebf932
Simple Hash : 5355696f77cfc89d0f5b3be90dccb66e7f337af303d2c66129de8c8ba5b02aed
Error code : ok
Result :
```

### **Updating a Key of another party**

This command updates a key in a key **** page and requires the page threshold to be met.

**Syntax**

```
accumulate page key update [key page url] [signing key name] [key index (optional)] [key height (optional)] [old key name] [new public key or name] [flags]
```

**Command**

```
./accumulate page key update acc://DefiDevs.acme/Keybook/1 Key1 Key1 Key2
```

The above command will return an output similar to the following:

```
Transaction Hash : f5b4ab98ff3b322bf513376acaad748d65847408c6b3e10909e32bd1c81401d9 

Signature 0 Hash : d9e3c4786353b89d1fa7bca22e2e317f2e4071e195e86f6f2bfd409d0516cb63 

Simple Hash : ffe7d185949a7322333a485590c8976fc1dd66855f7fc973dfae084f1afb455a 

Error code : ok 
```

### **Updating your own Key**

This command updates your own key in a key **** page and doesn't require the page threshold to be met.

```
./accumulate page key replace directorynetwork.acme/book/1 dnkey hello      


        Transaction Hash        : e1a36e712b0bb6c2335d0c03dbb2e8238dcbe7f25e07ede3f419d19af5adc981
        Signature 0 Hash        : db932235913e8f6d4d8bd5c0299f31bc4878e878878ab494f2b24279a022ffc3
        Simple Hash             : b32974949f5f81b2fffe6f6e04b5700db4ad5d1192970db3c5976b9a53dea884
        Error code              : ok
        Result                  :
```

```
    Transaction Hash        : e1a36e712b0bb6c2335d0c03dbb2e8238dcbe7f25e07ede3f419d19af5adc981
    Signature 0 Hash        : db932235913e8f6d4d8bd5c0299f31bc4878e878878ab494f2b24279a022ffc3
    Simple Hash             : b32974949f5f81b2fffe6f6e04b5700db4ad5d1192970db3c5976b9a53dea884
    Error code              : ok
    Result                  :
```

### **Locking/Unlocking a Key page**

This command is used to **lock** a Key page. This prevents "update" operation to a key page.

**Syntax**

```
accumulate page lock [key page url] [key name[@key book or page]] [flags]
```

**Command**

```
./accumulate page lock acc://RajagopalIndia456.acme/book/3 keyed25519NIVS@RajagopalIndia456.acme/book/1 
```

**Output**

```
Transaction Hash        : 4d0b16c471a19d7abcc2173ca5b268c28283a0e3c0764d776fdfbd1259aa1310      
Signature 0 Hash        : eb59b97b4a084f07205602a5dbe3fccf7ff7911e6f40540b627737fcc1dccd44      
Simple Hash             : 151016ca9c69c73cd0c36f0094350104bfabd6cda7d6edf63573c39326c1839f      
Error code              : ok
Result                  :
```

**To verify a locked key page**

To verify the locked key page, retrieve the value of key page. The following entry should be present in output.

_"transactionBlacklist":\["updateKeyPage"]_

{% code overflow="wrap" %}
```
./accumulate.exe get acc://RajagopalIndia456.acme/book/3 -j
{"chainId":"1827174d2c721b93eb85c867fdf2dacadf75b9118cd702bcd4e831978de43f8c","chains":[{"count":41,"height":41,"name":"main","roots":["4d0b16c471a19d7abcc2173ca5b268c28283a0e3c0764d776fdfbd1259aa1310",null,null,"cc592302f8b7e438aebab91abf97e88b0a3f77e34f0a3264a7244c72bfb6b717",null,"4ba548e009f93ef4f2cffbbc2c6c251f3afbae95facbcac4547f03d41431c46f"],"type":"transaction"},{"count":41,"height":41,"name":"main-index","roots":["012802c5ae03039ea8aa01200000000000000000000000000000000000000000",null,null,"46ce7e00434dcf5b35ae6f269b144f353829224e295f0f8f3cf05d60afd715b3",null,"c65ed6c7442a1d5826ba41a4f8685ee492d36ff7321c18f481e7cebbd7caa59b"],"type":"index"},{"count":37,"height":37,"name":"signature","roots":["eb59b97b4a084f07205602a5dbe3fccf7ff7911e6f40540b627737fcc1dccd44",null,"7ba62d5dd3593010efb1a8a3d0d35c7b29f9fb814451eae2247fccca62b3bd76",null,null,"e146cca3dade29f26b8cda0bcbd9ed8f86b896bbb53cd3f0c43ca23449f619f1"],"type":"transaction"}],"data":{"acceptThreshold":1,"creditBalance":9700,"keyBook":"acc://RajagopalIndia456.acme/book","keys"[{"publicKey":"3ebc9b367208e1834afc5a9819ca6ab54d84e2a529a76267d02594f5fe118db0","publicKeyHash":"3ebc9b367208e1834afc5a9819ca6ab54d84e2a529a76267d02594f5fe118db0"},{"publicKey":"40d2648776279fcefd975ecda62d06cd7204952d8637b5dc0d6cd2115bc34df9","publicKeyHash":"40d2648776279fcefd975ecda62d06cd7204952d8637b5dc0d6cd2115bc34df9"},{"publicKey":"4af9d6740c30b7cab4c3639bf4ffa0aedbc38db41978818d8e268fc4f4c29c9c","publicKeyHash":"4af9d6740c30b7cab4c3639bf4ffa0aedbc38db41978818d8e268fc4f4c29c9c"},{"publicKey":"51bc346a606cfa7de2834f04a6c69d560e47257a78b5f12caaa338605ae8d37d","publicKeyHash":"51bc346a606cfa7de2834f04a6c69d560e47257a78b5f12caaa338605ae8d37d"}],"threshold":1,"transactionBlacklist":["updateKeyPage"],"type":"keyPage","url":"acc://RajagopalIndia456.acme/book/3","version":38},"mainChain":{"count":41,"height":41,"roots":["4d0b16c471a19d7abcc2173ca5b268c28283a0e3c0764d776fdfbd1259aa1310",null,null,"cc592302f8b7e438aebab91abf97e88b0a3f77e34f0a3264a7244c72bfb6b717",null,"4ba548e009f93ef4f2cffbbc2c6c251f3afbae95facbcac4547f03d41431c46f"]},"merkleState":{"count":41,"height":41,"roots":["4d0b16c471a19d7abcc2173ca5b268c28283a0e3c0764d776fdfbd1259aa1310",null,null,"cc592302f8b7e438aebab91abf97e88b0a3f77e34f0a3264a7244c72bfb6b717",null,"4ba548e009f93ef4f2cffbbc2c6c251f3afbae95facbcac4547f03d41431c46f"]},"type":"keyPage"}  
```
{% endcode %}



This command is used to **unlock** a Key page.

**Syntax**

```
 accumulate page unlock [key page url] [key name[@key book or page]] [flags]
```

**Command**

<pre data-overflow="wrap"><code><strong>./accumulate page unlock acc://RajagopalIndia456.acme/book/3 keyed25519NIVS@RajagopalIndia456.acme/book/1</strong></code></pre>

**Output**

```
Transaction Hash        : 40c3de4f3688b9a9aa993537196b9f6e221fadb2137305f419a4f789f75a877f      
        Signature 0 Hash        : 5ae4def21f0387606bc6cac36f149aa85747ce916096bc74787e3c446d1dd92b      
        Simple Hash             : 550a22a7dd0d536787581840f3710ab7a317157858c1bd7d75e01d97c1bb5946      
        Error code              : ok
        Result                  :
```

### **Setting a Threshold for a Key Page**

By default, setting a threshold for a Key Page, the m of n will be 1 of 1. Because of this, any entry within the Key Page can update the signature threshold. In the example below, the number of Keys within acc://DefiDevs.acme/Keybook/2 is 3. Setting the threshold at two means that 2 of 3 signatures are required for the transaction to be processed.

**Syntax**

```
accumulate tx execute [origin url] [signing key name] [key index (optional)] [key height (optional)] [payload] 
```

**Command**

```
./accumulate tx execute acc://DefiDevs.acme/Keybook/2 Key1 '{\"type\": \"updateKeyPage\", \"operation\": [{ \"type\": \"setThreshold\", \"threshold\": 2 }]}'
```

The above command will return an output similar to the following:

```
Transaction Hash : 6130d09c7b8bc2ffbdf82f13b9a0a4b5144bc2878523e899549ed732c9829f22
Signature 0 Hash : 2990a1ee1894494859162ed9d6772454a55a8737960fcaa09e7f6d150c8ef944
Simple Hash : 881275aea93bd90879f8f8d6c4d7d479ccffdc18b31f89538c752f67b77b0368
Error code : ok
Result :
```

### **Multi-Signature Transactions**

A multi-signature transaction is defined by the signature threshold for a given Key Page. As a note, to sign with multiple keys at once you can add the --sign-with flag with a list of keys to a transaction.&#x20;

**Multi-Signature Transactions**&#x20;

A multi-signature transaction is defined by the signature threshold for a given Key Page. In the following examples, a new Key will be added to a Key Page using a multi-signature transaction. &#x20;

**Syntax**

```
accumulate page key add [key page url] [signing key name] [key index (optional)] [key height (optional)] [new key name] [flags]
```

&#x20;**Command**

```
./accumulate page key add acc://DefiDevs.acme/Keybook/2 Key5 Key1  
```

&#x20;The above command will return an output similar to the following:

```
Transaction Hash        : 72fb5fcdecbf8b30182e20eaeb4d218f13163fe15b2ff6543f8be7ea2d4a78e6 
Signature 0 Hash        : de3f985a3569b3537c591353db6a15a385578967b7ddc28910f6779bebce4cf3 
Simple Hash             : 8961c92b3adeadaae13eba36e935808d723c33806bc421937159d0a9498b33c6 
Error code              : ok 
Result                  : 
```

### **Pending Transaction**

A pending transaction can be queried to see the status.&#x20;

**Syntax**

```
./accumulate tx pending [txid]
```

**Command**

```
./accumulate tx pending 72fb5fcdecbf8b30182e20eaeb4d218f13163fe15b2ff6543f8be7ea2d4a78e6 
```

The above command will return an output similar to the following:

```
  Pending Tranactions -> Start: 0  Count: 1       Total: 1 
```

### **Sign Transaction Hash**

The second signer signs the transaction hash of the first transaction in the multi-signature sequence. If there are additional signers, they sign the same transaction hash.

**Syntax**

```
./accumulate tx sign [key page url] [signing key name] [txid]
```

**Command**

```
./accumulate tx sign acc://DefiDevs.acme/Keybook/2 Key3 72fb5fcdecbf8b30182e20eaeb4d218f13163fe15b2ff6543f8be7ea2d4a78e6   
```

The above command will return an output similar to the following:

```
    Transaction Hash        : 72fb5fcdecbf8b30182e20eaeb4d218f13163fe15b2ff6543f8be7ea2d4a78e6 
    Signature 0 Hash        : de79633b1ceced2652f29f7fcb813190c19d175dd1846e76b3e233da66252666 
    Simple Hash             : c87ef41af1233a666e9a833f50ee030ddcca08a1adaab76904846489220f3b8b 
    Error code              : ok 
    Result                  : 
```

### **Signing with a Delegate**

If a Delegate is specified in a Key Page Entry, the Delegate can use any entry within its Key Book to sign a transaction. If the Delegate is of a different ADI (remote), the signing key must be specified using \[keyname@adiname/keybookname]. In the example below, the Delegate is remote.

**Syntax**

```
./accumulate tx create [adi token account] [delegate signature] --delagator [delegator key page] [recipient][amount]
```

**Command**

```
./accumulate tx create keybooktest.acme/token2 ben@keybooktest.acme/keybook2 --delegator keybooktest.acme/keybook/1 acc://ea9b01213430a8b3150db607789dd5c5c1aa45fdf39bc001/ACME 100
```

The above command will return an output similar to the following:

```
Transaction Hash : 58589bc4521e9fcfec62e878797767449e13338e1954c64f625a2e077be0e1cc
Signature 0 Hash : 1b8415021629ed7711675ddb597d790ae9ca1e861cd7eb2133c19b348328e340
Simple Hash : 639e2d2c644c9b7951ebed616d8d239fe62daba81c6d0b7f4eaebc43c53c66a6
Error code : ok
Result :
```

### **Adding a Delegate and Public Key hash to a Key Page Entry**

**Syntax**

```
tx execute ./accumulate tx execute [Key Page] [Signing Key] '{type: updateKeyPage, operation: [{ type: add, entry: { owner: [Delegate], keyHash: [Public Key Hash]} }]}'
```

**Command**

```
./accumulate tx execute Delegatetest.acme/Keybook/1 newkey '{type: updateKeyPage, operation: [{ type: add, entry: { owner: acc://Delegatetest.acme/Keybook3, keyHash: d2aad80e11d0478015c51c197e2df99da3a2c3309fb4245efa370a7033cdc127 } }]}'
```

The above command will return an output similar to the following:

```
Transaction Hash : 619ec91821f0fec89a77d69ed1272f86e18fc70d78101660b4859f67f77fb90b
Signature 0 Hash : 3533879d4a34f614c80c4fddb5aaebd0fabc676f2610c5199fd6a4f697f4a163
Simple Hash : 42c71a77f5bc035d263887e052aa8e26911e92f07c6e025a8f3d94d2ae4eaf27
Error code : ok
Result :
```

### **Sign Transaction with Delegate**

**Syntax**

```
./accumulate tx sign [Key Page] [SingingKey@KeyBook][Transaction ID]
```

**Command**

```
./accumulate tx sign acc://Delegatetest.acme/Keybook/1 newkey@Delegatetest.acme/Keybook3 619ec91821f0fec89a77d69ed1272f86e18fc70d78101660b4859f67f77fb90b
```

The above command will return an output similar to the following:

```
Transaction Hash : 619ec91821f0fec89a77d69ed1272f86e18fc70d78101660b4859f67f77fb90b
Signature 0 Hash : fe1290db52481dfc99380a576a6db00dbdec588b37bc7e867e2a6f3493dc6206
Simple Hash : eccd36490ce21d1436e0d3b109922667a4f89f62f8247acd1f0dbce8ab413e31
Error code : ok
Result :
```

### **Updating a Delegate and Public Key Hash of a Key Page Entry (Signing with a Delegate)**

**Syntax**

```
./accumulate tx execute acc://Delegatetest.acme/Keybook/1 [Signing Key]'{type: updateKeyPage, operation: [{ type: update, oldEntry: {keyHash: [Public Key Hash], Delegate: [Delegate Key Book]} , newEntry: {keyHash: [Public Key Hash], Delegate: [Delegate Key Book]} }}]}'
```

**Command**

```
./accumulate tx execute acc://Delegatetest.acme/Keybook/1 newkey@Delegatetest.acme/Keybook3/1 '{type: updateKeyPage, operation: [{ type: update, oldEntry: {keyHash: 39c2ada31c6cb824e80f2a96f17e077a7edc9f02a93d34eede2616a5c9c3412c, Delegate: Delegatetest.acme/Keybook3} , newEntry: {keyHash: 785b7f22ab201ae3f391cc47b06e2da00bbd47e7600ba1c68ea2cdb2b26f00ef, Delegate: Delegatetest.acme/Keybook3}}]}' --delegator acc://Delegatetest.acme/Keybook/1
```

The above command will return an output similar to the following:

```
Transaction Hash : 139c736cbccfc146d7731694d3a146417ef39be59614d63da9795d56307d38fc
Signature 0 Hash : 772207a552c99e43193992617686bd30c3ecaad790cc3952eaf25e3116ee5715
Simple Hash : 17a4e1591126c98eb9c0080444d109d18110a8366f3365a4f11fc9741b304567
Error code : ok
Result :
```

### **Sign Transaction with Delegate**

**Syntax**

```
./accumulate tx sign [Key Book][Signing Key][Transaction ID]
```

**Command**

```
./accumulate tx sign acc://Delegatetest.acme/Keybook/1 newkey@Delegatetest.acme/Keybook3 619ec91821f0fec89a77d69ed1272f86e18fc70d78101660b4859f67f77fb90b
```

The above command will return an output similar to the following:

```
Transaction Hash : 139c736cbccfc146d7731694d3a146417ef39be59614d63da9795d56307d38fc
Signature 0 Hash : fe1290db52481dfc99380a576a6db00dbdec588b37bc7e867e2a6f3493dc6206
Simple Hash : eccd36490ce21d1436e0d3b109922667a4f89f62f8247acd1f0dbce8ab413e31
Error code : ok
Result :
```

### **Removing a Delegate and Public Key Hash of Key Page Entry**

**Syntax**

```
./accumulate tx execute acc://Delegatetest.acme/Keybook/1 [Signing Key] '{type: updateKeyPage, operation: [{ type: remove, entry: { owner: [Delegate Key Book], keyhash: [Public Key Hash}}]}'
```

**Command**

```
./accumulate tx execute acc://Delegatetest.acme/Keybook/1 newkey4 '{"type": "updateKeyPage", "operation": [{ "type": "remove", "entry": { "owner": "acc://Delegatetest.acme/Keybook7", "keyhash": "1071cce6eb3ffe8ff0739ee669d0f7b8d095095c088123ebe8039478ae2043fe"}}]}'
```

The above command will return an output similar to the following:

```
Transaction Hash : d2a93317575373327b3ba359ff7131d357fe3bbc4d05623a6e38ed23d2b1e35f
Signature 0 Hash : 2e64be2a1943017776ecdd9949876204b08ebde14ffdb4e832cc48f8ba4b546b
Simple Hash : 1d8f86444849e054f4286f10286ef8ebb9278ad19ed799eed68646896754617e
Error code : ok
Result :
```

### **Key Book Authorities**

An ADI and its accounts have a set of Key Books which manages the signers for that Account. When a Key Book Authority is added to an Account, the Key Book signs a transaction hash to approve its addition. The --auth flag can be added when creating an account to add multiple authorities at once.

### **Add an Authority**

When adding an Authority, the Authority must sign the transaction hash to approve its addition.

**Syntax**

```
accumulate auth add [account url] [signing key name] [key index (optional)] [key height (optional)] [authority url] [flags]
```

**Command**

```
./accumulate auth add acc://DefiDevs.acme/Tokens Key2 acc://DefiDevs.acme/Keybook2
```

The above command will return an output similar to the following:

```
Transaction Hash : 45171d54df1058d4766c353c12255c41875ac57ccaba44020af548eddc3aa0d9
Signature 0 Hash : c387c89886172288f39c14256c558c677be376013987ef3eb5888b9f064148a1
Simple Hash : 3da6716ca5915c47bbd180cf37d5359ffc4d79351f20c9f45ca5eb3d367955df
Error code : ok
Result :
```

### **Disable an Authority**

To disable an Authority, the Authority you are disabling must sign the transaction for approval.

**Syntax**

```
accumulate auth disable [account url] [signing key name] [key index (optional)] [key height (optional)] [authority url or index
```

**Command**

```
./accumulate auth disable acc://DefiDevs.acme/Tokens acc://Key3@DefiDevs.acme/Keybook2 acc://DefiDevs.acme/Keybook2
```

The above command will return an output similar to the following:

```
Transaction Hash : 1473f62845bfc30974b7c87b9c885d81bf2ca6e963c5f9bb2b12428af52538ae
Signature 0 Hash : b362f8a9abea3a177f7540102911c461a5fedbdbb1a53cb3ae7c297b119b5bb8
Simple Hash : 54fc208aa6dd08c0983376d1e0886ee82a9636e5b850ae5576458ab7cf9fc47a
Error code : ok
Result :
```

### **Enable an Authority**

Enabling a Disabled Authority also requires a signature from the Disabled Authority.

**Syntax**

```
accumulate auth enable [account url] [signing key name] [key index (optional)] [key height (optional)] [authority url or index (1-based)] [flags]
```

**Command**

```
./accumulate auth enable acc://DefiDevs.acme/Tokens Key2 acc://DefiDevs.acme/Keybook2
```

The above command will return an output similar to the following:

```
Transaction Hash : 76a62919ad23b8e9f790af52f78960787055a5376a2b7f4e747e9def63a6f892
Signature 0 Hash : b9b1735969bd711a190d0c8a84d2c6587c0036e680183177fc5c69b920e75f26
Simple Hash : f645f3c5fc414d41bf2ed53bb6bff3203929269ed6ebcaeac653cdabeab5dfc7
Error code : ok
Result :
```

### **Remove an Authority**

Whether a Key Book is enabled or disabled, updating the authority set requires a signature from the Key Book being removed.

**Syntax**

```
accumulate auth remove [account url] [signing key name] [key index (optional)] [key height (optional)] [authority url or index (1-based)] [flags]
```

**Command**

```
./accumulate auth remove acc://DefiDevs.acme/Tokens Key2 acc://DefiDevs.acme/Keybook2
```

The above command will return an output similar to the following:

```
Transaction Hash : de14677e318310c19c56fdc12aa7fbf6201c91bc851739c00de8636f28591569
Signature 0 Hash : c8099cc81b5877376c02b9669b501dd0b9c139a65bddee68fae28a5bc7a766d0
Simple Hash : e8912ec4e9104f4396303520d078d3357b034c0c988607ea5ebbd89fd93580af
Error code : ok
Result :
```

### **Create Sub-ADI and Sub-Sub-ADIs**

A Sub-ADI is an ADI created within an ADI. An example could be an organization that creates an ADI and different departments within the origination are Sub-ADIs.

**Syntax**

```
accumulate adi create [origin-adi-url] [wallet signing key name] [key index (optional)] [key height (optional)] [adi url to create] [public key or wallet key name] [key book url (optional)] [public key page 1 (optional)] Create new ADI for another ADI
```

**Command**

```
./accumulate adi create acc://DefiDevs.acme Key2 acc://DefiDevs.acme/Car Key2 acc://DefiDevs.acme/Car/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : 5b94f5c9a7b19cc2c519116c9019848df4de4fb31be0e5adf6c99802ab8683c2
Signature 0 Hash : 98a2bfb209e63da0be9d945cf8538555c5cac25d8a706ebe73d8070002b20de2
Simple Hash : 730ca4e3f825d078b219afbfae2ae50ffc382a736a86d3ae865e8f5b3d4ac713
Error code : ok
Result :
```

### **Adding Credits to a Sub-ADI Key Page**

**Syntax**

```
accumulate credits <origin lite account> <lite account or key page url><amount> 
```

**Command**

```
./accumulate credits acc://f338762f7013acb0fd5e1480c20df47ff836862adbd6e0f1/ACME acc://DefiDevs.acme/Car/Keybook/1 10000
```

The above command will return an output similar to the following:

```
Transaction Hash : c6eabf824a4710ad427306b4f0f72158f76a6d1ddda5d15c5ff7f5d3ae048a63
Signature 0 Hash : 05470466229b5747ce2c80e6dfd6176d0701e3e893dfc7408c9caa824a51ee21
Simple Hash : fbe8ba8ba462ec7edbed869a1e86036ac48db2230347b0e060b109e125c36943
Error code : ok
Result : Oracle $0.05 / ACME
Credits 10000.00
Amount 2000.00000000 ACME
```

### **Create a Sub-Sub-ADI**

In the example below, the Origin ADI URL is the Sub-ADI and the ADI URL to create is the Sub-Sub-ADI

**Syntax**

```
accumulate adi create [origin-adi-url] [wallet signing key name] [key index (optional)] [key height (optional)] [adi url to create] [public key or wallet key name] [key book url (optional)] [public key page 1 (optional)] Create new ADI for another ADI
```

**Command**

```
./accumulate adi create acc://DefiDevs.acme/Robot Key2 acc://DefiDevs.acme/Robot/MrRoboto Key2
```

The above command will return an output similar to the following:

```
Transaction Hash : 0c681b2bdf1c3608a675bb8a6111040979b33fb6c7f049c2fc31fe7ebb4dca31
Signature 0 Hash : 5190c67a22f61c53bba47cd9d8e081c971900c0d6b5bebf96468907646b5c2d4
Simple Hash : 971debec83777998f35715ba640429de57a4dc70b593997c6e10bd8a2f38a5cf
Error code : ok
Result :
```

### **ADI Token Account**

An ADI can have different account types such as an ADI Token Account. An ADI can have multiple ADI Token Accounts, but each ADI token account can only hold one type of token such as ACME, Accumulate’s native token.

| <p><strong>Token Account</strong></p><p>Sender/Receiver</p> | Lite Token Account | ADI Token Account | Sub-ADI Token Account |
| ----------------------------------------------------------- | ------------------ | ----------------- | --------------------- |
| Lite Token Account                                          | X                  | X                 | X                     |
| ADI Token Account                                           | X                  | X                 | X                     |
| Sub-ADI Token Account                                       | X                  | X                 | X                     |

This matrix doesn’t capture sub-sub ADI token accounts and sub-sub-sub ADI Token accounts etc.

### **Create an ADI Token Account**

The creation of an ADI Token Accounts requires Credits. These Credits must reside within the Key Page of the Key Book associated with the ADI Token Account. As per the fee schedule, 25 credits are required.

**Syntax**

```
accumulate account create token [actor adi] [signing key name] [key index (optional)] [key height (optional)] [new token account url] [tokenUrl] [keyBook (optional)] [flags]
```

**Command**

```
./accumulate account create token acc://DefiDevs.acme Key1 acc://DefiDevs.acme/Tokens acc://ACME acc://DefiDevs.acme/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : cb9e0d5d0c6b90395bf08deb1a048d9552dfa3a5e068318847a7d1573120c927
Signature 0 Hash : 9504352f6f0dcd467934f9497129468737bab04f9c10592fc15dd38b070a54ed
Simple Hash : c53950eff4d6f0a22e5bb72f231876ad1684b28a2a0f675ef3bf0deeef43c974
Error code : ok
Result :
```

### **QR Codes**

Within the CLI, QR codes can be generated for accounts such as an ADI token account.

**Syntax**

```
./accumulate account qr [Token account]
```

**Command**

```
./accumulate account qr acc://DefiDevs.acme/Tokens
```

The above command will return an output similar to the following:

![](<../.gitbook/assets/Screenshot 2022-07-20 at 15.00.43.png>)

### **Sub-ADI Token Account**

**Syntax**

```
accumulate account create token [actor adi] [signing key name] [key index (optional)] [key height (optional)] [new token account url] [tokenUrl] [keyBook (optional)] [flags]
```

**Command**

```
./accumulate account create token acc://DefiDevs.acme/Robot Key2 acc://DefiDevs.acme/Robot/Tokens acc://ACME acc://DefiDevs.acme/Robot/book
```

The above command will return an output similar to the following:

```
Transaction Hash : ab1bf8daa1513bd72a43d33dc5ee86d28d20ba8a275ae32a4340e512281816d1
Signature 0 Hash : 7f511785d08be697f7775445778ab52070b0ba8291569aadfb07ac574eccd112
Simple Hash : 9b2746b7a8adf4e52992d67015f4244aa2a07f9897c9c1391398d12c8a68862b
Error code : ok
Result :
```

### **Sending Tokens**

#### **Lite Token Account to Lite Token Account**

From the matrix above, you can send tokens in multiple ways.

**Syntax**

```
accumulate tx create [origin url] [signing key name] [key index (optional)] [key height (optional)] [to] [amount] Create new token tx
```

**Command**

```
./accumulate tx create acc://27259b5544176ede283ba745b5a6d1775a281ad2f28abc3d/ACME acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME 100
```

The above command will return an output similar to the following:

```
Transaction Hash : 7661c348b839429d33b62964a69e8c7a7b48a57655eb0ba75dee6e62a6539e15
Signature 0 Hash : 20bb93795e86b52a8379706b52121cc69a078b34a7bf0a542ba58446767a3bc1
Simple Hash : 12eea88a2b11d2d198465ca5a3d235745b376a2e89538d0794edac377f8d5b91
Error code : ok
Result :
```

**Lite Token Account to ADI Token Account**

**Syntax**

```
accumulate tx create [origin url] [signing key name] [key index (optional)] [key height (optional)] [to] [amount] Create new token tx
```

**Command**

```
./accumulate tx create acc://27259b5544176ede283ba745b5a6d1775a281ad2f28abc3d/ACME acc://DefiDevs.acme/Tokens 100
```

The above command will return an output similar to the following:

```
Transaction Hash : f3523717198218cdf68e0e1721dcbaaa0e26daa946ac0d444d6a2eb110d80766
Signature 0 Hash : 5da4435ab9efb98121b83a6f0f82dfa182e67ac2e67506d5ab16c03dd926e970
Simple Hash : 63b5804ea8978a3551b09ce9fd5735e3e467caad1ca0f83fbefc0d0bdabf1aba
Error code : ok
Result :
```

**Lite Token Account to Sub-ADI Token Account**

**Syntax**

```
accumulate tx create [origin url] [signing key name] [key index (optional)] [key height (optional)] [to] [amount] Create new token tx
```

**Command**

```
./accumulate tx create acc://27259b5544176ede283ba745b5a6d1775a281ad2f28abc3d/ACME acc://DefiDevs.acme/Robot/Tokens 50
```

The above command will return an output similar to the following:

```
Transaction Hash : dfc0e7985b39093905d3bbeba30a2c62f19e6a5831ab19eac23a806cc722a52a
Signature 0 Hash : c91e7e0dc8af91a86479e52c2c594a3c6e805f719fce2fd3c7349db4f4d151ed
Simple Hash : 2dee95a8ab0fc3aaaf1d9dbd15bc98e6bb4620d9968c99bc0e7e90e981ba0b48
Error code :
```

{% hint style="info" %}
The signing Key used to sign ADI related token transactions must be specified.
{% endhint %}

**ADI Token Account to Lite Token Account**

**Syntax**

```
accumulate tx create [Token url] [signing key name] [origin lite account] [amount]
```

**Command**

```
./accumulate tx create acc://DefiDevs.acme/Tokens Key2 acc://27259b5544176ede283ba745b5a6d1775a281ad2f28abc3d/ACME 5
```

The above command will return an output similar to the following:

```
Transaction Hash : 1a4df2b595cc31f6f757e746220a553e35f537657a0ed316a4a96efafef14b70
Signature 0 Hash : 9c9e3c8fb538c9be02b95104ed5d250df952a928522b121a9e4a332f90b007b5
Simple Hash : 53fb8484089d7d5446189b95fda6f13a596749cd05bf7152b3fa0f02a773d664
Error code : ok
Result :
```

**ADI Token Account to ADI Token Account**

**Syntax**

```
accumulate tx create [Token url] [signing key name] [Token url] [amount]
```

**Command**

```
./accumulate tx create acc://Google.acme/Tokens Key5 acc://DefiDevs.acme/Tokens 50000
```

The above command will return an output similar to the following:

```
Transaction Hash : b19693227a78e9a77b33c8ced3478859b546c5eb62432213ee166c244c82c9b3
Signature 0 Hash : fd62872f6b50d77ad2f7f5b1094044742753bef54b727cefcb9d374b81c93126
Simple Hash : afbd3cd9446cf8e2d330ad0196885b97e4b24117b37a97481c420ef3364dfa11
Error code : ok
Result :
```

**ADI Token Account to Sub-ADI Token Account**

**Syntax**

```
accumulate tx create [Token url] [signing key name] [Sub-Token url] [amount]
```

**Command**

```
./accumulate tx create acc://Google.acme/Tokens Key5 acc://DefiDevs.acme/Robot/Tokens 50000
```

The above command will return an output similar to the following:

```
Transaction Hash : e4c365656e79f2e32d8437e6d1d506a7af3f0dbb1e7b66be88c3b4733718d92d
Signature 0 Hash : e9604249de1ce9ea24f260fba43614f300485f73b7ebb577649753dd256b5add
Simple Hash : c4677739bafe5e0172d1cc809ac99f064ea44c1c20d0786b51acaf8b2581cc5d
Error code : ok
Result :
```

**Sub-ADI Token Account to Lite Token Account**

**Syntax**

```
accumulate tx create [Sub-Token url] [signing key name] [origin lite account] [amount]
```

**Command**

```
./accumulate tx create acc://Google.acme/Car/Tokens Key5 acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME 500
```

The above command will return an output similar to the following:

```
Transaction Hash : c113830891189d6629ba3a805c4986b9b2982c3c2b8fd56a4c3885f6f5f67f17
Signature 0 Hash : c00b898a3fad87c5409307ebe5fc4e36ec3a3b48591f098ac687a378a8fe6ad7
Simple Hash : 07356e79eb4667006b59c29a9cbc87a3eaf454182d0fb03e462514376d7cfd33
Error code : ok
Result :
```

**Sub-ADI Token Account to ADI Token Account**

**Syntax**

```
accumulate tx create [Sub-Token url] [signing key name] [Token url] [amount]
```

**Command**

```
./accumulate tx create acc://Google.acme/Car/Tokens Key5 acc://DefiDevs.acme/Tokens 500
```

The above command will return an output similar to the following:

```
Transaction Hash : b2ee0db7c9ec0408422debd5ec97b6e117719a5214ae461ffce55883f9e2d81d
Signature 0 Hash : 6a1b03cf932df5c7cf4e366c5d41c075a8854ab189b383555de5e1106ce33898
Simple Hash : b94358ff85c232bfef3523e9ca2e466281a181769c3c039127c1641d3601d4a7
Error code : ok
Result :
```

**Sub-ADI Token Account to Sub-ADI Token Account**

**Syntax**

```
accumulate tx create [Sub-Token url] [signing key name] [Sub-Token url] [amount]
```

**Command**

```
./accumulate tx create acc://Google.acme/Car/Tokens Key5 acc://DefiDevs.acme/Robot/Tokens 500
```

The above command will return an output similar to the following:

```
Transaction Hash : 164521b1d09a3d3b75014e24afef6fd7caa1e1b73de17a61f07ba51ceb6568da
Signature 0 Hash : d9615532fc9a5f23914ecddc2f7da94ed8066cb5928e12a8b0d9455595a50608
Simple Hash : 4d22ca9d28da2ce87928e5735069427b4b418df2a646391192289e6165f19fe5
Error code : ok
Result :
```

### **Staking**

Setup staking

Usage: accumulate staking convert \[account] \[key\[@signer]] \[flags]

Available Commands: convert Convert an existing token account into a staking account

Flags: \
\--delegate url The account the stake should be delegated to -h, --help help for staking \
****--rewards url Staking rewards account, if rewards should not be sent back into the staking account \
\--type StakingType Type of staking account (pure, delegated, core-validator, core-follower, or staking-validator) (default inactive)\
\--lockup Number of quarters stake will be locked (min. 2 max. 14)\
\
Delegated Staking Example:

./accumulate staking convert hello.acme/staking ben --delegate example.acme --rewards hello.acme/staking --type delegated --lockup 4\
\
Password: \*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*

```
    Transaction Hash        : 25c8e094d31e08cf13881591e812d27c342398858fa20cb70927e243e7830d3b
    Signature 0 Hash        : 6cb358549a29cfa4086851b9c47c2aa57d3bb284ef59568b059393d735a4ea6a
    Simple Hash             : d46e44f59efb4d6d4be73550d8c92a82338351ab7c2079ba88c404cd04c6eb1b
    Error code              : ok
    Result                  :
```

****

### **Token Issuer**

A Token Issuer defines the properties of a custom token to be issued such as the symbol and supply limit. When creating an ADI Token Account that will accept a custom token, the Token Issuer must be specified instead of acc://ACME. To create a Custom Lite Token account the Token Issuer must issue the tokens to the Lite Identity (URL without /ACME) with Token Issuer URL appended to the Lite Identity address.

### **Create a Token Issuer**

**Syntax**

```
accumulate token create [origin adi or lite url] [adi signer key name (if applicable)] [token issuer url][BS4] [symbol] [precision (0 - 18)] [supply limit] [properties URL (optional)] [flags]
```

**Command**

```
./accumulate token create acc://DefiDevs.acme Key2 acc://DefiDevs.acme/AI AI 1 100000000
```

The above command will return an output similar to the following:

```
Transaction Hash : 1c3831173fbe09247386fa9630f80de13b160dfb7d2f8361dfb7a3e440a492d9
Signature 0 Hash : ebaa7ebcd6a495d84b822bd8f70afe8c9b266321bc2955c3fdcba8a7eb9ebdbc
Simple Hash : 469615f0d9f4a31cccc5b641e752892a43c1a03eab8cb11c8eee95d8d6254724
Error code : ok
Result :
```

### **Create a Custom ADI Token Account**

**Syntax**

```
// Some code./accumulate account create token [ADI URL][Signing Key][ADI Token Account][Token Issuer]
```

**Command**

```
./accumulate account create token acc://DefiDevs.acme Key2 acc://DefiDevs.acme/AITokens acc://DefiDevs.acme/AI
```

The above command will return an output similar to the following:

```
Transaction Hash : 131c29f769d2a7d7ce8701128dbdaf1c844f998259dcad011c01ed37442ec9c7
Signature 0 Hash : 9bde03cfff80e951246523611cef2d716806efa4e3893c5ee5ecbdac7dea884f
Simple Hash : 32e9f4894f76d519e979672c142c2ab453787dd93acedd313ed8527dbc19a9fa
Error code : ok
Result :
```

### **Issuing Tokens**

**Syntax**

```
accumulate token issue [adi token url] [signer key name] [recipient url] [amount] [flags]
```

**Command**

```
./accumulate token issue acc://DefiDevs.acme/AI Key2 acc://DefiDevs.acme/AITokens 10000
```

The above command will return an output similar to the following:

```
Transaction Hash : fdc8a0a1e243471b49bb071afc06eb90b14b5319a936e7738029b47593346da3
Signature 0 Hash : 05f594fa041de539347d11362c0aea7a170519519eaf191ca5257a8168938bf8
Simple Hash : 203c7045e3ddd1c7fa6e48d325f3d12022626d39aaf186defe489f152850cfa3
Error code : ok
Result :
```

### **Creating a Custom Lite Token Account by Issuing Tokens to it**

Append the Token Issuer Account to the Lite Token Account Address to receive custom tokens.

**Command**

```
./accumulate tx create acc://DefiDevs.acme/AITokens Key2 acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/DefiDevs.acme/AI 10
```

The above command will return an output similar to the following:

```
Transaction Hash : 015515d4fea655d2f99af36adbdb4e9fdb7462b018d75916fb628ceadefe852b
Signature 0 Hash : 2a14c86cd3e20d2917a5884c24c66d263633176b4c3b2d63b51bc8ecd6417273
Simple Hash : 6e42d102fe9b29b226b3a48f0db1e9dd8a63c735e7db357d92e731609572dd5a
Error code : ok
Result :
```

### **Burn Tokens**

**Burn Tokens from a Lite Token Account**

**Syntax**

```
accumulate token burn [adi or lite token account] [adi signer key name (if applicable)] [amount] [flags]
```

**Command**

```
./accumulate token burn acc://0143b52490530b90eef9b1a2405e322c6badc1e90e200c56/ACME 10
```

The above command will return an output similar to the following:

```
Transaction Hash : 3b873d31fcb1555dece4e07288c936cb97bd9b95fcdc4975367ac593f6dfed64
Signature 0 Hash : a9281063dacd05fc5097a919d12a6498e7c3e339c77e970fb9832645e409daba
Simple Hash : b0f13b056216effccad96f2b328a3c579b86f8df147a9535d196638ebfc6bc0e
Error code : ok
Result :
```

### **Burn Tokens from an ADI Token Account**

A decimal value must be added (can be 0) when burning tokens

**Syntax**

```
 accumulate token burn [adi or lite token account] [adi signer key name (if applicable)] [amount] [flags]
```

**Command**

```
./accumulate token burn acc://DefiDevs.acme/Tokens Key2 9[BS5] .0
```

The above command will return an output similar to the following:

```
Transaction Hash : e1e2ca605288e35a78d2413156e3d718f601330f2d0c684494099d301d1b97e2
Signature 0 Hash : b11eba4bc508076d1b3e01d2eee40892eaccccc3d83efe17126b850c93057c8f
Simple Hash : 26f5d0f163f677da0d840e2fbbd17ace0663fe44c8de2c207cd95fdd2e42b70a
Error code : ok
Result :
```

### **Create an ADI Data Account**

Create an ADI Data Account

**Syntax**

```
accumulate account create data [actor adi url] [signing key name] [key index (optional)] [key height (optional)] [adi data account url] [key book (optional)] Create new data account
```

**Command**

```
./accumulate account create data acc://DefiDevs.acme Key1 acc://DefiDevs.acme/Data acc://DefiDevs.acme/Keybook
```

The above command will return an output similar to the following:

```
Transaction Hash : 55bf5c8fcb3603185e9c25f481d22843ff6c5a4398fa276d2764cdc91641a3f0
Signature 0 Hash : 8ef47e055cf47b4152f7243d3cc2e9f970b3dde79af614b8c6718f76b71219f3
Simple Hash : 0ad1a784211354d5893c25a42f7dabe5e02b65abbc3c57007add3a450c020bf8
Error code : ok
Result :
```

### **Write to an ADI Data Account**

**Syntax**

```
accumulate data write [data account url] [signingKey] [extid_0 (optional)] ... [extid_n (optional)] [data] Write entry to your data account. Note: extid's and data needs to be a quoted string or hex
```

**Command**

```
./accumulate data write acc://DefiDevs.acme/data Key2 "entryhashtest1"
```

The above command will return an output similar to the following:

```
Entry Hash :8de01ef68a5b5d667008f30e2099b8dd11120efc4fd1d21462521f68ab87d4bb
Transaction Hash : f3c71bd6b6677f69ef87e98d966b705a75dec0f8e8dfed292bd39b09e2ee2969
Signature 0 Hash : b0490493d82b23259672111ea5170ac19257a35b9de41d5278262eee7a326783
Simple Hash : 1c30a9a75adf93268a23d034a43fd358958ad7a91f794ecf10f888c96f7d1121
Error code : ok
Result : Account URL acc://DefiDevs.acme/data
Account ID dfe2c4ee93777ff5fb97e1d8f2ddd45336044e2a3396db8344a73b94e6fb0d45
Entry Hash 8de01ef68a5b5d667008f30e2099b8dd11120efc4fd1d21462521f68ab87d4bb
```

### **Querying an ADI Data Account by URL**

**Syntax**

```
accumulate data get [DataAccountURL] Get most current data entry by URL
```

**Command**

```
./accumulate data get acc://DefiDevs.acme/Data
```

The above command will return an output similar to the following:

```
{"type":"dataEntry","mainChain":{"height":4,"count":4,"roots":["55bf5c8fcb3603185e9c25f481d22843ff6c5a4398fa276d2764cdc91641a3f0","7b58817aa8a52bce3ffd8c40e11322dc945e3debc365d5cc7204be9500b12b7d","19f66cbbfad4153c1481d88a6990604c6bc46aac176c6347e269f6f9ff7f49b2","f3c71bd6b6677f69ef87e98d966b705a75dec0f8e8dfed292bd39b09e2ee2969"]},"data":{"entry":{"data":["656e747279686173687465737431"]},"entryHash":"8de01ef68a5b5d667008f30e2099b8dd11120efc4fd1d21462521f68ab87d4bb"},"chainId":"dfe2c4ee93777ff5fb97e1d8f2ddd45336044e2a3396db8344a73b94e6fb0d45"}
```

### **Querying an ADI Data Account by URL and a Specific Entry Hash**

**Syntax**

```
accumulate data get [DataAccountURL] [EntryHash] Get data entry by entryHash in hex
```

**Command**

```
./accumulate data get acc://DefiDevs.acme/Data 8de01ef68a5b5d667008f30e2099b8dd11120efc4fd1d21462521f68ab87d4bb
```

The above command will return an output similar to the following:

```
{"type":"dataEntry","mainChain":{"height":4,"count":4,"roots":["55bf5c8fcb3603185e9c25f481d22843ff6c5a4398fa276d2764cdc91641a3f0","7b58817aa8a52bce3ffd8c40e11322dc945e3debc365d5cc7204be9500b12b7d","19f66cbbfad4153c1481d88a6990604c6bc46aac176c6347e269f6f9ff7f49b2","f3c71bd6b6677f69ef87e98d966b705a75dec0f8e8dfed292bd39b09e2ee2969"]},"data":{"entry":{"data":["656e747279686173687465737431"]},"entryHash":"8de01ef68a5b5d667008f30e2099b8dd11120efc4fd1d21462521f68ab87d4bb"},"chainId":"dfe2c4ee93777ff5fb97e1d8f2ddd45336044e2a3396db8344a73b94e6fb0d45"}
```

### **Querying an ADI Data Account by URL and a Specific Index**

**Syntax**

```
accumulate data get [DataAccountURL] [start index] [count] expand(optional) Get a set of data entries starting from start and going to start+count. if "expand" is specified, data entries will also be provided
```

**Command**

```
./accumulate data get acc://DefiDevs.acme/Data 0 1
```

The above command will return an output similar to the following:

```
{"type":"dataSet","items":[{"entry":{},"entryHash":"a6b54c20a7b96eeac1a911e6da3124a560fe6dc042ebf270e3676e7095b95652"}],"start":0,"count":1,"total":3}
```

### **Write to an ADI Data Account (Scratch Chain)**

Write scratch data command:

**Syntax**

```
./accumulate data write [ADI Data Account][Signing Key] --scratch [data]
```

**Command**

```
./accumulate data write DeFiDevs.acme/data 1d92f317cb3ed1b2992d345ae9546ec0d66c069c4b471c04 --scratch "DATA"
```

The above command will return an output similar to the following:

```
Entry Hash :12e90b8e74f20fc0a7274cff9fcbae14592db12292757f1ea0d7503d30799fd2
Transaction Hash : 39890ec7018199c8a4186ecd20634e3a64c5d8e8c15835035689655d8d37e8ae
Signature 0 Hash : a30f0470c60bb21340de902609034d530694f6d81ca2ddf670bb98c1a349d675
Simple Hash : f9c49c07e7c0e2774fa9c22dfad5a5c100755b29f83cbffd53f84a059cc88787
Error code : ok
Result : Account URL acc://StebbyWebby.acme/superData
Account ID edb5a7e9186c418e3024cfa191d781929777470d21d7b2d4aa049f077737d589
Entry Hash 12e90b8e74f20fc0a7274cff9fcbae14592db12292757f1ea0d7503d30799fd2
```

### **Create a Sub-ADI Data Account**

**Syntax**

```
accumulate account create data [actor adi url] [key name[@key book or page]]  [adi data account url] --authority key
book (optional) 
```

The actor ADI is an AD or Sub-ADI

**Command**

```
./accumulate account create data acc://DefiDevs.acme/Robot Key2 acc://DefiDevs.acme/Robot/Data acc://DefiDevs.acme/Robot/Book
```

The above command will return an output similar to the following:

```
Transaction Hash : 9c60e74028f727337d60bf6239c5bfb1a46de9580a6d8c89b1bf184a9988da9b
Signature 0 Hash : d64a914c3f63804d2c38bd79805091f2f0a8d2072e9cbd517bb022d18dfe4cbe
Simple Hash : 1647fa7c763ec3b88aa9cb2e61cd28c1afed2ddffc869c9702bdbd8cb22c43df
Error code : ok
Result :
```

### **Write to a Sub-ADI Data Account**

**Syntax**

```
accumulate data write [data account url] [signingKey] [extid_0 (optional)] ... [extid_n (optional)] [data] Write entry to your data account. Note: extid's and data needs to be a quoted string or hex
```

**Command**

```
./accumulate data write acc://Test.acme/SubADITest/Data Key1 'Key6'
```

The above command will return an output similar to the following:

```
Entry Hash :2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
Transaction Hash : 1cda6093788c0d10a4f9ff0b8f135629388dc3446672147947ecd2c4a0c8c7a3
Signature 0 Hash : 2a53c605b56fa09977ae8a3ad8ed170e38b1900c5961b31d72d4e62dd547743e
Simple Hash : 6aaa93d3fe0830ff20943ab4911f40fdfd8611984e17ec9ec7aa21a956b70b97
Error code : ok
Result : Account URL acc://Test.acme/SubADITest/Data
Account ID a3bd84932993317d8987cbc1ecccb0d230565feb55096cc1fc9ea3637d520942
Entry Hash 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
```

### **Querying a Sub-ADI Data Account by URL**

**Syntax**

```
accumulate data get [DataAccountURL] Get most current data entry by URL
```

**Command**

```
./accumulate data get acc://Test.acme/SubADITest/Data
```

The above command will return an output similar to the following:

```
{"type":"dataEntry","mainChain":{"height":2,"count":2,"roots":[null,"d4b13e8793e57c63e8df020e07b13364d9404f1bfac83c183681cc59e6650a59"]},"data":{"entry":{"data":["68656c6c6f"],"type":"accumulate"},"entryHash":"2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"},"chainId":"a3bd84932993317d8987cbc1ecccb0d230565feb55096cc1fc9ea3637d520942"}
```

### **Querying a Sub-ADI Data Account by URL and a Specific Entry Hash**

**Syntax**

```
accumulate data get [DataAccountURL] [EntryHash] Get data entry by entryHash in hex
```

**Command**

```
./accumulate data get acc://Test.acme/SubADITest/Data 2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824
```

The above command will return an output similar to the following:

```
{"type":"dataEntry","mainChain":{"height":2,"count":2,"roots":[null,"d4b13e8793e57c63e8df020e07b13364d9404f1bfac83c183681cc59e6650a59"]},"data":{"entry":{"data":["68656c6c6f"],"type":"accumulate"},"entryHash":"2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"},"chainId":"a3bd84932993317d8987cbc1ecccb0d230565feb55096cc1fc9ea3637d520942"}
```

### **Querying a Sub-ADI Data Account by URL and a Specific Index**

**Syntax**

```
accumulate data get [DataAccountURL] [start index] [count] expand(optional) Get a set of data entries starting from start and going to start+count, if "expand" is specified, data entries will also be provided
```

**Command**

```
./accumulate data get acc://Test.acme/SubADITest/Data 0 10
```

The above command will return an output similar to the following:

```
{"type":"dataSet","items":[{"entry":null,"entryHash":"2cf24dba5fb0a30e26e83b2ac5b9e29e1b161e5c1fa7425e73043362938b9824"}],"start":0,"count":10,"total":1}
```

### **Write to a Sub-ADI Data Account (Scratch Chain)**

**Syntax**

```
accumulate data write [data account url] [signingKey] --scratch (optional) [extid_0 (optional)] ... [extid_n (optional)] [data]
```

**Command**

```
./accumulate data write DeFiDevs.acme/subadi/data 1d92f317cb3ed1b2992d345ae9546ec0d66c069c4b471c04 --scratch "DATA"
```

The above command will return an output similar to the following:

```
Entry Hash :12e90b8e74f20fc0a7274cff9fcbae14592db12292757f1ea0d7503d30799fd2
Transaction Hash : 39890ec7018199c8a4186ecd20634e3a64c5d8e8c15835035689655d8d37e8ae
Signature 0 Hash : a30f0470c60bb21340de902609034d530694f6d81ca2ddf670bb98c1a349d675
Simple Hash : f9c49c07e7c0e2774fa9c22dfad5a5c100755b29f83cbffd53f84a059cc88787
Error code : ok
Result : Account URL acc://StebbyWebby.acme/superData
Account ID edb5a7e9186c418e3024cfa191d781929777470d21d7b2d4aa049f077737d589
Entry Hash 12e90b8e74f20fc0a7274cff9fcbae14592db12292757f1ea0d7503d30799fd2
```

### **How to allow anyone to write to a data account?**

When an auth is **"disabled"** for a data account, anyone with valid signature can write into that account.

**Steps:**

1. Disable auth
2. Sign the transaction
3. Write into data account by signing with any valid user.&#x20;

**Disable Auth**

```
./accumulate auth disable acc://automation9876542.acme keyed25519SE1F acc://automation9876542.acme/book 
```

**Sign the transaction**

```
./accumulate tx sign acc://automation9876542.acme/book/1 keyed25519SE1F@automation9876542.acme/book fbbec95994a3d92ee0baa7a8b7a04b126b259309e8626fcc1f44b068cc9026b7 
```

**Write to data account**

{% code overflow="wrap" %}
```
./accumulate data write acc://automation9876542.acme/dataAccount72 keyed25519VUOK@RajagopalIndia789.acme/book "546573742064617461206d70684e55385a7a7467474c467649316a744748"
```
{% endcode %}

### **Minor Blocks**

**Syntax**

```
accumulate blocks minor [partition-url] [start index] [count] [tx fetch mode expand|ids|countOnly|omit (optional)] [block filter mode excludenone|excludeempty (optional)] 
```

The partition url is a BVN ADI, or a DN ADI

**Command**

```
./accumulate blocks minor acc://dn 0 2
```

The above command will return an output similar to the following:

```
Minor block result Start: 0 Count: 2 Total: 0
==========================================================================
--- block #1, blocktime 2022-05-03 17:20:17 +0000 UTC:
total tx count : 4
txid #1 : e43be90e349210456662d8b8bdc9cc9e5e46ccb07f2129e7b57a8195e5e916d5
txid #2 : c843452b4943c755c020ddc10b156fc78c712a187ce048f9036bda1703e03ef4
txid #3 : 0b6c57a48522f77d11996e36a195e74aa3f13b22b32f31024d565580532703b3
txid #4 : 3c8de66e0d6ca8ef397f3f0a438783179f6d4124f5bce864b5bde6f12e56a009
==========================================================================
--- block #3, blocktime 2022-05-03 17:22:31 +0000 UTC:
total tx count : 4
(type): Synthetic Anchor
Transaction Type: synthetic Anchor
Source: acc://bvn-BVN1
Major: false
RootAnchor: 49a1be0b0dc147d199c37e7c7e5cfd3107f1e437a6d82f32dc7fd6024e835289
RootIndex: 10
AcmeBurnt:
(type): Int
Block: 1
AcmeOraclePrice: 0
Receipts:
(type): Synthetic Anchor
Transaction Type: synthetic Anchor
Source: acc://bvn-BVN0
Major: false
RootAnchor: f5ec625566aebf3c0ef06883d836ef40bc91995ad0581491ee2d099d215ae7b4
RootIndex: 12
AcmeBurnt:
(type): Int
Block: 1
AcmeOraclePrice: 0
Receipts:
```

### **Major Blocks**

**Syntax**

```
accumulate blocks major [partition-url] [start index] [count]
```

The partition url is a BVN, ADI, or a DN ADI

**Command**

```
./accumulate blocks minor acc://dn 0 2
```

The above command will return an output similar to the following:

```
Major block result Start: 0      Count: 1        Total blocks: 8
==========================================================================
--- major block #1, major blocktime 0001-01-01 00:00:00 +0000 UTC:
    minor block index: 1
    minor block time : 2022-08-06 05:48:28 +0000 UTC
    minor block index: 2
    minor block time : 2022-08-06 05:48:28 +0000 UTC
    minor block index: 3
    minor block time : 2022-08-06 05:50:42 +0000 UTC
    minor block index: 4
    minor block time : 2022-08-06 05:50:43 +0000 UTC
    minor block index: 5
    minor block time : 2022-08-06 05:50:45 +0000 UTC
    minor block index: 7
    minor block time : 2022-08-06 05:50:48 +0000 UTC
    minor block index: 8
    minor block time : 2022-08-07 01:05:03 +0000 UTC
    minor block index: 9
    minor block time : 2022-08-07 01:05:05 +0000 UTC
```

### **Block Validator Network Minor Blocks**

**Syntax**

```
accumulate blocks minor [subnet-url] [start index] [count] [tx fetch mode expand|ids|countOnly|omit (optional)] [filter synth-anchors only blocks true|false (optional)] Get minor blocks
```

**Command**

```
./accumulate blocks minor acc://bvn-bvn0 0 2
```

The above command will return an output similar to the following:

```
Minor block result Start: 0 Count: 2 Total: 0
==========================================================================
--- block #1, blocktime 2022-05-03 17:20:17 +0000 UTC:
total tx count : 3
txid #1 : e43be90e349210456662d8b8bdc9cc9e5e46ccb07f2129e7b57a8195e5e916d5
txid #2 : c843452b4943c755c020ddc10b156fc78c712a187ce048f9036bda1703e03ef4
txid #3 : 0b6c57a48522f77d11996e36a195e74aa3f13b22b32f31024d565580532703b3
==========================================================================
--- block #3, blocktime 2022-05-03 17:22:31 +0000 UTC:
total tx count : 3
(type): Synthetic Anchor
Transaction Type: synthetic Anchor
Source: acc://dn
Major: false
RootAnchor: e5d3857d3766c53dd2831b550e3ca05d87a15549befd678cd6e5ec338ba97474
RootIndex: 13
AcmeBurnt:
(type): Int
Block: 1
AcmeOraclePrice: 500
Receipts:
(type): Synthetic Anchor
Transaction Type: synthetic Anchor
Source: acc://dn
Major: false
RootAnchor: e5d3857d3766c53dd2831b550e3ca05d87a15549befd678cd6e5ec338ba97474
RootIndex: 13
AcmeBurnt:
(type): Int
Block: 1
AcmeOraclePrice: 500
Receipts:
```

## Describe

**Describe the Accumulate Node**

./accumulate describe {"network":{"id":"DevNet","partitions":\[{"basePort":26656,"id":"Directory","nodes":\[{"address":"http://127.0.1.1:26656","type":"validator"}],"type":"directory"},{"basePort":26756,"id":"BVN1","nodes":\[{"address":"http://127.0.1.1:26756","type":"validator"}],"type":"blockValidator"}],"subnets":\[{"basePort":26656,"id":"Directory","nodes":\[{"address":"http://127.0.1.1:26656","type":"validator"}],"type":"directory"},{"basePort":26756,"id":"BVN1","nodes":\[{"address":"http://127.0.1.1:26756","type":"validator"}],"type":"blockValidator"}]},"networkAnchor":"0000000000000000000000000000000000000000000000000000000000000000","networkType":"directory","partitionId":"Directory","values":{"globals":{"feeSchedule":{"createIdentitySliding":\[204800000,102400000,51200000,25600000,12800000,6400000,3200000,1600000,800000,400000,200000,100000]},"majorBlockSchedule":"0 \*/12 \* \* \*","operatorAcceptThreshold":{"denominator":3,"numerator":2},"validatorAcceptThreshold":{"denominator":3,"numerator":2\}},"network":{"networkName":"DevNet","partitions":\[{"id":"BVN1","type":"blockValidator"},{"id":"Directory","type":"directory"}],"validators":\[{"partitions":\[{"active":true,"id":"Directory"},{"active":true,"id":"BVN1"}],"publicKey":"986511759eef5601701324cfa8961f99c3aad1dc62ef5932cbf63adc5e27a6b9","publicKeyHash":"aa157582befd1e5e150dbc4a0af48136e82a9b917b6f5af2ea5c732249ad4427"}]},"oracle":{"price":50000000},"routing":{"overrides":\[{"account":"acc://ACME","partition":"Directory"},{"account":"acc://bvn-BVN1.acme","partition":"BVN1"},{"account":"acc://dn.acme","partition":"Directory"}],"routes":\[{"partition":"BVN1"}]\}}}\


## Multiple operations in single transaction

## Send tokens to multiple parties&#x20;

User can "send tokens" to multiple parties in a single transaction as follows

{% code overflow="wrap" %}
```
accumulate tx execute acc://automationAdi138.acme/token24 addKeyed255198OA8 "{ type: sendTokens, to: [ { url: "acc://automationAdi138.acme/token943", amount: '10' }, { url: "automationAdi138.acme/token382", 
amount: '5' } ] }"
```
{% endcode %}

The above command will return an output similar to the following:

```
Transaction Hash        : 3260d61d1efdf01b3c19abe5aa24cbc44ba352e319da2240aba301a169263d69
        Signature 0 Hash        : 325bcfc2b50a05193d843d75fdb9f7d03410af31b0c73dc402c3c1c01046a86f
        Simple Hash             : c65c5fc325104e1839e0fc7c68226ee7533e1b32ebcf4dd9bb9381d010565b5d      
        Error code              : ok
        Result                  :
```

## Issue tokens to multiple parties&#x20;

User can "issue tokens" to multiple parties in a single transaction as follows

{% code overflow="wrap" %}
```
./accumulate tx execute acc://automationAdi138.acme/TokenIssuerVRG addKeyed255198OA8 "{ type: issueTokens, to: [ { url: "acc://automationAdi138.acme/CustomTokenDFQ2X", amount: '5' }, { url: "acc://automationAdi138.acme/CustomTokenE2b7g", amount: '5' } ] }"
```
{% endcode %}

The above command will return an output similar to the following:

```
Transaction Hash        : 0eb31c163d28d5ba6a6d049a31173d3470dc039a53dbe867c35c01a687b47776      
Signature 0 Hash        : a50215753c1d3a3d0978aae8e05c2e623be6570a9ca3da0edfb51f4e520d1078      
Simple Hash             : c6c5ed51cf4a2c6df64d6ca323fc15ce69b697fc7e1bdb7a00bffeec11b0707c      
Error code              : ok
Result                  :
```

## Multiple updates to a key page&#x20;

When a user wants to perform _"update"_ operation on a key page and _"add"_ a new key to a key page, he/she can perform both with a single transaction as follows

{% code overflow="wrap" %}
```
./accumulate tx execute acc://automation9876542.acme/book/2 keyed25519SE1F "{"type": "updateKeyPage", "operation": [{ "type": "update", "oldEntry": {"keyHash": "418ae889ddb30826e68fa66977f29e955a52951afb7056b88a76f13161777515"} ,"newEntry": {"keyHash": "69614ac2db2b9cb07b86bbc6a451f7120e66b1d077f83b0b0e2f09a05258d66e" }}, { "type": "add", "entry": {"owner": "acc://automation9876542.acme/book/2", "keyHash": 
"3ebc9b367208e1834afc5a9819ca6ab54d84e2a529a76267d02594f5fe118db0"}}]}"
```
{% endcode %}

The above command will return an output similar to the following:

```
Transaction Hash        : 20b1bd78b4776ab8defab7542fea5c04e13f6bff9222a20b13634d5622a7b6df      
        Signature 0 Hash        : c80f19d9ee945f41ae595f55a84867c8cbc4eb9baf030ad4454f9cf0275cfe77      
        Simple Hash             : 17d933a0dde79a71c6cfa2bf3c2495790aa8b6ce767c3f970f5596761caa1d5a      
        Error code              : ok
        Result                  :
```

To validate the transaction

```
./accumulate.exe get acc://automation9876542.acme/book/2 

        Credit Balance  :       99.99

        Index  Nonce                          Key Name       Delegate  Public Key Hash
        0      1969-12-31 19:00:00 -0500 EST  key1                     3ebc9b367208e1834afc5a9819ca6ab54d84e2a529a76267d02594f5fe118db0
        1      1969-12-31 19:00:00 -0500 EST  CustomKeymJbU            69614ac2db2b9cb07b86bbc6a451f7120e66b1d077f83b0b0e2f09a05258d66e
```

## Multiple updates to a key page&#x20;

When a user wants to perform multiple _"updateAccountAuth"_ operation, he/she can perform them with a single transaction as follows

{% code overflow="wrap" %}
```
./accumulate tx execute acc://automation9876542.acme keyed25519SE1F "{"type": "updateAccountAuth", "operations": [{ "type": "disable", "authority": "acc://automation9876542.acme/dataAccount82"} ,{ "type": "enable", "authority": "acc://automation9876542.acme/book"}]}" 
```
{% endcode %}

The above command will return an output similar to the following:

```

        Transaction Hash        : 35fc8b37f6242b237c6576e36faec7be8aa8edfe8690b483a0ee0cb7a1621ed4      
        Signature 0 Hash        : 1bb5b781775bbaa790ea15da80681fc943113dddc1af1659b7a78ad665c70b9b      
        Simple Hash             : 174927780ebb211a01c15785ff1b785d07209a5b98eb5fb54b7c27f744992e36      
        Error code              : ok
        Result                  :
```

## Encrypt

Encrypt Wallet Database \
./accumulate encrypt





****
