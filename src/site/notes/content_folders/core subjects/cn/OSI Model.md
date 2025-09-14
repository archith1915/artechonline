---
{"dg-publish":true,"permalink":"/content-folders/core-subjects/cn/osi-model/","title":"The OSI Model","dgShowToc":true}
---

The OSI or the Open System Interconnection model is a set of rules that explains how computers communicate over a network. This model consists of 7 layers and each layer has specific functions.

1. [[content_folders/core subjects/cn/OSI Model#Physical Layer\|Physical Layer]]
2. [[content_folders/core subjects/cn/OSI Model#Data Link Layer\|Data Link Layer]]
3. [[content_folders/core subjects/cn/OSI Model#Network Layer\|Network Layer]]
4. [[content_folders/core subjects/cn/OSI Model#Transportation Layer\|Transportation Layer]]
5. [[content_folders/core subjects/cn/OSI Model#Session Layer\|Session Layer]]
6. [[content_folders/core subjects/cn/OSI Model#Presentation Layer\|Presentation Layer]]
7. [[content_folders/core subjects/cn/OSI Model#Application Layer\|Application Layer]]


# Physical Layer

Physical layer is the bottom most layer that connects the devices or computers physically. This layer consists of hubs, repeaters, modems and cables. The data in this layer is transmitted in the form of bits (stream of bits).

Various [[content_folders/core subjects/cn/Topologies\|topologies]] can be used to organize the devices in this layer.


# Data Link Layer

The next layer in the OSI model is the Data Link Layer. This layer is responsible for node-to-node transfer of data. The data is transmitted in packets called Frames. The data link layer is responsible for physical addressing where it assigns MAC addresses to IP packets and transmit them between computers using local media discussed in the [[content_folders/core subjects/cn/OSI Model#Physical Layer\|physical layer.]]

> MAC address can be found on the NIC of the device.

DLL is embedded in the NIC as a software.

# Network Layer

The network layer is responsible for transmitting data from one network to another. The data is sent in the form of packets. Routers ensure that the data is transmitted and **forwarded** correctly. The network layer performs three major operations.

1. Logical addressing - The data packets are assigned with logical addresses using IPv4 or IPv6 of the source and destination to form IP packets and ensure proper routing and delivery.
2. Routing - Routing refers to forwarding the data packets on to the correct paths and to the correct routers to have it delivered to the destination safely and at the earliest.
3. Path determination - Each network can be accessed through various paths. It is crucial to choose the right to ensure quick and safe delivery of the data packets. The routers in the network layer choose the paths with least cost and least downtime.

# Transportation Layer

The functions of the transportation layer consists of segmentation, flow control and error control. 

Segmentation is the process if dividing the data packets received into small segments each assigned with source and destination port numbers and a sequence number. The port numbers guide the segments to the right node and process while the sequence number help put the packets together in the right order at the destination.

Flow control manages the data transmission rates. It adjusts the data transmission rate to ensure that the communication is smooth. Sometimes sources may transmit data at a faster rate that the receiver's processing capability, or vice versa. The transport layer informs the source or the destination of this mismatch and sees to it that the transmission rate is adjusted for proper communication.

The error control mechanism helps find and fix missing or corrupted data packets. The checksum assigned to each data packet helps the layer identify missing or corrupted packets and the repeated request-response mechanism is used to fetch or fix the missing or corrupted data packets.

This layer uses protocols like TCP (Transmission Control Protocol) which is a connection-oriented protocol that uses feedback and UDP (User Datagram Protocol) which is a connection-less protocol that happens to be faster with no feedback thus resulting in unordered delivery of packets and no possibilities for retrieval or lost packets unlike in TCP.

# Session Layer

The session layer is responsible for setting up and managing connections for communication. Assuming a typical server-client system, when the client wants to makes a resource request to the server, the session layer sets up a connection between the two.

The server first authenticates the user using username and password combinations and then authorizes to check if the user is permitted to use or request the resource. 

This layer uses APIs and NETBIOS for communication. The session layer keeps track of resources requested and downloaded or uploaded. As soon as the connection is terminated, the session ends and all the data stored (temporary) for that particular session is cleared.

# Presentation Layer

The presentation layer is responsible for three functions. Translation, compression and encryption/decryption of data.

1. The data received from the application layer is usually in text or numbers (ASCII). This data needs to be translated to make it machine understandable. For example, ASCII to EBCDIC format.
2. The data is then compressed to fasten it's transmission across the network. This compression can be both lossy and lossless.
3. The data is then encrypted to keep it safe while in transmission. The source encrypts the data and the destination decrypts it.

> Some of the protocols used in encryption are TLS (Transport layer security) and SSL (Secure socket layer).


# Application Layer

The application layer consists of the applications that use the internet or the network. Web browsers are a classic example for network applications. This layer uses protocols like HTTP, HTTPS, SMTP, FTP etc for data transmission.

