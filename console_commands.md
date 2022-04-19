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
  ### ``createrawtransaction [{"txid":"hex","vout":n,"sequence":n},...] [{"address":amount,...},{"data":"hex"},...] ( locktime replaceable )``

``Create a transaction spending the given inputs and creating new outputs.
Outputs can be addresses or data.
Returns hex-encoded raw transaction.
Note that the transaction's inputs are not signed, and
it is not stored in the wallet or transmitted to the network.``
``Arguments:``
```
1. inputs (json array, required) The inputs

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

"address": amount, (numeric or string, required) A key-value pair. The key (string) is the sin address, the value (float or string) is the amount in BTC

...

},

{ (json object)

"data": "hex", (string, required) A key-value pair. The key must be "data", the value is hex-encoded data

},

...

]

3. locktime (numeric, optional, default=0) Raw locktime. Non-0 value also locktime-activates inputs

4. replaceable (boolean, optional, default=false) Marks this transaction as BIP125-replaceable.

Allows this transaction to be replaced by a transaction with higher fees. If provided, it is an error if explicit sequence numbers are incompatible.
```

``Result:``
```
"hex" (string) hex string of the transaction
```
  

``Examples:``
```
createrawtransaction "[{\"txid\":\"myid\",\"vout\":0}]" "[{\"address\":0.01}]"

createrawtransaction "[{\"txid\":\"myid\",\"vout\":0}]" "[{\"data\":\"00010203\"}]"

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "createrawtransaction", "params": ["[{\"txid\":\"myid\",\"vout\":0}]", "[{\"address\":0.01}]"]}' -H 'content-type: text/plain;' http://127.0.0.1:8332/

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "createrawtransaction", "params": ["[{\"txid\":\"myid\",\"vout\":0}]", "[{\"data\":\"00010203\"}]"]}' -H 'content-type: text/plain;' [http://127.0.0.1:8332/](http://127.0.0.1:8332/)
```
  

### ``createwallet "wallet_name" ( disable_private_keys blank "passphrase" avoid_reuse descriptors load_on_startup external_signer )``

``Creates and loads a new wallet.``

``Arguments:``
```
1. wallet_name (string, required) The name for the new wallet. If this is a path, the wallet will be created at the path location.

2. disable_private_keys (boolean, optional, default=false) Disable the possibility of private keys (only watchonlys are possible in this mode).

3. blank (boolean, optional, default=false) Create a blank wallet. A blank wallet has no keys or HD seed. One can be set using sethdseed.

4. passphrase (string, optional) Encrypt the wallet with this passphrase.

5. avoid_reuse (boolean, optional, default=false) Keep track of coin reuse, and treat dirty and clean coins differently with privacy considerations in mind.

6. descriptors (boolean, optional, default=false) Create a native descriptor wallet. The wallet will use descriptors internally to handle address creation

7. load_on_startup (boolean, optional) Save wallet name to persistent settings and load on startup. True to add wallet to startup list, false to remove, null to leave unchanged.

8. external_signer (boolean, optional, default=false) Use an external signer such as a hardware wallet. Requires -signer to be configured. Wallet creation will fail if keys cannot be fetched. Requires disable_private_keys and descriptors set to true.
```
  

``Result:``
```
{ (json object)

"name" : "str", (string) The wallet name if created successfully. If the wallet was created using a full path, the wallet_name will be the full path.

"warning" : "str" (string) Warning message if wallet was not loaded cleanly.

}
```
  

``Examples:``
```
createwallet "testwallet"

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "createwallet", "params": ["testwallet"]}' -H 'content-type: text/plain;' http://127.0.0.1:8332/

> sin-cli -named createwallet wallet_name=descriptors avoid_reuse=true descriptors=true load_on_startup=true

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "createwallet", "params": {"wallet_name":"descriptors","avoid_reuse":true,"descriptors":true,"load_on_startup":true}}' -H 'content-type: text/plain;' http://127.0.0.1:8332/
```
  
### ``decodeburnanddatascript "hexstring"``

``Decode a hex-encoded script.``

``Arguments:``
```
1. hexstring (string, required) the hex-encoded script

  

Result:

{ (json object)

"sizeCheck" : true|false, (boolean) true/false

"positionOPCheck" : true|false, (boolean) true/false

"pubkeyhash" : "hex", (string, optional) pubkeyhash

"address" : "str", (string, optional) address

"info" : "str" (string, optional) data in tx

}
```
  

``Examples:``
```
decodeburnanddatascript "hexstring"

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "decodeburnanddatascript", "params": ["hexstring"]}' -H 'content-type: text/plain;' http://127.0.0.1:8332/
```
  

### ``decodepsbt "psbt"``

