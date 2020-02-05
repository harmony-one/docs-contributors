# Useful Commands

## How to Copy Your Keys

#### AWS:

```text
cd downloads/
chmod 400 YOUR_PEM_FILE
ssh -i......from amazon connect 
sudo yum update
mkdir -p ~/.hmy/keystore 
scp -i <PEMFILE> <WALLETID> ec2-user@<INSTANCEIPADDRESS>:/home/ec2-user/.hmy/keystore
scp -i <PEMFILE> <BLSKEY> ec2-user@<INSTANCEIPADDRESS>:
```

#### Vultr:

```text
apt update && apt upgrade
mkdir -p.hmy/keystore
scp <WALLETID> root@<INSTANCEIPADDRESS>:/root/.hmy/keystore
scp <BLSKEY> root@<INSTANCEIPADDRESS>:
```

## How to Get Your Wallet

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

NOTE: The wallet.sh is being deprecated, so please use the Harmony CLI going forward.

## Node Monitoring

#### Checking for "BINGO"s/consensus:

```text
tac latest/zero*.log | grep -am 1 "BINGO"
```

#### Checking Wallet Balances:

```text
./hmy --node=https://api.s0.p.hmny.io/ balances one1wh4p0kuc7unxez2z8f82zfnhsg4ty6dupqyjt2
```

#### Checking YOUR shard and last synced block height

```text
./hmy blockchain latest-header
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x9e86705046739d2edf481bed6a767cc2c2139251f7adae63b7a603f181006412",
    "blockNumber": 3170,
    "epoch": 21,
    "lastCommitBitmap": "ffffffffff06",
    "lastCommitSig": "25916b5b0cfeae733ebf19a5c6c51627f240c19835dd6f5e779f4a48d6742cc41562e6829c27c54fe36e0fab18284a0596d054e47e490bf1c0579a31c38a17e5d67e759c76c69f501786b11b8984c74ecfa1524f9cdd6d00a0b4ea70836cae09",
    "leader": "one1xj6vlvavzar46qdpgyepsv0sr6ululqwldj0vf",
    "shardID": 0,
    "timestamp": "2019-12-11 12:04:56 +0000 UTC",
    "unixtime": 1576065896,
    "viewID": 3170
  }
}
```

{% hint style="info" %}
./hmy cli without the node parameter will use your localhost node data
{% endhint %}

#### Checking the network status, last block, epoch, leaders, based on the shard number

{% tabs %}
{% tab title="Shard 0" %}
```text
./hmy blockchain latest-header --node=https://api.s0.p.hmny.io
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xae23db112d22062be6a0f065ecc3989d4e9559ad6a1f34fe4344d021907e8c2e",
    "blockNumber": 415749,
    "epoch": 5543,
    "lastCommitBitmap": "fffffffffffffffb0f00",
    "lastCommitSig": "06efa677bdd327d3d9602fd246c214edb35e447692dccc2219ef08ce2fa026b96f3826fcb5a2a3f724222ecef4af66029f3b5d677e54534519ad2a405ad3b336dd5145dcc083fc2330b9d0bb398affd1745cab274b5019f32cba0287bd5e5a17",
    "leader": "one18ahxsrk9g4h4gz5r8ema7nyw6g9zpun5hhp54d",
    "shardID": 0,
    "timestamp": "2019-12-11 12:18:21 +0000 UTC",
    "unixtime": 1576066701,
    "viewID": 415745
  }
}
```
{% endtab %}

{% tab title="Shard 1" %}
```text
./hmy blockchain latest-header --node=https://api.s1.p.hmny.io
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0x65d528672301b1c086b4f2db89ce20f6977f7aeaa494073352e211ac29f55179",
    "blockNumber": 456065,
    "epoch": 5543,
    "lastCommitBitmap": "ffffffffffffffff0f00",
    "lastCommitSig": "c8e049810c1f649625259f684e99f4a9cfc51cf01b2dd032f884136c9922ebb8fe0929e366bbf8122e430402d04d4804362013302994d4924c2990bdffeacb4b79e075c1897947a7ec5be44eef6f1bd1e013b80008f28085c15e17aa49629a09",
    "leader": "one1vaqzxt50ltk9hq4d44lgxmj4pj2x533fsp2acx",
    "shardID": 1,
    "timestamp": "2019-12-11 12:21:52 +0000 UTC",
    "unixtime": 1576066912,
    "viewID": 456065
  }
}
```
{% endtab %}

