# ``Commands``


``The SINOVATE Core wallet has a rich set of commands which give comprehensive control of the wallet and blockchain transactions. There are two sets of commands that can be used with SIN Core wallets:``

-   Console commands to use on a wallet that is already running.
    
-   Startup commands to use when starting up a wallet.
    

``This manual focuses on the console commands given to a running wallet and can be sent using RPC (Remote Procedure Calls). The command line to the sind server wallet and the sin-qt desktop GUI (Graphical User Interface) wallet can be entered using the Debug window.``

  

Console command line (see Figure 1).

Figure 1. The sin-qt Console

Note the warning message in red in Figure 1 and be careful using the private key commands (dumpprivkey and dumpwallet) with Mainnet wallets.

Console commands for the server wallet sind are given using the Command Line Interface application sin-cli on the system command line prompt (see Figure 2).

Figure 2. System command line prompt

You can always get a list of the current console commands using the help command (see Figure 3.)

Figure 3. The help command

## ``Console Commands :``

``Console commands are given to a running SIN Core wallet and provide additional information and control. Console commands are required to operate the sind server wallet, a "headless" wallet with no graphical user interface.``

``One hundred thirty-six console commands with some good references for the 112 inherited from bitcoin. In addition, 13 "hidden" commands are used by developers and won't show up in the "help" list.``

