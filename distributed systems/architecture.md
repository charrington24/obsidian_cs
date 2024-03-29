#distributed_systems 
#architecture
### Architectural Styles
- Layered Architecture:
	- layer above uses services from layer below
	- Protocol, service, interface
		- layer n locally communicates with layer n on another machine, m with m, etc. 
		- protocol is specified by prepending header info before passing down to layer below
		- each layer reads the header that pertains to it, strips it, and passes it up
	- three-layer view:
		- application-interface layer
		- processing layer- has application functionality without specific data
		- data layer
- Object-based architecture:
	- components are objects and linked via procedure calls
	- can be on different machines
	- objects have states, methods, and an interface
	- encapsulate and offer methods on data
	- RESTful architecture
		- interface is standardized
		- views system as a collection of resources
		- resources can be modified with PUT, GET, DELETE, and POST
		- simple interface means a lot has to be done in parameter space
	- SOAP (simple object access protocol) is alternate to REST
- publish-subscribe architecture:
	- temporal coupling and referential coupling

|  | temporally coupled | temporally decoupled |
| ---- | ---- | ---- |
| referentially coupled | direct | mailbox |
| referentially decoupled | event-based | shared data space |
- example: Linda tuple space
### Middleware organization
- **Wrapper** or **adapter** commonly used to offer up-to-date interface around legacy component
- header files are a form of interface- header file that uses another header file is a wrapper
- if applications and wrappers are directly connected, you get O(N^2) wrappers. wrapping through a broker you only get O(N)
### Centralized organizations
- client-server
- multi-tiered centralized systems:
	- single-tiered: dumb terminal/mainframe
	- two-tiered: client-server
	- three-tiered: each layer on a separate machine
- you can split two-tiered into a lot of different configurations, with varying parts of UI, application, and database levels split between client and server
- edge computing- lots of computation moved to client
### Decentralized organizations
- vertical distribution- divide apps onto three logical layers and run each component from a different layer
- horizontal distribution
- peer-to-peer- all processes are equivalent
- structured P2P: nodes have precise neighbors that they communicate with
	- uses a **semantic-free index**- each data item is uniquely associated with a key. usually use a hash function to get the key
	- P2P system stores those key-value pairs
	- looking up with key k means routing request to node with identifier k
	- ex: chord
		- nodes organized in a ring with an m-bit identifier
- unstructured P2P:
	- each node maintains list of neighbors. overlay is a random graph; edge exists with random probability
	- search techniques:
		- flooding: pass request to all neighbors- request ignored if receiving node has seen it before. Often limited by time-to-live (max # hops) but can be very costly
		- random walk: pass request to random neighbor
- super-peer networks:
	- have **index servers** in unstructured P2P
	- **brokers** can decide where to store data
	- overlay network between superpeers, not weak normal peers