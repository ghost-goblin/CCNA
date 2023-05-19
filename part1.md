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

