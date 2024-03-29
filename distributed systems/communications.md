#distributed_systems 
#networking 
#communication
- basic networking model: iSO model described in [[basic networking]] 
- why is the layer model so fragmented? 
	- allows you to plug and play- can mix wired and wireless layers
	- internet "bottleneck" is IP- all of internet uses this protocol
	- implemented by prepending a header to the payload received by layer above
- drawbacks: extra functionality, violates access control 
- we'll be most exposed to the **transport layer** in dist systems. TCP and UDP are the protocols used here
	- TCP: connection-oriented, reliable, stream
	- UDP: unreliable, best-effort
- where do sockets live? between the **session** and **transport** layers
- transport, network, data link, physical layer are all in kernel space, not user space (because they touch hardware)
- **middleware** lives above transport layer
	- provides common services/protocols that can be used by different applications
- adapted layering scheme:
	- application (application level protocol)
	- middleware (middleware protocol)
	- OS (host-to-host protocol)
	- hardware (physical/link-level protocol)
- client/server is transient and synchronous
	- client issues req and blocks until it gets reply
	- drawbacks: failures have to be handled immediately, client gets blocked, may not be ideal
- message-oriented-middleware
- see [[remote procedure calls]]
- need to understand synchronous/asynchronous and transient/persistent
