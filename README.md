# bank.m 

### Please don't transfer token to bank.m until sidechain is launched. (2019-02-26 21:00:00)

## Mainnet
Send MEETONE token from mainnet to sidechain:
```
cleos -u http://mainnet.meet.one push action eosiomeetone transfer '["MAINNET_ACCOUNT","bank.m","100.0000 MEETONE","SIDECHAIN_ACCOUNT"]' -p MAINNET_ACCOUNT
```
bank.m only accept MEETONE token, `SIDECHAIN_ACCOUNT` must be has suffix `.m`

query transfered informations:
by transfer account:

```
cleos -u http://mainnet.meet.one get table bank.m bank.m book --index 2 --key-type -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```

by transaction id:
```
cleos -u http://mainnet.meet.one get table bank.m bank.m book --index 3 --key-type -L transaction_id -U transaction_id
```

## Sidechain

query synchronous information which transfered from mainnet:
by mainnet transfer account:
```
cleos -u http://sidechain-test.meet.one:8888 get table bank.m bank.m synchrobook --index 2 --key-type -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```
field `quantity` is negative means MEETONE token transfered from mainnet to sidechain has succeed.
