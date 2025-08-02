## Table of Contents

#### 1. Other
1. Services
2. API
3. What is the URL? Its Relationship with IP
4. NAT Protocol (Abbreviated)
#### II. Conceptual Overview and Their Relationships
[Detailed Version] Carrier, Optical Modem, Router, Switch, Network Card, IP Address, Ethernet Protocol
#### III. TCP/IP Five-Layer Model
Physical Layer, Data Link Layer, Network Layer, Transport Layer, and Service Layer
#### IV. Examples
- (I) Zhang San and Li Si Cursed at Wang Wu
- (II) Guangzhou PC, Zhongshan Router/Switch, Zhuhai PC
- [Abbreviated Version] Internet Company, Carrier, Optical Modem, Router, Switch, Network Card, IP Address, Ethernet Protocol

## I. Other:
1. Service: The process that provides the service

2. API: Specifies how to make requests (e.g., what data to pass and in what format) and how to receive and interpret responses

3. URL? The Relationship with IP?
- What does a URL look like?
https://www.example.com:443/docs/index.html?id=1#top
- Split into:
- Protocol (https)
- Hostname (www.example.com)
- Port (443, optional)
- Path (/docs/index.html)
- Query string (?id=1)
- Fragment (#top)
- IP mapping process
- Browser receives URL → Extracts hostname www.example.com
- DNS resolution → Returns 93.184.216.34 (this is the IP)
- TCP three-way handshake connects to 93.184.216.34:443
- Sends HTTP request: GET /docs/index.html?id=1 …
- Server returns the webpage based on the path, query string, and fragment
- Summary
- URLs are user-oriented and contain all the information about "who to contact and what resource to request."
- IP addresses are network-routing-oriented and only determine which machine the packet should be sent to.
- A domain name can be associated with multiple IP addresses (load balancing); a single IP address can also be associated with multiple domain names (virtual hosting).
- Domain names are "Easy-to-remember" aliases for difficult-to-remember numeric IP addresses (e.g., www.example.com)

4. NAT (Network Address Translation) --> A NAT device (usually a router or firewall) sits between private and public networks.
- Converts private IP addresses to public IP addresses (and vice versa).
- Primarily addresses IPv4 address depletion and provides a degree of network security isolation.
- IPv4 address shortage: Public IP addresses (IP addresses directly accessible from the internet) are limited in number. Most organizations (homes, companies) cannot obtain enough public IP addresses to allocate to all internal devices.
- Private IP addresses: To address address shortages, private IP addresses (e.g., 192.168.x.x, 10.x.x.x, 172.16.x.x - 172.31.x.x) are used. These addresses are not routable on the internet and can only be used within a local area network.
- Accessing the internet: If all devices could only use private IP addresses, they would be unable to directly access servers on the internet.

## 2. Concepts and Their Relationships:

#### (I) Concepts
* **Service Provider (ISP):** A company that provides internet connectivity services. They own a vast network infrastructure (including fiber optic cables, servers, routers, etc.) and provide internet access to users (homes, businesses, etc.).
- The internet is called the public network
* **Optical Modem:** An optical modem is an access device provided by a service provider to home or business users. Its primary function is to convert optical signals into electrical signals so that home devices (such as routers and computers) can understand and use them. Conversely, it converts electrical signals into optical signals and transmits them back to the service provider's network via optical fiber. The optical modem is typically located at the entrance to the user's network.
- (Core)** A user's home broadband access ultimately connects to the service provider's network via optical fiber. **
* **Router:** A router is a device that connects different networks. Its core function is to forward data packets based on IP addresses, determining the optimal path for data from one network to another. In a home setting, a router typically connects an optical modem to the internal network (such as computers, mobile phones, and switches). A router is a key device for internet connectivity.

* **Switch:** A switch is primarily used to connect devices within the same network. It efficiently forwards data frames within a local area network (LAN) based on MAC addresses. Typically, in a home or office network, a switch (sometimes integrated into a router) connects multiple computers, printers, and other devices.
- It doesn't necessarily connect computers or printers; any device can be plugged into a switch.
* **MAC Address:** A MAC address is the physical address of a network interface card (NIC), also known as a hardware address. It is uniquely assigned globally by the card manufacturer and is used to identify a network device at the data link layer. A MAC address is fixed and bound to the device.
* **IP Address:** An IP address is a logical address used to identify devices on a network at the network layer. IP addresses are configurable and are used to route data between different networks. The IP addresses we commonly encounter are public IP addresses (assigned by carriers for internet access) and private IP addresses (used within home or business LANs and assigned by routers).

* Network Card: A network card is a hardware interface for a computer or other network device. It converts data into signals (electrical, optical, etc.) that can be transmitted over the network and converts received signals back into data. Each network card has a unique MAC address.
* Ethernet Protocol: Ethernet is a widely used LAN technology standard. It defines the data frame format, MAC address addressing, and access control mechanisms on shared media. The Ethernet protocol primarily operates at the physical layer and the data link layer.

#### (II) The Relationship Between Them
1. Carriers Provide Connections, and Optical Modems Act as Access Bridges: Carriers connect the internet to users' homes via optical fiber. Optical modems convert the carrier's optical signals into electrical signals that can be processed by home devices.
2. **A router connects different networks and enables internet access:** A router connects a home LAN (connected to the external network via an optical modem) with the external network (the internet). It is responsible for routing data packets from the internal network to the external network, and vice versa, based on IP addresses.

3. **A switch connects devices within the same network:** If you need to connect multiple devices for communication within a LAN, you can use a switch (or the built-in switching function of a router). A switch efficiently forwards data within the LAN using MAC addresses.
4. **A network card is the physical interface for communication and has a MAC address:** Any device that needs to participate in communication (computers, mobile phones, routers, switches, etc.) must have a network card. A network card has its own unique MAC address.
5. **MAC addresses are used for addressing within a LAN, while IP addresses are used for addressing across networks:** At the data link layer, MAC addresses are used to accurately locate a target device within the same network segment. At the network layer, IP addresses are used to locate a target device across different networks.

## III. TCP/IP Five-Layer Model
## Physical Layer
No addressing function
Media: Cable, fiber optic cable, twisted pair, etc.
1. Two types of signals (signal forms):
- Analog signals: Continuous, like sound
- Digital signals: Discrete in nature
2. Two types of signals (physical carriers/mediums):
- Electrical signals: Transmitted via voltage/current on metal conductors.
- Wave signals: Transmitted via electromagnetic waves (radio or optical fiber).
3. Electrical and wave signals can be both analog and digital.

## Data Link Layer
MAC --> [Who am I, who am I sending to, what information is being sent, and whether the information is error-free] --> Intermediate point (switch (switch table) --> Send to a designated person

#### 1. A network card is hardware: It is the physical interface that connects a computer to a network medium (such as a cable or optical fiber). It converts digital signals within the computer into physical signals that can travel over copper wire, optical fiber, or air.
- Hidden under the keyboard (more precisely, integrated into the motherboard, which is located under the keyboard).
- They can be wired or wireless: wireless network cards transmit and receive waves; wired network cards provide a network port.
- Stores MAC addresses (physical addresses)
- There are as many physical addresses as there are network cards.

#### 2. Switch: MAC address
- Has a switch table: Addressing function, which contains the correspondence between sockets and physical devices.
- Provides fault tolerance because IP addresses can change.
- Connects devices in the same building (a small network can have multiple switches, and switches can be connected to each other).

#### 3. Ethernet protocol: Like writing an email, it contains sender information (address), recipient information, and content.
- Not a network, but a protocol.
[P.S. Wi-Fi protocol: The protocol that implements this protocol is called Wi-Fi.]

## Network layer: Connects different small networks.
- The essence of a network is data transmission.

#### 1. Router: IP address
- Router, helps find the router.
- Communication on the Internet is addressed through the router.
- Home routers mostly act as switches.

#### 2. IP protocol
- There's no ability to prevent data loss (the data link layer does).
- An IP address is assigned by the hardware device it's connected to. A device can have a custom private IP address, but it needs a public IP address to access the internet.

#### 3. Access Point (AP)
- Wireless switch
- A device that implements the Wi-Fi protocol at home is called an access point.
- It has router functionality but acts as an AP.

## Transport Layer
TCP Protocol

## Application Layer
Information transmission: HTTP; HTTPS. These protocols specify the format for data transmission.
- Does not include video formats: HTTPS places blocks here, while other protocols place videos (protocols act like porters).
- txt, xml, json --> Text
- html (URL: contains videos and images) --> Used to demarcate areas
- HTTP request methods: PUT, GET, DELETE, POST, etc. (add, delete, modify, and query)

## 4. Examples
(1) Zhang San and Li Si scold Wang Wu

Zhang San, Li Si, and Wang Wu's computers are connected to the same switch, corresponding to Ports a, b, and c

Zhang San wants to send a message cursing Wang Wu to Li Si. Implementation process:

Simple summary: Zhang San packages the cursing text layer by layer --> The switch only looks at the MAC address and uses the switch table to find port b corresponding to Li Si's computer --> Li Si receives the complete message.

(II) Guangzhou PC, Zhongshan Router/Switch, Zhuhai PC
Guangzhou PC, Zhongshan Router/Switch, Zhuhai PC
I want to send a message from Guangzhou --> It's equivalent to a large package.
1. Application layer: Wrapped with protocols such as HTTP; the large package is split into five smaller packages and sent.
2. Transport layer: TCP ensures stability, assigning sequence numbers to each package. --> Wrapped with TCP and other protocols; only four packages are received. After sorting, it is found that only 1, 3, 4, and 5 have been received, missing 2. The transport layer of the Zhuhai PC sends a request to the Guangzhou PC to resend package 2.
- TCP (reliable transmission) or UDP (unreliable transmission)
3. Network Layer: Enclosed in the IP protocol, the IP header contains the source IP address (the IP address of the Guangzhou PC) and the destination IP address (the IP address of the Zhuhai PC).
4. Data Link Layer: Enclosed in the Ethernet protocol, the Ethernet frame header contains the source and destination MAC addresses. For node-to-node transmission, the packet contains the recipient, sender, and a small secret between the two parties.
- Ethernet Protocol: Contains the recipient, sender, content, and a small secret between the two parties (to ensure authenticity, verify information, and prevent tampering).
- Node-to-node transmission on the same link
1. Ethernet frame header: The sender is the MAC address of the Guangzhou PC's network card, and the recipient is the MAC address of the Guangzhou LAN gateway. ---> Data leaves the Guangzhou PC's LAN (to the next node).

2. The Zhongshan router receives the frame: The sender is the MAC address of the Zhongshan router's current forwarding interface, and the recipient is the MAC address of the next device on the Zhongshan LAN heading toward Zhuhai. ---> This continues until the data reaches the Zhuhai network boundary and is ultimately sent to the Zhuhai PC (to the next node).
- Frame header inspection: Verifies that the recipient's MAC address is the recipient's own MAC address.
- Frame check: Ensures the data has not been tampered with.
- Decapsulation (data link layer): Strips off the Ethernet frame header to reveal the IP datagram within.
- Content: IP datagram.
- Checks the destination IP address and determines the routing path based on the routing table.
- Frame: The basic unit of the data link layer; a large package formed by encapsulating a network layer packet with an Ethernet protocol layer is called a frame. (The distinction between packet and frame is due to the different layers, but they essentially mean the same thing.)

3. From the Zhuhai network border router to the Zhuhai PC:
- Sender MAC Address: The MAC address of the Zhuhai network border router
- Recipient MAC Address: The MAC address of the Zhuhai PC

4. Zhuhai PC Receives and Reassembles the Frame:
- Data Link Layer (Zhuhai PC): Receives the frame and finds that the recipient's MAC address is its own. It verifies the frame and strips off the frame header, obtaining the IP datagram.
- Network Layer (Zhuhai PC): Checks the IP datagram header and finds that the destination IP address is its own. It strips off the IP header, obtaining the TCP segment.
- Transport Layer (Zhuhai PC):
- Received TCP segments are sorted according to the sequence number in the TCP header.
- The previously mentioned missing "packet 2" triggers the retransmission mechanism (described above). Once all segments are received and acknowledged in order, they are reassembled into the original application layer data.
- Application Layer (Zhuhai PC): Receives the reassembled data (e.g., HTTP request) and performs appropriate processing (displaying web page content, etc.).

### 3. **Core Component Relationships:**
* **Internet Company:**
- Internet: Also known as the public network (you can only access the internet with a public IP address)
* **Service Provider (ISP):** Provides internet services.
- They buy the internet from the ISP and then sell it to us.
* **Optical Modem:** Converts the carrier's signal (light or electricity) into a signal usable by your home devices. It's the "key" to your internet access.
- The NAT technology and protocols in the optical modem convert IP addresses into MAC addresses.
- If the internet is a highway, the optical modem is a special toll booth, giving us an identity (a public IP address) to access the highway (access the internet). **The special feature is that the identities given are limited (if only one identity is given, it's like only one car can access the highway). **Identities are rotated: Why is the internet in shopping malls so slow? Because there are so many people, switching identities is slow.
- To send messages, the optical modem converts our private IP address to a public IP address.
* **Router:** The "brains" of the home network, connecting the optical modem to all devices. It's responsible for routing data between different networks (such as your home network and the internet) and assigning IP addresses to your home.
* **Switch:** If your home has many devices, a switch (sometimes integrated into a router) is responsible for connecting these devices within the same local area network (LAN), allowing them to communicate efficiently.
* **Network Card:** The "physical interface" of devices like computers and phones, allowing them to connect to the internet. Each network card has a unique **MAC address**.
* **MAC address:** The network card's "identity card," globally unique, used to precisely locate a device within the same LAN.
* **IP address:** The device's "house number" within the network, used to locate it between different networks. Your computer typically has an internal (private) IP address, and your router has an external (public) IP address that connects to the internet.
* **Ethernet Protocol:** A set of rules that dictate how MAC addresses are used to send data within the same LAN (for example, how data is packaged into "frames").