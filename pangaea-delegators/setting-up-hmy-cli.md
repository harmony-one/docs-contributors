# Installing Harmony CLI wallet

## Download Harmony CLI wallet

```text
curl -LO https://harmony.one/hmycli && mv hmycli hmy && chmod +x hmy
```

or alternatively use this, if the above version will not work for creating a wallet below \(for MacOSX users\) and also note that instead of using ./hmy you have to use ./hmy.sh:

```text
curl -O https://raw.githubusercontent.com/harmony-one/go-sdk/master/scripts/hmy.sh
chmod u+x hmy.sh
./hmy.sh -d
```

## New wallet creation <a id="new-local-account-creation"></a>

Creation of a new account is done as a function of a generated `bip39` mnemonic with 256 bits of entropy. You need to provide an account alias name of your choice \(keep it simple and clean\) and also need provide a passphrase:

```text
./hmy keys add example-account --use-own-passphrase
Enter passphrase for account
Repeat the passphrase:
```

When creating keys this way, `hmy` will ask you to provide a passphrase without repeating it on the screen.‌ The example-account is just a name you can pick, so pick something simple.  
Make sure you keep track of this passphrase for future use because the passphrase is used to decrypt the keystore when signing transactions.

To know where you wallet file has been created, just run the following command:

```text
./hmy keys location
```

The command above will return the location of your wallet file. Backup this wallet file somewhere else.‌‌

You can check the wallets \(local accounts\) with the following command:

```text
./hmy keys list
NAME                                  ADDRESS

acc3                                  one1wh4p0kuc7unxez2z8f82zfnhsg4ty6dupqyjt2
example-account                       one1658znfwf40epvy7e46cqrmzyy54
```

## Checking wallet balances

You can check wallet balances with the following command:

```text
./hmy --node="https://api.s0.p.hmny.io" balances one1wh4p0kuc7unxez2z8f82zfnhsg4ty6dupqyjt2
```

