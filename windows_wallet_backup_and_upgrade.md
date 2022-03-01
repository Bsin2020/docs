## Windows QT Wallet Backup and Upgrade Guide

  

* First of all, don't forget to back up your current data.

* Close your wallet.

* Open the Run window using the WIN + R key combination.


* Enter the `%appdata%/SIN` command and click the OK button. Thus, you will reach the directory where your SIN data is kept.

![run](assets/img/misc/run.png)
 

Your wallet.dat file can be either in the wallets directory or in the SIN home directory, depending on the situation. Pay attention to this and back up these files to a suitable medium. We recommend that you do this periodically.

  
![directory](assets/img/misc/directory.png)


Download the latest version of Windows Wallet at [https://github.com/SINOVATEblockchain/SIN-core/releases](https://github.com/SINOVATEblockchain/SIN-core/releases)
 

![release](assets/img/misc/release.png)
  

Replace the `sin-qt.exe` file in the compressed file you downloaded with the `sin-qt.exe` file you are currently using.


## Resync Windows wallet
In case you need to resync your local wallet in Windows:
* Close wallet;
* Create a shortcut;
* Rick click on shortcut and select properties;
* add in target, at the end of the path ` -reindex` (space -reindex, see screenshot below)
* wait full resync

![](assets/img/misc/win_wallet_reindex.png)
