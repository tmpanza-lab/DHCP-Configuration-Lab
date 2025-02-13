# Cisco – DHCP Configuration Lab

## Objective

In this lab I will perform a DHCP configuration for a small campus network.
I will configure a router outside interface as a DHCP client. I will then set up DHCP services, using a Cisco router first and then an external DHCP server. The external DHCP server is inside the campus LAN but outside the router.

### Skills Learned

- Understanding DHCP Client Configuration.
- Setting Up DHCP Services on a Router.
- Integrating an External DHCP Server.
- Differentiating Between Router-Based and External DHCP Services.
- Troubleshooting DHCP Configurations.


### Tools Used

- Cisco IOS Vendor-specific CLI.
- Layer 2 or Layer 3 Switches (Physical or Virtual).
- FortiOS Command Line Interface (CLI)
- Routers (Physical or Virtual).
- GNS3 for simulated network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*
 ![image](https://github.com/user-attachments/assets/11126687-6829-4a32-a220-9b902759fc60)


## Steps

## Cisco DHCP Client

1.	You have not acquired a static public IP address from the Internet service provider. Configure the outside interface FastEthernet 0/0 on R1 to receive its IP address using DHCP. The Service Provider is already configured and you have no access to it.

![image](https://github.com/user-attachments/assets/c11eeb79-8c89-434c-911c-5ac865042619)
 

2.	Verify that R1 received its public IP address via DHCP (you may need to wait a few minutes for the address to be assigned).

![image](https://github.com/user-attachments/assets/75ac4037-3aac-4d3e-afac-d03ac6e22520)
 

3.	What is the IP address of R1’s DHCP server?

The DHCP server is at 203.0.113.1. We can get this information by viewing the DHCP lease information.

![image](https://github.com/user-attachments/assets/e99b4184-4afa-444e-b2af-9d5afa47e081)
 


## Cisco DHCP Server

4.	Enable the DHCP service on R1 so it gives out IP addresses to the PCs in the 10.10.10.0/24 subnet.Leave IP addresses 10.10.10.1 – 10 free to be assigned to servers and printers. 10.10.20.10 is the DNS server.

![image](https://github.com/user-attachments/assets/40409017-ab8e-4116-8f4e-2033d4d1544c)
 

5.	Verify the clients received their IP information via DHCP.

![image](https://github.com/user-attachments/assets/7dae9dcd-8c03-42f8-8b77-1c726693abb4)
 
## Windows 10 Client
![image](https://github.com/user-attachments/assets/b87880db-80cd-439a-a35e-0a4ee6c95096)
 

6.	Verify the clients can ping the DNS server by its hostname ‘DNSserver’ (it might take some time for DNS to resolve the hostname).

![image](https://github.com/user-attachments/assets/84b61a20-e37d-4c56-bbdb-02f77913a47c)


7.On R1, verify both clients received an IP address via DHCP.

![image](https://github.com/user-attachments/assets/d3abadf3-8a76-49f2-b59e-6a6ec94995a6)
 

8.	Cleanup – remove the DHCP server configuration on R1. You will use an external DHCP server instead in the next section.

![image](https://github.com/user-attachments/assets/c1e73a50-7e7d-41d8-8f6c-f5ba35d9ba4b)


9.	Enter the command ‘ipconfig /release’ on the PCs to release their IP addresses.

![image](https://github.com/user-attachments/assets/c095ff3b-307e-4a72-b625-ccf1782df8cf)
 


10.	Enter the command ‘ipconfig /renew’ on the PCs and verify they can no longer obtain an IP address via DHCP.

![image](https://github.com/user-attachments/assets/73ec03ed-b4e3-4a2a-9612-089fd05a7b0d)
![image](https://github.com/user-attachments/assets/4d49bc42-87b3-4a60-81c6-8274366c0b08)
 

## External DHCP Server

11.	The server at * 10.10.20.10 has been configured as a DHCP server with a scope of IP addresses for the * 10.10.10.0/24 subnet, but the PCs there are not receiving IP addresses. Why is this?

* DHCP requests use broadcast traffic. R1 is not forwarding the requests on to the DHCP server as routers do not forward broadcast traffic by default.

![image](https://github.com/user-attachments/assets/cf8f95f8-7f53-464a-a9eb-de0779a4af0b)
 


12.	Configure the network to allow the PCs to receive their IP addresses from the DHCP server.

![image](https://github.com/user-attachments/assets/49fcbc05-9584-4b40-90b4-79acbac674f2)
 

14.	Verify the clients received their IP information via DHCP.

![image](https://github.com/user-attachments/assets/2984c66e-6da6-41c1-96f4-44b46eebdb5d)
![image](https://github.com/user-attachments/assets/a1e83bca-f880-4308-ae8e-a54f7e198e9c)
![image](https://github.com/user-attachments/assets/03ee894d-12d6-4771-a795-db4304e7a20a)

 
 
 
