
#distributed_systems 
Google has internal RPC system- called Stubby
### RPCs 
- RPCs just black box the remote execution 
- can technically be on the same machine, as long as the address spaces are different 
- client calls function, which calls **client stub**. Stub packages message for OS, which sends message to remote OS. Remote OS gives to remote stub, which calls server
#### parameter passing for RPCs: 
- client and server may have different data representations, so they must agree on encoding
- copy in/out (can't assume parameter values while procedure executing)
- can't pass references to global data
- so tldr you can't have full access transparency
#### in practice 
- you want the RPC runtime to locate the server rather than the client having to hardcode it
- this is handled by a directory server if client to server binding- older transparent implementation. This is a DCE (distributed computing environment)
- on Linux, rpcinfo command inquires what services are run locally - port list
![[Screenshot_20240129_171434_Canvas Student.jpg]]