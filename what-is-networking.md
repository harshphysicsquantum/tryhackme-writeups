What is Networking write-up | tryhackme

Task 1
Networking is the practice of connecting computers, devices, and systems to share data, resources, and services efficiently and securely. It enables communication between devices, access to the internet, file and application sharing, and remote work. Networking also forms the backbone of modern IT infrastructure, supporting websites, cloud services, and online communication. In cybersecurity, understanding networking is essential, as it helps detect threats, secure data transfer, and protect systems from attacks.
What is the key term for devices that are connected together?
Network

Task 2
Network can be one of two types:
A private network
A public network

Who invented the World Wide Web?
Tim Berners-Lee

Task 3
Devices on a network are very similar to humans in the fact that we have two ways of being identified:
Our Name
Our Fingerprints

Now we can change our name through deed poll, but we can't, however, change our fingerprints. Every human has an individual set of fingerprints which means that even if they change their name, there is still an identity behind it. Devices have the same thing: two means of identification, with one being permeable. These are:
An IP Address
A Media Access Control (MAC) Address - think of this as being similar to a serial number.

IP Addresses
Briefly, an IP address (or Internet Protocol) address can be used as a way of identifying a host on a network for a period of time, where that IP address can then be associated with another device without the IP address changing.
An IP address is a set of numbers that are divided into four octets. The value of each octet will summarise to be the IP address of the device on the network. This number is calculated through a technique known as IP addressing & subnetting, but that is for another day. What's important to understand here is that IP addresses can change from device to device but cannot be active simultaneously more than once within the same network.
IP Addresses follow a set of standards known as protocols. These protocols are the backbone of networking and force many devices to communicate in the same language, which is something that we'll come onto another time. However, we should recall that devices can be on both a private and public network. Depending on where they are will determine what type of IP address they have: a public or private IP address.
Public IP addresses are given by your Internet Service Provider (or ISP) at a monthly fee (your bill!)
MAC Addresses
Devices on a network will all have a physical network interface, which is a microchip board found on the device's motherboard. This network interface is assigned a unique address at the factory it was built at, called a MAC (Media Access Control ) address. The MAC address is a twelve-character hexadecimal number (a base sixteen numbering system used in computing to represent numbers) split into two's and separated by a colon. These colons are considered separators. For example, a4:c3:f0:85:ac:2d. The first six characters represent the company that made the network interface, and the last six is a unique number.
However, an interesting thing with MAC addresses is that they can be faked or "spoofed" in a process known as spoofing. This spoofing occurs when a networked device pretends to identify as another using its MAC address. When this occurs, it can often break poorly implemented security designs that assume that devices talking on a network are trustworthy. Take the following scenario: A firewall is configured to allow any communication going to and from the MAC address of the administrator. If a device were to pretend or "spoof" this MAC address, the firewall would now think that it is receiving communication from the administrator when it isn't.
We will simply have to change the MAC Address of Bob to that of Alice.
We got the flag.
What does the term "IP" stand for?
Internet Protocol
What is each section of an IP address called?
Octet
How many sections (in digits) does an IPv4 address have?
4
What does the term "MAC" stand for?
Media Access Control
Deploy the interactive lab using the "View Site" button and spoof your MAC address to access the site. What is the flag?
THM{YOU_GOT_ON_TRYHACKME}

Task 4
Ping is one of the most fundamental network tools available to us. Ping uses ICMP (Internet Control Message Protocol) packets to determine the performance of a connection between devices, for example, if the connection exists or is reliable.
The time taken for ICMP packets travelling between devices is measured by ping, such as in the screenshot below. This measuring is done using ICMP's echo packet and then ICMP's echo reply from the target device.
Pings can be performed against devices on a network, such as your home network or resources like websites. This tool can be easily used and comes installed on Operating Systems (OSs) such as Linux and Windows. The syntax to do a simple ping is ping IP address or website URL. Let's see this in action in the screenshot below.
What protocol does ping use?
ICMP
What is the syntax to ping 10.10.10.10?
ping 10.10.10.10
What flag do you get when you ping 8.8.8.8?
THM{I_PINGED_THE_SERVER}
What I Learned & Why It's Important in Security
From this lesson, I learned the fundamentals of networking, including how devices communicate and identify each other using IP and MAC addresses. I understood the difference between private and public networks, and how IP addresses are assigned and structured using octets. I also learned that while IP addresses can change, MAC addresses are unique hardware identifiers, although they can be spoofed. Additionally, I learned about the ping tool and how it uses the ICMP protocol to test connectivity between devices.
This knowledge is important in cybersecurity because networking forms the foundation of all cyber activities. Understanding IP and MAC addresses helps in identifying devices, tracking attackers, and detecting suspicious behavior such as spoofing. Learning about tools like ping is useful for troubleshooting networks and checking connectivity during attacks or defenses. Concepts like MAC spoofing also highlight how attackers can bypass weak security, which helps in building stronger defenses.
Overall, this lesson is important because it builds a strong base for understanding how cyberattacks happen on networks and how they can be detected, analyzed, and prevented.