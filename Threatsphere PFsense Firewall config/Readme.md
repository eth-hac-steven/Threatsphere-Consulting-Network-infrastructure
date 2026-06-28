# Threatsphere Firewall configuration

##  Prerequisites
  - virtualbox 😃/VM ware ☹️
  - PFsense iso installed
  - A windows pc 

Please refer to [this](https://github.com/eth-hac-steven/Home-lab-Virtual-Machine-Setup/tree/main/PFsense%20Firewall%20Installation) to install the firewall iso in virtualbox

### Note 
- when setting the hostname, avoid uppercases letters
- If you want to use  your physical system 
   - change Adapter 2 on the Pfsense VM to Host-only connection
   - Then follow the step 
- This allows your physical system to speak directly to the firewall bypassing the need on the Win 11 vm(still recommended though)

### PFsense  setup
- Device Setup
   - Make sure that the win pc and  PFsense are on the same LAN network 

- Start the Machines
- On PFsense you should see this

   ![ip address](image.png)    

- Take note of the LAN IP address : 192.168.1.1/24
- On the Win system go to your browser
- Enter the IP address in the url bar
- This warning should come up
  
![pfsense-config-browser-warning](pfsense-config-browser-warning.png)

- Click ```Advance``` 
- Click on ```continue to 192.168.1.1```
- which bring you to the login page

![(pfsense-config-browser-login](pfsense-config-browser-login.png)

- The username : admin
- The password : pfsense

Welcome to the Pfsense dashbaord
![alt text](pfsense-config-wizard.png)
 
like the screenshot says the ```wizard provides guidance through the initial configuration of pfsense```, so

- click ```Next```

![alt text](pfsense-config-wizard-pt2.png)

- click ```Next```

### General information section
 - leave the hostname as the default
   - if you have something custom you can enter it eg ```threatspherecon```
- leave the Domain-name as the default
   - if you have something custom you can also enter it eg NW.firewall.

![alt text](pfsense-config-wizard-pt3.png)

- leave the Primary and Secondary DNS as is (Blank), can be configure later if needed.

![alt text](pfsense-config-wizard-pt3(DNs).png) 
- Click ```next```

### Time Server section
![alt text](pfsense-config-wizard-time.png) 
- Click ```next```

### Configure WAN interface
  
  The WAN aka Wide area network is responsible for recieving internet from the ISP (Internet Sevice provider).

 ![alt text](pfsense-config-wizard-pt4-WAN.png)

- leave the configuration Type as "DHCP"
   - This should be only set to static if you and your ISP has agreed upon a specific IP that will be used to deliver internet to your Enterprise

- Leave all other as is 

- Check Both options in the RFC section

![alt text](pfsense-config-wizard-pt4-WAN-pt2.png)

- Click Next
 
### Configure LAN interface
 This section is where device would be connected and be able to recieve internet connection.

![alt text](pfsense-config-wizard-pt4-LAN.png)

- leave as is 

- click Next

### Setting A New Admin Password

![alt text](pfsense-config-wizard-password.png)

- set a new admin password
   - This is important even in a homelab like this as default password also leads to breaches in actual enterprise enviroment, practice make perfect.

- Click Next

###  Reload to save configuration

![alt text](pfsense-config-wizard-reload.png)


- Click Reload 

### Wizard Complete

![alt text](pfsense-config-completion.png)

- click Finish

### Dashboard

![alt text](pfsense-Dashboard.png)

#### PFsense Configuration Completed
   Congrats, with this the Firewall is up and running but more configuration is needed for the best security, configs like

   - Vlan Segmentation
   - Captive Portal
   - Bandwith control
   - firewall rules
   - Content-filtering 
   - and more ....


