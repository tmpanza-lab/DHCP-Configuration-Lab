# DHCP Configuration – Lab 

## Objective

The objective of this lab exercise is to familiarize yourself with the configuration and management of Dynamic Host Configuration Protocol (DHCP) in a small campus network environment. In this lab you will perform a DHCP configuration for a small campus network. You will configure a Router’s outside interface as a DHCP client. You will then set up DCHP services, using a Cisco router first and then an external DHCP server. The external DHCP server is inside the campus LAN but outside the router.

### Skills Learned

- Understanding DHCP Client Configuration.
- Setting Up DHCP Services on a Router.
- Integrating an External DHCP Server.
- Differentiating Between Router-Based and External DHCP Services.
- Troubleshooting DHCP Configurations.

### Tools Used

- Cisco IOS Vendor-specific CLI.
- Layer 2 or Layer 3 Switches (Physical or Virtual).
- Routers (Physical or Virtual).
- GNS3: For simulating network devices and configurations.
- Cisco Packet Tracer: Simplified tool for learning and configuring VLANs.
- PuTTY (Terminal Emulator Software).


## Steps

Note that the external DHCP server at 10.10.20.10 will not be used until the last
part of the lab.

## Lab Topology
![image](https://github.com/user-attachments/assets/50aa8524-198c-400b-8db2-7c2806d41189)

## DHCP Client

1) You have not acquired a static public IP address from the Internet service provider. Configure the outside interface FastEthernet 0/0 on R1 to
receive its IP address using DHCP. The Service Provider is already configured and you have no access to it.
![image](https://github.com/user-attachments/assets/2ebb44e0-3ab6-48bf-b8a6-9afd852e771a)

2) Verify that R1 received its public IP address via DHCP (you may need to wait a few minutes for the address to be assigned).
![image](https://github.com/user-attachments/assets/48e500a7-ae0e-4d0d-84bd-37ba61906e31)

3) What is the IP address of R1’s DHCP server?

The DHCP server is at 203.0.113.1. We can get this information by viewing the DHCP lease information.
![image](https://github.com/user-attachments/assets/2ee59fe1-6189-41d1-b84c-e12faaf4c93a)


## Cisco DHCP Server

4) Enable the DHCP service on R1 so it gives out IP addresses to the PCs in the 10.10.10.0/24 subnet. Leave IP addresses 10.10.10.1 – 10 free to be assigned to servers and printers. 10.10.20.10 is the DNS server.
![image](https://github.com/user-attachments/assets/d6b9b2e6-b4e7-4415-8d82-2743f69be2a3)

5) Verify the clients received their IP information via DHCP.
![image](https://github.com/user-attachments/assets/b308b446-b6d4-48cf-ab57-3c7638aea795)


6) Verify the clients can ping the DNS server by its hostname ‘DNSserver’ (it might take some time for DNS to resolve the hostname).
![image](https://github.com/user-attachments/assets/221b6860-d322-4c2a-acac-5a49fe25d658)

7) On R1, verify both clients received an IP address via DHCP.
![image](https://github.com/user-attachments/assets/35317761-ba1d-45ce-88c9-609c79197baf)

8) Cleanup – remove the DHCP server configuration on R1. You will use an external DHCP server instead in the next section.
![image](https://github.com/user-attachments/assets/4d6183bc-a4dc-469c-ac8e-f9862ba19b21)


9) Enter the command ‘ipconfig /release’ on the PCs to release their IP addresses.
![image](https://github.com/user-attachments/assets/796457cb-7d0e-4ad5-991c-170c115302c2)

10) Enter the command ‘ipconfig /renew’ on the PCs and verify they can no longer obtain an IP address via DHCP
![image](https://github.com/user-attachments/assets/b4ac7e9f-51d7-430e-9361-85dc03a7d7ee)


## External DHCP Server

11) The server at 10.10.20.10 has been configured as a DHCP server with a scope of IP addresses for the 10.10.10.0/24 subnet, but the PCs there are not receiving IP addresses. Why is this?

## DHCP requests use broadcast traffic. R1 is not forwarding the requests on to the DHCP Server as reouters do not forward broadcast traffic by default.

12) Configure the network to allow the PCs to receive their IP addresses from the DHCP server.

On the interface where they are received, configure the router to forward DHCP requests to the server.
![image](https://github.com/user-attachments/assets/9d6938d9-2ff7-4969-b608-0f66c8cb601a)

14) Verify the clients received their IP information via DHCP
15) ![image](https://github.com/user-attachments/assets/1be859fa-22ac-442a-93a4-f61c93fcedda)

