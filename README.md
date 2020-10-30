# How to Run Algorand Node On Windows 10 Using Windows Subsystem For Linux (WSL 2).
       INSTALLING WSL2
       
STEP 1 - Enabling The Windows Subsystem for Linux and Virtual Machine Platform.

  Open PowerShell as Administrator and Run

  $ dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

 - Enable Virtual Machine Feature.

  $ dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
or
 - "click windows logo key + Q,Search for turn windows feature from your search bar, 
   look for "Virtual Machine Platform" and Windows Subsystem for Linux and enable them.
   make sure the checkboxes are check and restart your system when prompted.

2 - Update to WSL 2.

 To download WSL 2 click https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

  Requirements:
   
   For x64 systems: Version 1903 or higher, with Build 18362 or higher.
   For ARM64 systems: Version 2004 or higher, with Build 19041 or higher.
   Builds lower than 18362 do not support WSL 2. Use the Windows Update Assistant to update your version of Windows.
   To check your system version and OS build number, select Windows logo key + R, type "winver", select OK.
   Update to the latest Windows version in the Settings menu.
   version 1707,1903 or 1909 builds can install WSL 2 too – but must first install Windows Update KB4566116.

  restart your system at this point or you may find that things don’t work as intended.
3. Set WSL 2 as default.

  Open PowerShell as Administrator and run this command to set WSL 2 as the default version of WSL:

  $ wsl --set-default-version 2

4. Install a Linux Distro

  Linux distros are available including CentOS, Pengwin, Desbian, Fedora, Remix, and Alpine Linux. 
  as algorand node image will be pulled from the ubuntu-18.04 dockerhub.
  I recommend installing Ubuntu-18.04 LTS 
  To install Ubuntu on Windows 10 open the Microsoft Store app, search for “Ubuntu 18.04”, and hit the “Get” button:
 
  Whilst you in the Microsoft Store I highly recommend that you also install the open source Windows Terminal app.
  This tool is designed to give you the best possible WSL experience.

5 - make Ubuntu-18.04 default distro.
 $ wsl.exe --set-version Ubuntu-18.04 2


6 - Use WSL 2
  When you installed Ubuntu-18.04 a shortcut was added to the Start Menu. Use this to “open” Ubuntu-18.04 terminal 
  The first time you run the distro things will get installed a little time. This is expected; 
  You will be prompted to set a username and password for use on the distro. Try to pick something you won’t forget.

7 -   How to download, Install and Run the Algorand Node.

  Open the Ubuntu-18.04 terminal from your start menu or search box.

 - make a directory
    user@user_pc $ mkdir node

 - enter the directory
    user@user_pc $ cd node

 - pull the algorand installer file.
    user@user_pc $ wget https://raw.githubusercontent.com/algorand/go-algorand-doc/master/downloads/installers/update.sh

 - Make the system know is an executable file.
    user@user_pc $ chmod 544 update.sh

 - Download the node it will take some time please wait.
    user@user_pc $ ./update.sh -i -c stable -p ~/node -d data -n

 - Start the node
    user@user_pc $ ./goal node start -d data

 - Check the node status
    user@user_pc $ ./goal node status -d data



 
