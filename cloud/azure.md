*quiting a process in linux*: q / ctrl z / ctrl c 

### instructions for creating ssh key 
* 1. navigate to .ssh folder 
  * can use the ls -a command to see the hidden folders 
* 2. run the ssh-keygen command 
* 3. follow the prompts 


### instructions for creating a virtual network 

public subnet 10.0.2.0/24 + private subnet 10.0.3.0/24 - all use sections of the space (not full half)

tech501 - emily-2-subnet-vnet 
space (CIDR) 10.0.0.1/16 aprox 65,000 IPadresses 

look up IP version 4 


### instructions for creating VM: 

Our virtual machine:
Name: tech501-your_name-first-vm
Region: UK South
Security: standard
Image (i.e. the OS that will go onto the machine): Ubuntu Pro 18.04 LTS Gen 2 [LTS means long term support for ~7 years]
Size: Standard_B1s — 1 vcpu, 1 GiB [very important to set correctly because this impacts pricing]
Administrator account: adminuser
Use existing key pair stored in Azure (use the one with your name)
Select inbound ports: allow HTTP and SSH traffic
Disks tab:
OS disk type: Standard SSD
Networking tab:
Virtual network: your named version
Subnet: public-subnet
Choose Delete public IP and NIC when VM is deleted option

conect > select nateive ssh > start 

fill in window: 
- provide ssh key path 
- use provided code 
- paste into terminal,say 'yes' if asked permissions 
- can check that you are in the vm by running a command such as pwd 

### deleting vm 

home > resouce group > tech501 
filter for name
delete: disk, network interface group, maybe the network security key, public IP, VM itself 
keep: virtual network + ssh group 

## running a new vm 

first run 2 commands: 
- sudo apt update
- sudo apt upgrade -y 

making a script: 
nano prevision.sh 
sudo apt install nginx
sudo systemct1 restart nginx
status nginx
sudo systemctl enable nginx
