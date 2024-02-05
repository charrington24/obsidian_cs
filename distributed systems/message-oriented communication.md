#distributed_systems 
#communication
### Message-oriented communication
- NOTE: TODO: missed lecture on 1/31. Go back and fill in notes form remainder of lecture 3 slides (more detailed stuff on RPCs, sockets, DCE, request-reply, pipelines, publish-subscribe)
- **MPI (message passing interface)**- advanced transient messaging
	- mostly used when high-performance computing is needed
- **AMQP (Advanced Message Queueing Protocol)**
	- exchanges accept messages from producers and route them to queues
	- binding decouples message from producers and has rules for routing to destination queue
	- message queues are bound to an exchange and exist until used up by client
	- connection: physical TCP between client and producer. has many channels
	- channel: virtual conduit between client and broker
	- routing strategies: direct, fanout, topic, header. all use different algorithms
	