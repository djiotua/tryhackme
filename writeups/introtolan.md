# Intro to LAN

Learn about some of the technologies and designs that power private networks

---

# Task 1 - Introducing LAN Topologies

## Introducing LAN Topologies

Over the years, there has been experimentation and implementation of various network designs.  In reference to networking, when we refer to the term "_topology_", we are actually referring to the design or look of the network at hand. Let's discuss the advantages and disadvantages of these topologies below.

### Star Topology

The main premise of a _star_ topology is that devices are individually connected via a central networking device such as a _switch_ or _hub_. This topology is the most commonly found today because of its reliability and scalability - despite the cost.

Any information sent to a device in this topology is sent via the central device to which it connects. Let's explore some of these advantages and disadvantages of this topology below:

Because more cabling & the purchase of dedicated networking equipment is required for this topology, it is _more expensive_ than any of the other topologies. However, despite the added cost, this does provide some significant advantages. For example, this topology is much _more scalable_ in nature, which means that it is very easy to add more devices as the demand for the network increases.

Unfortunately, the more the network scales, the _more maintenance_ is required to keep the network functional. This increased dependence on maintenance can also make troubleshooting faults much harder. Furthermore, the star topology is still prone to failure - albeit reduced. For example, if the centralised hardware that connects devices fails, these devices will no longer be able to send or receive data. Thankfully, these centralised hardware devices are often robust.