{% tab title="Shard 2" %}
```text
./hmy blockchain latest-header --node=https://api.s2.p.hmny.io
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "blockHash": "0xd5775e720a9bcc5a88fd13aac27d72365f4724d6a513ecf39af53c1bb826823d",
    "blockNumber": 453475,
    "epoch": 5543,
    "lastCommitBitmap": "ffffffffffffffff0f4000",
    "lastCommitSig": "701bad22a95b7ee937446c3f614755d1729f19b5976f1230af6de65fd7ecc0d8b95795396a55d78994b5a8ecaed77d028721f76a58e9919ab01f4aba36a6f3a3dda3aaf39b313e5d623e73ca83d71fc1631ae964e1747826662652be85fada18",
    "leader": "one18vn4hpu8jpu8p9pql59m7p0x8dqrpsw0jzav9u",
    "shardID": 2,
    "timestamp": "2019-12-11 12:22:26 +0000 UTC",
    "unixtime": 1576066946,
    "viewID": 453508
  }
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
You should not be in _tmux_. To safely detach from _tmux_, refer to the section above.
{% endhint %}

## How do I check my logs? <a id="how-do-i-check-my-logs"></a>

Be sure you are in the _tmux_ session your node is running in. For instructions on attaching to a _tmux_ session, refer to the steps in the _tmux_ section above.

Use the command **tail -n** _**"number of lines"**_ **latest/**_**"log file name"**_**\*.log** to print your logs. Replace the sections inside the quotation marks with the respective information you are searching for.

For example, if you want to look at the last **100** lines of the **validator** log, use:

```text
tail -n 100 latest/validator*.log
```

If you want to look at the last **100** lines of the **zerolog**, use:

```text
tail -n 100 latest/zerolog*.log
```

To **find specific information** within logs, the command  
**`grep -i "search keyword" latest/"log file name"*.log | tail -n "number of lines"`**  
will print all lines within the specified log with exact matches to the keyword.

For example, to look for the last 10 BINGOs within the zerolog, use:

```text
grep -i bingo latest/zerolog*.log | tail -n 10
```

### Checking your node's connectivity to the bootnodes

First of all, you may install **netcat** command as a network diagnostic tool. This [document](https://ixnfo.com/en/installing-and-using-netcat.html) may provide some guidance. Then, use the following command to check the bootnode connectivity.

For Mainnet bootnodes use these IP's:

```text
nc -tv -w3 100.26.90.187 9874
nc -tv -w3 54.213.43.194 9874
nc -tv -w3 13.113.101.219 12019
nc -tv -w3 99.81.170.167 12019

# all of them should return something like the following