``Return a JSON object representing the serialized, base64-encoded partially signed SIN transaction.``


``Arguments:``
```
1. psbt (string, required) The PSBT base64 string
```
  ``Result:``
```
{ (json object)

"tx" : { (json object) The decoded network-serialized unsigned transaction.

... The layout is the same as the output of decoderawtransaction.

},

"unknown" : { (json object) The unknown global fields

"key" : "hex", (string) (key-value pair) An unknown key-value pair

...

},

"inputs" : [ (json array)

{ (json object)

"non_witness_utxo" : { (json object, optional) Decoded network transaction for non-witness UTXOs

...

},

"witness_utxo" : { (json object, optional) Transaction output for witness UTXOs

"amount" : n, (numeric) The value in BTC

"scriptPubKey" : { (json object)

"asm" : "str", (string) The asm

"hex" : "hex", (string) The hex

"type" : "str", (string) The type, eg 'pubkeyhash'

"address" : "str" (string) SIN address if there is one

}

},

"partial_signatures" : { (json object, optional)

"pubkey" : "str", (string) The public key and signature that corresponds to it.

...

},

"sighash" : "str", (string, optional) The sighash type to be used

"redeem_script" : { (json object, optional)

"asm" : "str", (string) The asm

"hex" : "hex", (string) The hex

"type" : "str" (string) The type, eg 'pubkeyhash'

},

"witness_script" : { (json object, optional)

"asm" : "str", (string) The asm

"hex" : "hex", (string) The hex

"type" : "str" (string) The type, eg 'pubkeyhash'

},

"bip32_derivs" : [ (json array, optional)

{ (json object, optional) The public key with the derivation path as the value.

"master_fingerprint" : "str", (string) The fingerprint of the master key

"path" : "str" (string) The path

},

...

],

"final_scriptsig" : { (json object, optional)

"asm" : "str", (string) The asm

"hex" : "str" (string) The hex

},

"final_scriptwitness" : [ (json array)

"hex", (string) hex-encoded witness data (if any)

...

],

"unknown" : { (json object) The unknown global fields

"key" : "hex", (string) (key-value pair) An unknown key-value pair

...

}

},

...

],

"outputs" : [ (json array)

{ (json object)

"redeem_script" : { (json object, optional)

"asm" : "str", (string) The asm

"hex" : "hex", (string) The hex

"type" : "str" (string) The type, eg 'pubkeyhash'

},

"witness_script" : { (json object, optional)

"asm" : "str", (string) The asm

"hex" : "hex", (string) The hex

"type" : "str" (string) The type, eg 'pubkeyhash'

},

"bip32_derivs" : [ (json array, optional)

{ (json object)

"pubkey" : "str", (string) The public key this path corresponds to

"master_fingerprint" : "str", (string) The fingerprint of the master key

"path" : "str" (string) The path

},

...

],

"unknown" : { (json object) The unknown global fields

"key" : "hex", (string) (key-value pair) An unknown key-value pair

...

}

},

...

],

"fee" : n (numeric, optional) The transaction fee paid if all UTXOs slots in the PSBT have been filled.

}
```
  

``Examples:``
```
decodepsbt "psbt"
```
  
  

### ``decoderawtransaction "hexstring" ( iswitness )``

``Gives the decoded data from a raw hex-encoded transaction. Here we decode the results from createrawtransaction above.``
```
decoderawtransaction 0200000<snip>f33ad0000000

{

"txid": "c93dace459f5ac38c9d28ded224e47364abdde5e3fa947dc2d9c4422afb8852",

"hash": "c93dace459f5ac38c9d28ded224e47364abdde5e3fa947dc2d9c4422afb8852",

"version": 2,

"size": 119,

"vsize": 119,

"locktime": 0,

"vin": [

{

"txid": "17b3f9ef530695ef2e0368e445a3b59bf12811bdfd42325bb14248e72deb7e2",

"vout": 0,

"scriptSig": {

"asm": "",

"hex": ""

},

"sequence": 4384362583

}

],

"vout": [

{

"value": 1.00000000,

<snip>

}

]

}
```
  

### ``decodescript "hexstring"``

``Decode a hex-encoded script, for example, decode the script for a mulitsig address:``
```
decodescript 52460396bc49812bad50949fbc0bbd44e95bf32a5695519b3ff267a5d93cba3bd169b2393cd4864da4c2786dd3322fcfcb239c3db185ef33fa14836b8fecf36c68bb84ddac92f2

{

"asm": "2 0396c2483bbc207827fbc06fb32f48bf28450b5fb973032b742aeedd98dadcf3ba 02ba529ef3455bcc4339dbd7269acc2de135ff65a33c706a9beef48c37ab2a95ab 2 OP_CHECKMULTISIG",

"reqSigs": 2,

"type": "multisig",

"addresses": [

"Sgw5Ds4Py6J2oBX3EKP3kyde2UpnWn7eV",

"SK3bx79fzkei5XF7h2q7wB4s6MK99u29x"

],

"p2sh": "mKa7c52cX97eK4vdk35jV442p3j59hk3R"

}
```
  

