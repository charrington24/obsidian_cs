
#dbms 
#neo4j 
#cypher 
#graphs 
#infosec 
#cybersecurity 

###### read privileges:
- TRAVERSE
	- ability to go from one node to the next. necessary to view relationships. 
	- allows u to find some entity
- READ 
	- ability to actually view an entity's properties
- MATCH
	- combo traverse and read (u can find stuff and read it)

###### write privileges:
- CREATE
	- make nodes and relationships
- DELETE
	- delete nodes/relationships
- SET LABEL
- REMOVE LABEL
- SET PROPERTY
- MERGE
	- combines match, create, and set
- WRITE
	- all write operations
- ALL GRAPH PRIVILEGES
	- all read/write operations