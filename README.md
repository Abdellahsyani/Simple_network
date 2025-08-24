# 📘 Understanding IP Addressing and Subnetting

- This document explains the concepts of IP addresses, subnet masks, subnetting, and key networking components in a clear and practical way.

----

## ✅ What is an IP Address?

An IP address is a unique number assigned to each device on a network to identify it and allow communication. There are two main versions:

- IPv4: 32-bit address, represented in four octets (e.g., 192.168.1.1).

    - Maximum addresses: 2^32 = 4,294,967,296 (about 4.3 billion).

- IPv6: 128-bit address, designed to overcome the limitations of IPv4 by providing an almost unlimited number of addresses.

### Why IPv6?

- IPv4 addresses are limited and cannot provide unique addresses for every device in the world. IPv6 offers a much larger address space.

- Private vs. Public IP

    - Public IP: The address assigned to your network by your Internet Service Provider (ISP). It is globally unique and used on the internet.

    - Private IP: Used inside local networks. These addresses are not routable on the internet and are reserved for internal communication.

- Common private IP ranges:

    - ```10.0.0.0 – 10.255.255.255```

    - ```172.16.0.0 – 172.31.255.255```

    - ```192.168.0.0 – 192.168.255.255```

- Why do we need them?
If every device required a unique public IP, we would run out of IPv4 addresses quickly. Instead, each network uses private IPs internally, and a single public IP is shared for internet access using NAT.

----

## ✅ What is a Subnet Mask?

A subnet mask is a 32-bit number that splits an IP address into two parts:
    - Network part: Identifies the network.
    - Host part: Identifies devices within that network.

- Example:
``` IP Address:  192.168.1.10
Subnet Mask: 255.255.255.128
Binary:      11111111.11111111.11111111.10000000
```

 Here:
    - 1s represent the network bits.
    - 0s represent the host bits.

- #### How to calculate the number of IP addresses?
Count the number of 0 bits in the subnet mask.
Formula:
```Number of addresses = 2^number_of_zeros```

Example:
```
Subnet Mask: 255.255.255.128 → /25
Network bits: 25 (1's)
Host bits: 7 (0's)

2^7 = 128 total addresses
1 for Network ID (all zeros)
1 for Broadcast (all ones)
126 usable IPs
```
----
## ✅ Why Subnetting?

Subnetting allows splitting a large network into smaller networks for:

    - Better organization.

    - Improved security.

    - Reduced broadcast traffic.

----
## ✅ Key Networking Components
--
### Router

- A router is a networking device that connects different networks, such as your local network (LAN) to the internet (WAN).

- It routes data between networks based on IP addresses.

- It typically includes:

    - DHCP (to assign IP addresses automatically).

    - NAT (to share a single public IP among multiple devices).

    - Firewall (to filter and protect data traffic).

--
### Switch

A switch connects multiple devices within the same local network (LAN).

- Works at Layer 2 (Data Link Layer) of the OSI model.

- Forwards data based on MAC addresses.

- Unlike a hub, a switch sends data only to the intended device, improving efficiency.

--
### DHCP (Dynamic Host Configuration Protocol)

DHCP automatically assigns IP addresses and network configurations (subnet mask, gateway, DNS) to devices when they join a network.

- Prevents IP conflicts.

- Eliminates manual configuration.

Example: When you connect your phone to Wi-Fi, DHCP gives it an IP like ```192.168.1.5```.

--
### NAT (Network Address Translation)

NAT translates private IP addresses into a public IP address when devices access the internet.

- Allows multiple devices to share one public IP.

- Keeps track of requests to send responses back to the correct device.

--
### DNS (Domain Name System)

DNS converts human-readable domain names into IP addresses.

- Example: ```www.google.com → 142.250.183.14```.

- Without DNS, you would need to remember IP addresses for websites.

--
### Firewall

A firewall is a security system that monitors and filters incoming and outgoing traffic.

- Can be hardware-based (in routers) or software-based (on computers/servers).

- Blocks unauthorized access while allowing legitimate communication.

- Uses rules and policies to permit or deny traffic.

----
## ✅ OSI Model (Open Systems Interconnection)

The OSI model is a conceptual framework that describes how data moves across a network in 7 layers. Each layer has its own role:

| Layer | Name         | Function                                              |
|-------|-------------|-------------------------------------------------------|
| 7     | **Application** | Interfaces with user applications (e.g., web browsers, email) |
| 6     | **Presentation**| Translates data formats (encryption, compression)  |
| 5     | **Session**      | Manages sessions between devices                   |
| 4     | **Transport**    | Ensures reliable data delivery (TCP/UDP)          |
| 3     | **Network**      | Handles logical addressing (IP addresses) and routing |
| 2     | **Data Link**    | Manages MAC addresses and frames within a LAN      |
| 1     | **Physical**     | Deals with cables, signals, and hardware transmission |


 - How it relates to our components:
    - Router works at Layer 3 (Network).
    - Switch works at Layer 2 (Data Link).
    - Firewall operates at multiple layers (mainly 3, 4, and sometimes 7).
    - DNS is an Application Layer (Layer 7) service.
    - DHCP also works at the Application Layer (Layer 7).

## Image
[An example of the work fllow](/home/abdellah/Pictures/Screenshots/image.png)
