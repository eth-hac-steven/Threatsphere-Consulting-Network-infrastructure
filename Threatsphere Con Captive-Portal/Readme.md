# Threatsphere Captive Portal Setup

A Captive portal is an important part of Network access control in an Enterprise environment. Users connecting to the network need to authorize with credentials like username and password or vouchers.

---
### Prerequisites  

- pfSense installed
- pfSense VLAN created

### Set-up 

- Login to your pfSense dashboard
- Click on the menu 
- Click on ```Service```
- Click on ```Captive Portal```

![pfSense Services menu with Captive Portal option highlighted](./images/THcon-Captive-portal-config-pt1.png)

- Click on Add 

![Captive Portal zones list with Add button](./images/THcon-Captive-portal-config-pt2.png)

- Enter a Zone name eg Human_Res
- Enter a Zone Description eg Zone for Human-Res staff
- Click ```Save and Continue```

![Captive Portal zone creation form with name and description fields](./images/THcon-Captive-portal-config-pt3(zozne-name).png) 

- Check "Enable Captive Portal"
- In Interface, select "HumanRes"

PS
- Also do this for the LAN interface you are currently connected to.

pfSense has done a good job in telling us what each feature does. Remember that Enterprise environments differ, so what you are doing should suit yours.

![Captive Portal settings with Enable option and HumanRes interface selected](./images/THcon-Captive-portal-config-pt3-enabing-interface.png)

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

![Captive Portal zones overview showing all configured zones](./images/THcon-Captive-portal-Zones.png)

### Creating User Accounts for the Different Segments

- Click on the menu
- Click on System
- Click on User Manager

![System menu with User Manager option selected](./images/THcon-Captive-portal-user-config.png)

First we create groups 

- Click on ```Groups```
   - Groups simply help to apply configs to all user added to this group instead of doing it one by one
- Click on ```Add```

![User Manager interface showing Groups tab with Add button](./images/THcon-Captive-portal-user-config-pt2.png) 

- Enter a Group Name
- Enter a Description

![Group creation form with name and description fields](./images/THcon-Captive-portal-user-config-pt3.png) 


- In the assigned privilegedes section
- click on Add
  - this is important, without this the user accounts created would be denied access and or rejected
- select User-Service : Captive Portal

![Assiginng privilegedes to the different groups](THcon-Captive-portal-Group-privilegdes.png)

- click on Save

- Do this for all others

![Multiple user groups displayed in the Groups list](./images/THcon-Captive-portal-user-config-pt4.png) 

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

![User account creation form with username, password, and full name fields](./images/THcon-Captive-portal-user-account-creation.png)


Make sure to add the user as a member of the right groups

- By selecting it and clicking on "Move to Members List"

![User group assignment interface showing available and member groups](./images/THcon-Captive-portal-user-account-creation-pt2.png)

- And repeat for the other users

![User account list showing all created user accounts with their assigned groups](./images/THcon-Captive-portal-user-account-display.png)

With all that done you should see this appear in  your browser  

![PFsense defualt Captive-portal page](./images/captive-portal-page.png)

### Confirmation

 Now lets Test the user account created, using anyone of the authenticatin methods 

 #### Before login

![Captive-portal-before-login](./images/THcon-Captive-portal-before-login.png)

 #### After login

![Captive-portal-after-login](./images/THcon-Captive-portal-after-login.png)

you see the logout pop up windows

 #### Captive portal  Access logs

 - Click on the menu 
 - click on status 
 - click on captive portal 
 - selct the zone
 - you see who is logged in 


![success-login](./images/success-login.png)  




