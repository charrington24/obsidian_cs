#dbms 
#neo4j 
#plug_power 
#cypher 
#graphs 

###### Merging nodes
- either matches pattern entirely or creates a new instance; no partial matching
- individual nodes can be merged with a label, with properties
- can also make new nodes based on some existing property
	```cypher 
	MATCH (n:Label)
	MERGE (m:NewLabel {name: n.someProperty})
	```
	- this creates a new node of type NewLabel for each distinct value of the property

###### create/match
- can specify what to do if the instance is created vs if it's matched using:
	```cypher
	MERGE (n:Label {name: 'foo'})
	ON CREATE
		// code to execute if pattern created
	ON MATCH 
		// code to execute if pattern matched
	RETURN //whatever
	```

###### relationships
- to create a relationship with merge, one source node must be specified (can use MATCH to do this)
	- the other node can also be specified or can be pattern matched i think
	```cypher
	MATCH 
		(guy:Person {name: 'specificGuy'}),
		(n:Label {properties})
	MERGE (guy)-[:RELATED]->(n)
	```
- useful if you want to simultaneously create a new node and link it to another node 