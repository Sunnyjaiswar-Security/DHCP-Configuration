# DHCP-Configuration

# Objective
* To configure DHCP (Dynamic Host Configuration Protocol) in Cisco Packet Tracer.
*  To automatically assign IP addresses to client PCs from a DHCP server or router.
*  To reduce manual IP configuration and avoid IP address conflicts.
*  To verify that all client devices receive valid network settings through DHCP.

# Requirements 
*  Cisco Packet Tracer software
*  1 PT Router 
*  1 PT Switch 
*  2 or more PCs (clients)
*  Copper Straight-Through Ethernet cables
*  Configured IP network (network address and subnet mask)
*  DHCP service enabled on the router or DHCP server

  ## Step 1: Connect the Devices
Connect all devices using Copper Straight-Through cables.
*  PT-Router Fa0/0 → PT-Switch Fa0/1
*  PC0 FastEthernet0 → PT-Switch Fa0/2
*  PC1 FastEthernet0 → PT-Switch Fa0/3
After connecting the devices, verify that all links turn green, indicating successful physical connectivity.


 <img width="941" height="500" alt="Screenshot 2026-10-12 193517" src="https://github.com/user-attachments/assets/4f9ebe58-c4a2-4641-9d97-8efa5f74ccfd" />


## Step 2: Open the PT-Router
1.	Click on the PT-Router in the Cisco Packet Tracer workspace.
2.	Open the CLI (Command Line Interface) tab.
3.	Press Enter to access the router command prompt.
4.	The router is now ready for DHCP configuration commands.
 
<img width="1125" height="601" alt="image" src="https://github.com/user-attachments/assets/4ceb7d20-92bb-4ab1-90ed-9ae819b696f6" />


<img width="1351" height="722" alt="Screenshot 2026-10-12 194607" src="https://github.com/user-attachments/assets/e85afe02-af28-42d7-90c9-f89972624fd8" />


## Step 3: Enter Configuration Mode
Open the router CLI and enter privileged mode, then enter global configuration mode.
Commands:
- Router> en
- Router# config t
- Router(config)#
### Example:
- Router> en
- Router# config t
- Enter configuration commands, one per line. End with CNTL/Z.
- Router(config)#
- After entering global configuration mode, the router is ready for DHCP configuration.
  
<img width="1352" height="200" alt="Screenshot 2026-10-12 195047" src="https://github.com/user-attachments/assets/dc09ede1-89f6-44f3-b725-f2a07b3cb81a" /> 

## Step 4: Configure the Router Interface
Configure the FastEthernet0/0 interface and assign an IP address.

Command:
- Router(config)# int fa0/0
- Router(config-if)# ip add 192.168.1.1 255.255.255.0
- Router(config-if)# no shutdown
- Router(config-if)# exit
### Example:
- Router(config)# int fa0/0
- Router(config-if)# ip address 192.168.1.1 255.255.255.0
- Router(config-if)# no shutdown

### %LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up

- Router(config-if)# exit
- Router(config)#
- This step assigns the IP address 192.168.1.1/24 to the router interface and enables the interface.

  <img width="1325" height="318" alt="Screenshot 2026-10-12 195108" src="https://github.com/user-attachments/assets/bfe1ee4c-301d-4aa6-b7df-e687eb500e88" />


## Step 5: Activate the Router Interface
After assigning the IP address, enable the FastEthernet0/0 interface using the no shutdown command.

Command:
- Router(config-if)# no shutdown
### Example:
- Router(config-if)# no shutdown

### %LINK-5-CHANGED: Interface FastEthernet0/0, changed state to up
%LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up
- The FastEthernet0/0 interface becomes active (up), and the connection between the PT-Router and PT-Switch is successfully established.
  
<img width="1355" height="717" alt="Screenshot 2026-10-12 195224" src="https://github.com/user-attachments/assets/0ca90f9f-b484-4350-ba73-fa46ad36a508" />
 

## Step 6: Create a DHCP Pool
Create a DHCP pool named sunnypool.

