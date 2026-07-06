# Analyze Network Attacks

## Project Overview
This project demonstrates the analysis of a simulated network attack using Wireshark.

### Objectives
- Analyze captured network traffic.
- Identify suspicious TCP and HTTP activity.
- Detect indicators of a SYN flood attack.
- Document findings in a professional incident report.

**TCP_Packet_Log**
| No. | Time (s) | Source | Destination | Protocol | Info |
|-----:|---------:|--------|-------------|----------|------|
| 47 | 3.144521 | 198.51.100.23 | 192.0.2.1 | TCP | 42584→443 [SYN] Seq=0 Win=5792 Len=120 |
| 48 | 3.195755 | 192.0.2.1 | 198.51.100.23 | TCP | 443→42584 [SYN, ACK] Seq=0 Win=5792 Len=120 |
| 49 | 3.246989 | 198.51.100.23 | 192.0.2.1 | TCP | 42584→443 [ACK] Seq=1 Win=5792 Len=120 |
| 50 | 3.298223 | 198.51.100.23 | 192.0.2.1 | HTTP | GET /sales.html HTTP/1.1 |
| 51 | 3.349457 | 192.0.2.1 | 198.51.100.23 | HTTP | HTTP/1.1 200 OK (text/html) |
| 52 | 3.390692 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 53 | 3.441926 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [SYN, ACK] Seq=0 Win=5792 Len=120 |
| 54 | 3.493160 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [ACK] Seq=1 Win=5792 Len=0 |
| 55 | 3.544394 | 198.51.100.14 | 192.0.2.1 | TCP | 14785→443 [SYN] Seq=0 Win=5792 Len=120 |
| 56 | 3.599628 | 192.0.2.1 | 198.51.100.14 | TCP | 443→14785 [SYN, ACK] Seq=0 Win=5792 Len=120 |
| 57 | 3.664863 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 58 | 3.730097 | 198.51.100.14 | 192.0.2.1 | TCP | 14785→443 [ACK] Seq=1 Win=5792 Len=120 |
| 59 | 3.795332 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=120 |
| 60 | 3.860567 | 198.51.100.14 | 192.0.2.1 | HTTP | GET /sales.html HTTP/1.1 |
| 61 | 3.939499 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=120 |
| 62 | 4.018431 | 192.0.2.1 | 198.51.100.14 | HTTP | HTTP/1.1 200 OK (text/html) |
| 63 | 4.097363 | 198.51.100.5 | 192.0.2.1 | TCP | 33638→443 [SYN] Seq=0 Win=5792 Len=120 |
| 64 | 4.176295 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [SYN, ACK] Seq=0 Win=5792 Len=120 |
| 65 | 4.255227 | 192.0.2.1 | 198.51.100.5 | TCP | 443→33638 [SYN, ACK] Seq=0 Win=5792 Len=120 |
| 66 | 4.256159 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 67 | 5.235091 | 198.51.100.5 | 192.0.2.1 | TCP | 33638→443 [ACK] Seq=1 Win=5792 Len=120 |
| 68 | 5.236023 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 69 | 5.236955 | 198.51.100.16 | 192.0.2.1 | TCP | 32641→443 [SYN] Seq=0 Win=5792 Len=120 |
| 70 | 5.237887 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 71 | 6.228728 | 198.51.100.5 | 192.0.2.1 | HTTP | GET /sales.html HTTP/1.1 |
| 72 | 6.229638 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 73 | 6.230548 | 192.0.2.1 | 198.51.100.16 | TCP | 443→32641 [RST, ACK] Seq=0 Win=5792 Len=120 |
| 74 | 6.330539 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 75 | 6.330885 | 198.51.100.7 | 192.0.2.1 | TCP | 42584→443 [SYN] Seq=0 Win=5792 Len=0 |
| 76 | 6.331231 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 77 | 7.330577 | 192.0.2.1 | 198.51.100.5 | TCP | HTTP/1.1 504 Gateway Time-out (text/html) |
| 78 | 7.351323 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 79 | 7.360768 | 198.51.100.22 | 192.0.2.1 | TCP | 6345→443 [SYN] Seq=0 Win=5792 Len=0 |
| 80 | 7.380773 | 192.0.2.1 | 198.51.100.7 | TCP | 443→42584 [RST, ACK] Seq=1 Win=5792 Len=120 |
| 81 | 7.380878 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 82 | 7.383879 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 83 | 7.482754 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 84 | 7.581629 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 85 | 7.680504 | 192.0.2.1 | 198.51.100.22 | TCP | 443→6345 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 86 | 7.709377 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 87 | 7.738241 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 88 | 7.767105 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 89 | 13.895969 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 90 | 13.919832 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 91 | 13.943695 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 92 | 13.967558 | 192.0.2.1 | 198.51.100.16 | TCP | 443→32641 [RST, ACK] Seq=1 Win=5792 Len=120 |
| 93 | 13.991421 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 94 | 14.015245 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 95 | 14.439072 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 96 | 14.862899 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 97 | 14.886727 | 198.51.100.9 | 192.0.2.1 | TCP | 4631→443 [SYN] Seq=0 Win=5792 Len=0 |
| 98 | 15.310554 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 99 | 15.734381 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 100 | 16.158208 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 101 | 16.582035 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 102 | 17.005862 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 103 | 17.429678 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 104 | 17.452693 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 105 | 17.475708 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 106 | 17.498723 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 107 | 17.521738 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 108 | 17.544753 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 109 | 17.567768 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 110 | 17.590783 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 111 | 18.413795 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 112 | 18.436807 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 113 | 18.459819 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 114 | 18.482831 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 115 | 18.506655 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 116 | 18.529667 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 117 | 18.552679 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 118 | 18.875692 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 119 | 19.198705 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 120 | 19.521718 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 121 | 19.844731 | 192.0.2.1 | 198.51.100.9 | TCP | 443→4631 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 122 | 20.167744 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 123 | 20.490757 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 124 | 20.813770 | 192.0.2.1 | 203.0.113.0 | TCP | 443→54770 [RST, ACK] Seq=1 Win=5792 Len=0 |
| 125 | 21.136783 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 126 | 21.459796 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 127 | 21.782809 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 128 | 22.105822 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 129 | 22.428835 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 130 | 22.751848 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 131 | 23.074861 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 132 | 23.397874 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 133 | 23.720887 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 134 | 24.043900 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 135 | 24.366913 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 136 | 24.689926 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 137 | 25.012939 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 138 | 25.335952 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 139 | 25.658965 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 140 | 25.981978 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 141 | 26.304991 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 142 | 26.628004 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 143 | 26.951017 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 144 | 27.274030 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |
| 145 | 27.597043 | 203.0.113.0 | 192.0.2.1 | TCP | 54770→443 [SYN] Seq=0 Win=5792 Len=0 |

