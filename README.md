# ARP Traffic Analysis Using Wireshark on Ubuntu

## 1. Project Overview

This project demonstrates the practical analysis of the Address Resolution Protocol (ARP) using Wireshark on Ubuntu Linux.

The objective was to capture and examine ARP Requests and ARP Replies to understand how devices discover MAC addresses on a local network.

## 2. Objectives

- Understand the purpose of ARP.
- Capture ARP packets using Wireshark.
- Identify ARP Requests and ARP Replies.
- Examine sender and target IP and MAC addresses.
- Understand how a device learns another device's MAC address.

## 3. Tools and Environment

- Operating System: Ubuntu Linux
- Packet Analysis Tool: Wireshark
- Network Connection: Wi-Fi
- Network Interface: wlo1

## 4. Procedure

1. Identified the active network interface using the Linux `ip route` command.
2. Opened Wireshark and selected the wireless interface (`wlo1`).
3. Started a packet capture.
4. Applied the display filter `arp` to display ARP traffic only.
5. Identified ARP Requests and ARP Replies.
6. Examined the packet details to identify sender and target addresses.

## 5. Observations and Findings

A total of eight ARP packets were observed during the capture.

The packets followed this pattern:

- Packet 1: ARP Request
- Packet 2: ARP Reply
- Packet 3: ARP Request
- Packet 4: ARP Reply
- Packet 5: ARP Request
- Packet 6: ARP Reply
- Packet 7: ARP Request
- Packet 8: ARP Reply

The first request-and-reply pair was examined in detail.

### ARP Request

The default gateway requested the MAC address associated with the Ubuntu computer's IP address.

The target MAC address was `00:00:00:00:00:00`, indicating that the target MAC address was not yet known in the ARP request.

### ARP Reply

The Ubuntu computer responded with its MAC address.

The gateway could then associate the Ubuntu computer's IP address with its MAC address.

*Note: Actual network identifiers have been omitted from this public documentation for privacy.*

## 6. Key Learnings

- ARP maps IPv4 addresses to MAC addresses on a local network.
- ARP Requests are broadcast.
- ARP Replies are normally unicast.
- The device that owns the requested IP address provides its MAC address.
- Devices use ARP to discover the MAC address of their default gateway when communicating outside their local subnet.

## 7. Conclusion

This practical exercise provided hands-on experience with ARP packet capture and analysis using Wireshark on Ubuntu Linux.

It demonstrated how devices use ARP to discover MAC addresses and communicate across a local network.

The exercise also introduced practical packet inspection skills that form part of network troubleshooting and cybersecurity analysis.
## 8. Verification Using Ubuntu Network Commands

The packet observations were independently verified using Ubuntu terminal commands.

### Commands Used

- `ip route` - Identified the default gateway and active network interface.
- `ip neigh` - Displayed the IP-to-MAC address mapping in the neighbour table.
- `ip link show wlo1` - Displayed the MAC address of the wireless interface.

### Verification Results

The gateway MAC address observed in Wireshark matched the gateway entry in the Ubuntu neighbour table.

Similarly, the Ubuntu interface MAC address matched the sender MAC address observed in the ARP Reply.

This confirmed the consistency of the packet capture and the system's network information.
