# Threatsphere Captive Portal Setup

A Captive portal is an important part of Network access control in an Enterprise environment. Users connecting to the network need to authorize with credentials like username and password or vouchers. With this setup, you can enforce security policies and control network access efficiently.

---
### Prerequisites  

- pfSense installed
- pfSense VLAN created

### Set-up 

- Login to your pfSense dashboard
- Click on the menu 
- Click on ```Service```
- Click on ```Captive Portal```

![alt text](/images/THcon-Captive-portal-config-pt1.png)

- Click on Add 

![alt text](/images/THcon-Captive-portal-config-pt2.png)

- Enter a Zone name eg Human_Res
- Enter a Zone Description eg Zone for Human-Res staff
- Click ```Save and Continue```

![alt text](/images/THcon-Captive-portal-config-pt3(zone-name).png) 

- Check "Enable Captive Portal"
- In Interface, select "HumanRes"

pfSense has done a good job in telling us what each feature does. Remember that Enterprise environments differ, so what you are doing should suit yours.

![alt text](/images/THcon-Captive-portal-config-pt3-enabling-interface.png)

- Set Idle Timeout: 30 
- Check "Logout Pop-up Window"
- After Authentication URL: https://www.google.com
- Check "Preserve User Database"
- Leave Concurrent Connection as is
- Check "Enable Per-user Bandwidth Restriction"
- Set Default Download: 1024kbit/s (aka 1mbps)
- Set Default Upload: 1024kbit/s (aka 1mbps)
- Leave the Authentication Method as is 
- Select "Local Database" for Authentication Server
- Select "Local Database" for Secondary Authentication Server
- Click on Save
- Repeat for all the VLAN segments

![alt text](/images/THcon-Captive-portal-Zones.png)

### Creating User Accounts for the Different Segments

- Click on the menu
- Click on System
- Click on User Manager

![alt text](/images/THcon-Captive-portal-user-config.png)

First we create groups 

- Click on ```Groups```
- Click on ```Add```

![alt text](/images/THcon-Captive-portal-user-config-pt2.png) 

- Enter a Group Name
- Enter a Description

![alt text](/images/THcon-Captive-portal-user-config-pt3.png) 

- Do this for all others

![alt text](/images/THcon-Captive-portal-user-config-pt4.png) 

Now let's create user accounts for users in our Enterprise:
- Victoria Dane - Accounting
- Doris Madison - Human-Res
- Tolu Anderson - Underwriter

### Creating User Accounts

- Click on User
- Click on Add
- Enter Username
- Enter Password
- Enter Full Name

![alt text](/images/THcon-Captive-portal-user-account-creation.png)


Make sure to add the user as a member of the right groups

- By selecting it and clicking on "Move to Members List"

![alt text](/images/THcon-Captive-portal-user-account-creation-pt2.png)

- And repeat for the other users

![alt text](/images/THcon-Captive-portal-user-account-display.png)
