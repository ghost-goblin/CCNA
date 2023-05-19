<div align='center'>

# 🛸 Cisco Certified Network Associate
## ☎️ Network Fundamentals
  
### 🏠 [HOME](README.md)
### ✏️ Download the study guide [here](https://learningcontent.cisco.com/documents/marketing/study-plans/2023_CCNAExam_StudyTool.pdf)


</div>


- - -

# OSI Open Systems Interconnect Model

| LAYER        | TCP/IP STACK                       | Devices  | Definition                                                                   |
|--------------|------------------------------------|----------|------------------------------------------------------------------------------|
| Application  | Application (Data)                 |          | Represents data users encodes and controls the dialog                        |
| Presentation |                                    |          |                                                                              |
| Session      |                                    |          |                                                                              |
| Transport    | Transport (Segment) TCP/UDP        |          | Supports communication between end devices across a diverse network          |
| Network      | Internet (Packet) IP Address       | Routers  | Provides logical addressing and determines the best path through the network |
| Data Link    | Network Access (Frame) MAC Address | Switches | Controls the hardware devices and media that make up a network               |
| Physical     |                                    | Hub      |                                                                              |

> P, D, N, T, S, P, A … Please Do Not Throw Sausage Pizza Away!

# The Upper OSI Layers

## 7. The Application Layer

- Provides network services to the applications of the user and does not provide services to any other OSI layer.
- Establishes the availability of intended communication partners.
- Synchronizes and establishes agreement on procedures for error recovery and control of data integrity.

## 6. The Presentation Layer

- Ensures that the information that is sent at the application layer of one system is readable by the application layer of another system.
- Translate among multiple data formats using a common format (e.g. computers with different encoding schemes).

## 5. The Session Layer

- Establishes, manages and terminates sessions between two communicating hosts.
- The session layer also synchronizes dialog between the presentation layers of the 2 hosts and manages their data exchange.
- Offers efficient data transfer, CoS (Class of Service) and exception reporting of upper layer problems.

# The Lower OSI Layers

## 4. The Transport Layer

1. TCP / UDP
2. Port Number
- Defines services to segment, transfer and reassemble for individual communications between the end devices.
- Breaks down large files into smaller segments that are less likely to incur transmission problems.

## 3. The Network Layer

- **Source** and **Destination IP Address**.
- Operates at Layer 3.
- Provides connectivity and path selection between 2 host systems that may be located on geographically separated networks,
- Manages connectivity of hosts by providing logical addressing.

## 2. The Data-Link Layer

- **Source** and **Destination MAC Address** (layer 2 address)
- How data is formatted for transmission and how to access to physical media is controlled.
- Includes error detection and correction to ensure reliable delivery of data.

## 1. The Physical Layer

- Enables bit transmission between end devices.
- Defines the specification needed for activating, maintaining and deactivating the physical link between end devices.
- Voltage levels, physical data rates, maximum transmission distances, physical connectors etc.

- - -

# Cisco Operating System

## Internetwork Operating System (IOS)

Cisco devices do not have a default IP address, so we need to set one up before we can connect to it over the network. We need a **console connection** to make the initial configurations including adding IP addresses.

## Console Cable *(DB9 to RJ45)*

### The newer cables USB to Mini-USB

> Use “Ctrl-A” to move back to move back to the start of the line

