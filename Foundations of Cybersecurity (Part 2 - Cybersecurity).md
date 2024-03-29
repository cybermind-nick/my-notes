## IMPORTANT TIP
Always use the CIA framework to analyse any cybersecurity system (Confidentiality, Integrity and Availability)
## 19 Feb, 2024

What will we learn:
- Securing networks
- Securing applications
- Security protocols
- Security policies
- Cryptography and network applications

#### Cybersecurity is divided into two main parts/disciplines
- Information Security: CIA ___(Confidentiality, Integrity and Availability)___
- Network Security

Security mechanisms are typically more than a particular algo or protocol

## 21 Feb, 2024 (Tutorial Demonstraction)

Fast Typing (It'll be messy, a lot to observe and take note of)

TCP 3way Handshake
TCP __guarantees__ segment delivery

Before any data is exchanged between two nodes (PC/Server), a session is established using the 3-way handshake

Session is ended using a 4-way teardown (sometimes it is 3-way)


## 26 Feb, 2024 (SSL/TLS)

SSL
- In every SSL session, the server MUST authenticate itself to the client
- SSL is a way for the server to prove itself to the client. This is because a client's service request may be intercepted and responded to by an impersonator


## 27 Feb, 2024
Connections happen WITHIN sessions. A connection can be lost after a data exchange. Multiple connections happen in a single session.

### Handshake protocol
This consist of three main parts
- Authenticate each other
- Negotiate encryption and MAC algorithms
- Negotiate crypto


## 4 March, 2024
### VPNs
VPNs use a protocol suite called IPSec

### VPN Types
Transport VPNs
Tunnel VPNs

These correspond to the two major MODES of IPSec:
- Transport mode (only encapsulating the payload)
- Tunnel mode (encapsulating everything, including headers and IP addresses)

### IPSec
IPSec provides encryption at the IP layer. This is where VPNs work, as they can be used to mask IPs too (if you use the tunnel approach)

### Scope of IPSec VPN
We need to approach this by knowing what VPNs prioritise. This is: authentication and encryption

IPSec enables us to encrypt the header (Which TLS doesn't, because we need it to establish connection, ie, handshake) because we are providing alternative IP addresses to establish connections/do handshakes

### Talking about IPSec Modes
#### Transport Mode
- Only the datagram payload is encrypted  and authenticated
##### Use cases
- Remote access to University network
- VoIP

#### Tunnel Mode
- Entire datagram is encrypted
- Encrypted datagram is encapsulated in a new datagram with it's own IP header, tunneled to destination
##### Use cases
IoT, site-to-site connections

### Encapsulating Security Payload (ESP)
Encapsulating Security Payload (ESP) is in charge of CI (Confidentiality and Integrity) and can sometimes also be in charge of A (Availability) too

ESP is comprised of:
- Security Parameters index -> Security Association (SA) arbitrary value used with the destination IP address
- Anti-Replay sequence number -> Monotonically increasing number


## 5 March, 2024
### Kerberos
Kerberos is an authentication protocol
It uses 3rd party servers for authentication
It is designed for an open distributed environment

#### Important Kerberos Terms
It involves a tifecter
- Key distribution center
- Authentication service
- Ticket Granting Ticket (TGT)
- Ticket Granting Service
- Ticket
- Session Key
- Different key
- Principals

#### What's the flow?
You go to the authentication service/server. Once you have been authorised, you go to the Ticket Granting Server/Service (TGS) where you get an "invitation" to use a service. Then you go to the application/service you want to use and present the __valid__ invitation to use the service. Next... ENJOY!!!

##### Let's get into the details, shall we?


## Free form lecture notes
### Firewalls
Firewalls filter. They do not decrypt. So they filter using packet headers (the info that they contain)

#### Intrusion Detection System (IDS)
IDS - Detect intruders

#### Intrusion Prevention System (IPS)
IPS - Protect from intruders (we use this today)

## Cloud Security


## 18 March 2024
### Email Security