![star](https://github.com/djiotua/tryhackme/assets/134016731/b236e967-d121-4c1e-9750-358228fe4e83)

### Bus Topology

This type of connection relies upon a single connection which is known as a _backbone_ cable. This type of topology is similar to the leaf off of a tree in the sense that devices (leaves) stem from where the branches are on this cable.
Because all data destined for each device travels along the same cable, it is very quickly prone to becoming _slow_ and _bottlenecked_ if devices within the topology are simultaneously requesting data. This bottleneck also results in very difficult troubleshooting because it quickly becomes difficult to identify which device is experiencing issues with data all travelling along the same route.

However, with this said, bus topologies are one of the easier and more _cost-efficient_ topologies to set up because of their expenses, such as cabling or dedicated networking equipment used to connect these devices.

Lastly, another disadvantage of the bus topology is that there is _little redundancy_ in place in case of failures. This disadvantage is because there is a single point of failure along the backbone cable. If this cable were to break, devices can no longer receive or transmit data along the bus.

![bus](https://github.com/djiotua/tryhackme/assets/134016731/2d1a669f-7731-4c04-9314-f68c1961da31)

### Ring Topology

The _ring_ topology (also known as _token_ topology) boasts some similarities. Devices such as computers are connected directly to each other to form a loop, meaning that there is _little cabling_ required and _less dependence_ on dedicated hardware such as within a star topology. 

A ring topology works by sending data across the loop until it reaches the destined device, using other devices along the loop to forward the data. Interestingly, a device will only send received data from another device in this topology if it does not have any to send itself. If the device happens to have data to send, it will send its own data first before sending data from another device.

Because there is only one direction for data to travel across this topology, it is fairly easy to troubleshoot any faults that arise. However, this is a double-edged sword because it isn't an efficient way of data travelling across a network, as it may have to visit many multiple devices first before reaching the intended device.

Lastly, ring topologies are _less prone to bottlenecks_, such as within a bus topology, as large amounts of traffic are not travelling across the network at any one time. The design of this topology does, however, mean that a fault such as cut cable, or broken device will result in the entire networking breaking. 

![ring](https://github.com/djiotua/tryhackme/assets/134016731/91f39250-3180-481d-b67c-0a728451208f)

## What is a Switch?

_Switches_ are dedicated devices within a network that are designed to aggregate multiple other devices such as computers, printers, or any other networking-capable device using ethernet. These various devices plug into a switch's port. Switches are usually found in larger networks such as businesses, schools, or similar-sized networks, where there are many devices to connect to the network. Switches can connect a large number of devices by having ports of 4, 8, 16, 24, 32, and 64 for devices to plug into.

Switches are much _more efficient_ than their lesser counterpart (hubs/repeaters). Switches keep track of what device is connected to which port. This way, when they receive a packet, instead of repeating that packet to every port like a hub would do, it just sends it to the intended target, thus reducing network traffic.

![switches](https://github.com/djiotua/tryhackme/assets/134016731/53b26470-0a91-49c3-978c-8b086b7ddf6e)

Both Switches and Routers can be connected to one another. The ability to do this _increases the redundancy_ (the reliability) of a network by adding multiple paths for data to take. If one path goes down, another can be used. Whilst this may reduce the overall performance of a network because packets have to take longer to travel, there is _no downtime_ -- a small price to pay considering the alternative.

## What is a Router?

It's a router's job to connect networks and pass data between them. It does this by using _routing_ (hence the name router!).

Routing is the label given to the process of data travelling across networks. Routing involves creating a path between networks so that this data can be successfully delivered.

Routing is useful when devices are connected by many paths, such as in the example diagram below.

![routing2](https://github.com/djiotua/tryhackme/assets/134016731/9856386d-644f-4d4a-9684-d29a5f089d97)

## Practical

Attached to this task is an interactive practical featuring the discussed LAN topologies. Learn about the various ways in which they are vulnerable to breaking. Break the LAN topologies to retrieve the flag.

---

_1. What does LAN stand for?_

  <details>
    <summary>Answer</summary>

    Local Area Network
  </details>

_2. What is the verb given to the job that Routers perform?_

  Hint: This is the term given to deciding what route packets should take.

  <details>
    <summary>Answer</summary>

    Routing
  </details>

_3. What device is used to centrally connect multiple devices on the local network and transmit data to the correct location?_

  Hint: Something smarter than a hub/repeater.

  <details>
    <summary>Answer</summary>

    Switch
  </details>

_4. What topology is cost-efficient to set up?_

  Hint: *** Topology

  <details>
    <summary>Answer</summary>

    Bus Topology
  </details>

_5. What topology is expensive to set up and maintain?_

  Hint: **** Topology

  <details>
    <summary>Answer</summary>

    Star Topology
  </details>

_6. Complete the interactive lab attached to this task. What is the flag given at the end?_

  <details>
    <summary>Answer</summary>

    THM{TOPOLOGY_FLAWS}
  </details>

  <details>
    <summary>Explanation</summary>

    Click "View Site" (green box) to start the interactive lab.
    For the ring topology, I cut (clicked on) a cable anywhere, in which the packets no longer travelled.
    For the bus topology, I sent as much packets as I can (rapidly clicking) until the topology could no longer handle the data flow.
    Finally, for the star topology, I simply broke (clicked on) the central switch, then received the flag for this question.
  </details>

---

# Task 2 - A Primer on Subnetting

As we've previously discussed throughout the module so far, Networks can be found in all shapes and sizes - ranging from small to large. _Subnetting_ is the term given to splitting up a network into smaller, miniature networks within itself. Think of it as slicing up a cake for your friends. There's only a certain amount of cake to go around, but everybody wants a piece. Subnetting is you deciding who gets what slice & reserving such a slice of this metaphorical cake.

Take a business, for example; You will have different departments such as:

- Accounting
- Finance
- Human Resources

![subnet22](https://github.com/djiotua/tryhackme/assets/134016731/ad45a740-17a3-4d5f-91ca-701ade1ca270)

Whilst you know where to send information in real life to the correct department, networks need to know as well. Network administrators use subnetting to categorise and assign specific parts of a network to reflect this.

Subnetting is achieved by splitting up the number of hosts that can fit within the network, represented by a number called a _subnet mask_. Let's refer back to our diagram from the first room in this module.

![subnet1](https://github.com/djiotua/tryhackme/assets/134016731/38e8aa51-12e4-43d6-bf1b-7c4acf759de8)

As we can recall, an IP address is made up of four sections called _octets_. The same goes for a subnet mask which is also represented as a number of four bytes (32 bits), ranging from 0 to 255 (0-255).

Subnets use IP addresses in three different ways:

- Identify the network address
- Identify the host address
- Identify the default gateway
  
Let's split these three up to understand their purposes into the table below.

| Type | Purpose | Explanation | Example |
| --- | --- | --- | --- |
| Network Address | This address identifies the start of the actual network and is used to identify a network's existence. | For example, a device with the IP address of 192.168.1.100 will be on the network identified by 192.168.1.0 | 192.168.1.0 |
| Host Address | An IP address here is used to identify a device on the subnet. | For example, a device will have the network address of 192.168.1.1 | 192.168.1.100 |
| Default Gateway | The default gateway address is a special address assigned to a device on the network that is capable of sending information to another network. | Any data that needs to go to a device that isn't on the same network (i.e. isn't on 192.168.1.0) will be sent to this device. These devices can use any host address but usually use either the first or last host address in a network (.1 or .254) | 192.168.1.254 |

Now, in small networks such as at home, you will be on one subnet as there is an unlikely chance that you need more than 254 devices connected at one time.

However, places such as businesses and offices will have much more of these devices (PCs, printers, cameras and sensors), where subnetting takes place.

Subnetting provides a range of benefits, including:

- Efficiency
- Security
- Full control

We'll come on to explore exactly how subnetting provides these benefits at a later date; however, for now, all we need to understand is the security element to it. Let's take the typical café on the street. This cafe will have two networks:

1. One for employees, cash registers, and other devices for the facility.
2. One for the general public to use as a hotspot.

Subnetting allows you to separate these two use cases from each other whilst having the benefits of a connection to larger networks such as the Internet.

---

_1. What is the technical term for dividing a network up into smaller pieces?_

  <details>
    <summary>Answer</summary>

    Subnetting
  </details>

_2. How many bits are in a subnet mask?_

  Hint: This can be converted into 4 bytes.

  <details>
    <summary>Answer</summary>

    32
  </details>

_3. What is the range of a section (octet) of a subnet mask?_

  Hint: Smallest to largest

  <details>
    <summary>Answer</summary>

    0-255
  </details>

_4. What address is used to identify the start of a network?_

  Hint: ******* Address

  <details>
    <summary>Answer</summary>

    Network Address
  </details>

_5. What address is used to identify devices within a network?_

  Hint: **** Address

  <details>
    <summary>Answer</summary>

    Host Address
  </details>

_6. What is the name used to identify the device responsible for sending data to another network?_

  <details>
    <summary>Answer</summary>

    Default Gateway
  </details>

---

# Task 3 - The ARP Protocol

Recalling from our previous tasks that devices can have two identifiers: A MAC address and an IP address, the _ARP_ protocol or _Address Resolution Protocol_ for short, is the technology that is responsible for allowing devices to identify themselves on a network.

Simply, the ARP protocol allows a device to associate its MAC address with an IP address on the network. Each device on a network will keep a log of the MAC addresses associated with other devices.

When devices wish to communicate with another, they will send a broadcast to the entire network searching for the specific device. Devices can use the ARP protocol to find the MAC address (and therefore the physical identifier) of a device for communication.

## How does ARP Work?

Each device within a network has a ledger to store information on, which is called a cache. In the context of the ARP protocol, this cache stores the identifiers of other devices on the network.

In order to map these two identifiers together (IP address and MAC address), the ARP protocol sends two types of messages:

1. ARP Request
2. ARP Reply
   
When an _ARP request_ is sent, a message is broadcasted to every other device found on a network by the device, asking whether or not the device's MAC address matches the requested IP address. If the device does have the requested IP address, an _ARP reply_ is returned to the initial device to acknowledge this. The initial device will now remember this and store it within its cache (an ARP entry). 

This process is illustrated in the diagram below.

![b27c024d90342c60dd5cb35765e7ed7b](https://github.com/djiotua/tryhackme/assets/134016731/38b916ce-a644-4d98-89d2-d541e19d9468)

---

_1. What does ARP stand for?_

  <details>
    <summary>Answer</summary>

    Address Resolution Protocol
  </details>

_2. What category of ARP Packet asks a device whether or not it has a specific IP address?_

  <details>
    <summary>Answer</summary>

    Request
  </details>

_3. What address is used as a physical identifier for a device on a network?_

  Hint: *** Address

  <details>
    <summary>Answer</summary>

    MAC Address
  </details>

_4. What address is used as a logical identifier for a device on a network?_

  Hint: ** Address

  <details>
    <summary>Answer</summary>

    IP Address
  </details>

---

# Task 4 - The DHCP Protocol

IP addresses can be assigned either manually, by entering them physically into a device, or automatically and most commonly by using a _DHCP (Dynamic Host Configuration Protocol)_ server. When a device connects to a network, if it has not already been manually assigned an IP address, it sends out a request (_DHCP Discover_) to see if any DHCP servers are on the network. The DHCP server then replies back with an IP address the device could use (_DHCP Offer_). The device then sends a reply confirming it wants the offered IP Address (_DHCP Request_), and then lastly, the DHCP server sends a reply acknowledging this has been completed, and the device can start using the IP Address (_DHCP ACK_).

![DHCP](https://github.com/djiotua/tryhackme/assets/134016731/489146f5-a637-4843-804d-ec262bbf0119)

---

_1. What type of DHCP packet is used by a device to retrieve an IP address?_

  Hint: DHCP ********

  <details>
    <summary>Answer</summary>

    DHCP Discover
  </details>

_2. What type of DHCP packet does a device send once it has been offered an IP address by the DHCP server?_

  Hint: DHCP *******

  <details>
    <summary>Answer</summary>

    DHCP Request
  </details>

_3. Finally, what is the last DHCP packet that is sent to a device from a DHCP server?_

  Hint: DHCP ***

  <details>
    <summary>Answer</summary>

    DHCP ACK
  </details>

---

# Task 5 - Continue Your Learning: OSI Model

Continue your learning by joining the "OSI Model" room.

---

1. Join the ["OSI Model" room](https://tryhackme.com/room/osimodelzi).

No answer needed.

---

END OF ROOM
