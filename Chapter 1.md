## Chapter 1: Network Fundamentals

The main topics covered in this chapter are the following:

- This chapter introduced you to various network components, including the client, server, hub, switch, router, media, and WAN link.
- One way to classify networks is by their geographical dispersion. Specifically, these network types were identified: LAN, WAN, CAN, MAN, PAN, WLAN, and SAN.
- Another approach to classifying networks is based on a network’s topology. Examples of network types, based on topology, include bus, ring, star, partial mesh, full mesh, and hub and spoke. This text also provided information on the various wireless topologies available.
- This chapter contrasted client/server and peer-to-peer networks.

* * *

## Converged Network

A term given to a network transporting multiple types of traffic (for example, voice, video, and data) is converged network. A converged network might offer significant cost savings to organizations that previously supported separate network infrastructures for voice, data, and video traffic. This convergence also potentially **reduces staffing costs**, because **only a single network needs to be supported**, rather than separate networks for separate traffic types.

* * *

## The Network Components

- ***Client***: The term client defines *the device an end user uses to access a network*.
- ***Server***: A server, as the name suggests, *serves up resources to a network*. These resources might include email on email server, web pages as offered by a web server, or files available on a file server.
- ***Hub***: A hub is *an older technology that interconnects network components*, such as clients and servers. If you chain too many hubs together, network errors can result. A hub *is a Layer 1 device and does not perform any inspection of the traffic it passes*. Rather, a hub simply receives traffic in a port (that is, a receptacle to which a network cable connects) and repeats that traffic out all the other ports. Remember, for the local area network (LAN), *the hub is considered obsolete*.
- ***Switch***: A switch *interconnects network components*, and switches *are available with a variety of port densities*. A switch learns which devices live off of which ports. It looks at the destination address and, if the switch knows the destination address, it forwards the traffic out of the appropriate port. *Consider a switch a Layer 2 device*, which means that *it makes its forwarding decisions based on addresses that are physically burned into a network interface card (NIC)* installed in a host. This *burned-in address is a Media Access Control (MAC) address.*
- ***Router***: Consider a router to be *a Layer 3 device, it makes its forwarding decisions based on logical network addresses*. When traffic comes into a router, *the router examines the destination IP address* of the traffic and, based on the router’s database of networks (that is, the routing table), it intelligently forwards the traffic out the appropriate interface.
- ***Media***: The previously mentioned *devices need to be interconnected via some sort of media*. This media could be copper cabling. It could be a fiber-optic cable. Media might not even be a cable, as is the case with wireless networks, where radio waves travel through the media of air. *Media varies in its cost, bandwidth capacity, and distance limitation*. For example, although fiber-optic cabling is more expensive than unshielded twisted-pair cabling, it can typically carry traffic over longer distances and has a greater bandwidth capacity.
- ***WAN link***: Most networks connect to one or more other networks via a Multiprotocol Label Switching (MPLS) network, the link that interconnects those networks is typically referred to as a wide area network (WAN) link.

* * *

## Networks Defined by Geography

- ***Local area network (LAN)***: A LAN interconnects network components within a local area. Examples of common LAN technologies are Ethernet (that is, IEEE 802.3) and wireless networks (that is, IEEE 802.11)
- ***Wide area network (WAN)***: A WAN interconnects network components that are geographically separated. Multiprotocol Label Switching (MPLS) and Asynchronous Transfer Mode (ATM) are examples of WAN technologies.
- ***Wireless local area network (WLAN)***: A local area network made up of wireless networking devices is a wireless local area network (WLAN).
- ***Storage area network (SAN)***: You can construct a high-speed, highly reliable network for the express purpose of transmitting stored data.
- ***Campus area network (CAN)***: Building-centric LANs were interconnected. By these LANs being interconnected, another network type was created, a CAN.
- ***Metropolitan area network (MAN***): A MAN interconnects locations scattered throughout a metropolitan area. One example of a MAN technology is Metro Ethernet, which features high speeds
- ***Personal area network (PAN)***: A PAN is a network whose scale is even smaller than a LAN. A connection between a PC and a digital camera via a universal serial bus (USB) is a PAN, or a Bluetooth connection between your cell phone and your car’s audio system is considered a wireless PAN (WPAN).

* * *

## Networks Defined by Topology

- ***Physical Topology***: A Topology where all devices are connected (Peer-to-peer or switch based) and can share things directly to each other
    
- ***Logical Topology***: A Topology where files are shared in a ring by the switch and could be recieved anywhere in the ring by the reciever.
    
