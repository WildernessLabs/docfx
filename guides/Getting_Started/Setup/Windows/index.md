# Windows Setup

## Prerequisites
[Vagrant](https://www.vagrantup.com)
[VirtualBox](https://www.virtualbox.org)

### Windows only
You need to disable Hyper-V in order to use the VirtualBox hypervisor. This can be done by opening **Windows Features** in the Control Panel.

Athough Vagrant supports other VM hosts such as VMWare and Hyper-V, we require VirtualBox to access Meadow over USB.

## Create the Meadow deployment Virtual Machine
1. Download **Vagrantfile** and **config.sh** to the folder (working folder) where you'll create your virtual machine (VM)
2. Open the Command Prompt
3. Using the command prompt, navigate to your working folder
4. Enter *vagrant up* to create the virtual machine - this make take several minutes

Your virtual machine is now running. You can access your VM by entering 'vagrant ssh' from the command prompt.
