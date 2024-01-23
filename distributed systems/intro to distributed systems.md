#distributed_systems
#lecture 
#csce438
#networking 
Formal analysis: 
	![[Pasted image 20240122164210.png]]
	response time: total time to process request after submission
	![[Pasted image 20240122164232.png]]

Scalability
	- geographical scalability
	- we can hide latencies from the user: async functions (think callbacks)
	- can move some computations to client- similar to **edge computing**, where computations are moved to the "edge" of the cloud layer
	- DNS and WWW are both decentralized- good for spreading computation around
	- replication problem: having a lot of caches/copies of data leads to inconsistencies, so **global synchronization** is needed if inconsistencies can't be tolerated

Pitfalls
	false assumptions: 
		network is reliable, secure, homogeneous, topology doesn't change, latency is zero, bandwidth is infinite, transport cost is zero, etc

Types of distributed systems:
	- parallel computing was the start of high performance distributed computing
	- cluster computing: group of high-end systems connected via LAN
	- grid computing: many nodes, dispersed across organizations/large area. uses **virtual organizations** to manage resource allocation etc
	- cloud computing: lots of virtualization. very heavy on computation
	- middleware and EAI: middleware manages various server applications. simplifies job of clients
		**remote procedure calls (RPCs)**: requests sent as local calls, packaged as messages, processed, returned to client, and result of server computation is returned as the result of the original function call. This is an easier alternative to sockets
		**message oriented middleware (MOM)** client pushes message to middleware and middleware takes care of actually delivering message
	- distributed pervasive systems
		- new next gen distributed system paradigm- nodes are small, mobile, embedded in larger systems, and blend into user environment. think phones, IoT devices, etc. Silicon valley plot point
		- three types:
			- ubiquitous systems: devices accessible transparently, continuously present, unobtrusive to user
			- mobile computing: location is likely to change over time. unstable but disruption-tolerant. messages can be passed between network of "friends" **discovery** is an important concept here- how to build your community without global knowledge? 
				- j gets added to i's community when j's familiar set has a lot of overlap with i's community (about 60% is good)
				- two communities can be merged if their intersection/union passes some threshold
				- ![[Pasted image 20240122170239.png]]
			- sensor/actuator networks: many small power-restricted nodes
