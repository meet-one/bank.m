
## Guide

Transfer memo format: `target_account@to_chain_name user_defined_memo`

For example: 
```
test.m@meetone transfer to meetone chain.
eosiomeetone@eosio transfer to eosio chain.
```

to_chain_name:
```
EOSIO mainnet name: eosio
MEETONE sidechian name: meetone
```

### Transfer MEETONE token from EOSIO mainnet to MEETONE sidechain:
```
cleos -u https://mainnet.meet.one push action eosiomeetone transfer '["MAINNET_ACCOUNT","bank.m","100.0000 MEETONE","SIDECHAIN_ACCOUNT@meetone user_defined_memo"]' -p MAINNET_ACCOUNT
```
bank.m only accept MEETONE token, `SIDECHAIN_ACCOUNT` name should be end with `.m`

### Transfer MEETONE token from MEETONE sidechain to EOS mainnet:
```
cleos -u https://fullnode.meet.one transfer "SIDECHAIN_ACCOUNT" "bank.m" "100 MEETONE" "MAINCHAIN_ACCOUNT@eosio user_defined_memo" -p SIDECHAIN_ACCOUNT
```

## Query

### query EOSIO mainnet transfer to MEETONE sidechain records:

all records:
```
cleos -u https://mainnet.meet.one get table bank.m meetone books -l -1
```

query transfer records by account name:
```
cleos -u https://mainnet.meet.one get table bank.m meetone books --index 2 --key-type i64 -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```

query transfer records by transaction id:
```
cleos -u https://mainnet.meet.one get table bank.m meetone books --index 3 --key-type sha256 -L transaction_id -U transaction_id
```

### query synchronous information which transfered from mainnet:

all record:
```
cleos -u https://fullnode.meet.one get table bank.m eosio synchrobooks -l -1
```

query transfer records by account name:
```
cleos -u https://fullnode.meet.one get table bank.m eosio synchrobooks --index 2 --key-type i64 -L MAINNET_ACCOUNT -U MAINNET_ACCOUNT
```
If field `quantity` is negative, it means MEETONE token is already transferred.
