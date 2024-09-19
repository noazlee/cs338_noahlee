# Assignment 2 - Intro to Wireshark - Noah Lee - September 19th 2024

## ===== DAYTIME =====  
1. Identify the parts of the TCP 3-way handshake by listing the frame summaries of the relevant frames. 
1 192.168.64.2 129.6.15.28 TCP 74 [SYN]
2 129.6.15.28 192.168.64.2 TCP 66 [SYN, ACK]
3 192.168.64.2 129.6.15.28 TCP 54 [ACK]

2. What port number does the client (i.e. nc on your Kali computer) use for this interaction?
44946

3. Why does the client need a port?
To have an address to receive the packets back from the server.

4. What frame contains the actual date and time? 
4 129.6.15.28 192.168.64.2 DAYTIME 105 DAYTIME Response

5. What do [SYN] and [ACK] mean?
[SYN] signifies that the packet is a synchronization packet for the purposes of setting up communication. [ACK] indicates the packet is an acknowledgement packet which is acknowledging information given from the other side.

6. Which entity (the nc client or the daytime server) initiated the closing of the TCP connection? How can you tell?
The server sent the initial [FIN] packet - we can tell by looking at the packets in chronological order.

## ===== HTTP =====  
1. How many TCP connections were opened? How can you tell?


2. Can you tell where my homepage (index.html) was requested?


3. Can you tell where my photograph (jeff-square-colorado.jpg) was requested? 