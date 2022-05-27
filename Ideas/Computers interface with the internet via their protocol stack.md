*Computers interface with the internet via their protocol stack.* In order to translate a message into a format that can be carried over the internet to another location, a computer must execute a hierarchy of protocols. This is called a *protocol stack.* 

The standard protocol stack is the TCP/IP stack. The TCP/IP stack has four basic layers. 
- Application protocols layer: specific protocols dependent on application (email, browser, etc).
- Transmission control protocol (TCP): directs packets ([[Data is sent across the internet in packets]]) to specific apps on your machine via port number. 
- Internet protocol (IP): directs packets to specific computer based on IP address. 
- Hardware layer: converts between binary packet data and network signals

Data travels down the stack on your machine, and then back up it on the destination machine. 

#idea/compsci 

---
[1] [[How Does the Internet Work? (2002)]]