### ``decodetimelockscript "hexstring"``

``Decode a hex-encoded script.``

  ``Arguments:``
```
1. hexstring (string, required) the hex-encoded script
```
  ``Result:``
```
{ (json object)

"sizeCheck" : true|false, (boolean) true/false

"firstOPCheck" : true|false, (boolean) true/false

"timelockSize" : n, (numeric, optional) OP_CODE hex

"timelockValue" : n, (numeric, optional) OP_CODE value

"pubkeyhash" : "hex", (string, optional) pubkeyhash

"address" : "str" (string, optional) address

}
```
  
``Examples:``
```
decodetimelockscript "hexstring"

> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "decodetimelockscript", "params": ["hexstring"]}' -H 'content-type: text/plain;' [http://127.0.0.1:8332/](http://127.0.0.1:8332/)
```
  

### ``deriveaddresses "descriptor" ( range )``

``Derives one or more addresses corresponding to an output descriptor.``

``Examples of output descriptors are:``
```
pkh(<pubkey>) P2PKH outputs for the given pubkey

wpkh(<pubkey>) Native segwit P2PKH outputs for the given pubkey

sh(multi(<n>,<pubkey>,<pubkey>,...)) P2SH-multisig outputs for the given threshold and pubkeys

raw(<hex script>) Outputs whose scriptPubKey equals the specified hex scripts
```
  

``In the above, <pubkey> either refers to a fixed public key in hexadecimal notation, or to an xpub/xprv optionally followed by one``

``or more path elements separated by "/", where "h" represents a hardened child key.``

``For more information on output descriptors, see the documentation in the doc/descriptors.md file.``


``Arguments:``
```
1. descriptor (string, required) The descriptor.

2. range (numeric or array, optional) If a ranged descriptor is used, this specifies the end or the range (in [begin,end] notation) to derive.
```
  ``Result:``
```
[ (json array)

"str", (string) the derived addresses

...

]
```
  
``Examples:``

``First three native segwit receive addresses``
```
deriveaddresses "wpkh([d34db33f/84h/0h/0h]xpub6DJ2dNUysrn5Vt36jH2KLBT2i1auw1tTSSomg8PhqNiUtx8QX2SvC9nrHu81fT41fvDUnhMjEzQgXnQjKEu3oaqMSzhSrHMxyyoEAmUHQbY/0/*)#cjjspncu" "[0,2]"
```
    

### ``disconnectnode "[address]" [nodeid]``

``Disconnects a peer (node) using either the IP address or node number. For example, sin-qt will return "null," sind will return nothing.``
```
disconnectnode "35.198.0.76:20970"
null
```
  

### ``dumpprivkey "address"``

``Displays the private key for a given address in WIF (Wallet Import Format). The wallet must be unlocked (and not for "staking only") for this command to work.``
```
dumpprivkey "SXfSbN8DaT21Z6L3Pw52UexuP8zW4mY6h"
V3vaEHms4VpciP85UsufQf3Gfa9p5gatBGm6Z4rD8FxzFLdXE5V
```
  
### ``dumpwallet "filename"``

``Writes all the wallet "private keys" to a file in clear text (unencrypted) format. The wallet must be fully decrypted (not just for staking only) for this command to work. Returns the filename. Dumpwallet will save all the private keys and their addresses; it will not save watch-only addresses (which do not have private keys in the wallet). This file contains all the private keys in the wallet (1,000 or more), be very careful and do not store the dump file online.``

``On PC:``
```
dumpwallet "C:\Users\<username>\Desktop\Backups\dump 2018-10-30.txt"
  {

"filename": "C:\\Users\\<username>\\Desktop\\Backups\\dump 2018-10-30.txt"

}

  ```

``File:``
```
Wallet dump created by SIN v22.x.x

* Created on 2022-03-31T01:56:32Z

* Best block at time of backup was 241161 (b11d5169d66d39cbcd848e2ea3f9adfcee1c22af945f100aec9e762d88609e2e),

mined on 2018-10-31T01:55:28Z
extended private masterkey: <snip>
```
  ``On Mac:``
```
dumpwallet /Users/<USERNAME>/Desktop/dump_2018-12-15.txt

{

"filename": "/Users/<USERNAME>/Desktop/dump_2018-12-15.txt"

}
```
  