``Commands can have required or optional parameters, and more numerous parameters are entered in JSON (JavaScript Object Notation) format with escaped double quotes ( \" ) as shown below.``

``Typical parameters for these commands are SIN addresses, block hashes, contact addresses, etc. In addition, some of the commands will have an optional parameter "minconf" (minimum confirmations), which allows you to get a response for a transaction or block with at least that number of confirmations.``

``The chain query bitcoin API reference [http://chainquery.com/bitcoin-api](http://chainquery.com/bitcoin-api) explains the parameters and gives examples of the commands inherited from bitcoin. The bitcoin chain query API reverence gives 67 commands, of which 2 are not in SIN (estimatepriority, getgenerate), and two (gettransaction, walletpassphrase) have an additional parameter for SIN. See also [https://bitcoin.org/en/developer-reference#remote-procedure-calls-rpcs](https://bitcoin.org/en/developer-reference#remote-procedure-calls-rpcs).``

``Advanced interfaces to the SIN Core wallet (full node) can use these "console commands" as RPCs (Remote Procedure Calls) over a dedicated port connection to the node. To build an exchange hot wallet or server node for a mobile DAPP (Distributed Application), you can use RPCs following these same console commands. The client node offers a JSON-RPC interface over HTTP sockets to perform various operational functions and manage the local node.``

``A quick comment on "accounts." Accounts were an ill-fated way from bitcoin to track balances for what are UTXO transaction-based values, and "accounts" are deprecated and will be phased out by version 0.18.``

``Here are some command groupings that are useful for various tasks:``

-   Peer connections: getconnectioncount, getpeerinfo, addnodes, getnetworkinfo
    
-   Staking: getstakinginfo, getwalletinfo, getnetworkinfo
    
-   Sending: listaddressgroupings, sendtoaddress, sendmany, sendmanywithdupes
    
-   Raw transactions: crearterawtransaction, signrawtransaction, combinerawtransactoins, sendrawtransaction
    

  

## ``Startup Commands``

``Startup commands give additional control and recovery options when launching the wallet. For example, you can use startup commands for various kinds of blockchain recovery techniques and extra debug logging or additional controls. If you use these startup commands, make sure you have a good backup of the wallet.dat file.``

``See the startup commands on the sin-qt wallet with Help - Command line options:``

Figure 4. Startup commands

and on the command line itself with "sind -?":

Figure 5. Startup commands from the command line

## ``Console Commands A - Z``

Responses are given for default parameters for these console commands documented below (SIN version 0.16 - winter 2018/2019). Commands marked DEPRECATED should not be used because they will be removed and replaced in future wallet versions; for example, commands using "account" will be removed in version 0.18.

Using the command "help \" will give complete information about the command and relevant parameters, formatted so you can copy and paste (replacing the addresses, transactions IDs, etc., as required). The format below shows the command with parameters followed by the response. In some cases, parameters or responses are truncated with the term "\." Where noted, some commands only work with the regtest (Regression Test) network. Also, many commands will return "null" for sin-qt and return nothing for command-line systems.

### ``abandontransaction "txid"``

``Works on transactions not in the blockchain or mempool, used in testing.``

```
abandontransaction "0cc99a30bc2064041ea4263835b4ed594ff500c56d6b14e4970aeee548e71389"
Transaction not eligible for abandonment (code -5)
```
### ``abortrescan``

``Stops a wallet rescan triggered by a command such as importprivkey. This command can be issued by opening a 2nd command line window (where the first window is scanning), in which case the command will stop the scan and return "true."``
```
sin-cli abortrescan

true
```
  

### ``addmultisigaddress nrequired ["key",...] ( "account" "address_type" )``

``Add a multi-signature address to the wallet so you can receive and send from that address. Run the command on each machine that will be signing and backup the wallet.dat file. The address can be a SIN address or hex-encoded public key. Use importaddress to add the multisig address on each signing wallet.``

``This functionality is only intended for use with non-watch-only addresses. See importaddress for watch-only p2sh address support. Use of account is DEPRECATED). See also validateaddress.``
```
addmultisigaddress 2 "[\"SgdaD9b3ppKowoC45EZMtepjjBfnvEe6m\",\"SFmr8vY29reHj73XSHfdWvkV3mD57Kqd8\"]"
{

"address": "mHB9w64hHbm2YtCxyqS8kG3g77b2gbSvK",

"redeemScript": "5321538ef45ab52bd53508adfda3cfe82ebcaf0495963729e5ff2a8e5aeecdd4cdd23daea03cf4394ad4c578caff2d297ce937c3afba5bc56f31c786b2addf56c72ab"

}
```
  

### ``addnode "node" "add|remove|onetry"``

``Attempts to add a node with a known IP address. This command is helpful for new wallets that are having trouble making peer connections. Here are some excellent IP addresses to add; you can put these commands in one after another, then the wallet will try for a few minutes to make a peer connection with each. Sind returns nothing:``

```
addnode 35.200.159.68:20970 add
addnode 35.197.138.163:20970 add
addnode 35.226.31.206:20970 add
addnode 35.200.130.53:20970 add
addnode 35.192.54.161:20970 add
```
sin-qt returns "null" after each (see Figure 6).

Figure 6. Entering the addnode command

### ``analyzepsbt "psbt"``

``Analyzes and provides information about the current status of a PSBT and its inputs``

``Arguments:``

``1. psbt (string, required) A base64 string of a PSBT``

  Result:
```
{ (json object)

"inputs" : [ (json array)

{ (json object)

"has_utxo" : true|false, (boolean) Whether a UTXO is provided

"is_final" : true|false, (boolean) Whether the input is finalized

"missing" : { (json object, optional) Things that are missing that are required to complete this input

"pubkeys" : [ (json array, optional)

"hex", (string) Public key ID, hash160 of the public key, of a public key whose BIP 32 derivation path is missing

...

],

"signatures" : [ (json array, optional)

"hex", (string) Public key ID, hash160 of the public key, of a public key whose signature is missing

...

],

"redeemscript" : "hex", (string, optional) Hash160 of the redeemScript that is missing

"witnessscript" : "hex" (string, optional) SHA256 of the witnessScript that is missing

},

"next" : "str" (string, optional) Role of the next person that this input needs to go to

},

...

],

"estimated_vsize" : n, (numeric, optional) Estimated vsize of the final signed transaction

"estimated_feerate" : n, (numeric, optional) Estimated feerate of the final signed transaction in BTC/kvB. Shown only if all UTXO slots in the PSBT have been filled

"fee" : n, (numeric, optional) The transaction fee paid. Shown only if all UTXO slots in the PSBT have been filled

"next" : "str", (string) Role of the next person that this psbt needs to go to

"error" : "str" (string, optional) Error message (if there is one)

}
```
  

``Examples:``

```
analyzepsbt "psbt"
```
  
  

### ``backupwallet "destination"``

``The destination can be a filename or a path with a filename. The wallet must be fully decrypted (not just for staking only) for this command to work. sin-qt will return "null," sind returns nothing. On Windows:``
```
backupwallet "C:\Users\<username>\Desktop\Backups\backup2018-10-21.dat"

null
```
  

### ``bumpfee "txid" ( options )``

``Bumps the transaction fee, replacing it with a new transaction by adjusting the change. The new fee can be calculated automatically or by using various options.``
```
bumpfee "cae25062777fca1bce7f860dd238af2be4495f4aef1b5a15bbee260b4c3cde2"
{

"txid": "ecbc798c140b5104ae3d5828493e8e5ef04131dd0e44eb7fa7e1abba24901a5",

"origfee": 0.00090400,

"fee": 0.00093061,

"errors": [

]

}
```
  
### ``clearbanned``

``Clear all banned nodes' IPs. sin-qt returns "null", sind gives no response.``
```
clearbanned
null
```

### ``combinepsbt ["psbt",...]``

``Combine multiple partially signed SIN transactions into one transaction.``

``Implements the Combiner role.``

``Arguments:``
```
1. txs (json array, required) The base64 strings of partially signed transactions``

[

"psbt", (string) A base64 string of a PSBT

...

]
```
  
``Result:``
```
"str" (string) The base64-encoded partially signed transaction
```
  
``Examples:``
```
combinepsbt '["mybase64_1", "mybase64_2", "mybase64_3"]'
```
  
### ``combinerawtransaction ["hexstring",...]``

``Combine multiple partially signed raw transactions into one transaction. The combined transaction may be another partially or fully signed transaction. Here two raw transactions are combined:``
```
combinerawtransaction "[\"0200000001b<snip>000000\", \"0200000001c<snip>000000\"]"

0200000001b<snip>000000
```
  

### ``converttopsbt "hexstring" ( permitsigdata iswitness )``

``Converts a network serialized transaction to a PSBT. This should be used only with createrawtransaction and fundrawtransaction``

``createpsbt and walletcreatefundedpsbt should be used for new applications.``


``Arguments:``
```
1. hexstring (string, required) The hex string of a raw transaction

2. permitsigdata (boolean, optional, default=false) If true, any signatures in the input will be discarded and conversion

will continue. If false, RPC will fail if any signatures are present.

3. iswitness (boolean, optional, default=depends on heuristic tests) Whether the transaction hex is a serialized witness transaction.

If iswitness is not present, heuristic tests will be used in decoding.

If true, only witness deserialization will be tried.

If false, only non-witness deserialization will be tried.

This boolean should reflect whether the transaction has inputs

(e.g. fully valid, or on-chain transactions), if known by the caller.
```
  

``Result:``
```
"str" (string) The resulting raw transaction (base64-encoded string)
```
  
``Examples:``

``Create a transaction``
```
createrawtransaction "[{\"txid\":\"myid\",\"vout\":0}]" "[{\"data\":\"00010203\"}]"
```
``Convert the transaction to a PSBT``
```
converttopsbt "rawtransaction"
```
  

### ``createmultisig nrequired ["key",...]``

``DEPRECATED. Use addmultisigaddress.``

### ``createrawtransaction [{"txid":"id","vout":n},...] {"address":amount,"data":"hex",...} ( locktime ) ( replaceable )``

``Create a hex-encoded raw transaction sending some inputs to outputs. The transaction must then be signed and sent to the network; see signrawtransaction and sendrawtransaction. Returns a hex-encoded raw transaction. If you are sending coins, make sure to create a change address to return the change; any difference between the input and output values will be taken as the transaction fee. You could pay a hefty transaction fee if you don't work out the math.``

```
createrawtransaction "[{\"txid\":\"17b3f9ef530695ef2e0368e445a3b59bf12811bdfd42325bb14248e72deb7e2\",\"vout\":0}]" "{\"Sd5eHho389mJMCxSzAbe31w2vntTc7192\":1.0, \"SdXtq55Bf443Lkme2hdj4mD8KKepk32f6\":0.99}"
 

020000001d637cf207c6418fb6220cfcb2b141ba5d230f0ba0a43c68b358aff9a8a6000000000fffffff0509e5f50480000001983a952d5fb15a70832ffdc3cadd3dc7749a49bf053ed6defacd09ef6060000000187aa814bd4ae4167bebbf56bb7c51c5eabf35d50a5c6e7f33ad0000000
```
  

### ``createpsbt [{"txid":"hex","vout":n,"sequence":n},...] [{"address":amount,...},{"data":"hex"},...] ( locktime replaceable )``

``Creates a transaction in the Partially Signed Transaction format.``

``Implements the Creator role.``

``Arguments:``
```
1. inputs (json array, required) The json objects

[

{ (json object)

"txid": "hex", (string, required) The transaction id

"vout": n, (numeric, required) The output number

"sequence": n, (numeric, optional, default=depends on the value of the 'replaceable' and 'locktime' arguments) The sequence number

},

...

]

2. outputs (json array, required) The outputs (key-value pairs), where none of the keys are duplicated.

That is, each address can only appear once and there can only be one 'data' object.

For compatibility reasons, a dictionary, which holds the key-value pairs directly, is also

accepted as second parameter.

[

{ (json object)

"address": amount, (numeric or string, required) A key-value pair. The key (string) is the sin address, the value (float or string) is the amount in SIN

...

},

{ (json object)

"data": "hex", (string, required) A key-value pair. The key must be "data", the value is hex-encoded data

},

...

]

3. locktime (numeric, optional, default=0) Raw locktime. Non-0 value also locktime-activates inputs

4. replaceable (boolean, optional, default=false) Marks this transaction as BIP125 replaceable.

Allows this transaction to be replaced by a transaction with higher fees. If provided, it is an error if explicit sequence numbers are incompatible.
```
  
``Result:``
```
"str" (string) The resulting raw transaction (base64-encoded string)
```
``Examples:``
```
createpsbt "[{\"txid\":\"myid\",\"vout\":0}]" "[{\"data\":\"00010203\"}]"

  ```
  ### ``Coming soon...``
