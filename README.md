> **Project's Score:** [![mnaimi's 42 NetPractice Score](https://badge42.vercel.app/api/v2/cl1txsvi6008009jppddlp1hr/project/2645050)](https://github.com/JaeSeoKim/badge42)

# Net_Practice
This project is a general practical exercise to let you discover networking.

## Network Communications _(Devices)_
When a Client sends a request to a Server, it stamps its IP Address _(Source)_ along with the Server's IP Address _(Destination)_ inside the request _Packet_ (more on that later), and so as the Server when it sends the requested Data back.

The reason for that is because that specific request may be passed between different Hosts, and for these hosts to know whether the request was made for them or not, they need to know the _"who sent what to who"_ informations, which are embedded in the previously mentioned _Packet_.

#### IP Addresses
An IP Address is basically just a number that represents a Host (as previously mentionned), we can represent it in a _Human readable_ way like this:

```text
192.168.0.1
```

or in a _Computer savy_ way like this: 

```text
11000000.10101000.00000000.00000001
```

We can Conclude from this that IP Addresses are just **32bit** combinations of _ones_ and _zeros_

#### Repeater
If two hosts are located very far from each others physically, then the chance of a _Signal Decay_ to happen automatically increases _(btw Signal Decay means that the signal gets weaker and weaker as it travels through greater distances, until it gets lost eventually)_.

This problem can be solved by installing a **Repeater** between two hosts to ensure that the signal gets Regenerated along the way in order to avoid the previously mentioned _Signal Decay_ problem, i.e. when a Host sends a signal to another Host, the Repeater grabs that signal, and sends a Duplicate of that signal _(an identical signal)_ to the receiving host that way the signal stays alive throughout its journey to reach its destination.

#### Hub
Another problem that we may face as a Network Technicien _(I know that you're not one, but hypothetically speaking)_, is that you'll need to connect different Hosts so they can communicate with each other, one way to do it is to physically connect every Hosts with  every other Host, so if we have a Network containing 5 Hosts, the total amount of connections would be 10, and that may be problematic in networks with dozens of Hosts.

To avoid this problem, really smart people invented what is called a **Hub** which is basically just a multi-port Repeater, i.e. is repeats the received signals to all the hosts that are connected to it.

But this solution comes with another problem. When we send some data to another Hosts through a Hub, that Hub sends that data to every Hosts connected to it, and this may be considered as a privacy problem.

#### Bridge
Bridges may be considered as a solution to the Hub problem that we previously explained. It comes with two ports, each connected to a Hub.

Its only role is to distinguish whether the signal coming from one of the Hubs belongs to one of this latter's directly-connected Hosts or not, i.e. the bridge knows where each Host is located _(right side or left side)_, so when a host tries to send some data to another host that is directly connected to it _(with only a Hub in the middle)_, the signal gets sent to the Hub, then this latter sends it to every other device that's connected to it, including the Bridge, but the Bridge knows that the Destination Host isn't located on its other side, so it doesn't repeat that signal, and with this it lowers the posibility of Hosts receiving undestined data.

While all of this may seem practical, at the end of the day, we find out that the Privacy problem isn't solved yet _(partially speaking)_, because we still have Hosts receiving data that wasn't destined to them.

#### Switch
Switches are like a combination of _Repeaters_ and _Bridges_, they receive a signal from a Host, but unlike the _Repeater_ and much like the _Bridges_, they only send it to the appropriate Receiving Host instead to all of the connected Hosts

Hosts connected to a single Switch form a **Network**, precicely a _Local Area Network_ aka _LAN_, this has the disadvantage of not being able to send data to a Hosts that is not connected to the same _Switch_.

Switches perform three actions :
- **Learn:** Update the MAC Address Table with mapping of _Switch Port --> Source MAC_, this is usually done when a Host gets connected to the Switch after this latter was inactive
- **Flood:** Duplicate and send the frame out all the switch ports _(except receiving port)_, this happens when the _Destination MAC Address_, present in the sent frame, isn't available in the MAC Address Table
- **Forward:** Use MAC Address Table to deliver the Frame to the appropriate Switch Port

Switches have MAC Addresses and IP Addresses themselves, the reasong for that is that you'll need to connect to them sometimes, using Telnet or SSH, in order to configure them.

#### Router
Routers alow us to connect different _LAN_s with each other, forming a _Wide Area Network_ aka a _WAN_. As a matter of fact, a Router may also connect different _WAN_s with each others.

I.e. a Router is a device whose primary purpose is to route or move data between networks

## The OSI Model _(Open Systems Interconnection)_
The OSI Model is a method of thinking of computer networking in terms of abstraction layers. Different communication protocols with similar functions are grouped into different logical layers on the OSI Model. I.e. it is a method used to comprehend how networking or how data transfering occurs in its most basic interpretation.

#### Application Layer
_Network process to computer programs_:
- The application layer provides an interface for the end user operating a device connected to a network. This layer is what the user sees, in terms of loading an application (such as Web browser or e-mail); that is, this application layer is the data the user views while using these applications.
- Examples of application layer functionality include:
  - Support for file transfers
  - Ability to print on a network
  - Electronic mail
  - Electronic messaging
  - Browsing the World Wide Web.

#### Presentation Layer
_Data representation, security encryption, convert computer code to network formatted code_:
- The Presentation Layer would be able to properly interpret a message sent through the network this layer is responsible for the proper translation or interpretation.

#### Session Layer
_Interhost communication, managing sessions between programs_:
- The Session Layer establishes request/response communication. When needed, a session is started with authentication, after which a request is sent. After a response the session might be ended or a new request is sent.
- This is the first layer where a client/server concept is introduced. Where a specific device might change the role from client to server or vice versa.

#### Transport Layer
_End-to-end connections, reliability and flow control_:
- The Transport Layer is the level at which system reliability and quality are ensured.
- This layer manages traffic flow through the network layer to reduce congestion on a network, and performs error checking ensuring quality of service by resending data when data has been corrupted.
- Some of the most popular methods of encryption and firewall security take place on this layer.
- This layer ensures data gets sent to the proper App by implementing an addressing scheme called Ports.
- Clients select random Ports for each connection

#### Network Layer
_Path determination and logical addressing_:
- The Routing Layer works to coordinate related parts of a data conversation to ensure that large files are transferred.
- In other words, while the data link layer deals with the method in which the physical layer is used to transfer data, the network layer deals with organizing that data for transfer and reassembly.
- This layer also handles aspects of Routing Protocols using IP Addresses, and also finding the available _(best)_ path(s) from one network to another to ensure delivery of the data.

#### Data Link Layer
_Physical addressing_:
- The Data Layer is mainly the method in which information from the network is broken down into frames and transmitted over the physical layer.
- This layer is also responsible for some Error detection and correction and some addressing so different devices can tell each other apart in larger systems using MAC Addresses.

#### Physical Layer
_The physical infrastructure used to send and receive signals_:
- The Physical Layer refers to electrical and physical aspects of devices. In particular, it specifies how a device sends and receives information, such as using copper wires or fiber-optic cables.
- Examples of this include Ethernet or fiber optic cables, phone cords used for dial-up or DSL services, the coaxial cable used to provide broadband internet, the wires used to connect various components of a computer or even the radio signals used in wireless communication.
- Other functions of the physical layer include the conversion of signals into something that another layer can use (referred to as a bit), and adjusting the signal to allow for multiple users to use the same connections.

## The TCP/IP Model
...

## Data tranfer
whenevr a Host tries to send data to another Host, a Process called **Encapsulation** occurs, which is basically addind more layers to the data that's being sent in order for it to be sent to the right destination.
1. It starts with adding some _TCP_ data to the original _DATA_, we get something called a _Segment_
2. After that we add some _Network_ data _(IP Addresse)_ to the previously assembeled _Segmant_, and we get something called a _Packet_
3. And before we sed that to the Physical layer, we add some _Data link_ stuff to the previously assembeled _Packet_ in order to get what we call a _Frame_
4. and we send that sh!? to the _Physical Layer_ which is basically just _1s_ and _0s_ going through cables or through radio waves _(in case of a Wireless network)_


## Glossary
| Word                 | Definition |
| -------------------- | ---------- |
| **Hosts**            | Any device that sends and/or receives data from other devices |
| **Clients**          | Hosts that initiate requests, i.e. devices that request data from other devices |
| **Servers**          | Hosts that respond to Clients by sending the appropriate data, i.e. devices that provide other devices with the data that this latter requested |
| **IP Addresses**     | The identity of Hosts inside a specific Network, i.e. a bunch of numbers that represent a single Host inside a Network, it helps with the communication between multiple hosts inside a network by identifying _**who** sent **what** to **who**_ |
| **Access Points**    | ... |
| **Layer 3 Switches** | ... |
| **Firewalls**        | ... |
| **Load Balancers**   | ... |
| **IDS/IPS**          | ... |
| **Proxies**          | ... |
| **NAT**              | ... |
| **Classless**        | ... |
| **TCP/UDP**          | ... |
| **NIC**              | ... |

## Ressources

- [**Practical Networking**](https://www.youtube.com/c/PracticalNetworking) YouTube Channel:
  - [_Networking Fundamentals_](https://youtube.com/playlist?list=PLIFyRwBY_4bRLmKfP1KnZA6rZbRHtxmXi) Playlist
  - [_Subnetting Mastery_](https://youtube.com/playlist?list=PLIFyRwBY_4bQUE4IB5c4VPRyDoLgOdExE) Playlist

