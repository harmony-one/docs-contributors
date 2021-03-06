# Getting all delegations for a Validator

All delegations that are associated with a validator can be queried using Harmony CLI as follows:

```text
./hmy --node="https://api.s0.p.hmny.io" blockchain delegation by-validator one1pdv9lrdwl0rg5vglh4xtyrv3wjk3wsqket7zxy
```

The output should show the delegations for the given validator:

```text
{
  "id": "0",
  "jsonrpc": "2.0",
  "result": [
    {
      "Undelegations": null,
      "amount": 14000000000000000000,
      "delegator_address": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016",
      "reward": 0,
      "validator_address": "0x0b585f8daefbc68a311fbd4cb20d9174ad174016"
    }
  ]
}
```

