# Sending a Transaction with a Lite Token Account

This tutorial will teach you how to create and fund an account, send tokens between the two, send credits, check account balance, and check transaction info.

Lite Accounts are a ‘lite’ version of ADIs that may appeal to users who want to send and receive tokens and maintain a record of their token accounts and transactions despite their comparatively limited utility and flexibility. For more information, see the [Lite Account Deep Dive](../deep-dive/anonymous-token-chains.md) section.

### **Requirements:**

* Basic CLI Knowledge
* [CLI Setup](https://docs.accumulatenetwork.io/accumulate/setup/cli-setup)
* Git

### **1: Generate a lite account**

The first step is to create a lite token account using the account generate command.

This command will create an account URL and the corresponding public key stored locally on your computer.

```
./accumulate account generate
```

{% hint style="info" %}
If you are on Windows, you must use ./accumulate.exe instead.
{% endhint %}

Once you run the command, you should get an output with the address for your token account. It will look something like the following:

```
acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME :   c11d64fa7aca19c365fb4e392fac540033493911e604bf629465132392d18ba4
```

### **2: Funding your account**

You will fund your new account using the faucet command, which will broadcast the existence of your new account and give you some free tokens.

Since this command requires broadcasting to the network, you need to ensure you are connected to a node. We do that with the -s flag then the server address for the node we wish to connect to comes next.

{% hint style="info" %}
Your account connects to the accumulate testnet by default.
{% endhint %}

If you want to connect to the devnet, add this flag and argument -s [https://devnet.accumulatenetwork.io/v2](https://devnet.accumulatenetwork.io/v2)\


**Syntax**

```
./accumulate faucet <your account address> 
```

**Example**

```
./accumulate faucet acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME
```

The above command will return an output similar to the following:

```
 Transaction Hash : 00cf5a4366492b678465b2e4ff73bbe7df99d9eee7b85f053b6c4ee8bf29fbdd 
 Envelope Hash : 89b5a24c608e4d67e23a700acba1db03e4202b9c0a881e2ef5b4fdbfffe3fa5c 
 Simple Hash : 6493d0887aa9838f6d522b3a84a5843308e32f699ae4150da14ad89ad827bc40 
 Error code : ok
```

### **3: Send Credits**

Credits are payments made by users to compensate for the computing energy required to process and validate transactions on the Accumulate protocol.

To send ACME tokens to another account, you need to purchase credits with ACME and send them to a recipient.

Check this [link](https://docs.accumulatenetwork.io/accumulate/getting-started/fees) to view the Base Fees for different transactions.

To send credits to your lite account, run the example command in your terminal

The command below gives your accumulate URL the access to send credits to another lite account.

**Syntax:**

```
accumulate credits <origin lite account> <lite account or key page url><amount> 
```

\
**Example**

```
./accumulate credits acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME 10
```

The above command will return an output similar to the following:

```
 Transaction Hash : d64847cee49418516596c905b12f0002cc6b06decec1356e9c48f0040c1b6f4f 
 Envelope Hash : d24209b25204e300cd53be560cf91fdbeb4eb05f572f7c5acc96a58443658b0e 
 Simple Hash : 07b567df37b86050f6ef636e9118d23926206f459ffd4f82d28f208e7d2151b1 
 Error code : ok 
```

### **4: Check your Balance**

Check the account balance to see how many tokens you have received from the faucet. Then, use the account get command.

**Syntax**

```
./accumulate account get <your account address> 
```

**Example**

```
./accumulate account get acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME 
 
```

The above command will return an output similar to the following:

```
Account Url : acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME 
Token Url : acc://ACME 
Balance : unknown 
Credits : 0 
Nonce : 0 
```

To get it in a json format a -j flag

```
./accumulate account get acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME -j
```

The above command will return an output similar to the following:

```
{"type":"liteTokenAccount","mainChain":{"height":1,"count":1,"roots":["e0ae7b03ca99b41eb1e545fa9b647d933e7b74b127224eef6743e45fdc7b9ac0"]},"data":{"balance":"1000000000","creditBalance":"0","keyBook":"","managerKeyBook":"","tokenUrl":"acc://ACME","type":"liteTokenAccount","url":"acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME"},"chainId":"9c92f4565ea7bc81191a201b2a778e004222b4b3f8701ee57eaca29cb12579d9"}
```

### **5: Send Tokens**

Let's try sending some ACME tokens from one account to the other. You can use the account we already funded as the sending account. You'll need to create an additional account to receive the tokens.

To send the tokens, use the command below.

**Syntax:**

```
./accumulate tx create <sending account> <receiving account> <Amount> 
```

**Example:**

```
./accumulate tx create acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME acc://b3e4778e8940f13e4ddf1716b453b366e2a4b3a59b99bd03/ACME 5 
```

The above command will return an output similar to the following:

```
 Transaction Hash : f8174628b1236865d71473d542691da5c7887210052972bdc22dff97866955ae 
 Envelope Hash : 0c0cb20f870fed7d648641c04689459dbaa591aa5fbef52a7d459967fac3dbc6 
 Simple Hash : 72036bde24d55a7e54177fa9268f94b5281596fca2c82d3074f9cec8dfacda6b 
 Error code : ok
```

### **6: Get Transaction Hash:**

Finally, let's make sure that the transaction was successful. You will use the tx get command to do that, and you will pass in the transaction id ("txid") that you received in the response output from step 5.

**Syntax:**

```
./accumulate tx get <transaction hash>
```

**Example:**

```
./accumulate tx get f8174628b1236865d71473d542691da5c7887210052972bdc22dff97866955ae 
```

The above command will return an output similar to the following:

```
Send unknown from acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME to  
  - Synthetic Transaction :  
--- 
  - Transaction : f8174628b1236865d71473d542691da5c7887210052972bdc22dff97866955ae 
  - Signer Url : acc://5c33543157a40920252fa27d20079925807f611a9c4746c4/ACME 
  - Signatures : 
  - : 02474b235a3ae7fd5c8afc86a731d7b90b79aa9feb3cbb58b3d3aa452f3e48ce2b8bb88bfa7aada62a6b8ed9d2c269a13f31a0d3343d0958c9a337b9d8bd9507 (sig) / c11d64fa7aca19c365fb4e392fac540033493911e604bf629465132392d18ba4 (key) 
  - Key Page : 1 (height) / 0 (index) 
=== 
  - Synthetic Transaction 0 : 4e148c20cf0838718485597c60ce3d7880914d298337bd040b7799ea196b9606 
```
