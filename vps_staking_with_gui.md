
# This guide is to create VPS staking solution with a GUI interface for beginners.

Expert users may not require the installation of the GUI Desktop can interact with the wallet only thourgh command lines.

  
 - STEP 1: Create an account in a VPS provider.

This solution has been configured with OVHCloud with a VPS of 3.6 EUR per month.

You can choose our own provider until you meet the following minimal requirements:

Ubuntu VPS With 18.04 OS
2GB RAM, 2Core CPU, 20GB Storage
Root access to Ubuntu or “sudo” access

  

STEP 2: Installation of VPS with Putty
```
apt-get update
```
```
apt-get -y install software-properties-common
```
 ```
apt-add-repository -y ppa:bitcoin/bitcoin
```
  
```
apt-get update
```
  

```
sudo apt-get install -y openssh-server build-essential git automake autoconf pkg-config libssl-dev libboost-all-dev libprotobuf-dev libdb5.3-dev libdb5.3++-dev protobuf-compiler cmake curl g++-multilib libtool binutils-gold bsdmainutils pkg-config python3 libevent-dev screen libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libqrencode-dev libprotobuf-dev protobuf-compiler mc unzip bash-completion
```
  

## Install GNOME To Have GUI on Ubuntu 18.04

Implementing a Ubuntu VPS With a GUI is super easy and needs a couple of commands to be executed. Here I will show you how to install Linux VPS with GUI on Ubuntu 18.04 and xRDP service. GNOME offers a great work environment and design, which makes you more productive. Recommended for users who store documents using online services. Also, It can be easily integrated with online accounts/services.

### Requirements

-   [Ubuntu VPS](https://operavps.com/ubuntu-vps/) With 18.04 OS
    
-   2GB RAM, 2Core CPU, 20GB Storage
    
-   Root access to Ubuntu or “sudo” access
    

### Instructions

Connect to your VPS through SSH, and make sure the OS and current software are updated to the latest version by entering the following command:
```
sudo apt update -y
```
  ```
sudo apt upgrade -y
```
Note: There are two versions of GNOME(minimal and full) and you need to install only one of those.

-   Using GNOME Minimal desktop (Vanilla)
    

Vanilla will set up a basic GNOME shell and minimal pre-installed applications. Perform the following command to install Vanilla GNOME.
```
sudo apt install gnome-session gdm3
```
![Install Linux VPS With GUI Using GNOME Minimal desktop (Vanilla)](https://lh3.googleusercontent.com/7VTkrGl37WPOMR_Cidn20WfRzidHbwODFvbaPIE3ckBSrpmmFhjwmW6sPyLBA-2tVGr-0PvfOtihrZHc1MUYNfhYy6LWiLPI4WLkWUKOCb66ycpwlRoruyqeMfsNYFDEy-jfLEMl)

-   Using GNOME Full Desktop
    

To have a full Ubuntu package with GNOME desktop and all applications, you need to use “tasksel” command.
```
sudo apt install tasksel
```
Then, install the GNOME with “tasksel”.
```
sudo tasksel install ubuntu-desktop
```
![Install Linux VPS With GUI Using GNOME Full Desktop](https://lh3.googleusercontent.com/6n7AUQXxMuOFpAqQjMdGsjI-pH-49weV6pRVGKI-QHXUBum2IgjUv5mmkz8W3QwncAq8x6IhKE-6WCFsZ5YOhuRRyH1trJI4dFpUMQLAkgL6yBD5I1gtWdWGDWGnu2eZK9Qmr98x)

After you installed GNOME, make a new username, set a password, and process a reboot:
```
sudo adduser newuser
```
```
sudo passwd newuser
```
```
sudo reboot
```
Now you should be able to log in (via newuser username) to your VPS with GUI through the console.

## Install xRDP on Ubuntu 18.04

Console access has many disadvantages and is mostly used when the system has lost access to the Internet, you want to check and fix the problem, so it is not suitable for everyday use. Instead of a console, it is better to use remote access faster and has more advantages than the console.

xRDP is a Remote Desktop Protocol (RDP) service that allows RDP clients to your Linux VPS with GUI. The GNOME is already installed on Ubuntu and you have access to the GUI through the console, but to have access remotely, you must install a service like xRDP.

1.  Install xrdp on Ubuntu 18.04.  
    sudo apt-get install xrdp -y
    
2.  Allow the RDP default port on the UFW firewall.  
  ```
    sudo ufw allow 3389/tcp
```

Create a polkit configuration file.  
```
sudo nano /etc/polkit-1/localauthority.conf.d/02-allow-colord.conf  
```
Input the following inside it, and save.  
```
polkit.addRule(function(action, subject) {
if ((action.id == “org.freedesktop.color-manager.create-device” || action.id == “org.freedesktop.color-manager.create-profile” || action.id == “org.freedesktop.color-manager.delete-device” || action.id == “org.freedesktop.color-manager.delete-profile” || action.id == “org.freedesktop.color-manager.modify-device” || action.id == “org.freedesktop.color-manager.modify-profile”) && subject.isInGroup(“{group}”))
{
return polkit.Result.YES;
}
});
```
    
4.  Finally, restart xrdp.  
```
 sudo /etc/init.d/xrdp restart
```

### Connect To Ubuntu VPS with RDC

If you have successfully installed the xRDP and GNOME, you should now be able to connect it via Remote Desktop Connection(RDC) software like connecting to a [Windows VPS](https://operavps.com/windows-vps/).

[How To Use Windows RDP Remote Desktop](https://operavps.com/how-to-use-windows-rdp-remote-desktop/)

After you logged in to the remote environment, you will see some options for connection. Select the “Xorg” option, and enter the username and password.

![connect to linux vps with gui through Xorg](https://lh6.googleusercontent.com/kclRSDWI_D7CnyQsBupxOUF3qGra5LeEsYeh8F9FaznsBibn36-MraOn97sRLg6PDsCR4038p2riYS4g-zxWfkueGicfZIWkSZhpGjvdyEtkE1r4poZaipKKc7xtKx9URSvUbK2h)

Before finishing the installation, do the folllowing command in the SSH terminal:
```
sudo usermod -aG sudo newuser
```
STEP 4: Installation of the Linux Wallet

The GUI Desktop allows you to use the wallet in a graphical way. 

First, install the last Linux wallet version: 
https://github.com/SINOVATEblockchain/sinovate/releases

To open the wallet, you must make the file as an executable.
Navigate in the folder to the Downloads folder. Right click on the ZIP file and "Extract Here".
It generates a folder. Open it and copy/paste the sin-qt file in a folder of your choice.
In the folder of sin-qt, open a terminal. Right click in the folder and choose "Open a Terminal".
In this terminal, do the following commands:
```
sudo chmod a+x sin-qt
```
To launch the wallet, do the command:
```
./sin-qt
```
To update quickly the wallet, please follow this guide:

https://docs.sinovate.io/#/bootstrap

STEP 5: Let's stake

Follow this guide: https://docs.sinovate.io/#/what_is_staking

