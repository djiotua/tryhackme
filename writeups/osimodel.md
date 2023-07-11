# OSI Model

Learn about the fundamental networking framework that determines the various stages in which data is handled across a network

---

# Task 1 - What is the OSI Model?

The _OSI_ model (or Open Systems Interconnection Model) is an absolute fundamental model used in networking. This critical model provides a framework dictating how all networked devices will send, receive and interpret data.

One of the main benefits of the OSI model is that devices can have different functions and designs on a network while communicating with other devices. Data sent across a network that follows the uniformity of the OSI model can be understood by other devices.

The OSI model consists of seven layers which are illustrated in the diagram below. Each layer has a different set of responsibilities and is arranged from Layer 7 to Layer 1.

At every individual layer that data travels through, specific processes take place, and pieces of information are added to this data, which is what we'll come to discuss in the upcoming tasks within this room. However, for now, we only need to understand that this process is called encapsulation and what the OSI model looks like in the diagram below.

![osimodel](https://github.com/djiotua/tryhackme/assets/134016731/ad945ac8-c511-4ee4-a300-c13fb919a627)

---

_1. What does the "OSI" in "OSI Model" stand for?_

  <details>
    <summary>Answer</summary>

    Open Systems Interconnection
  </details>

_2. How many layers (in digits) does the OSI model have?_

  <details>
    <summary>Answer</summary>

    7
  </details>

_3. What is the key term for when pieces of information get added to data?_

  <details>
    <summary>Answer</summary>

    Encapsulation
  </details>

---

# Task 2 - Layer 7 - Application

![application](https://github.com/djiotua/tryhackme/assets/134016731/58bf5330-ed5f-45f7-90b6-1a5d9d64cf80)

The application layer of the OSI model is the layer that you will be most familiar with. This familiarity is because the application layer is the layer in which protocols and rules are in place to determine how the user should interact with data sent or received.

Everyday applications such as email clients, browsers, or file server browsing software such as FileZilla provide a friendly, _Graphical User Interface (GUI)_ for users to interact with data sent or received. Other protocols include _DNS_ (Domain Name System), which is how website addresses are translated into IP addresses.

![browser](https://github.com/djiotua/tryhackme/assets/134016731/03f0f508-1d2c-4ea5-ae27-f3477b3c3388)

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Application
  </details>

_2. What is the technical term that is given to the name of the software that users interact with?_

  <details>
    <summary>Answer</summary>

    Graphical User Interface
  </details>

---

# Task 3 - Layer 6 - Presentation

![presentation](https://github.com/djiotua/tryhackme/assets/134016731/74b63ec1-52d3-4bcf-aeaa-4841ca0bbe31)

Layer 6 of the OSI model is the layer in which standardisation starts to take place. Because software developers can develop any software such as an email client differently, the data still needs to be handled in the same way — no matter how the software works.

This layer acts as a translator for data to and from the application layer (layer 7). The receiving computer will also understand data sent to a computer in one format destined for in another format. For example, when you send an email, the other user may have another email client to you, but the contents of the email will still need to display the same.

Security features such as data encryption (like HTTPS when visiting a secure site) occur at this layer.

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Presentation
  </details>

_2. What is the main purpose that this Layer acts as?_

  Hint: This layer translates data from one format to another.

  <details>
    <summary>Answer</summary>

    Translator
  </details>

---

# Task 4 - Layer 5 - Session

![session](https://github.com/djiotua/tryhackme/assets/134016731/b0dec978-902a-4e8b-9f86-7a16ed442748)

Once data has been correctly translated or formatted from the presentation layer (layer 6), the session layer (layer 5) will begin to create a connection to the other computer that the data is destined for. When a connection is established, a session is created. Whilst this connection is active, so is the session.

The session layer (layer 5) synchronises the two computers to ensure that they are on the same page before data is sent and received. Once these checks are in place, the session layer will begin to divide up the data sent into smaller chunks of data and begin to send these chunks (packets) one at a time. This dividing up is beneficial because if the connection is lost, only the chunks that weren't yet sent will have to be sent again — not the entire piece of the data (think of it as loading a save file in a video game).

What is worthy of noting is that sessions are unique — meaning that data cannot travel over different sessions, but in fact, only across each session instead.

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Session
  </details>

_2. What is the technical term for when a connection is successfully established?_

  Hint: These are unique per connection.

  <details>
    <summary>Answer</summary>

    Session
  </details>

_3. What is the technical term for "small chunks of data"?_

  <details>
    <summary>Answer</summary>

    Packets
  </details>

---

# Task 5 - Layer 4 - Transport

![transport](https://github.com/djiotua/tryhackme/assets/134016731/d291af5a-23c6-495f-9243-3ab05037d564)

Layer 4 of the OSI model plays a vital part in transmitting data across a network and can be a little bit difficult to grasp. When data is sent between devices, it follows one of two different protocols that are decided based upon several factors:

- TCP
- UDP

Let's begin with TCP. The _Transmission Control Protocol (TCP)_. Potentially hinted by the name, this protocol is designed with reliability and guarantee in mind. This protocol reserves a constant connection between the two devices for the amount of time it takes for the data to be sent and received.

Not only this, but TCP incorporates error checking into its design. Error checking is how TCP can guarantee that data sent from the small chunks in the session layer (layer 5) has then been received and reassembled in the same order.

Let's summarise the advantages and disadvantages of TCP in the table below.

| Advantages of TCP | Disadvantages of TCP |
| --- | --- |
| Guarantees the accuracy of data. | Requires a reliable connection between the two devices. If one small chunk of data is not received, then the entire chunk of data cannot be used. |
| Capable of synchronising two devices to prevent each other from being flooded with data. | A slow connection can bottleneck another device as the connection will be reserved on the receiving computer the whole time. |
| Performs a lot more processes for reliability. | TCP is significantly slower than UDP because more work has to be done by the devices using this protocol. |

TCP is used for situations such as file sharing, internet browsing or sending an email. This usage is because these services require the data to be accurate and complete (no good having half a file!).

In the diagram below, we can see how a picture of a dog is broken down into small pieces of data (known as packets) from the "webserver", where the "computer" re-constructs the picture of the dog into the correct order.

![tcpdog](https://github.com/djiotua/tryhackme/assets/134016731/9cdd3796-696e-4333-9761-3e10cdc61685)

Now let's move onto the _User Datagram Protocol_ (or _UDP_ for short). This protocol is not nearly as advanced as its brother - the TCP protocol. It doesn't boast the many features offered by TCP, such as error checking and reliability. In fact, any data that gets sent via UDP is sent to the computer whether it gets there or not. There is no synchronisation between the two devices or guarantee; just hope for the best, and fingers crossed.

Whilst this sounds disadvantageous, it does have its merits, which we'll layout in the table below.

| Advantages of UDP | Disadvantages of UDP |
| --- | --- |
| UDP is much faster than TCP. | UDP doesn't care if the data is received. |
| UDP leaves the application layer (user software) to decide if there is any control over how quickly packets are sent. | It is quite flexible to software developers in this sense. |
| UDP does not reserve a continuous connection on a device as TCP does. | This means that unstable connections result in a terrible experience for the user. |

Using the same example as before, we can now see that only Packets #1 and #3 have been received by the "Computer", meaning that half of the image is missing.

![udpdog](https://github.com/djiotua/tryhackme/assets/134016731/9161338c-7968-4d63-83e8-0c8017fc256f)

UDP is useful in situations where there are small pieces of data being sent. For example, protocols used for discovering devices (ARP and DHCP that we discussed in [Room 2 - Intro to LAN](https://tryhackme.com/room/introtolan)) or larger files such as video streaming (where it is okay if some part of the video is pixelated. Pixels are just lost pieces of data!).

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Transport
  </details>

_2. What does TCP stand for?_

  <details>
    <summary>Answer</summary>

    Transmission Control Protocol
  </details>

_3. What does UDP stand for?_

  <details>
    <summary>Answer</summary>

    User Datagram Protocol
  </details>

_4. What protocol guarantees the accuracy of data?_

  <details>
    <summary>Answer</summary>

    TCP
  </details>

_5. What protocol doesn't care if data is received or not by the other device?_

  <details>
    <summary>Answer</summary>

    UDP
  </details>

_6. What protocol would an application such as an email client use?_

  <details>
    <summary>Answer</summary>

    TCP
  </details>

_7. What protocol would an application that downloads files use?_

  <details>
    <summary>Answer</summary>

    TCP
  </details>

_8. What protocol would an application that streams video use?_

  <details>
    <summary>Answer</summary>

    UDP
  </details>

---

# Task 6 - Layer 3 - Network

![network](https://github.com/djiotua/tryhackme/assets/134016731/01647a58-38bf-4f98-9d46-c58ccd200ddb)

The third layer of the OSI model (network layer) is where the magic of routing & re-assembly of data takes place (from these small chunks to the larger chunk). Firstly, routing simply determines the most optimal path in which these chunks of data should be sent.

Whilst some protocols at this layer determine exactly what is the "optimal" path that data should take to reach a device, we should only know about their existence at this stage of the networking module. Briefly, these protocols include _OSPF (Open Shortest Path First)_ and _RIP (Routing Information Protocol)_. The factors that decide what route is taken is decided by the following:

- What path is the shortest? I.e. has the least amount of devices that the packet needs to travel across.
- What path is the most reliable? I.e. have packets been lost on that path before?
- Which path has the faster physical connection? I.e. is one path using a copper connection (slower) or a fibre (considerably faster)?

At this layer, everything is dealt with via IP addresses such as 192.168.1.100. Devices such as routers capable of delivering packets using IP addresses are known as Layer 3 devices — because they are capable of working at the third layer of the OSI model.

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Network
  </details>

_2. Will packets take the most optimal route across a network? (Y/N)_

  <details>
    <summary>Answer</summary>

    Y
  </details>

_3. What does the acronym "OSPF" stand for?_

  <details>
    <summary>Answer</summary>

    Open Shortest Path First
  </details>

_4. What does the acronym "RIP" stand for?_

  <details>
    <summary>Answer</summary>

    Routing Information Protocol
  </details>

_5. What type of addresses are dealt with at this layer?_

  Hint: Devices on a network use these. For example, 192.168.1.100

  <details>
    <summary>Answer</summary>

    IP Addresses
  </details>

---

# Task 7 - Layer 2 - Data Link

![datalink](https://github.com/djiotua/tryhackme/assets/134016731/15452c8f-8003-412c-8195-cb6701bd6682)

The data link layer focuses on the physical addressing of the transmission. It receives a packet from the network layer (including the IP address for the remote computer) and adds in the physical _MAC (Media Access Control)_ address of the receiving endpoint. Inside every network-enabled computer is a _Network Interface Card (NIC)_ which comes with a unique MAC address to identify it.

MAC addresses are set by the manufacturer and literally burnt into the card; they can't be changed -- although they can be spoofed. When information is sent across a network, it's actually the physical address that is used to identify where exactly to send the information.

Additionally, it's also the job of the data link layer to present the data in a format suitable for transmission.

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Data Link
  </details>

_2. What is the name of the piece of hardware that all networked devices come with?_

  Hint: NIC

  <details>
    <summary>Answer</summary>

    Network Interface Card
  </details>

---

# Task 8 - Layer 1 - Physical

![physical](https://github.com/djiotua/tryhackme/assets/134016731/4ae338c3-57f9-4964-abee-1f657f844e70)

This layer is one of the easiest layers to grasp. Put simply, this layer references the physical components of the hardware used in networking and is the lowest layer that you will find. Devices use electrical signals to transfer data between each other in a binary numbering system (1's and 0's).

For example, ethernet cables connecting devices, such as in the picture below.

![e2d1f02e7e81bb6f5223a3356a053ab5](https://github.com/djiotua/tryhackme/assets/134016731/3dd1f3ac-ef74-412a-8714-efd4269bb18b)

---

_1. What is the name of this Layer?_

  <details>
    <summary>Answer</summary>

    Physical
  </details>

_2. What is the name of the numbering system that is both 0's and 1's?_

  <details>
    <summary>Answer</summary>

    Binary
  </details>

_3. What is the name of the cables that are used to connect devices?_

  <details>
    <summary>Answer</summary>

    Ethernet Cables
  </details>

---

# Task 9 - Practical - OSI Game

Can you escape the OSI dungeon? Climb the levels in the correct order to escape the dungeon and reveal the flag! (Can you beat our staff high score of 19 seconds?)

Click the "_View Site_" button on the right to start.

---

_1. Escape the dungeon to retrieve the flag. What is the flag?_

  <details>
    <summary>Answer</summary>

    THM{OSI_DUNGEON_ESCAPED}
  </details>

  <details>
    <summary>Explanation</summary>

    Remember Layers 1 (bottom) to 7 (top). Getting the order correct results in the flag.
  </details>

---

# Task 10 - Continue Your Learning: Packets & Frames

Continue your learning by joining the "_Packets and Frames_" room.

---

_1. Join the ["Packets and Frames" room](https://tryhackme.com/room/packetsframes)._

No answer needed.

---

END OF ROOM