```
Cisco IOS CLI:=================================    ____ ____|    \(____|     `._____ ____|       _|___(____|     .'     |____/=================================Router> (The User Exec prompt)Router> ? (Ask for help :-\)Router> enable (Privileged Exec mode) /disable (to esc.)Router# show ?Router# show ip interface briefRouter# show running configRouter# show run int fast0/0Router# show run | begin hostname (case sensitive regular expression)Router# show run | include/exclude interfaceRouter# show run | section bgpRouter# configure terminal (Global Configuration)Router(config)# ?Router(config)# hostname Router1Router(config)# do show ip interface brief (Show cmd at global config mode)Router(config)# interface fastEthernet 0/0Router(config-if)# exit (takes you back to global config)Router(config-if)# end (takes you back to Privileged Exec mode)=================================
```

## Cisco IOS Configuration Management

```
Router# conf tRouter(config)# hostname Router1Router1(config)# do show startup-configRouter1(config)# do show running-configRouter1(config)# endRouter1# copy run startup-config (Privileged Exec mode)Router1# copy run flash:my-configRouter1# show flashRouter1# write erase startRouter1# copy flash:my-config startRouter1# copy run tftpRouter1# more flash:myconfig
```

## Configuration Storage Locations

- The IOS image is stored in flash
- The startup configuration is stored in NVRAM
- The running configuration is stored in RAM
- Running config is loaded into RAM from the startup config when the device boots up


# The Transport Layer Header, TCP & UDP

## Layer 4 - The Transport Layer

- Provides transparent layer of data between host and is resonsible for end-to-end *error recovery* and *flow control*

- Flow control is the process of adjusting data from the sender to ensure effective delivery. #### Session Multiplexing - The process by which a host is able to support multiple sessions simultaneously and manage the individual traffic streams over a single link. # TCP (Transport Control Protocol)


# The TCP Three-Way Handshake

```
   _______________                        |*\_/*|________  |  ___________  |                      ||_/-\_|______  |  | |           | |                      | |           | |  | |   0   0   | |        ---->         | |   0   0   | |  | |     -     | |        SYN           | |     -     | |  | |   \___/   | |        <---          | |   \___/   | |  | |___     ___| |        SYN ACK       | |___________| |  |_____|\_/|_____|        --->          |_______________|    _|__|/ \|_|_...........ACK............._|________|_   / ********** \                          / ********** \ /  ************  \                      /  ************  \--------------------                    --------------------$ tcp header --20 bytes 0                   1                   2                   3 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|       Source Port (16)        |    Destination Port (16)      |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|                    Sequence Number (32)                       |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|                Acknowledgment Number (32)                     |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+| Offset|  Res. |     Flags     |             Window            |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|            Checksum           |         Urgent Pointer        |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|                    Options                    |    Padding    |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

# UDP (User Datagram Protocol)



```
$ protocol udp --oddchar "-" --startchar "-" --endchar "-" 0                   1                   2                   3 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1-----------------------------------------------------------------|          Source Port          |        Destination Port       |-----------------------------------------------------------------|             Length            |            Checksum           |-----------------------------------------------------------------
```


# The Network Layer (Layer 3)

- Responsible for *routing packets* to their destination and for **Quality of Service**
- **Internet Protocol** is the most well known layer 3 protocol
- A connectionless protocol with no acknowledgements at layer 3
- Other layer 3 protocols include: **ICMP** (Internet Control Message Protocol / Ping) and **IPSec**
- Layer 2 uses MAC Addresses and the logical seperation between networks is done at layer 3 i.se. subnetting

```
1518 bytes MTU$ protocol ip --bits 16 0                   1 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|Version|  IHL  |Type of Service|+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|          Total Length         |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|         Identification        |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|Flags|     Fragment Offset     |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|  Time to Live |    Protocol   |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|        Header Checksum        |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|                               |+         Source Address        +|                               |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|                               |+      Destination Address      +|                               |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+|            Options            |+               +-+-+-+-+-+-+-+-+|               |    Padding    |+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

# Unicast, Broadcast and Multicast Traffic

# IPv4 Address

- 32-bits, 4 octets in dotted-descimal format, each octet is 8 bits long

```
ipconfig --ip address, subnet mask and default gateway --windowsifconfig --ip address and subnet mask                  --linuxip route --default gateway                             --linuxCISCO IOSRouter> enableRouter# show ip interface briefRouter# show interface
```

# Static vs. Automatic Addressing

- Dynamic Host Configuration Protocol (DHCP) assigns IP addresses automatically to client machines
- IP Addresses are usually set manually on servers, printers and network devices; routers and switches

# IPv4 Classes

## Class A

- IP Range: **1.0.0.0** to **126.0.0.0**
- First octet value range from 1 to 127
- Subnet Mask: 255.0.0.0 (8 bits)
- Number of Networks: 126
- Number of Hosts per Network: 16,777,214 ## Class B
- Range: **128.0.0.0** to **191.255.0.0**
- First octet value range from 128 to 191
- Subnet Mask: 255.255.0.0 (16 bits)
- Number of Networks: 16,382
- Number of Hosts per Network: 65,534
- Class B Private APIPA Range: 169.254.0.0 to 169.254.255.255

> Automatic Private IP Addressing (APIPA) is a feature on Microsoft Windows-based computers to automatically assign itself an IP address within this range if a Dynamic Host Configuration Protocol (DHCP) server is not available. A DHCP server is a device on a network that is responsible for assigning IP address to devices on the network.
 

## Class C

- Range: **192.0.0.0** to **223.255.255.0**
- First octet value range from 192 to 223
- Subnet Mask: 255.255.255.0 (24 bits)
- Number of Networks: 2,097,150
- Number of Hosts per Network: 254 ## Class D
- Not allocated to hosts and are used for **multicasting**
- Range: **224.0.0.0** to **239.255.255.255**
- First octet value range from 224 to 239
- Number of Hosts per Network: Multicasting ## Class E
- Reserved for research purposes
- Range: **240.0.0.0** to **255.255.255.255**
- First octet value range from 240 to 255 ## Loopback Addresses
- IP Range: **127.0.0.1** to **127.255.255.255**

# RFC 1918 Private IPv4 Addressing

+ Assigned to hosts and not routable on the internet
+ Most enterprises today use RFC 1918 addresses and NAT

---

# The Data-Link Layer (Layer 2)

- Frames are encoded and decoded into bits at Layer 2
- Error detection and correction for the physical layer
- Ethernet is the *layer 2* medium used on LAN networks

## Media Access Control

The 48-bit hexadecimal MAC address has two parts: 1. The first 24 bits is the OUI (Organizationally Unique Identifier) and identifies the manufacturer of the Ethernet Port, assigned by the IEEE 2. The last 24 bits are vendor assigned The burned in MAC address on every NIC port in the world is globally unique e.g. **00:50:56:C0:00:08**

## How to find your MAC Address?
```
Cisco IOS: show interface
Windows: ipconfig /all
Linux: ifconfig
```

## The Different Types of Data and their Layers

1. Application = Data
2. Transport - Segment
3. Network - Packet
4. Data-link - Frame

# The Physical Layer (Layer 1)

- OSI Layer 1 conveys the bit stream, electrical impulse, light or radio signals, though the network at the electrical and mechanical level
- Provides the hardware means of sending and receiving data, including defining cables, interface cards and physical aspects

## Ethernet LAN connections can be carried over:

- Coaxial cable (no longer used)
- Twisted copper pair cable
- Fiber cable
- Wireless

> RJ-45 max length = 100m
> 
- **Cat 5** / **5e** - Gigabit Ethernet
- **Cat 6** - 10 Gigabit Ethernet

# Straight-Through vs Crossover UTP Cable

- Copper UTP (Unshielded Twisted Pair) cables are commonly used to connect desktop computers to switches
- Straight-Through connect end device of different types eg. PC or router to a switch
- Crossover connect devices of the same type eg. 2 computers/2 switches
- Modern switches support **Auto MDI-X**; receive and transmit signals are reconfigured automatically to yield the expected result

# Fiber Optic Cables

- Support longer distances or higher bandwidth requirements i.e. between separate buildings in a campus
- Switch to switch connections in a building
- **Single-mode** fiber optic cables: more expensive, long distances
- **Multi-mode** fiber: less expensive
- **Port** at the back of the Switch > **Transceiver** > **Fiber Optic Cable** connector
- **PoE Switch**: use a power injector