``File:``
```
Wallet dump created by SIN core v22.x.x

* Created on 2018-12-16T02:22:59Z

* Best block at time of backup was 148510

(ca8a9457a69882b395bf56671e3661e148d3aca4a7b6c77398804229e7fb58f4),

mined on 2018-05-06T02:45:52Z
extended private masterkey: <snip>
```
  

### ``encryptwallet "passphrase"``

``Encrypts the wallet with "passphrase" for first-time encryption. After encryption, any calls that interact with private keys such as sending or signing will require passphrase entry to enable these functions. See also walletpassphrase, walletlock and walletpassphrasechange. After this command runs, the wallet will shut down.``
```
encryptwallet "you should always use a long and strong passphrase."
``` 
``(wallet exits)``

### ``echo "message"``

``Hidden command. Simply echo back the input arguments. This command is for testing.``

``The difference between echo and echojson is that echojson has argument conversion enabled in the client-side table in sin-cli and the GUI. There is no server-side difference. Here we echo the parameters used to set up a multisig address.``
```
echo "[\"sghwDvb1pyJoqoAD2ESMTevvvjUfNvReDn\",\"sfKr7vXdmroHi61XUUHedXvgV2mDx9Kudb\"]"

[

"[\"sghwDvb1pyJoqoAD2ESMTevvvjUfNvReDn\",\"sfKr7vXdmroHi61XUUHedXvgV2mDx9Kudb\"]"

]
```
  

### ``echojson "message"``

``Hidden command. Simply echo back the input arguments. This command is for testing.``

``The difference between echo and echojson is that echojson has argument conversion enabled in the client-side table in sin-cli and the GUI. There is no server-side difference. Here we echo the parameters used to set up a multisig address.``
```
echojson

"[\"SghwDvb1pyJoqoAD2ESMTevvvjUfNvReDn\",\"SfKr7vXdmroHi61XUUHedXvgV2mDx9Kudb\"]"
[

[

"SghwDvb1pyJoqoAD2ESMTevvvjUfNvReDn",

"SfKr7vXdmroHi61XUUHedXvgV2mDx9Kudb"

]

]
```
  

### ``echoipc "arg"``

  

``Echo back the input argument, passing it through a spawned process in a multiprocess build.``

``This command is for testing.``
 

``Arguments:``
```
1. arg (string, required) The string to echo
```
  
``Result:``
```
"str" (string) The echoed string.
```
  ``Examples:``
```
echo "Hello world"
> curl --user myusername --data-binary '{"jsonrpc": "1.0", "id": "curltest", "method": "echo", "params": ["Hello world"]}' -H 'content-type: text/plain;' http://127.0.0.1:8332/
```
   

### ``estimaterawfee conf_target (threshold)``

``Hidden command. WARNING: This command is unstable and may disappear or change, and the results are tightly coupled to the calling parameters.``

``It gives fee estimates for short, medium, and long-term confirmations and provides mempool statistics for transactions with those fees. In addition, it estimates the approximate fee per kilobyte needed for a transaction to begin confirmation within conf_target blocks.``
```
estimaterawfee 6
{
"short": {
"feerate": 0.01000002,
"decay": 0.962,
"scale": 1,
"pass": {
"startrange": 490954,
"endrange": 1e+099,
"withintarget": 14.31,
"totalconfirmed": 14.31,
"inmempool": 0,
"leftmempool": 0
},
"fail": {
"startrange": 0,
"endrange": 490954,
"withintarget": 3.57,
"totalconfirmed": 3.57,
"inmempool": 0,
"leftmempool": 0
}
},
"medium": {
"feerate": 0.00419464,
"decay": 0.9952,
"scale": 2,
"pass": {
"startrange": 403909,
"endrange": 490954,
"withintarget": 28.94,
"totalconfirmed": 28.94,
"inmempool": 0,
"leftmempool": 0
},
"fail": {
"startrange": 0,
"endrange": 403909,
"withintarget": 2.45,
"totalconfirmed": 2.45,
"inmempool": 0,
"leftmempool": 0
}
},
"long": {
"feerate": 0.00420764,
"decay": 0.99931,
"scale": 24,
"pass": {
"startrange": 403909,
"endrange": 626596,
"withintarget": 190,
"totalconfirmed": 190,
"inmempool": 0,
"leftmempool": 0
},
"fail": {
"startrange": 0,
"endrange": 403909,
"withintarget": 12.93,
"totalconfirmed": 12.93,
"inmempool": 0,
"leftmempool": 0
}
}
}
```

### ``estimatesmartfee conf_target ("estimate_mode")``

``Estimates the approximate fee per kilobyte needed for a transaction to begin confirmation within conf_target blocks.``
```
estimatesmartfee 10

{
"feerate": 0.00420597,
"blocks": 10
}
``` 
