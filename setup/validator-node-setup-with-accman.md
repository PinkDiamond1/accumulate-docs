# Validator Node Setup with Accman

Please complete the Follower Node Setup guide. To become a Validator Node, a Follower Node is created first. It is recommended to use Accman for this process.

![](<../.gitbook/assets/image (2).png>)

Select "Accumulate - Manage Node" and hit Enter

![](<../.gitbook/assets/image (3).png>)

Scroll Down to “Display Registration Info” and Click Enter

![](../.gitbook/assets/image.png)

The Public Key (pubkey) is what an Operator will provide as their **Validator Key** to the Protocol

The address is a Hash of the Public Key

It is recommended that the Operator's **Operator Key** is different than the Validator Key\


An **Operator Key** can be generated in the Command Line Interface

./accumulate key generate \[Key Name]

./accumulate key generate operatorkey1&#x20;

Password: \*\*\*\*\*\*\*\*&#x20;

name : operatorkey1 lite account : acc://11d3217fda3c863c2e66936826987edb3a4467f540279689/ACME\
public key : **1df37076ff875fc2a9c99a647622d33b1c194ff0d821c40b93fffac1743acca2**\
key type : ed25519

The Public Key in the Output will server as the **Operator Public Key**

_Please Provide the **Validator Public Key** and **Operator Public Key** to a member of the Operator Key Page. Two-thirds of the Operators will sign a transaction to add your **Operator Key** and a second transaction to add your **Validator Key.**_\