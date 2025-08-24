# 📘 Understanding IP Addressing and Subnetting

- This document explains the concepts of IP addresses, subnet masks, subnetting, and key networking components in a clear and practical way.

----

## ✅ What is an IP Address?

- An IP address is a unique number assigned to each device on a network to identify it and allow communication. There are two main versions:

- IPv4: 32-bit address, represented in four octets (e.g., 192.168.1.1).

- Maximum addresses: 2^32 = 4,294,967,296 (about 4.3 billion).

- IPv6: 128-bit address, designed to overcome the limitations of IPv4 by providing an almost unlimited number of addresses.

 - Why IPv6?

- IPv4 addresses are limited and cannot provide unique addresses for every device in the world. IPv6 offers a much larger address space.

 - Private vs. Public IP

- Public IP: The address assigned to your network by your Internet Service Provider (ISP). It is globally unique and used on the internet.

- Private IP: Used inside local networks. These addresses are not routable on the internet and are reserved for internal communication.

- Common private IP ranges:

- 10.0.0.0 – 10.255.255.255

- 172.16.0.0 – 172.31.255.255

- 192.168.0.0 – 192.168.255.255

- Why do we need them?
- If every device required a unique public IP, we would run out of IPv4 addresses quickly. Instead, each network uses private IPs internally, and a single public IP is shared for internet access using NAT.

----

## ✅ What is a Subnet Mask?

A subnet mask is a 32-bit number that splits an IP address into two parts:

Network part: Identifies the network.

Host part: Identifies devices within that network.

- Example:
``` IP Address:  192.168.1.10
Subnet Mask: 255.255.255.128
Binary:      11111111.11111111.11111111.10000000
```

 - Here:

- 1s represent the network bits.

- 0s represent the host bits.

- How to calculate the number of IP addresses?

- Count the number of 0 bits in the subnet mask.
- Formula:
```
Subnet Mask: 255.255.255.128 → /25
Network bits: 25 (1's)
Host bits: 7 (0's)

2^7 = 128 total addresses
1 for Network ID (all zeros)
1 for Broadcast (all ones)
126 usable IPs
```

## ✅ Why Subnetting?

Subnetting allows splitting a large network into smaller networks for:

Better organization.

Improved security.

Reduced broadcast traffic.

## ✅ Key Networking Components
### Router

- A router is a networking device that connects different networks, such as your local network (LAN) to the internet (WAN).

- It routes data between networks based on IP addresses.

- It typically includes:

- DHCP (to assign IP addresses automatically).

- NAT (to share a single public IP among multiple devices).

- Firewall (to filter and protect data traffic).

### Switch

- A switch connects multiple devices within the same local network (LAN).

- Works at Layer 2 (Data Link Layer) of the OSI model.

- Forwards data based on MAC addresses.

- Unlike a hub, a switch sends data only to the intended device, improving efficiency.

### DHCP (Dynamic Host Configuration Protocol)

- DHCP automatically assigns IP addresses and network configurations (subnet mask, gateway, DNS) to devices when they join a network.

- Prevents IP conflicts.

- Eliminates manual configuration.

- Example: When you connect your phone to Wi-Fi, DHCP gives it an IP like 192.168.1.5.

### NAT (Network Address Translation)

- NAT translates private IP addresses into a public IP address when devices access the internet.

- Allows multiple devices to share one public IP.

- Keeps track of requests to send responses back to the correct device.

### DNS (Domain Name System)

- DNS converts human-readable domain names into IP addresses.

- Example: www.google.com → 142.250.183.14.

- Without DNS, you would need to remember IP addresses for websites.

### Firewall

- A firewall is a security system that monitors and filters incoming and outgoing traffic.

- Can be hardware-based (in routers) or software-based (on computers/servers).

- Blocks unauthorized access while allowing legitimate communication.

- Uses rules and policies to permit or deny traffic.
