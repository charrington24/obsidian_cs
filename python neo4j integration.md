#neo4j #cypher #python 
###### driver() function
```python 
	SpecificDatabase.driver(connectionString, auth=, [additional])
```
arguments:
- connection string
	- 
	```python 	
	scheme://initial server address:port?additional
	```
	- scheme:
		- neo4j: unencrypted connection
		- neo4j+s: encrypted connection and verifies certificate
		- neo4j+ssc: encrypted but doesn't verify certificate
	- address is for the DBMS
	- port (part of address) required if not default 
- authentication method
	- usually just username and password
	```python 
	auth = (username, password)
	```
- optional additional config