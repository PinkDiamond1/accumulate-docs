# CLI setup

The Accumulate CLI (Command Line Interface) installation and the binary installation are the fastest way to get Accumulate running locally. This guide will show you how to set up Accumulate locally.

## Two ways of CLI setup

* Binary installation
* From the source

### **1. Binary Installation**

**Installation for three OS**

These are the supported Operating system.

**Widnows | Mac OS | Linux**&#x20;

**Step 1:** Download Accumulate binary file.

If you are running macOS on an Intel-based Mac, use accumulate-darwin-amd64. If you are running macOS on an Apple-silicon Mac, use accumulate-darwin-arm64.

{% tabs %}
{% tab title="Windows" %}
{% embed url="https://gitlab.com/accumulatenetwork/core/wallet/-/jobs/3280126469/artifacts/file/accumulate-windows-amd64.exe" %}
Amd64
{% endembed %}

{% embed url="https://gitlab.com/accumulatenetwork/core/wallet/-/jobs/3280126469/artifacts/file/accumulate-windows-arm64.exe" %}
Arm64
{% endembed %}
{% endtab %}

{% tab title="Mac OS" %}
{% embed url="https://gitlab.com/accumulatenetwork/core/wallet/-/jobs/3280126469/artifacts/file/accumulate-linux-amd64" %}
amd64
{% endembed %}

{% embed url="https://gitlab.com/accumulatenetwork/core/wallet/-/jobs/3280126469/artifacts/file/accumulate-darwin-arm64" %}
arm64
{% endembed %}
{% endtab %}

{% tab title="Linux" %}
{% embed url="https://gitlab.com/accumulatenetwork/core/wallet/-/jobs/3280126469/artifacts/file/accumulate-darwin-amd64" %}
amd64
{% endembed %}

{% embed url="https://gitlab.com/accumulatenetwork/core/wallet/-/jobs/3280126469/artifacts/file/accumulate-linux-arm64" %}
arm64
{% endembed %}
{% endtab %}
{% endtabs %}

**Step 2:** Move **accumulate** to a folder of your choice.

Moving it to your **documents** folder is recommended, making it easier to locate on your terminal.

**Step 3:** (optional): Rename the file to "accumulate"

It recommended renaming the binary file to "**accumulate**" so it will be shorter in the terminal.

{% hint style="warning" %}
**Make sure you have permission to open the file.**
{% endhint %}

**Step 4:**  Copy the binary file location and paste it into your terminal; you can do so by dragging and dropping it into your terminal for every command.

You can start using the [Accumulate CLI commands.](https://docs.accumulatenetwork.io/accumulate/cli/cli-reference)

**How to access Accumulate CLI from anywhere in the terminal.**

{% hint style="info" %}
&#x20;**This is an optional step**
{% endhint %}

This step makes it easier to run accumulate since you can call it anywhere in your terminal.

You can follow the instructions in this [link](https://zwbetz.com/how-to-add-a-binary-to-your-path-on-macos-linux-windows/#windows-cli)



### 2. From source

#### **Preparing the installation**

The CLI installation guide needs two requirements.

* GO language 1.18 version
* Terminal or any command line interface of your choice

#### **Step 1: Clone accumulate**

```
git clone https://gitlab.com/accumulatenetwork/core/wallet.git
```

#### **Step 2: Locate accumulate folder**

```
cd wallet
```

#### **Step 4: Build Accumulate**

This command works for Mac/Linux and Windows

```
go build ./cmd/accumulate
```

Once you run the command above, an **accumulate** binary file should appear in the root directory `accumulate`, which enables the CLI Commands.

#### **Step 5: Create a seeded wallet**

This command will create a mnemonic seed and wallet locally.

```
./accumulate wallet init create
```

After running the command above, you will be requested to write down your generated **mnemonic phrase** in the terminal and press enter.

{% hint style="info" %}
Please keep your **mnemonic phrase** safe, it will help you restore the wallet.
{% endhint %}

Also, if you have an existing Accumulate wallet, then you can `import` the wallet using the command below.

```
./accumulate wallet init import
```

Import a mnemonic seed via the command prompt or import a wallet backup file to create a wallet

To backup, your wallet

```
accumulate wallet export mywallet.json
```

To restore from the backup

```
accumulate wallet init import keystore mywallet.json
```

#### **Step 5: Start the CLI Tool**

To test that the Accumulate is installed correctly, run the below command without arguments.

**On Mac / Linux / Windows**

```
./accumulate
```
