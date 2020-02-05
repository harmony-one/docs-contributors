---
description: Harmony CLI tool is replacing the wallet.sh as the main wallet tool.
---

# Using the Harmony CLI tool

* [Windows Subsystem for Linux \(WSL\) \(First Time Users\)](windows-subsystem-for-linux-wsl-first-time-users.md)
* [Download and installation](download-and-installation.md)
* [Query Balances](query-balances.md)
* [Creating, sending transactions](creating-sending-transactions.md)
* [Querying the blockchain](querying-the-blockchain.md)
* [Full CLI Reference](full-cli-reference.md)
* [Key management](key-management.md)

## TL;DR <a id="tl-dr"></a>

For the impatient, use `hmy cookbook` to see the most common examples & proper arguments.

![](https://blobscdn.gitbook.com/v0/b/gitbook-28427.appspot.com/o/assets%2F-LlEOlYqEG_GKuO5Rehq%2F-Lp21XcoWeKFnec8JA1u%2F-Lp21ZYPTwg8Nn6M7d7t%2Fhmy-cookbook.gif?generation=1568787812963900&alt=media)

## Introduction <a id="introduction"></a>

`hmy` is the offical CLI provided by Harmony. You can use it as a local wallet and as a way to interact with your `Ledger Nano` device. Completely open-source, you can track its development and post any issues encountered and your feature suggestions [here](https://github.com/harmony-one/go-sdk).

Be sure to include the output of `$ hmy version` in your bug reports and preferably include the additional output printed when the environment variable HMY\_ALL\_DEBUG is set to true, like so:

`$ HMY_ALL_DEBUG=true hmy transfer ...`

## Features <a id="features"></a>

With the `hmy` CLI you can send signed transactions to the Harmony blockchain, check previous transactions and recover keys from previous mnemonics.

## Platforms <a id="platforms"></a>

* OSX: main development platform
* Linux: tested
* Windows: tested / working under Windows Subsystem for Linux \(WSL\) 

