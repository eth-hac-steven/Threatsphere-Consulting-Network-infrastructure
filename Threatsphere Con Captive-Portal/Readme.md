# Threatsphere Captive Portal Setup

A Captive portal is an important part of Network access control in an Enterprise enviroment. User connecting to the network need authorize credentials like username and password or vouvhers. With the captive portal system admin can control the who and what a user does on the network and also ensure accounting.

---
### Prerequisites  

- Pfsense installed
- PFsense VLan-created

### Set-up 

- login to your pfsense Dashboard
- Click on the menu 
- click on ```Service```
- click on ```Captive portal```

![alt text](THcon-Captive-portal-config-pt1.png)

- Click on add 

![alt text](THcon-Captive-portal-config-pt2.png)

- Enter a Zone name eg Human_Res
- Enter a Zone Description eg Zone for Human-Res staff
- click ```save and continue```

![alt text](THcon-Captive-portal-config-pt3(zozne-name).png) 

- check "Enable captive portal"
- In interface , select "HumanRes"

Pfsense has done a good job in telling us waht each feature does, remember Enterprise enviroment differ so what you are doing should suite yours.

![alt text](THcon-Captive-portal-config-pt3-enabing-interface.png)

- set idle timeout : 30 
- Check "logout pop-up window"
- After authentication url : https://www.google.com
- Check "Preserve User Database"
- leave Concurrent conncetin as is
- Check "Enable  Per-user Bandwith restriction"
- Set Default Download : 1024kbit/s  aka 1mbps
- Set Default upload : 1024kbit/s  aka 1mbps
- Leave the Authentication Method as is 
- select "local database" for Authentication Server
- select "local database" for Secondary Authentication Server
- click on save
- Repeat for all the VLAN segment

![alt text](THcon-Captive-portal-Zones.png)

 ### Creating User account for the different segments

- click on the menu
- click on system
- click on User Manager

![alt text](THcon-Captive-portal-user-config.png)

First we create groups 

- Click on  ``Groups``
- click on  ``Add``

![alt text](THcon-Captive-portal-user-config-pt2.png) 

- Enter a Group-name
- Enter a Description

![alt text](THcon-Captive-portal-user-config-pt3.png) 

- Do this for all others

![alt text](THcon-Captive-portal-user-config-pt4.png) 

 Now lets create User account for user in our Enterprise
- Victoria Dane - Accounting
- Doris Madison - Human-Res
- Tolu Anderson - Underwriter

### 

- Click on user
- Click on add
- Enter username
- Enter passwords
- Enter Fullname

![alt text](THcon-Captive-portal-user-account-creation.png)


make sure add the user to be members of the right groups

- By selecting it and clicking on "Move to members list"

![alt text](THcon-Captive-portal-user-account-creation-pt2.png)

- And repeat for the other users

![alt text](THcon-Captive-portal-user-account-display.png)