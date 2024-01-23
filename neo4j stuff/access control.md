
#neo4j 
#dbms 
#cypher 
#graphs 
#cybersecurity
#infosec

##### overview
- there's [[rbac]] (role-based access control), but you can further fine-tune it 
- you can GRANT roles/priveleges to users, and also priveleges to roles (or public, which is everyone)

###### grant:
- syntax:
	```cypher
	GRANT privelege ON {GRAPH(S) {* or *[list of graphs]}} [entity] TO role[]
	```
- can be a single graph (for any graph u just refer to it by its database name btw), a list of graphs by name (formatted in brackets), or all graphs (\*). 
- entity can specify certain elements in a graph
	- this would be: NODES label, RELATIONSHIPS type, or ELEMENTS label (for nodes and relationships)
	- \* means all and u can include multiple if u use comma
- stuff u can grant:
	- [[access privileges]]

###### commands, generally
- GRANT:
	- give a permission 
	- like a whitelist
- DENY:
	- deny a permission (does not negate an already-granted permission!!!)
	- like a blacklist
- REVOKE: 
	- undo (revoke) a granted or denied permission
	- can be REVOKE GRANT or REVOKE DENY or just REVOKE if u don't wanna specify

###### questions i have
- how do you allow a user to see their own data (just the one user) but not all users?
	- maybe have username as a property of a user node. have each users home node (is this a thing you can do? i know u can have home databases but idk about home nodes) be their personal node; have this visible to them and nothing else
	- could maybe also do it by granting access if user id = n.username and denying access otherwise? 