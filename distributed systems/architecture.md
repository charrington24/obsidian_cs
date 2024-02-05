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