# Analyzing Network Attacks from Wireshark TCP/HTTP Log

This analysis is based on the Wireshark TCP/HTTP Log information presented to me assuming I'm a Security Analyst working for a travel agency that advertises sales and promotions on the company's website.

# WORK DONE STARTS FROM HERE

The network protocol analyzer log shows that the web server struggled with establishing connection on port 443. Port 443 is used to establish a secure connection between Web browsers and the web servers which is widely used TCP port for HTTPS traffic. The web server suffered a continuous SYN flood attack, which is a type of DoS (Denial of Service) attack that simulates TCP connection and floods a server with SYN packets. Due to the continuous SYN request from the malicious attacker's IP address the web server suffered communication establishment on the TCP protocol which resulted in delayed response giving out "time-out error message" as the Web server was overloaded with several SYN requests to respond to in order to establish a connection. 
The log shows that a particular I.p. address (203.0.113.0) was flooding the Web server with numerous abnormal SYN packet every second, causing the employees, whom where the legitimate website visitors to have distributions in access the website. This is strongly attributed to a DoS attack, to stop the services being rendered by the Travel Agency through their website.

This attack operated by taking advantage of the first Handshake that occurs when visitors of a website tries to establish connection with the Web server using the TCP protocol. 
•	At first, the visitor of the website tries to connect to the Web server to access the Web pages by  sending out SYN(synchronise) packet to the Web server. 
•	The Web server will respond with a SYN / ACK (Synchronise acknowledge) packet to acknowledge the device request from the visitor of the website, then the server will wait for the final step of the handshake from the website visitor's device before releasing its resources. 
•	Finally, the visitor's device sends an ACK (Acknowledge) packet to the server acknowledging the connection, this establishes a TCP connection. 
However, when the SYN packet requests is sent to the Web server until it overload the server, then the server will unable to respond to the requests. This is a type of network attack that targets a network or a server and floods it with network traffic to obstruct normal business operations,hence Denial of Service (DoS).
The Web serve tends to be overwhelmed or shutdown and be unable to handle the requests of SYN packets when a large number of SYN packets are sent to it at once or continuously. This will typically stop every operation of communication establishment under the TCP protocol with any device trying to access the Web page.

The log from the packet analyzer clearly indicated that a DoS (Denial of Service attack) was being carried out on it from this I. P. address  (203.0.113.0).  At the log no. 52 - 54 after the log started recording, it shows the request of the SYN packet request from malicious attacker was properly handled by the web server, however from log no. 57 the attacker continued sending more SYN requests. As at web server was still handling connections traffic with its visitors, which was showed as one of the employees with the IP address 198.51.100.14 completed the three TCP connection handshake as indicated on log no 55,56,58. Then, the employee's device browser requests to GET the sales.html Web page as on log no 60 using the GET command, and the server responded as in log no 62. After that, the Web sever started struggling as no other successful connection was recorded after another employee with the IP address 198.51.100.5 completed the three TCP connection handshake but was presented with a "Time-out" error message on log no 77 when it requested to get sales.html page on log 71. 
An **HTTPS1.1 504 Gateway Time-out(text/html)** error message is sent by a gateway server when a responds from a server takes too long. The malicious attacker continued to send the SYN packet requests every second. From log 73, employees started receiving RST, ACK (Reset Acknowledge) packet as a result of the server suffering from the overwhelming SYN packet requests from the malicious attacker. An **RST, ACK packet** would be sent to a website visitor if the SYN, ACK packet is not received by the web server. The malicious attacker also started receiving the RST, ACK from log no 83,but the SYN packet requests continued. After the RST, ACK packet was sent by the Web server to an employee with the IP address 198.51.100.9 on log no 121, the Web server stopped responding to the legitimate employee Website visitor traffic. The log from malicious attacker was the only record that kept coming in, sending SYN packet requests on the Web server.
This impacted the network performance by overwhelming the Web server, hence disrupting it's normal operation, denying it's ability to render it's service due to the large number of SYN packets requested from the server by the malicious attacker carrying out this SYN flood attack.
Firewalls can be configured against this IP address to temporary solve this problem while adequate steps should be carried out to stop and prevent this attack from happening again. 

## Key Findings

- Multiple TCP SYN packets originated from 203.0.113.0.
- The server repeatedly responded with RST/ACK packets.

