
Kathara physical setup (collision domains)
## General rundown of the commands

1. V-prefixed commands  (low level for configure up a single device)
	example:
	- **vstart**: start a new device 
	- **vconfig**: attaches network interfaces to a running device 
	- **vclean**: halts a device 
2. I-prefixed commands  (easier to use enviroment to set complex labs)
	- **lstart** : **starts** kathara lab from a .conf 
	- **lclean** :**stops** every virtual machine without name 
	- **lrestart**: halt and reboot the lab 
	- **linfo**: provides informations about a lab 
3. global commands (management of commands):
	- **check** : Check the system enviroment 
	- **connect** : connect to a running Kathara machine 
	- **list**: show all running machine s
	- **settings** : show and edit Kathara setting 
	- **wipe** alla kathara machines and links and settings


## Share stuff between the host and the devices
- /shared directory inside a device directly points to the /shared inside the lab


[[Kathara Physical setup(Phy level)]]
[[Network setup(Logical part)]]


