
#dbms
#neo4j
#cypher
#graphs

see also: [[general database concepts]] and [[access control]]

###### making a basic object:
```cypher
CREATE (name:type {properties})
```
- property formatting: property_title:'value', other_title:'value'

###### constraints: 
- can limit property values
- referenced via label
```cypher
CREATE CONSTRAIN ON (n:Label) ASSERT (n.property) WHATEVER
```
- whatever can be UNIQUE 

###### indexing:
```cypher
CREATE INDEX FOR (n:Label) ON (n.property)
```

###### finding nodes:
```cypher
MATCH (n:Label) RETURN n 
```
- this will return all nodes w label
```cypher
MATCH (n:Label {property: "value"}) RETURN n 
```
- will return all nodes w specified property
- can limit number of nodes returned w LIMIT num clause at end (only returns num # of nodes)
```cypher
MATCH (n:Label) WHERE condition RETURN n 
```
- self-explanatory
- can also limit what gets returned:
```cypher
RETURN n.property
``` 
- only lists the property, doesn't return the whole node
- all of these only deal w nodes so far not relationships

###### relationship queries:
```cypher
MATCH (n:Label {properties})-[:relationship]->(ns) RETURN n, ns
```
- this will map out all nodes n w the property and nodes connected via relationship

###### connections w edge weights/shortest path:
```cypher
MATCH (n:Label {properties})-[*n..m]-(toReturn) RETURN DISTINCT toReturn
```
- this will return all nodes between n and m edges away from the node(s) n. the distinct modifier just prevents repeat returns 

###### shortest path
- shortestPath() is a built in feature
```cypher
MATCH p=shortestPath(n:Label {properties})-[*]-(m:Label {properties})) RETURN p
```
- returns shortest path between nodes n and m
- this is a type of [[functions]]

###### merge
- pattern matching; either finds (MATCH) or creates (CREATE) a pattern to match the one specified
- [[merge]]