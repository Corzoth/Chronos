# Chronos
An ethical hacking lab project documenting the design and deployment of a Raspberry Pi–based red team drop box, emphasizing OPSEC, automation, and realistic adversary workflows.


***CURRENT STATUS***: incomplete  

HARDWARE:
* Raspberry pi 4 model B with 8gb ram
* 128gb A2 Micro SD card
* 256gb external SSD
* USB2 to ethernet converter
* Support machine(for installs and flashing)
  
The raspberry pi is setup with the intention that it should be ran headlessly, and without any persistant keyboard, mouse, or display.     

Operating System  
Raspberry pi OS lite (64 bit, no desktop)  

The pi is intentionally set up so that it is only interacted with through SSH (Secure shell) from the support machine. the login is set up such as the username and password are both impossible to brute force via low level techniques(hydra, wordlist based bruteforcing) by making a 128 character long mix of random letters, numbers, and symbols for each the username and the password. No GUI based tools or processes exist on the device.

Initial setup:  
The raspberry pi is accessed via the support machine through a connection via an ethernet cable. Since the goal is to have all interaction through SSH, I decided to challenge myself to not plug in a keyboard, mouse, or monitor to the pi for the entirety of the project. 

To achieve initial access to begin customising the pi and ensure that I'm the only one ever to access it directly, I started a DHPC server hosting off my support device (using dnsmasq) in order to assign the pi a static IP that I can then use in connecting via SSH. Because of this, the pi is not exposed to the internet during this stage of the setup.

Once the DHCP server is running, and the pi is connected, I ran arp -a in order to discover the automatically assigned IP adddress. I then connected to the pi via SSH, and attempted to assign it the static IP address of 192.168.50.2 (and assigned my support device 192.168.50.1 for simplicity). However, as I am inexperienced with projects such as this, I failed to assign this static IP address. However, tech being tech, it decided to assign itself 192.168.10.61 as a static IP. As of writing this, I dont really understand how this happened, but the goal of assigning (or in this case, discovering) a static IP for the DHCP server was successful.

Through SSH, I confirmed:
The pi runs headlessly
It is only accessible via SSH
The Pi can be accessed(implying that the initial setup was a success)

**Current state of the project**
* Pi is consistently accessible via SSH and a DHCP server
* Pi does not connect to the internet
* Only hardware on the pi is the pi itself, an ethernet cable, and an A2 micro SD.


**Next steps**
* Mount the external SSD
* Tool installation
* Persistant storage configuration
* Further automation and hardening
* Setting up connection to my home server (Hyperion repo soon to be created)

last updated on 28/1/26
