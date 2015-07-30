**Paycoin Testnet Wallet Setup**

This guide will get an operating qt wallet setup on a virtual machine for use on the testnet

**Required Downloads**
- [Virtual Box (latest release)](https://www.virtualbox.org/wiki/Downloads "Virtual Box")
- [Ubuntu 64 bit (latest release)](http://www.ubuntu.com/download/desktop)

**Download and install Virtual Box from the installation file before proceeding.**

**Create Virtual Machine - Virtual Box** * (VMWare Users:: Instructions are at the bottom of this guide)
- After installing and opening Virtual Box the first time:
- Click "new" to bring up the new VM window.
- Name the Vm "Paycoin Testnet" (you can name it anything you'd like)
```bash
Type: Linux
Version: Ubuntu (64 bit)
Memory Size: 1024mb (to help make compiling easier)
Hard Drive: Create a virtual hard drive now
Hard drive file type: VDI (you can choose whatever works best for your situation)
Storage on physical hard drive: Dynamically Allocated
File Location and Size: Click the Folder icon to change the location of the file that will house
your VM.
Drag the slider to the size of the hard drive you'd like to allocate to the VM (the 8gb default
should be more than enough, you can allocate more if you have the space)
```
- Click "Create"
This will take you back to the Oracle VM VirtualBox manager, and you will now have a VM in
the list named "Paycoin Testnet"

**Installing Ubuntu**
- Click on your new VM in Virtual Box and choose "start"
- This will prompt you for a startup disk. Click the folder icon and choose the
- “ubuntu-14.xx.x-desktop-amd64.iso” file you downloaded from the ubuntu site.
- After selecting the iso click "start"
- This will start the Ubuntu installation process.
- After a few moments the setup installation window will come up in your virtual machine:
- Choose "install ubuntu"
- Preparing to install ubuntu will come up next, Check the box for "Download updates while
- installing" Click "continue"
- Installation type: Erase disk and install ubuntu Click "install now"
- Click continue for the confirmation to write to the disk
- Select your local time zone, click continue
- Select your preferred languages and keyboard, click continue
- Create a user, computer name and password, click continue
- The installation will now proceed

**Once complete you will be prompted to restart your vm.**
- The system will prompt you to hit the "Enter key" when it restarts, this will unmount the ISO
and boot from the hard drive
- Once your VM reboot is complete you'll be presented with the login screen.
Log in to your fresh VM with the username and password you created.

**Install Virtual Box Addons**
- click on the "devices" menu (the virtual box menu at the top of the window) and choose
"insert guest additions cd image"
- ubuntu will load that virtual cd and ask you if you'd like to run the guest additions
click "run"
- enter your password
- it will run some installation files to make the vm work a little smoother inside virtual box
(including resizing the screen)
- When complete it will prompt you to press return to close the window.
- Press enter.
- Reboot ubuntu by clicking the power icon in the top right corner and choosing "Shutdown"
and then "Restart" from the shutdown menu that appears.
- After rebooting you should be able to resize your screen and it will scale. etc.

**This is a good time to take a snapshot of the VM as it's now ready to use base.**
- Click the "Machine" menu and choose "Take Snapshot"
- Name the Snapshot "Ubuntu Base Install" (anything that makes sense to you) and click ok.

**Paycoin Wallet Dependencies Installation:**
Click the Ubuntu Icon on the top left of the screen, search for terminal
Open a new terminal window
Once in the terminal window and at the command prompt we'll install the dependencies

**Install Dependencies:**
```bash
sudo apt-get update
sudo add-apt-repository -y ppa:bitcoin/bitcoin
sudo apt-get update
sudo apt-get -y install build-essential git libboost-all-dev libssl-dev qt4-qmake libqt4-dev
libdb4.8-dev libdb4.8++-dev libminiupnpc-dev libminiupnpc8 libqrencode-dev
```

**Download and compile wallet**
```bash
git clone https://github.com/PaycoinFoundation/paycoin.git paycoin
cd paycoin
sudo qmake
sudo make
./paycoin-qt
```
This should launch the paycoin QT wallet.
Once it opens close the wallet (it will start syncing, this is not the blockchain you’re looking for
so just close it out)

**Create .conf for testnet**
- Click the File Explorer from ubuntu menu on the left of the screen (it looks like a filebox)
- Click the "View" menu at the top of the ubuntu window (not virtualbox/vmware) and choose
"show hidden files"
- This will add some additional folders to the home folder window that is currently open
- open .paycoin (note the . before paycoin, it's a different folder than the paycoin folder)
- ***delete everything in the .paycoin folder***
- After the folder is empty:
- right click in the window choose new document > empty document
- right click the untitled document you just created and choose "rename"
- rename the document paycoin.conf
- right click paycoin.conf and choose "open with gedit"
- put the following lines in the paycoin.conf file

```bash
testnet=1
paycoinport=9000
rpcallowip=127.0.0.1
rpcport=9001
rpcuser=MakeAUsername
rpcpassword=MakeAPassword(Strong)
maxconnections=400
addnode=tseed.paycoin.com
```
Save the .conf file
Click the "Home" shortcut in the left side of the open window
open the paycoin folder
double click paycoin qt

**Welcome to the Paycoin Testnet. Now let’s mine some blocks and get those coins
staking!** (instructions below)

**To CPU Mine on Testnet**
- With the QT wallet open:
- Click Help >debug window
- click the console tab
- type: setgenerate true 1
- hit enter
- this will cpu mine with 1 core
- to stop mining
- type: setgenerate false

**Create Virtual Machine (VMWare)**
- File > New Virtual Machine
- Choose Installer Disc Image file > select the ubuntu .iso you downloaded click next
- Enter name, username, password for the vm > next
- Name the VM and choose the location you wish to save it to > next
- Choose the disk split you prefer > next
- Hard drive size: default > next
- Choose the disk split that best works for you (default is ok) > next
- Installation will launch, refer to "installing ubuntu" Start at step: “ After a few moments the setup installation window will come up in your virtual machine:
- Choose "install ubuntu"”
