## Week 5 Exercise: Security Protocols and Private Network

**1. Sana is wondering what is VPN and how she can benefit from it, explain to her VPN, its applications and the possible ways of implementing it.**
+ VPN facilitates communications between companies and their partners, internal communications of a geographically distributed company, or remote communications between a mobile and its company. It is mainly based on establishing an IP tunnel to exchange data. VPN can be imlemented using TLS and IPSec. IPSEC VPN is useful for 
Remote access scenario and Interconnecting LANs. TLS VPN is useful for Remote access to private network scenario.

**2. What is IP tunnelling?**
+  IP tunnelling is creating a private channel where two distant devices can coomunicate as if they were local. It is based on encapsulating an IP packet into another IP packet.

**3. A client and server want to communicate, explain the steps of establishing TLS exchanges**
(1) The client initiates handshake by sending hello message.
(2) The server responds and agrees on security parameters. The server provides a certificate for authentication.
(3) The server sends serverhello done message.
(4) The client sends pre-master secret message, encrypted with server's public key.
(5) The client switches to new cipher suite(algorithm & parameters for encryption).
(6) The client indicates the handshake is done.
(7) The server switches to the given cipher suite.
(8) The client sends handshake finished message.
(9) Secure connection is achieved and they communicate through this connection.

**4. What are the TLS subprotocols?**
+ TLS handshake protocol, TLS cipher protocol, TLS alert protocol
  
**5. Why SSL was discarded?**
+ Lack of security

**6. What network attacks do you think we can stop using TLS?**
+ Because the communication is encrypted, TLS can stop eavesdropping, tampering, and message forgery between two communicating network endpoints.

**7. What network attacks do you think we can stop using IPSec?**
+ Network-based attacks from untrusted computers, attacks that can result in the DoS, Data corruption.
+ Using IPSec  keeps the data encrypted and makes sure they all reached their destination without any alterations on their way.





