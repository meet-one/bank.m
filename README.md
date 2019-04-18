
## Guide
### Transfer MEETONE token from EOS mainnet to MEETONE sidechain:
```
cleos -u https://mainnet.meet.one push action eosiomeetone transfer '["MAINNET_ACCOUNT","bank.m","100.0000 MEETONE","SIDECHAIN_ACCOUNT"]' -p MAINNET_ACCOUNT
```
bank.m only accept MEETONE token, `SIDECHAIN_ACCOUNT` name should be end with `.m`

### Transfer MEETONE token from MEETONE sidechain to EOS mainnet:
```
cleos -u https://fullnode.meet.one transfer "SIDECHAIN_ACCOUNT" "bank.m" "100 MEETONE" "MAINCHAIN_ACCOUNT" -p SIDECHAIN_ACCOUNT
```

## Query

query transfer records:
```
cleos -u https://mainnet.meet.one get table bank.m bank.m book -l -1
```

query transfer records by account name:
```
cleos -u https://mainnet.meet.one get table bank.m bank.m book --index 2 --key-type -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```

query transfer records by transaction id:
```
cleos -u https://mainnet.meet.one get table bank.m bank.m book --index 3 --key-type -L transaction_id -U transaction_id
```

query synchronous information which transfered from mainnet:
```
cleos -u https://fullnode.meet.one get table bank.m bank.m synchrobook -l -1
```

query transfer records by account name:
```
cleos -u https://fullnode.meet.one get table bank.m bank.m synchrobook --index 2 --key-type -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```
If field `quantity` is negative, it means MEETONE token is already transferred.
