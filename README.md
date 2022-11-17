# Orphanet_hierarchies_service API
Service dedicated to support implementation and usage of Orphanet's classifications

This API focuses on Rare diseases classifications based on ORDO (Orphanet Rare Diseases Ontology)

A clinical entity (group of diseases, disorder or subtype), for which an ORPHAcode exist, could belong to several medical domains (classifications)

This service help to navigate from an ORPHAcode throught the levels of classifications

### API parameters
{ORPHAcode} : an ORPHAcode of a clinical entities as a node to start with (Mandatory)
IRI or code are accepted. 
ex:
/traverse?code=http://www.orpha.net/ORDO/Orphanet_558 
/traverse?code=558

{way} : from the node, path to levels. Expected 'up' (to "parents"), 'down' (to "childs") (optional. Without, retrieve +1/-1 from node)
/traverse?code=558&way=down will return for each level, all the descendants of the specified Code

{level} : level to reach from the ORPHAcode as starting point (optional. Without, return all available levels)

{classif} : specify 1 to n Orphanet classifications ID to traverse (optional. Without, return results from all classifications)

Supported Classifications list:
/ClassifTraversal/hierarchies/list


### Set of examples
Endpoint:
[http://155.133.131.171:8080/ClassifTraversal/hierarchies]

Supported Classifications list:
/ClassifTraversal/hierarchies/list

ex: ORPHAcode 558 (Marfan syndrome)
http://155.133.131.171:8080/ClassifTraversal/hierarchies/traverse?code=http://www.orpha.net/ORDO/Orphanet_558
http://155.133.131.171:8080/ClassifTraversal/hierarchies/traverse?code=558

http://155.133.131.171:8080/ClassifTraversal/hierarchies/traverse?code=558&classif=199&classif=189
(Marfan Syndrome starting node, 2 classifications used)

http://155.133.131.171:8080/ClassifTraversal/hierarchies/traverse?code=558&way=down
(Marfan Syndrome starting node, way down)

http://155.133.131.171:8080/ClassifTraversal/hierarchies/traverse?code=558&way=up
(Marfan Syndrome starting node, all the ascendants of the specified Code.)

http://155.133.131.171:8080/ClassifTraversal/hierarchies/traverse?code=558&way=up&level=3&classif=199&classif=189
(Marfan Syndrome starting node, way up to 3 level max, through 2 classification


