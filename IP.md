#network 
IP (Internet Protocol) is a [[network layer]] protocol, deals with network addressing and routing. 

In an IP network, each machine is assigned an unique IP address (e.g., 165.1.2.3), and the IP software is responsible for routing a message from the source IP to the destination IP. 

In IPv4 (IP version 4), the IP address consists of 4 bytes, each ranges from 0 to 255, separated by dots, which is called a _quad-dotted form_. This numbering scheme supports up to 4G addresses on the network.  The latest IPv6 (IP version 6) supports more addresses.  

Since memorizing number is difficult for most of the people, an english-like domain name, such as `www.nowhere123.com` is used instead.  The [[DNS]] (Domain Name Service) translates the domain name into the IP address (via distributed lookup tables). 

A special IP address 127.0.0.1 always refers to your own machine.  It's domain name is "`localhost`" and can be used for _local loopback testing_.

