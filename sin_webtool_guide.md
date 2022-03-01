**Introduction to WebTool, a browser based lightweight Wallet.** 

The Sinovate Wallet comes in different flavors. 
There is a Wallet application available for all kind of Operating Systems, 
including Windows, MacOS, Linux, IOS, and Android and there is the WebTool Wallet. 

The WebTool Wallet is special in that it runs inside a normal Web Browser, making it lightweight 
and a good alternative when the other Wallet applications are not available. 

In order to use the Webtool Wallet, you'll need to do two things: 
1) You need to download the WebTool files and place them on your device, so that the 'WebToolOpenWithaBrowser.html' can be loaded into the device web browser.

2) You need to load a [PRIVATE KEY] from your other Wallet. This document will describe the steps needed to do those two things and the features of the WebTool Wallet.

# Features
    
-   Send coin nominative feature
-   Invoice payment transaction with attached information
-   Vote E-Governance vote 
    
# Make a Keyfile
    

Download the latest version from [https://github.com/SINOVATEblockchain/SINWebTool/releases/](https://github.com/SINOVATEblockchain/SINWebTool/releases/)

Extract the files to a suitable folder on your computer.
 

![](assets/img/sin_webtool_guide/webtool01.png)


Double-clicking the WebToolOpenWithaBrowser file will open SIN WebTool in your current browser.

Open your SIN-core wallet to use in Online Mode. Find and copy the address you want to process from the Coin Control window.
 

![](assets/img/sin_webtool_guide/webtool02.png)  
  

Access the Console tab by following the Help / Debug Window menu.
If your wallet is encrypted, temporarily disable it by following the steps below.


![](assets/img/sin_webtool_guide/webtool03.png)

  
**yourpassword:** enter your valid wallet password instead.

**1000:** For example, the wallet was decrypted for 1000 seconds. You can set a time for you.
 

**Note:** If your wallet is not encrypted, you can skip this step. However, we strongly recommend protecting your wallet with a password.


After these processes, we can proceed to the Key File creation phase.
  
  
![](assets/img/sin_webtool_guide/webtool04.png)


**youraddress:** The address we copy and process on the Coin Control window.
**newpassphrase:** A new password required for operations on SIN WebTool.


**Sample:**


![](assets/img/sin_webtool_guide/webtool05.png)

  
When we run the command, a key file is generated. You can find the key file in the folder where you run the SIN-qt file.


![](assets/img/sin_webtool_guide/webtool06.png)


![](assets/img/sin_webtool_guide/webtool07.png)

  
Open SIN WebTool in your browser and click the Choose File button.

  
![](assets/img/sin_webtool_guide/webtool08.png)

  
  

You will be asked to specify the file. Scroll to the SIN-Qt.folder.


Select the Keyfile file and click on the open button.



![](assets/img/sin_webtool_guide/webtool09.png)

  

When the "Keyfile" is installed successfully, you will receive a message that you have Full Control on SIN WebTool as well as address and balance information on the screen.


![](assets/img/sin_webtool_guide/webtool10.png)

  

# Send
    

Click the "Send" button on the left menu


![](assets/img/sin_webtool_guide/webtool11.png)

  

Select the desired amount from the Coin Control drop-down menu. Or write the amount you want to send to the Amount section and click the "Auto select coins" button. Thus, the amount you want to send will be selected automatically. In the meantime, you should see the message "Coin Control is Updated" at the top right.


![](assets/img/sin_webtool_guide/webtool12.png)

  

Then enter the password you provided during the Keyfile creation box in the Passphrase box and click the "Verify Input" button.

  
![](assets/img/sin_webtool_guide/webtool13.png)



The "True" message informs us that the transaction was successful.

Now we can enter the address we will send SIN and click the "Create-Sign" button.

  
  
![](assets/img/sin_webtool_guide/webtool14.png)

When the signing is successful, you can complete the sending process with the "Send" button.


![](assets/img/sin_webtool_guide/webtool15.png)

  

As a result of this process, you will be informed with the message **"Transaction is broadcasted to the network with success!"**. You will also be given a tx number for the transaction.



![](assets/img/sin_webtool_guide/webtool16.png)

  



# R.S.V Vote
    

With this feature, you can vote on existing voting.

Click the "R.S.V Vote" button on the left menu

  

![](assets/img/sin_webtool_guide/webtool17.png)

  
  

1- Enter a proposalID. (For example 10000000)

2 - Enter Yes / No for your vote

3- Click the Verify input button

You will be charged 1 SIN for this voting.

  


![](assets/img/sin_webtool_guide/webtool18.png)

  

Enter your password and then click the Create-Sign button.

  

![](assets/img/sin_webtool_guide/webtool19.png)

  

![](assets/img/sin_webtool_guide/webtool20.png)

  

Once your vote has been submitted successfully, you will be given a Transaction ID.



![](assets/img/sin_webtool_guide/webtool21.png)

