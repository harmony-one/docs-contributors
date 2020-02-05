---
description: Guide provided by Ionut from Chainnode Capital
---

# Validator Migration from One Server to Another

### Prerequisites:

* An existing validator with a BLS key and wallet key
* An SCP client with UI or directly with terminal
  * Windows: WINSCP
  * Mac: Cyberduck

## Wallet file

1. Find the Wallet file on the existing server of the validator under /.hmy/keystore. 
2. Copy this file on the new server for the same validator in the same folder /.hmy/keystore. 

![](https://lh3.googleusercontent.com/mm1dy16CVG1El9-783S4XoVvDGxvNPeYCUUJGtU4tcQgCo4L6FXqymPFChdpCFU-DBniTXxf4Zkb6EUHjB13AfGKNIp7S02KeKQ4FjqwRBL6P_PkM_1oFkdCF-pdylKod9iKQphd)

## BLS key file

1. Find the BLS Key file on the existing server of the validator under the existing user, in this case root but it can well be under your created user.
2. Copy this file on the new server for the same validator in the same folder. 

![](https://lh3.googleusercontent.com/lvBId3VheTI31xRYyITMeBtCQ8xzOhgZJ2DAMbXRuMkAVfKfTDtvdCJLzqmxXRVERVR_UYN0m1t9EmiLV0elDnueMLsAWjfk5CJ3Wa-RoN9JbxusBCXOqZNO8MxTIUQKvXNUucIx)

## Install the wallet\(in terminal\):

curl -LO [https://raw.githubusercontent.com/harmony-one/harmony/pangaea/scripts/wallet.sh](https://raw.githubusercontent.com/harmony-one/harmony/pangaea/scripts/wallet.sh) //downloads script

chmod u+x wallet.sh

./wallet.sh -d

**Important:** Before you launch and sync the node you have to think about the syncing strategies with the latest state of the blockchain. Currently you have to back up your DB on the existing server and then copy it on the new server and sync from there.

The alternative is to start the validator on the new server and wait until it has the latest state of the harmony blockchain. Once it has, you can stop the validator on the old server and check if you are still validating and getting rewards. If this is the case, then it means the migration on the new server worked.

The solution in the future is probably going to be to have blockchain checkpoints and download a backed up version close to the real state and sync from there.

### Launch and run node:

sudo yum install -y tmux //installs tmux

tmux new-session -s node //creates tmux session

curl -LO [https://raw.githubusercontent.com/harmony-one/harmony/pangaea/scripts/node.sh](https://raw.githubusercontent.com/harmony-one/harmony/pangaea/scripts/wallet.sh) //downloads script

chmod a+x node.sh

sudo ./node.sh //sync your node to harmony blockchain

Cntrl+b then d to detach from tmux

**Once you have your new server up and synchronized to the blockchain, you can shutdown the old server and make a last backup if you consider so.**