- ***Bus Topology***: A bus topology, typically uses a cable running through the area needing connectivity. Devices that need to connect to the network then tap into this nearby cable.
    
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | One cable is used per network segment. | Less cable is needed to install a bus topology, as compared with other topologies. | Because a single cable is used per network segment, the cable becomes a potential single point of failure. |
        | To support appropriate electrical characteristics of the cable, the cable requires a terminator (of a specific resistance) at each end of the cable. | Depending on the media used by the bus, a bus topology can be less expensive. | Troubleshooting a bus topology can be difficult because problem isolation might need an inspection of multiple network taps to make sure they either have a device connected or they are properly terminated. |
        | Bus topologies were popular in early Ethernet networks. | Installation of a network based on a bus topology is easier than some other topologies, which might require extra wiring to be installed. | Adding devices to a bus might cause an outage for other users on the bus. |
        | Network components tap directly into the cable via a connector such as a T connector or a vampire tap. |     | An error condition existing on one device on the bus can affect performance of other devices on the bus. |
        |     |     | A bus topology does not scale well because all devices share the bandwidth available on the bus. Also, if two devices on the bus simultaneously request access to the bus, an error condition results. |
        
- ***Ring Topology***: Where traffic flows in a circular fashion around a closed network loop. Typically, a ring topology sends data, in a single direction, to each connected device in turn, until the intended destination receives the data
    
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Devices are interconnected by connecting to a single ring or, in some cases (for example, FDDI), a dual ring. | A dual-ring topology adds a layer of fault tolerance. Therefore, if a cable break occurred, connectivity to all devices could be restored. | A break in a ring when a single ring topology is used results in a network outage for all devices connected to the ring. |
        | Each device on a ring includes both a receiver (for the incoming cable) and a transmitter (for the outgoing cable). | Troubleshooting is simplified in the event of a cable break, because each device on a ring contains a repeater. When the repeater on the far side of a cable break does not receive any data within a certain amount of time, it reports an error condition, typically in the form of an indicator light on a network interface card (NIC). | Rings have scalability limitations. Specifically, a ring has a maximum length and a maximum number of attached stations. Once either of these limits is exceeded, a single ring might need to be divided into two interconnected rings. A network maintenance window might need to be scheduled to perform this ring division. |
        | Each device on the ring repeats the signal it receives. |     | Because a ring must be a complete loop, the amount of cable required for a ring is usually higher than the amount of cable required for a bus topology serving the same number of devices. |
        
- ***Star Topology***: A hub at the center of the topology and a collection of clients individually connected to the hub. In LANs, that centralized device was typically a hub back in the early 1990s. Modern networks, however, usually have a switch. The star topology is the most popular physical LAN topology in use today, with an Ethernet switch at the center of the star and unshielded twisted-pair (UTP) cable used to connect from the switch ports to clients
    
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Devices have independent connections back to a central device (for example, a hub or a switch). | A cable break only impacts the device connected via the broken cable, and not the entire topology | More cable is required for a star topology, as opposed to bus or ring topologies because each device requires its own cable to connect back to the central device. |
        | Star topologies are commonly used with Ethernet technologies. | Troubleshooting is relatively simple because a central device in the star topology acts as the aggregation point of all the connected devices | Installation can take longer for a star topology, as opposed to a bus or ring topology, because more cable runs that must be installed. |
        
- ***Hub-and-Spoke***: When interconnecting multiple sites (for example, multiple corporate locations) via WAN links, a hub-and-spoke topology has a WAN link from each remote site (that is, a spoke site) to the main site (that is, the hub site). hub-and-spoke topology helps minimize WAN expenses by not directly connecting any two spoke locations. If two spoke locations need to communicate between themselves, their communication is sent via the hub location.
    
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Each remote site (that is, a spoke) connects back to a main site (that is, the hub) via a WAN link. | Costs are reduced (as compared to a full-mesh or partial-mesh topology) because a minimal number of links is used. | Suboptimal routes must be used between remote sites because all intersite communication must travel via the main site. |
        | Communication between two remote sites travels through the hub site. | Adding one or more additional sites is easy (as compared to a full-mesh or partial-mesh topology) because only one link needs to be added per site. | Because all remote sites converge on the main site, this hub site potentially becomes a single point of failure. |
        |     |     | Because each remote site is reachable by only a single WAN link, the hub-andspoke topology lacks redundancy |
        
- ***Full-Mesh Topology***: Whereas a hub-and-spoke WAN topology lacked redundancy and suffered from suboptimal routes, a full-mesh topology, directly connects every site to every other site. Because each site connects directly to every other site, an optimal path can be selected, as opposed to relaying traffic via another site. Also, a full-mesh topology is highly fault tolerant.
    
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Every site has a direct WAN connection to every other site. | An optimal route exists between any two sites. | A full-mesh network can be difficult and expensive to scale, because the addition of one new site requires a new WAN link between the new site and every other existing site |
        | The number of required WAN connections can be calculated with the formula w = n * (n – 1) / 2, where w = the number of WAN links and n = the number of sites. | A full-mesh network is fault tolerant because one or more links can be lost and reachability between all sites might still be maintained. |     |
        |     | Troubleshooting a full-mesh network is relatively easy because each link is independent of the other links. |     |
        
