#networking 
#cryptography
#cybersecurity 
ISO reference model
1. physical (bits)
2. data link (start of packet, end of packet, checksum)
3. network (forwards packets between links)
4. transport (between source and destination; numbering, retransmission of packets)
5. session (only sometimes required- for file transfer, checkpoint, etc)
6. presentation
7. application layer

IP protocols usually combine 5-7 into a single "application layer"
[[layering]] 
layer 3 protocols
- IPv4 is common layer 3 protocol
- layer 3 packet contains source layer 3 address and destination layer 3 address
- can have multiple processes on the receiving machine- protocol type determines this (filters between TCP, UDP, whatever)

layer 4 protocols: UDP, TCP, ICMP
- these have a source port and a destination port, which allows multiple processes on the same machine to talk using TCP or UDP
- TCP has sequence number and ASK number (highest number of data received), UDP doesn't
- also has flags (SYN- start a connection, FIN- end a connection)

DNS
- hierarchical; there's an organization (ICANN) that creates TLDs (top level domains) and assigns them. there are about 1500 TLDs; these are the rightmost component in an address
- URL has DNS name embedded

Protected sessions (TLS (ssl), SSH)
- https only verifies that the website you're visiting is legit; it doesn't verify you
- you can authenticate both ways- this is a cryptographically protected session. often done by having secret keys
- different keys for encryption vs integrity protection
	- alice says prove you're bob
	- bob says i'm bob, prove you're alice
	- alice says i'm alice
	- they now have a cryptographically secure conversation

HTTP and HTTPS (HTTP on top of TLS)
- GET and PUT are main commands
- HTML can encode links as URLs to go to other pages
- page can specify what human sees on link text, what they see when they mouse over it, and where the link actually goes

Cookies
	HTTP is stateless (doesn't remember anything), so it saves info called cookies
	the server sends a little file as a "cookie" that the browser stores. when you call a page, the browser searches its cookies and sends any cookies that match the address back to the server
	cookies could have session ID, and states could be stored on server
	or cookies could have the whole state stored (this is insecure)

Active vs Passive attacks
	**passive attack**: eavesdropper listens to packets being transmitted, but doesn't modify or inject
	**active attack**: listener modifies or injects traffic. MITM (**man in the middle** or **meddler in the middle**)
	MITM can spoof the creation of a secure session

Legal Issues
	patents on public key cryptography slowed down the spread of public key cryptography
	export controls: US says you cant encrypt anything more than a 40 bit key, doesn't want you to export encrypted stuff, but you could still encrypt stuff domestically

Authentication and Authorization
	access control maintained with ACL (access control list)
	grouping students- like [[rbac]] makes maintaining an ACL much easier. ACL is just some boolean combination of groups. May also have properties like hours of access, etc

DOS (Denial of Service)
	didn't used to be considered a big deal until it started happening
	early attack: alice just sends a ton of SYNs to bob. this fills up his TCP table since TCP has to track all the connection numbers
	- one defense: make bob's table bigger
	- another defense: block IPs that send a bunch of incomplete requests
	next version: spoof sender IP address
	- defense: alice has to prove that she can receive packets before bob makes a TCP table entry. bob is **stateless** until alice is proven
	- bob uses a secret function given alice's IP to determine the initial sequence number "y". when she sends a packet back, bob can check with the function whether "y" is the correct number. this means that bob doesn't have to make a table entry until after alice sends a packet back, preventing his TCP from being clogged up
	another version: send a bunch of traffic with bob's IP, bob gets a lot of fake annoying responses
	more: make DNS unreachable, spoof DNS
	another way: malware infects computers, turns computers into "bots"
	- this is DDOSing. defeats DOS defenses because the bots aren't lying about source IP
	- defenses: content delivery network (putting your thing on lots of servers so it doesn't get overwhelmed), avoid malware that turns computers into bots

NAT (Network Address Translation)
	IP addresses are too small (4 bytes), so they let multiple networks use the same IPs locally
	when you talk outside your local cluster (where you have a unique IP),
	NAT box maps from private IP g to a global IP K for outgoing requests, and translates K back to g for incoming requests
	- this means that nobody can talk to you unless you've talked to them first

Firewalls
	early firewall: box that sits between corporate network and rest of Internet and filters packet-by-packet which IP addresses and TCP ports are allowed to talk (**packet filter**)
	stateful: keep track of connections; can allow connections initiated from inside
	distributed firewall: centrally configured software on all machines that enforces firewall rules
	you can make a sort of DMZ... quarantine zone... between two firewalls where you can look at files from the Internet. this is called an application-level gateway