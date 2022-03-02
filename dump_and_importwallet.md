**

## Dump and Import Wallet Guide

**

*This guide includes the ``dumpwallet`` and ``importwallet`` steps for migrating from SIN-Core v.1.0.0.2 to v22.0.0*
    <br>
![](https://lh3.googleusercontent.com/NyFJBJFLLlx89KTx2cEsgPbw5yFU09055i-mK4DGEZieVGTL88S-ePws4VCgycpcocIEWqA9LOEwuq0h72x8_ea-RPkGL1yQpC0r30CSiMT5JxO5_VhMcr_tnfG---9b8m8CaxOG)

  <br>

:warning: Don't forget to backup your old wallet.dat file first.:warning:
  <br>
  

:bulb: This guide assumes you have a working and synchronized SIN-Core v1.0.0.2.  
 
If your wallet is encrypted :closed_lock_with_key:, open the console and enter the following command as convenient for you.  

    walletpassphrase [your_password] [ timeout]  

E.g.

![](https://lh3.googleusercontent.com/h3NdudN1l5Z8a5teM4HXbhBY1ubjwPI1oGOSmJCRb_C-1Gztv9x2RnfCoRguJIWVyDXPZnbf0krTtdCuf_ghI-qOvA68x7q_n_qfRiUbscrF_8e_ktXj8nkmbzfj7_dcKgjKcmKm)

  

This command will disable :unlock: the encryption for the timeout period.

![](https://lh3.googleusercontent.com/YW2v-PNcYw4K4rAuJN-ifrujgsZzKvTMils4I3OKx2cVyZPc6uCyuTmuYuLvztpC5c-QBdZ7MH7HMfK80VLe0P0tJ5EC3q07rpJaAwQAm3h3BIhJiAp8NdV5UX1mWFq4el9MbITI)

  
  
  

Now we will dump our wallet.dat file into a file named my-old-wallet.txt.

![](https://lh5.googleusercontent.com/00QQ_EVpuYzwltQhTkmmc-lfjWomoMkeqykPO4FTe_qk2n2PaW_4PkXSSkMkTxkaBc2ofxJM1B7TX28Muc6-3z-sQCeY-FJ7RSNKeL8ljtOrtC5DtI7L4oMKNI9U8fnTHjPD1HXC)

  
  <br>

![](https://lh6.googleusercontent.com/1EXEb_EiZUXJAIAndiyBS38_HCg0MsL0vvP15xIfPbIKpBhukKiQwdubtex8lBAAjowZRQvqlnBzkSM2uSSfrEMWGU_Cu-19Zrv8ycV4ahdJd_q_9y2lMbFOAt8-Vwdhq98kkFte)
<br>

As a result of the process, you can see the my-old-wallet.txt file in the folder where we run the sin-qt file.

![](https://lh6.googleusercontent.com/ER1PGwK4puQtHwKIHkxqPChdVbwMq7YqbqJW7Qk_wnBBr0wo3HBwwru30nT8JgK8Za5FJRiKGsBJuX9yMNZ8V6AoeWDDRo-Gkxz-1nCfo1iEZTCM2SDIhh42ORg-JtTZmbA3VOBO)

Now we can close the old wallet.

For Windows by default: go to the %appdata%/SIN folder. :warning: Be sure to back up your wallet.dat file again, and delete everything. :warning:


Download a new wallet from the below link and replace it with the old sin-qt.  
[https://github.com/SINOVATEblockchain/sinovate/releases/latest/](https://github.com/SINOVATEblockchain/sinovate/releases/latest/)

  

Download the latest bootstrap files from the link below.  
[https://service.sinovate.io/mainnet/latest/bootstrap.zip](https://service.sinovate.io/mainnet/latest/bootstrap.zip)

  
  

For information about Bootstrap, see the guide below.  
[https://docs.sinovate.io/#/bootstrap](https://docs.sinovate.io/#/bootstrap)

  
  

Wait for the wallet to sync. And create a new wallet.

  

![](https://lh3.googleusercontent.com/qttc1wGkpx3MMjAP3KuP6eR4HVzRfBEgrYxgkGNh5pFkBSLcIn0lkJb5CrPmBuyi3w1hkHyiBg5kDpLdp0wlcjd9UMYu_KJwNgK7VIDViNxp3qHs9Lh1Bz3HZ7qmtfPNDxZc8ypM)

  

Go to console and enter the following command
<br>
```  
importwallet my-old-wallet.txt  
```
<br>

  
![](https://lh6.googleusercontent.com/luxfQZZAE5gsBWKObzEAaYmxp8_2IUdeZccXuxhCxx4UzBAGBF5q0aRgkKhIbX4fxCg5oBwE0D32TWYnw0MfgM9R16pb6cvxo70AKhqEDlRqPmql0zmR1NtEAPAuUUFXt3fy2OVr)  
  <br>
  
![](https://lh4.googleusercontent.com/FerYzfXVEFYY7BiDGW4GZKcI6-yELQAfBmZvPqimhG1IJmmheyPUmuwMyoMZufD6FBEB4yx28S-WJis8s5rRchvbJP5BOqVftKR3cpGt8gHjtDO6pWYfuGNmRo69E6m1wf_TT5Bw)
<br>

![](https://lh6.googleusercontent.com/bIlVs3iT62_f8ehizwn2lQWoMEY38TanqfPuDLrp0PIWKyHsvME-fvN7d5D0NoblHFe2MoyseJeXaXXnfHw4XIo0prXysfbIPo_UipMM0iQddjNhvcjI0gEiaZaqQ43pmXVJpQ3i)  
  

Depending on the density of your wallet.dat file, this process may take some time.  
  <br>
  
![](https://lh5.googleusercontent.com/6QZo6RIilWAnNHMnnaDaL0Q6U0AlwB_q4GNzaS8YE_PRLCuYFIxFbM9fsqJYnrSnrJkULVGU4f_slzmpBbO--7fUmLi-bwXxhmKysUsKbL_Vcq44hhwAMxmHDpOi5MStZrhntu6V)

Congratulations  
:warning: Don't forget to protect your wallet again with a strong password and back it up frequently. :warning:
