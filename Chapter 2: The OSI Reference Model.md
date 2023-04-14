---
title: 'Chapter 2: The OSI Reference Model'
updated: 2023-04-14 08:05:18Z
created: 2023-04-14 06:24:18Z
latitude: 35.68919750
longitude: 51.38897360
altitude: 0.0000
---

## Summary

Here are the main topics covered in this chapter:

- The ISO’s OSI reference model consists of seven layers: physical (Layer 1), data link (Layer 2), network (Layer 3), transport (Layer 4), session (Layer 5), presentation (Layer 6), and application (Layer 7). The purpose of each layer was presented, along with examples of technologies living at the individual layers, as it pertains to networking.
- The TCP/IP stack was presented as an alternative model to the OSI reference model. The TCP/IP stack consists of four layers: network interface, Internet, transport, and application. These layers were compared with the seven layers of the OSI model.
- This chapter discussed how port numbers are used to associate data at the transport layer with a proper application layer protocol. Examples of common application layer protocols in the TCP/IP suite were presented, along with their port numbers.

* * *

## The OSI Model

- ***Layer 1 -** The **physical** layer*: The concern of the physical layer is the transmission of bits on the network along with the physical and electrical characteristics of the network.
    
    - **Note:** A hub interconnects PCs in a LAN. However, it is considered a physical layer device because a hub takes bits coming in on one port and retransmits those bits out all other ports. At no point does the hub interrogate any addressing information in the data.
        
    - **How to represent bits on the medium**: Data on a computer network is represented as a binary expression. For example, the presence or the absence of voltage on a wire portrays a binary 1 or a binary 0. Similarly, the presence or absence of light on a fiber-optic cable renders a 1 or 0 in binary. This type of approach is called *current state modulation*. An alternate approach to portraying binary data is state transition modulation, where the transition between voltages or the presence of light shows a binary value.
        
        - **Note**: Other modulation types include amplitude modulation (AM) and frequency modulation (FM). AM uses a variation in a waveform’s amplitude (that is, signal strength) to portray the original signal. However, FM uses a variation in frequency to stand for the original signal.
    - **Wiring standards for connectors and jacks**: For example, the TIA/EIA-568-B standard describes how to wire an RJ-45 connector for use on a 100BASE-TX Ethernet network.
        
    - **Physical topology**: Layer 1 devices view a network as a physical topology.
        
    - **Synchronizing bits**: For two networked devices to successfully communicate at the physical layer, they must agree on when one bit stops and another bit starts.
        
        - **Asynchronous**: With this approach, a sender states that it is about to start transmitting by sending a start bit to the receiver. When the receiver sees this, it starts its own internal clock to measure the next bits. After the sender transmits its data, it sends a stop bit to say that it has finished its transmission.
        - **Synchronous**: This approach synchronizes the internal clocks of both the sender and the receiver to ensure that they agree on when bits begin and end. A common approach to make this synchronization happen is to use an external clock.
    - **Bandwidth usage**:
        
        - **Broadband**: Divides the bandwidth available on a medium into different channels. A sender can then transmit different communication streams over the various channels. For example, consider frequency-division multiplexing (FDM) used by a cable modem.
        - **Baseband**: Baseband technologies, in contrast, use all the available frequencies on a medium to send data. Ethernet is an example of a networking technology that uses baseband.
    - **Multiplexing strategy**: Allows multiple communications sessions to share the same physical medium.
        
        - **Time-division multiplexing (TDM)**: TDM supports different communication sessions on the same physical medium by causing the sessions to take turns. For a brief period, defined as a time slot, data from the first session is sent, followed by data from the second session. This continues until all sessions have had a turn, and the process repeats itself.
        - **Statistical time-division multiplexing (StatTDM)**: StatTDM dynamically assigns time slots to communications sessions on an as-needed basis.
        - **Frequency-division multiplexing (FDM)**: FDM divides a medium’s frequency range into channels, and different communication sessions send their data over different channels. this approach to bandwidth usage is called broadband.
- ***Layer 2 -*** *The* ***data link*** *layer*: Its processes are referred to collectively as data link control (DLC). The data link layer is unique from the other layers in that it has two sublayers of its own: MAC and LLC. Examples of devices defined by data link layer standards include switches, bridges, and NICs.
    
    - **Note**: NICs are not entirely defined at the data link layer because they are partially based on physical layer standards, such as a NIC’s network connector.
    - **Media Access Control (MAC)**:
        - **Physical addressing**: A common example of a Layer 2 address is a MAC address, which is a 48-bit address assigned to a device’s network interface card (NIC).  The first 24 bits of the 48-bit address is the vendor code. The last 24 bits of a MAC address are assigned by the manufacturer, and they act as a serial number for the device. No two MAC addresses in the world should have the same value.
        - **Logical topology**: Layer 2 devices view a network as a logical topology.
        - **Method of transmitting on the media**: With several devices connected to a network, there needs to be some strategy for deciding when a device sends on the media. Otherwise, multiple devices might send at the same time and thus interfere with one another’s transmissions.
    - **Logical Link Control (LLC)**:
        - **Connection services**: When a device on a network receives a message from another device on the network, that recipient device can give feedback to the sender in the form of an acknowledgment message. The two main functions provided by these acknowledgment messages are as follows:
            - **Flow control**: Limits the amount of data a sender can send at one time; this prevents the sender from overwhelming the receiver with too much information.
            - **Error control**: Allows the recipient of data to let the sender know whether the expected data frame was not received or whether it was received but is corrupted.
        - **Synchronizing transmissions**: Senders and receivers of data frames need to coordinate when a data frame is being transmitted and should be received. The three methods of performing this synchronization are:
            - **Isochronous**: With isochronous transmission, network devices look to a common device in the network as a clock source, which creates fixed-length time slots. Network devices can determine how much free space, if any, is available within a time slot and then insert data into an available time slot. A time slot can accommodate more than one data frame. Isochronous transmission does not need to provide clocking at the beginning of a data string (as does synchronous transmission) or for every data frame (as does asynchronous transmission). As a result, isochronous transmission uses little overhead when compared to asynchronous or synchronous transmission methods
            - **Asynchronous**: With asynchronous transmission, network devices reference their own internal clocks, and network devices do not need to synchronize their clocks. Instead, the sender places a start bit at the beginning of each data frame and a stop bit at the end of each data frame. An additional bit, called the parity bit, might also be added to the end of each byte in a frame to detect an error in the frame. If the receiver of a byte is configured for even parity error detection and receives a byte where the total number of bits (including the parity bit) is even, the receiver can conclude that the byte was not corrupted during transmission.
                - **Note**: Using a parity bit to detect errors might not be effective if a byte has more than one error.
            - **Synchronous**: With synchronous transmission, two network devices that want to communicate between themselves must agree on a clocking method to show the beginning and ending of data frames. One approach to providing this clocking is to use a separate communications channel over which a clock signal is sent. Another approach relies on specific bit combinations or control characters to indicate the beginning of a frame or a byte of data. Rather than using parity bits, synchronous communication runs a mathematical algorithm on the data to create a cyclic redundancy check (CRC). If both the sender and the receiver calculate the same CRC value for the same chunk of data, the receiver can conclude that the data was not corrupted during transmission.
- ***Layer 3 -*** *The* ***network*** *layer*: Examples of devices found at the network layer include routers and multilayer switches. The most common Layer 3 protocol in use, and the protocol on which the Internet is based, is IPv4. However, IPv6 is beginning to be more common on networks today.
    
    - **Logical addressing**: Whereas the data link layer uses physical addresses to make forwarding decisions, the network layer uses logical addressing to make forwarding decisions. The most widely deployed routed protocol is Internet Protocol (IP).
    - **Switching**: Engineers often associate the term switching with Layer 2 technologies; however, the concept of switching also exists at Layer 3.
        - **Packet switching**: With packet switching, a data stream is divided into packets. Each packet has a Layer 3 header that includes a source and destination Layer 3 address.
        - **Circuit switching**: Circuit switching dynamically brings up a dedicated communication link between two parties for those parties to communicate. Example: the telephone company’s switching equipment interconnects your home phone with the phone system of the business you are calling. This interconnection (that is, circuit) only exists for the duration of the phone call.
        - **Message switching**: Message switching is usually not well suited for real-time applications because of the delay involved. Specifically, with message switching, a data stream is divided into messages. Each message is tagged with a destination address, and the messages travel from one network device to another network device on the way to their destination.
    - **Route discovery and selection**: Because Layer 3 devices make forwarding decisions based on logical network addresses, a Layer 3 device might need to know how to reach various network addresses. For example, a common Layer 3 device is a router. A router can maintain a routing table indicating how to forward a packet based on the packet’s destination network address. A router can have its routing table populated via manual configuration (that is, by entering static routes), via a dynamic routing protocol (for example, RIP, OSPF, or EIGRP), or simply by the fact that the router is directly connected to certain networks.
    - **Connection services**: Just as the data link layer offers connection services for flow control and error control, connection services also exist at the network layer. Connection services at the network layer can improve the communication reliability, if the data link’s LLC sublayer is not performing connection services.
        - **Flow control (also known as congestion control)**
        - **Packet reordering:** Allows packets to be placed in the proper sequence as they are sent to the receiver.
- ***Layer 4 -*** *The* ***transport*** *layer*: Acts as a dividing line between the upper layers and lower layers of the OSI model. Specifically, messages are taken from upper layers (Layers 5–7) and are encapsulated into segments for transmission to the lower layers (Layers 1–3). Similarly, data streams coming from lower layers are deencapsulated and sent to Layer 5 (the session layer), or some other upper layer, depending on the protocol.
    
    - **Transmission Control Protocol (TCP)**: A connection-oriented transport protocol. Offers reliable transport, in that if a segment is dropped, the sender can detect that drop and re-transmit the dropped segment.
    - **User Datagram Protocol (UDP)**: A connection-less transport protocol. Connection-less transport protocols offer unreliable transport, in that if a segment is dropped, the sender is unaware of the drop, and no re-transmission occurs.
    - **Windowing**: TCP communication uses windowing, in that one or more segments are sent at one time, and a receiver can attest to the receipt of all the segments in a window with a single acknowledgment. In some cases, TCP uses a sliding window, where the window size begins with one segment. If there is a successful acknowledgment of that one segment, the window size doubles to two segments. Upon successful receipt of those two segments, the next window holds four segments. This exponential increase in window size continues until the receiver does not acknowledge successful receipt of all segments within a certain amount of time—known as the round-trip time (RTT), which is sometimes called real transfer time—or until a configured maximum window size is reached.
    - **Buffering**: With buffering, a device (for example, a router) uses a chunk of memory (sometimes called a buffer or a queue) to store segments if bandwidth is not available to send those segments. A queue has a finite capacity, however, and can overflow (that is, drop segments) in case of sustained network congestion.
- ***Layer 5 -*** *The* ***session*** *layer*: Is responsible for setting up, maintaining, and tearing down sessions. H.323 is an example of a session layer protocol, which can help set up, support, and tear down a voice or video connection. Keep in mind, however, that not every network application neatly maps directly to all seven layers of the OSI model. The session layer is one of those layers where it might not be possible to name what protocol in each scenario is running in it. Network Basic Input/Output System (NetBIOS) is one example of a session layer protocol.
    
    - \*\*Note: \*\*NetBIOS is an application programming interface (API) developed in the early 1980s to allow computer-to-computer communication on a small LAN. IBM needed to support over larger Token Ring networks. As a result, enhanced the scalability and features of NetBIOS with a NetBIOS emulator named NetBIOS Extended User Interface (NetBEUI).
    - **Setting up a session**:
        - Checking user credentials (for example, username and password).
        - Assigning numbers to a session’s communication flows to uniquely find each one.
        - Negotiating services needed during the session.
        - Negotiating which device begins sending data.
    - **Maintaining a session**:
        - Transferring data
        - Reestablishing a disconnected session
        - Acknowledging receipt of data
    - **Tearing down a session:** A session can be disconnected based on agreement of the devices in the session. Alternatively, a session might be torn down because one party disconnects (either intentionally or because of an error condition). If one party disconnects, the other party can detect a loss of communication with that party and tear down its side of the session.
- ***Layer 6 -*** *The* ***presentation*** *layer*: Handles formatting the data being exchanged and securing that data with encryption.
    
    - **Data formatting**: As an example of how the presentation layer handles data formatting, consider how text is formatted. Some applications might format text using American Standard Code for Information Interchange (ASCII), while other applications might format text using Extended Binary Coded Decimal Interchange Code (EBCDIC). The presentation layer handles formatting the text (or other types of data, such as multimedia or graphics files) in a format that allows compatibility between the communicating devices.
    - **Encryption**
- ***Layer 7 -*** *The* ***application*** *layer*: The application layer supports services used by end-user applications. For example, email is an application layer service that does exist at the application layer, whereas Microsoft Outlook (an example of an email client) is an end-user application that does not live at the application layer. Another function of the application layer is advertising available services.
    
    - **Application services**
    - **Service advertisement:** Some applications’ services (for example, some networked printers) periodically send out advertisements, making their availability known to other devices on the network. Other services, however, register themselves and their services with a centralized directory (for example, Microsoft Active Directory), which can be queried by other network devices seeking such services.

* * *

## The TCP/IP Stack

The ISO developed the OSI reference model to be generic, in terms of what protocols and technologies could be categorized by the model. However, most of the traffic on the Internet (and traffic on corporate networks) is based on the TCP/IP protocol suite. Therefore, a more relevant model for many network designers and administrators to reference is a model developed by the United States Department of Defense (DoD). This model is known as the DoD model or the TCP/IP stack.

**Note**: An older protocol known as the Network Control Protocol (NCP) was similar to the TCP/IP protocol. NCP was used on ARPANET (the predecessor to the Internet), and it provided features like those offered by the TCP/IP suite of protocols on the Internet, although they were not as robust.

The TCP/IP stack is composed of the following layers:

- **Network interface (AKA network access layer)**: The TCP/IP stack’s network interface layer encompasses the technologies offered by Layers 1 and 2 (the physical and data link layers) of the OSI model.
- **Internet**: The Internet layer of the TCP/IP stack maps to Layer 3 (the network layer) of the OSI model. Although multiple routed protocols (for example, IP, IPX, and AppleTalk) live at the OSI model’s network layer, the Internet layer of the TCP/IP stack focuses on IP as the protocol to be routed through a network.
    - **The format of an IP Version 4 packet**:
        - ![IPV4.png](../_resources/IPV4.png)
        - The Protocol field shows the transport layer protocol from which the packet was sent or to which the packet should be sent. Also of note is the Time-to-Live (TTL) field. The value in this field is decremented by 1 every time this packet is routed from one IP network to another (that is, passes through a router). If the TTL value ever reaches 0, the packet is discarded from the network. This behavior helps prevent routing loops. As a common practice, the OSI layer numbers of 1, 2, and 3 are still used when referring to physical, data link, and network layers of the TCP/IP stack, even though the TCP/IP stack does not explicitly separate the physical and data link layers.
- **Transport**: The transport layer of the TCP/IP stack maps to Layer 4 (the transport layer) of the OSI model. The two primary protocols found at the TCP/IP stack’s transport layer are TCP and UDP.
    - **TCP Segment Format**:
        - ![TCP.png](../_resources/TCP.png)
        - Notice the fields for source and destination ports. As described later in this chapter, these ports identify to which upper-layer protocol data should be forwarded, or from which upper-layer protocol the data is being sent. Also Notice the field for window size. The value in this field determines how many bytes a device can receive before expecting an acknowledgment. As previously described, this feature offers flow control. The header of a TCP segment also contains sequence numbers for segments. With sequence numbering, if segments arrive out of order, the recipient can put them back in the proper order based on these sequence numbers. The acknowledgment number in the header shows the next sequence number the receiver expects to receive. This is a way for the receiver to let the sender know that all segments up to and including that point have been received. Due to the sequencing and acknowledgements, TCP is considered to be a connection-oriented transport layer protocol.
    - **UDP Segment Format**:
        - ![UDP.png](../_resources/UDP.png)
        - UDP is a connection-less, unreliable protocol. UDP lacks the sequence numbering, window size, and acknowledgment numbering present in the header of a TCP segment. The UDP segment’s header simply contains source and destination port numbers, a UDP checksum (which is an optional field used to detect transmission errors), and the segment length (measured in bytes). Because a UDP header is so much smaller than a TCP header, UDP becomes a good candidate for the transport layer protocol for applications that need to maximize bandwidth and do not require acknowledgments (for example, audio or video streams).
- **Application**: The biggest difference between the TCP/IP stack and the OSI model is found at the TCP/IP stack’s application layer. This layer addresses concepts described by Layers 5, 6, and 7 (the session, presentation, and application layers) of the OSI model.
    - With the reduced complexity of a four-layer model like the TCP/IP stack, network designers and administrators can more easily categorize a given networking technology into a specific layer. For example, with the TCP/IP stack, you could quickly figure out that H.323 is a higher-level protocol that gets encapsulated inside of TCP, and thus classify H.323 in the application layer of the TCP/IP stack.

* * *

## Common Application Protocols in the TCP/IP Stack

Application layer protocols in the TCP/IP stack are identifiable by unique port numbers. For example, when you enter a web address in an Internet browser, you are communicating with that remote web address using TCP port 80. Specifically, Hypertext Transfer Protocol (HTTP), which is the protocol used by web servers, uses TCP port 80. When you send traffic to that remote website, the packet you send out to the network needs not only the destination IP address (172.16.1.2 in this example) of the web server and the destination port number for HTTP (that is, 80), it also needs the source IP address of your computer (10.1.1.1 in this example). Because your computer is not acting as a web server, it. When the web server sends content back, the IP addresses and port numbers have now switched, with the web server as the source and your PC as the destination. With both source and destination port numbers, along with source and destination IP addresses, two-way communication becomes possible.s port is not 80. Instead, your computer selects a source port number greater than 1023.

- **Application Layer Protocols/Applications**:
    - | Protocol | Description | TCP Port | UDP Port |
        | --- | --- | --- | --- |
        | DHCP | Dynamic Host Configuration Protocol: Dynamically assigns IP address information (for example, IP address, subnet mask, DNS server’s IP address, and default gateway’s IP address) to a network device |     | 67, 68 |
        | DNS | Domain Name System: Resolves domain names to corresponding IP addresses | 53  | 53  |
        | FTP | File Transfer Protocol: Transfers files with a remote host (typically requires authentication of user credentials) | 20, 21 |     |
        | H.323 | A signaling protocol that provides multimedia communications over a network | 1720 |     |
        | HTTP | Hypertext Transfer Protocol: Retrieves content from a web server | 80  |     |
        | HTTPS | Hypertext Transfer Protocol Secure: Used to securely retrieve content from a web server | 443 |     |
        | IMAP | Internet Message Access Protocol: Retrieves email from an email server | 143 |     |
        | IMAP4 | Internet Message Access Protocol Version 4: Retrieves email from an email server | 143 |     |
        | LDAP | Lightweight Directory Access Protocol: Provides directory services (for example, a user directory that includes username, password, email, and phone number information) to network clients | 389 |     |
        | LDAPS | Lightweight Directory Access Protocol over SSH: A secured version of LDAP | 636 |     |
        | MGCP | Media Gateway Control Protocol: Used as a call control and communication protocol for Voice over IP networks |     | 2427, 2727 |
        | NetBIOS | Network Basic Input/Output System: Provides network communication services for LANs that use NetBIOS | 139 | 137, 138 |
        | NNTP | Network News Transport Protocol: Supports the posting and reading of articles on Usenet news servers | 119 |     |
        | NTP | Network Time Protocol: Used by a network device to synchronize its clock with a time server (NTP server) |     | 123 |
        | POP3 | Post Office Protocol Version 3: Retrieves email from an email server | 110 |     |
        | RDP | Remote Desktop Protocol: A Microsoft protocol that allows a user to view and control the desktop of a remote computer | 3389 |     |
        | rsh | Remote Shell: Allows commands to be executed on a computer from a remote user | 514 |     |
        | RTP | Real-time Transport Protocol: Used for delivering media-based data (such as Voice over IP) through the network | 5004, 5005 | 5004, 5005 |
        | RTSP | Real-Time Streaming Protocol: Communicates with a media server (for example, a video server) and controls the playback of the server’s media files | 554 | 554 |
        | SCP | Secure Copy: Provides a secure file-transfer service over an SSH connection and offers a file’s original date and time information, which is not available with FTP | 22  |     |
        | SFTP | Secure FTP: Provides FTP file-transfer service over an SSH connection | 22  |     |
        | SIP | Session Initiation Protocol: Used to create and end sessions for one or more media connections, including Voice over IP calls | 5061 | 5060 |
        | SMP | Server Message Block: Used to share files, printers, and other network resources | 445 |     |
        | SMTP | Simple Mail Transfer Protocol: Used for sending email | 25  |     |
        | SNMP | Simple Network Management Protocol: Used to monitor and manage network devices |     | 161 |
        | SNMPT | Simple Network Management Protocol Trap: A notification sent from an SNMP agent to an SNMP manager | 162 | 162 |
        | SNTP | Simple Network Time Protocol: Supports time synchronization among network devices, similar to Network Time Protocol (NTP), although SNTP uses a less complex algorithm in its calculation and is slightly less accurate than NTP |     | 123 |
        | SSH | Secure Shell: Used to securely connect to a remote host (typically via a terminal emulator) | 22  |     |
        | Telnet | Telnet: Used to connect to a remote host (typically via a terminal emulator) | 23  |     |
        | TFTP | Trivial File Transfer Protocol: Transfers files with a remote host (does not require authentication of user credentials) |     | 69  |
        

*Pages 74 to 105*
