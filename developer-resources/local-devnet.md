# Local DevNet

This guide assumes you have successfully [compiled](broken-reference) Accumulate and installed the binary to your path. If the binary is not installed to your path, replace `accumulate ...` with `./accumulate ...`, assuming the binary is in the current directory.

### Configure

* [ ] Choose the directory to store configuration and state in, such as `.nodes`
* [ ] Choose the base IP address for the first node, such as `127.0.25.1`
* [ ] Choose the number of BVNs to create
* [ ] Choose the number of validators and followers to create for each subnet
* [ ] Execute `accumulate init devnet [flags]`

{% hint style="danger" %}
On macOS, you need to create loopback aliases before you will be able to listen on `127.x.y.z` (except `127.0.0.1`). To create an alias for `127.0.25.1`, execute `sudo ifconfig lo0 alias 127.0.`25`.1.`
{% endhint %}

```shell-session
$ accumulated init devnet --work-dir .nodes --ip 127.0.25.1 --bvns 2 --followers 1 --validators 2
```

This will configure the DN and two BVNs, each with two validators and one follower, in `.nodes`, with IP addresses `127.0.25.1` through `127.0.25.9`.

### Run

To run all of the nodes from directory `.nodes`, execute:

```shell-session
$ accumulated run devnet -w .nodes
```

To run node 0 from directory `.nodes`, execute:

```shell-session
$ accumulated run -w .nodes/bvn0 -n 0
```

{% hint style="warning" %}
All validator nodes must be run together, and the DN must be run first. If nodes are run singly, you must launch all of the nodes.
{% endhint %}

{% hint style="warning" %}
The directory of your bvn0 folder maybe different.
{% endhint %}