Commands:
- Router(config)# ip dhcp pool sunnypool
- Router(dhcp-config)# network 192.168.1.0 255.255.255.0
- Router(dhcp-config)# default-router 192.168.1.1
- Router(dhcp-config)# exit
### Example:
- Router(config)# ip dhcp pool sunnypool
- Router(dhcp-config)# network 192.168.1.0 255.255.255.0
- Router(dhcp-config)# default-router 192.168.1.1
- Router(dhcp-config)# exit
- Router(config)#
- This DHCP pool will automatically assign IP addresses to client PCs.


 <img width="1353" height="247" alt="Screenshot 2026-10-12 195308" src="https://github.com/user-attachments/assets/5d90233c-cdb4-4657-a950-967abec78feb" />

## Step 7: Configure PC0 Using DHCP
After configuring DHCP on the router, configure PC0 to obtain an IP address automatically.
1. Click on PC0.
2.	Open the Desktop tab.
3.	Click IP Configuration.
4.	Select DHCP.
## Example:
DHCP request successful.

- IPv4 Address:      192.168.1.2
- Subnet Mask:       255.255.255.0
- Default Gateway:   192.168.1.1
- DNS Server:        0.0.0.0
- The DHCP request is successful, and PC0 automatically receives the IP address 192.168.1.2 from the router DHCP pool.

 <img width="1352" height="717" alt="Screenshot 2026-10-12 195350" src="https://github.com/user-attachments/assets/9a8763d1-01d4-4cf7-84a9-0b7bf5458b06" />


<img width="1353" height="716" alt="Screenshot 2026-10-12 195451" src="https://github.com/user-attachments/assets/91c3e5a1-8754-4973-bd48-fd5dac5f406c" />

## Step 8: Configure PC1 Using DHCP
After configuring DHCP on the router, configure PC1 to obtain an IP address automatically.
1.	Click on PC1.
2.	Open the Desktop tab.
3.	Click IP Configuration.
4.	Select DHCP.
## Example:
DHCP request successful.

- IPv4 Address:      192.168.1.3
- Subnet Mask:       255.255.255.0
- Default Gateway:   192.168.1.1
- DNS Server:        0.0.0.0
- The DHCP request is successful, and PC1 automatically receives the IP address 192.168.1.3 from the router DHCP pool.

  <img width="1353" height="716" alt="Screenshot 2026-10-12 195515" src="https://github.com/user-attachments/assets/c0e303ac-87b9-4e27-bcdd-917a9775ed68" />


<img width="1351" height="717" alt="Screenshot 2026-10-12 195535" src="https://github.com/user-attachments/assets/95856bdc-3b11-4e6e-9348-cf193e933712" />

 

## Step 9: Verify Network Connectivity of the New PC (PC2)
After adding a new PC2 to the network, check whether it is receiving an IP address from the DHCP server.
1.	Click on PC2.
2.	Open Desktop → IP Configuration.
3.	Select DHCP.
## Example:
DHCP request successful.

- IPv4 Address:      192.168.1.4
- Subnet Mask:       255.255.255.0
- Default Gateway:   192.168.1.1
- DNS Server:        0.0.0.0
- The message DHCP request successful confirms that the new PC2 is properly connected to the network and the DHCP configuration is working correctly.

 <img width="1352" height="715" alt="Screenshot 2026-10-12 195555" src="https://github.com/user-attachments/assets/85c3bff5-9d75-4ecc-ba06-2cf5c08e2974" />

<img width="1352" height="716" alt="Screenshot 2026-10-12 195630" src="https://github.com/user-attachments/assets/c96a027d-d56c-4f55-ba4b-43e8a2532c62" />

 
<img width="1352" height="716" alt="Screenshot 2026-10-12 195655" src="https://github.com/user-attachments/assets/f13e8f12-be90-442c-b001-664919b124a3" />

 

## Result
The DHCP configuration was successfully implemented in Cisco Packet Tracer using a PT-Router, PT-Switch, and PC-PT devices. All connected PCs (PC0, PC1, and PC2) automatically received IP addresses from the router DHCP pool. The network connectivity was successfully verified.
## Conclusion
The DHCP server was successfully configured on the PT-Router in Cisco Packet Tracer. All client devices obtained IP addresses automatically, confirming that the DHCP configuration and network connectivity were working correctly. This project demonstrated how DHCP simplifies network configuration by automatically assigning IP addresses to client devices.