Connection to 13.113.101.219 port 12019 [tcp/*] succeeded!
/multistream/1.0.0
```

For Pangaea bootnodes use these IP's:

```text
nc -tv -w3 54.218.73.167 9889
nc -tv -w3 18.232.171.117 9889

# all of them should return something like the following

Connection to 54.218.73.167 port 9889 [tcp/*] succeeded!
/multistream/1.0.0
```

If there is any issue that the bootnode can't connect, please contact our Discord or Telegram channel for help.

## Getting Keys list

to check your keys list, enter this command:

```text
./hmy keys list
```

## **Getting all active validators**

A list of validators that are currently part of the consensus committee \(current epoch\), can be queried using Harmony CLI as follows:

```text
./hmy --node="https://api.s0.p.hmny.io/" blockchain validator all-active
```

The output should show all the active validators:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": [
    "0x0b585f8daefbc68a311fbd4cb20d9174ad174016"
  ]
}
```

## **Getting all validators**

A history of all the validators can be queried using Harmony CLI as follows:

```text
./hmy --node="https://api.s0.p.hmny.io/" blockchain validator all
```

The output should show all validators in the system:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": [
    "0x0b585f8daefbc68a311fbd4cb20d9174ad174016"
  ]
}
```

## **Getting validator information**

Getting information about a validator can be performed using Harmony CLI as follows:

```text
./hmy --node="https://api.s0.p.hmny.io/" blockchain validator information one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy
```

The output should show the validator information for validator one address one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": {
    "active": false,
    "address": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
    "commission": {
      "commission_rates": {
        "max_change_rate": "0.050000000000000000",
        "max_rate": "0.900000000000000000",
        "rate": "0.100000000000000000"
      },
      "update_height": 109
    },
    "creation_height": 109,
    "description": {
      "details": "John the validator",
      "identity": "john",
      "name": "John",
      "security_contact": "Alex",
      "website": "john@harmony.one"
    },
    "max_total_delegation": 30000000000000000000,
    "min_self_delegation": 2000000000000000000,
    "slot_pub_keys": [
      "b9486167ab9087ab818dc4ce026edb5bf216863364c32e42df2af03c5ced1ad181e7d12f0e6dd5307a73b62247608611"
    ],
    "stake": 0,
    "unbonding_height": 0,
    "uptime": "1.000000000000000000"
  }
}
```

## **Getting all delegations by a delegator**

All delegations done by a delegator can be queried using Harmony CLI as follows:

```text
./hmy --node="https://api.s0.p.hmny.io/" blockchain delegation by-delegator one1pf75h0t4am90z8uv3y0dgunfqp4lj8wr3t5rsp
```

The output should show a list of delegations made by the delegator across validators:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": [
    {
      "Undelegations": [],
      "amount": 10000000000000000000,
      "delegator_address": "0x0a7d4bbd75eecaf11f8c891ed47269006bf91dc3",
      "reward": 0,
      "validator_address": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016"
    }
  ]
}
```

## Checking Current Nonce

Checking the nonce is important to understand if the transaction is succeed, if the nonce don´t increase means that the transaction did not succeed.

```text
./hmy blockchain current-nonce one146fgmm0rj4rmnm6rxjruyrr6pm5cfjfrdtvlr4 --node=https://api.s0.pga.hmny.io
```

## Looking for validators and delegators errors messages

```text
./hmy failures staking --node="https://api.s0.p.hmny.io"
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": [
    {
      "directive-kind": "CreateValidator",
      "error-message": "insufficient balance to pay for gas",
      "time-at-rejection": 1576049281,
      "tx-hash-id": "0xe02045667c208f860a62008dce2266e3a314b90b1c58db54245d2e1e1a274e67"
    },
    {
      "directive-kind": "Delegate",
      "error-message": "insufficient balance to stake",
      "time-at-rejection": 1576052305,
      "tx-hash-id": "0x32ece961a3ee9fb9842bb3d56d9e1b6d9f01ff5d2254b547d2b6373199f22b55"
    },
    {
      "directive-kind": "CreateValidator",
      "error-message": "insufficient balance to pay for gas",
      "time-at-rejection": 1576062960,
      "tx-hash-id": "0xc881bb739d8041066569c585bb10bd200ed673aa437c3524fae2a88ac1b754af"
    },
    {
      "directive-kind": "CreateValidator",
      "error-message": "insufficient balance to pay for gas",
      "time-at-rejection": 1576063726,
      "tx-hash-id": "0xc881bb739d8041066569c585bb10bd200ed673aa437c3524fae2a88ac1b754af"
    },
    {
      "directive-kind": "Delegate",
      "error-message": "total delegation can not be bigger than max_total_delegation",
      "time-at-rejection": 1576065393,
      "tx-hash-id": "0x4bf8c7ac8a9e332cd888e98b6d18408ef7fe076091ba38e8510735c6ea38fcba"
    },
    {
      "directive-kind": "Delegate",
      "error-message": "total delegation can not be bigger than max_total_delegation",
      "time-at-rejection": 1576065704,
      "tx-hash-id": "0x5b68d98279a52d67caa933f40e2fcb4540e787c71e73a52ea03288f31aa4ee43"
    },
    {
      "directive-kind": "CreateValidator",
      "error-message": "staking validator already exists",
      "time-at-rejection": 1576072069,
      "tx-hash-id": "0x14f9312d46449a8960368c4522d798783929169fa3a4162f64ec4f48d381739d"
    }
  ]
}
```

