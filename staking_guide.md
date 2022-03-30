# Staking, How?
    

For staking to take place, it is required to:

1.  Have SIN coins
    
2.  Unlock the wallet before staking.
    
3.  Keep the wallet open at all times; otherwise, it is not possible to stake it even if the coins are matured.
    
![](assets/img/qtwallet/staking.png)
  

First, select the "Staking" menu to show the Staking page. Next, click the Stake button on the right. After reading the warning, click Yes and enter the passphrase, tick "unlock for staking only" box for staking activation.

 ![](assets/img/qtwallet/warningstaking.png)

**IMPORTANT:** The Staking menu Stake button must be turned on for staking activation. The wallet must be online 24/7 for the staking to work.


# Useful console commands

**getstakinginfo**

Returns a json object containing staking-related information.
Result:
```
{                                    (json object)
  "blocks" : n,                      (numeric) The current block
  "currentblockweight" : n,          (numeric, optional) The block weight of the last assembled block (only present if a block was ever assembled)
  "currentblocktx" : n,              (numeric, optional) The number of block transactions of the last assembled block (only present if a block was ever assembled)
  "difficulty" : n,                  (numeric) The current difficulty
  "pooledtx" : n,                    (numeric) The size of the mempool
  "chain" : "str",                   (string) current network name (main, test, regtest)
  "warnings" : "str",                (string) any network and blockchain warnings
  "staking" : "str",                 (string) If staking is active or not
  "staking_available" : n,           (numeric) The amount of SIN which is currently available to stake
  "connections" : "str",             (string) If there are any connections to the network
  "unlockedwallet" : "str",          (string) if the wallet used for staking is unlocked
  "blocks_since_last_try" : n,       (numeric) The number of blocks in the current best chain since we last tried staking
  "hash_last_try" : "str",           (string) The hash of the block we last tried staking on top of
  "time_since_last_try" : n,         (numeric) The UNIX timestamp of when we last tried staking
  "available_at_last_try" : n,       (numeric) The amount of SIN we had available the last time we tried staking
  "number_attempts_last_try" : n,    (numeric) The number of attempts we did the last time we tried staking
  "wallet" : "str",                  (string) Wallet being used for staking
  "staking_nethash" : n              (numeric) Global stake weight
}
```

```
getstakinginfo

{
  "blocks": 901970,
  "difficulty": 524280.2499963045,
  "pooledtx": 9,
  "chain": "main",
  "warnings": "",
  "staking": false,
  "staking_available": 20,
  "connections": true,
  "unlockedwallet": true,
  "blocks_since_last_try": 0,
  "hash_last_try": "a4d2afd260db2d290175e8b0c3398bc5d382a1848fd841464cfe2bd169caea03",
  "time_last_try": 1648624170,
  "available_at_last_try": 20,
  "number_attempts_last_try": 20,
  "wallet": "47k",
  "staking_nethash": 300235537023044.2
}
```

**setstakingstatus status ( "wallet" )**

Sets staking status to either true or false. If no wallet is specified, staking is enabled for the wallet which executed the RPC call.
If a wallet is specified, staking is enabled for that wallet and that wallet only. Automatically disables staking for the other wallet(s).
Arguments:
1. status    (boolean, required) The status for staking, either true or false.
2. wallet    (string, optional) The name of the wallet to enable staking for.

Result:

```
{                           (json object)
  "wallet" : "str",         (string) Wallet chosen
  "status" : true|false     (boolean) Applied status
}
```
```

setstakingstatus false my_wallet

{
  "wallet": "my_wallet",
  "status": false
}
```

```

setstakingstatus true my_wallet

{
  "wallet": "my_wallet",
  "status": true
}
```
💡setstakingstatus is equivalent to the GUI switch 