- ***Partial-Mesh Topology***: Is a hybrid of the previously described hub-and-spoke topology and full-mesh topology. Specifically, a partial-mesh topology can be designed to offer an optimal route between selected sites while avoiding the expense of interconnecting every site to every other site.
    
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Selected sites (that is, sites with frequent intersite communication) are interconnected via direct links, whereas sites that have less frequent communication can communicate via another site. | A partial-mesh topology provides optimal routes between selected sites with higher intersite traffic volumes while avoiding the expense of interconnecting every site to every other site. | A partial-mesh topology is less fault tolerant than a full-mesh topology. |
        | A partial-mesh topology uses fewer links than a full-mesh topology and more links than a hub-and-spoke topology for interconnecting the same number of sites. | A partial-mesh topology is more redundant than a hub-and-spoke topology. | Is more expensive than a huband-spoke topology. |
        
- ***Wireless Topologies***:
    
    - ***Ad Hoc***: The simplest of wireless topologies is the ad hoc wireless network. This means that the wireless nodes are in charge of sending and receiving traffic to each other, without the assistance of infrastructure devices, such as switches or access points. Some network engineers refer to the ad hoc topology as simply a wireless peer-to-peer (P2P) type of network.
    - ***Infrastructure***: With the infrastructure topology, you have specialized wireless equipment for permitting the wireless communications to take place. Many homes today feature a wireless local area network (WLAN). A wireless access point (WAP) allows the various computers (and other wireless devices) to communicate with each other through the WAP acting like a hub device. This WAP connects to the service provider (SP) of the home user with a wired connection.
    - ***Mesh***: A specific type of ad hoc wireless topology is the mesh. This topology is more sophisticated than the ad hoc in that specialized nodes help move the traffic throughout the topology. Note that these devices are not as fancy as the access points found in an infrastructure type of topology.

* * *

## Networks Defined by Resource Location

- ***Client/Server Networks***: Where a dedicated file server gives shared access to files to the network’s clients. Administration is simpler than trying to administer network resources on multiple peer devices. The performance of a client/server network can be better than that of a peer-to-peer network. You can simplify backups because fewer locations must be backed up.
    
    - **Note**: A server in a client/server network could be a computer running a network operating system (NOS) such as Linux Server Alternatively, a server might be a host making its file system available to remote clients via the Network File System (NFS) service.
    - **Note**: A variant of the traditional server in a client/server network, where the server provides shared file access, is network-attached storage (NAS). A NAS device is a mass storage device that attaches directly to a network. Rather than running an advanced NOS, a NAS device usually makes files available to network clients via a service such as NFS.
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Client devices (for example, PCs) share a common set of resources (for example, file or print resources) located on one or more dedicated servers. | Client/server networks can easily scale, which might require the purchase of additional client licenses. | Because multiple clients might rely on a single server for their resources, the single server can become a single point of failure in the network. |
        | Resource sharing is made possible via dedicated server hardware and network operating systems. | Administration is simplified, because parameters, such as filesharing permissions and other security settings, can be administered on a server as opposed to multiple clients. | Client/server networks can cost more than peer-to-peer networks. For example, client/server networks might need the purchase of dedicated server hardware and a network OS with an appropriate number of licenses. |
        
- ***Peer-to-Peer Networks***: Peer-to-peer networks allow interconnected devices (for example, PCs) to share their resources with one another. Those resources could be, for example, files or printers. Peer-to-peer networks are seen in smaller businesses. Scalability for peer-to-peer networks is a concern, however. Specifically, as the number of devices (that is, peers) increases, the administration burden increases.
    
    - **Note**: Some networks have characteristics of both peer-to-peer and client/server networks. For example, all PCs in a company might point to a centralized server for accessing a shared database in a client/server topology. However, these PCs might simultaneously share files and printers between one another in a peer-to-peer topology. Such a network, which has a mixture of client/server and peer-to-peer characteristics, is called a hybrid network.
    - | Characteristics | Benefits | Drawbacks |
        | --- | --- | --- |
        | Client devices (for example, PCs) share their resources (for example, file and printer resources) with other client devices. | Peer-to-peer networks can be installed easily because resource sharing is made possible by the clients’ operating systems, and knowledge of advanced NOSs is not required | Scalability is limited because of the increased administration burden of managing multiple clients |
        | Resource sharing is made available through the clients’ operating systems. | Peer-to-peer networks usually cost less than client/server networks because there is no requirement for dedicated server resources or advanced NOS software. | Performance might be less than that seen in a client/server network because the devices providing network resources might be performing other tasks not related to resource sharing (for example, word processing). |
        
