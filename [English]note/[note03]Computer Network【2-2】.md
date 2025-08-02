https://blog.csdn.net/Royalic/article/details/119985591
- `Service`-> A program that runs continuously, receiving and responding to requests
- `Server`-> Can run programs (access) and allow others to access it

- The IP address must remain unchanged

- `Port`: Also called a socket. It identifies different network processes

------
### `Process` and `Thread`

A process contains threads: A thread is an execution unit within a process. A process contains at least one thread.
- Process --> Exclusive memory, containing all program information
- A thread is a sub-unit of a process

A process is an execution instance of a program and the basic unit for resource allocation and scheduling in the system. It contains all the resources required for program execution, such as memory, file handles, and devices.

A thread is an execution unit within a process and the smallest unit that the operating system can schedule operations on. It shares all resources owned by the process with other threads belonging to the same process, but it also has some private data.

------
### 1. Physical Layer

Connects different physical devices and transmits bit streams

1 byte == 8 bits

### 2. Data Link Layer: (stores MAC address -> physical address)
1. The data link layer provides reliable data transmission for the network layer;
2. The basic data unit is the frame; (encapsulated into frames)
![alt text](03Network_1.png)
3. Main protocol: Ethernet protocol;
4. Two important device names: bridge and switch.

- [Working at the Network Layer] Router -> IP address (IP table)
- Switch -> MAC address (physical address)

### 3. Network Layer
1. The network layer is responsible for routing data packets between subnets. In addition, the network layer also implements congestion control and internetworking.

2. The basic data unit is the IP datagram.

3. Major protocols included:

- **IP Protocol** (Internet Protocol);
- IP protocol forwarding process

![alt text](03Network_2.png)
- ICMP Protocol (Internet Control Message Protocol);
- ICMP messages can report errors or abnormalities; they are encapsulated within IP datagrams.

![alt text](03Network_3.png)
- ARP Protocol (Address Resolution Protocol);
- RARP Protocol (Reverse Address Resolution Protocol).

4. Important device: Router.

### IV. Transport Layer

1. The transport layer is responsible for segmenting upper-layer data and providing end-to-end reliable or unreliable transmission, as well as end-to-end error control and flow control.

2. Major protocols included: TCP (Transmission Control Protocol) and UDP (User Datagram Protocol).

3. Key equipment: Gateways.

### V. Application Layer

1. Provides an interface for operating systems or network applications to access network services.

2. The basic unit of data transmission is the message.

3. Major protocols included: FTP (File Transfer Protocol), Telnet (Remote Login Protocol), DNS (Domain Name Service), SMTP (Mail Transfer Protocol), POP3 (Post Office Protocol), HTTP.

Some Concepts