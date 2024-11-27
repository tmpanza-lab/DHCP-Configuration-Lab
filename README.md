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

# Load the Startup Configurations

Download the ‘23-1 DHCP Configuration.zip’ file here. Extract the project .pkt file
then open it in Packet Tracer. Do not try to open the project from directly inside
the zip file.Cisco 

## DHCP Client

1) You have not acquired a static public IP address from the Internet service
provider. Configure the outside interface FastEthernet 0/0 on R1 to
receive its IP address using DHCP. The Service Provider is already
configured and you have no access to it.
2) Verify that R1 received its public IP address via DHCP (you may need to
wait a few minutes for the address to be assigned).
3) What is the IP address of R1’s DHCP server?


## Cisco DHCP Server

4) Enable the DHCP service on R1 so it gives out IP addresses to the PCs in the 10.10.10.0/24 subnet. Leave IP addresses 10.10.10.1 – 10 free to be
assigned to servers and printers. 10.10.20.10 is the DNS server.
5) Verify the clients received their IP information via DHCP.
6) Verify the clients can ping the DNS server by its hostname ‘DNSserver’ (it might take some time for DNS to resolve the hostname).
7) On R1, verify both clients received an IP address via DHCP.
8) Cleanup – remove the DHCP server configuration on R1. You will use an external DHCP server instead in the next section.
9) Enter the command ‘ipconfig /release’ on the PCs to release their IP addresses.
10) Enter the command ‘ipconfig /renew’ on the PCs and verify they can no longer obtain an IP address via DHCP

## External DHCP Server

11) The server at 10.10.20.10 has been configured as a DHCP server with a scope of IP addresses for the 10.10.10.0/24 subnet, but the PCs there are not receiving IP addresses. Why is this?12) Configure the network to allow the PCs to receive their IP addresses from the DHCP server.
13) Verify the clients received their IP information via DHCP
