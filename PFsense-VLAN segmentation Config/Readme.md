# pfSense VLAN Segmentation Configuration

## VLAN Segmentation

This is an important setup in an enterprise network because it helps to:
- Control access for end-user devices
- Contain breaches and stop lateral movement
- Protect critical devices such as servers and firewalls

Currently the pfSense instance in this lab is on a flat network: any host can open a browser, reach the firewall web UI and attempt to brute-force it. We will segment the network to reduce that risk.

## Prerequisites

- pfSense basic setup completed (see: [pfSense firewall config](https://github.com/eth-hac-steven/Threatsphere-Consulting-Network-infrastructure/tree/main/Threatsphere%20PFsense%20Firewall%20config))
- A Windows PC for testing (optional)

## VLAN Setup

### Defining scope
We will create these VLANs and DHCP pools:
- Human-Res: 192.168.10.10–192.168.10.210 (reserve .1–.9 for static devices like printers)
- Accounting: 192.168.20.10–192.168.20.210 (reserve .1–.9 for static devices)
- Underwriting: 192.168.30.10–192.168.30.210 (reserve .1–.9 for static devices)

### Configuring VLANs
1. Log in to the pfSense web UI.
2. Open the menu and go to `Interfaces` → `Assignments`.

![pfSense Interfaces - Assignments](images/vlan-config-1.png)

3. Click on `VLANs` then click `Add`.

![pfSense Add VLAN](images/vlan-config-2.png)

4. Set the parent interface (e.g. `LAN`), set the VLAN tag (e.g. `10`), add a meaningful description and save.

![pfSense VLAN settings example](images/vlan-config-3.png)

5. Repeat for every VLAN in the scope.

![pfSense VLAN list](images/vlan-config-4.png)

### Interface assignments
1. Go to `Interfaces` → `Assignments`.
2. Click `Add` to create a new interface for each VLAN you created.

![Interface assignment](images/vlan-config-5.png)

3. Assign each VLAN to an OPT interface and save.

![Assigned interfaces list](images/vlan-config-6.png)

### Enabling VLAN interfaces
1. Click the new OPT interface (e.g. `OPT1`).
2. Check **Enable interface**, set a name (e.g. `Human-Res`) and set IPv4 configuration to **Static IPv4**.

![Enable interface settings](images/vlan-config-7.png)

3. Set the interface IP address (example: `192.168.10.1`).

![Interface IPv4 address](images/vlan-config-8.png)

4. Save and Apply Changes. Repeat for other VLAN interfaces.

![Interfaces overview](images/vlan-config-9.png)

## Enabling DHCP server
1. Open the menu: `Services` → `DHCP Server`.

![DHCP Server main page](images/vlan-config-Dhcp-server.png)

2. If a dependency warning appears (ISC DHCP is deprecated), enable KEA DHCP: `System` → `Advanced` → `Networking` → check **KEA DHCP** and save.

![Enable KEA DHCP](images/vlan-config-Dhcp-server-isc-dep-pt2.png)

3. Return to `Services` → `DHCP Server`. Under **Settings** enable *Early DNS* and *DNS registration*, then save and Apply Settings.

![DHCP server settings](images/vlan-config-Dhcp-server-isc-dep-pt4.png)

4. Select the VLAN interface (e.g. `Human-Res`) and check **Enable DHCP server on Human-Res**.

![Enable DHCP on Human-Res](images/vlan-config-Dhcp-server-isc-dep-pt5.png)

5. Enter the DHCP pool range according to the scope, e.g. `192.168.10.10`–`192.168.10.210`.

![Human-Res DHCP range example](images/HUMANRES-iprnage.png)

6. Save and Apply Changes. Repeat for other VLANs.

## Static IP mappings
Use static mappings for devices like printers and scanners.
1. In `Services` → `DHCP Server`, click the VLAN interface and scroll to **Static Mappings for this interface**.

![Static mapping list](images/vlan-config-static-ip-1.png)

2. Add the device MAC address and choose an IP from the reserved pool (.1–.9) and save.

![Add static mapping example](images/vlan-config-static-ip-2.png)

---

If you'd like, I can also:
- Compress the images to reduce repo size and speed up page load (I can produce optimized versions and update the files),
- Rename image files to cleaner, lowercase names (and update README accordingly),
- Or create a small index or gallery for the images.

Tell me which of the image tasks you'd like me to perform next: compress (lossy/lossless), rename, or both. If you want compression, tell me the target max file size or quality level (e.g., 60% quality, or max 100 KB per image).