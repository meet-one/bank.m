# bank.m 

## EOS mainnet
Send MEETONE token from mainnet to sidechain:
```
cleos -u https://mainnet.meet.one push action eosiomeetone transfer '["MAINNET_ACCOUNT","bank.m","100.0000 MEETONE","SIDECHAIN_ACCOUNT"]' -p MAINNET_ACCOUNT
```
bank.m only accept MEETONE token, `SIDECHAIN_ACCOUNT` must be has suffix `.m`

query transfered informations:

by transfer account:

```
cleos -u https://mainnet.meet.one get table bank.m bank.m book --index 2 --key-type -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```

by transaction id:
```
cleos -u https://mainnet.meet.one get table bank.m bank.m book --index 3 --key-type -L transaction_id -U transaction_id
```

## MEET.ONE sidechain

query synchronous information which transfered from mainnet:
by mainnet transfer account:
```
cleos -u https://sidechain-test.meet.one:8888 get table bank.m bank.m synchrobook --index 2 --key-type -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```
If field `quantity` is negative, it means MEETONE token is already transferred.
