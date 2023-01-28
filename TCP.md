#network 
Transmission Control Protocol

![What is a TCP 3-way handshake process?](https://afteracademy.com/images/what-is-a-tcp-3-way-handshake-process-three-way-handshaking-establishing-connection-6a724e77ba96e241.jpg)

TCP  is a transport-layer protocol, responsible for establish a connection between two machines. 

TCP consists of 2 protocols: TCP and [[UDP]] (User Datagram Package).  

TCP is _reliable_, each packet has a **sequence number**, and an **acknowledgement** is expected.  A packet will be re-transmitted if it is not received by the receiver.  Packet delivery is guaranteed in TCP.  

TCP _multiplexes_ applications within an [[IP]] machine. For each IP machine, TCP supports (multiplexes) up to 65536 [[port]]s (or [[socket]]s), from port number 0 to 65535.  

An application, such as HTTP or FTP, runs (or listens) at a particular port number for incoming requests. Port 0 to 1023 are pre-assigned to popular protocols, e.g., HTTP at 80, FTP at 21, Telnet at 23, SMTP at 25, NNTP at 119, and DNS at 53.  Port 1024 and above are available to the users.

In brief, to communicate over TCP/IP, you need to know (a) IP address or hostname, (b) Port number.