# Azure notes 


- [Azure notes](#azure-notes)
    - [Things to remember:](#things-to-remember)
  - [ssh key](#ssh-key)
    - [Creating ssh key on my machine](#creating-ssh-key-on-my-machine)
    - [Creating a virtual network](#creating-a-virtual-network)
  - [VM](#vm)
    - [Creating VM:](#creating-vm)
    - [deleting vm](#deleting-vm)


### Things to remember: 
all azure items must have an owner: my_name tag <br>
naming convention: tech501-my_name-thing_created-identifier

## ssh key 
### Creating ssh key on my machine
* 1. navigate to .ssh folder 
  * can use the ls -a command to see the hidden folders 
* 2. run the ssh-keygen command 
* 3. follow the prompts 

using the ssh key: 
ssh-copy-id (can be used to avoid re-entering)
can also go to vm on azure and copy from the connect menu 


### Creating a virtual network 

* public subnet 10.0.2.0/24 + private subnet 10.0.3.0/24 - all use sections of the space (not full half)
* tech501 - emily-2-subnet-vnet 
* space (CIDR) 10.0.0.1/16 aprox 65,000 IPadresses 
  <br>
**look up IP version 4** 

## VM 
### Creating VM: 

**Our virtual machine**: <br>
**Name**: tech501-your_name-first-vm <br>
**Region**: UK South <br>
**Security**: standard <br>
**Image (i.e. the OS that will go onto the machine)**: Ubuntu Pro 18.04 LTS Gen 2 [LTS means long term support for ~7 years] <br>
**Size:** Standard_B1s — 1 vcpu, 1 GiB [very important to set correctly because this impacts pricing] <br>
**Administrator account:** adminuser <br>
**Key pair**: Use existing key pair stored in Azure (use the one with your name) <br>
**Select inbound ports:** allow HTTP and SSH traffic <br>
**Disks tab:** <br>
  OS disk type: Standard SSD <br>
**Networking tab:**<br>
  Virtual network: your named version <br>
  Subnet: public-subnet <br>
  Choose Delete public IP and NIC when VM is deleted option <br>

> ### starting your virtual machine 
> connect > select native ssh > start 
> fill in window: 
> - provide ssh key path 
> - use provided code 
> - paste into terminal,say 'yes' if asked permissions 
> - can check that you are in the vm by running a command such as pwd 

### deleting vm 

home > resouce group > tech501 <br>
filter for name <br>
delete: disk, network interface group, maybe the network security key, public IP, VM itself <br>
keep: virtual network + ssh group <br>


