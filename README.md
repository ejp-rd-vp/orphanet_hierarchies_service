# Orphanet_hierarchies_service API
Service dedicated to support implementation and usage of Orphanet's classifications

This API focuses on Rare diseases classifications based on ORDO (Orphanet Rare Diseases Ontology)
A clinical entity (group of diseases, disorder or subtype), for which an ORPHAcode exist, could belong to several medical domains (classifications)
This service help to navigate from an ORPHAcode throught the levels of classifications

### API parameters
{ORPHAcode} : an ORPHAcode of a clinical entities as a node to start with (Mandatory)
{Depth} : level to reach from the ORPHAcode as starting point (optional)
{path} : from the node, path to levels. Expected 'Ascendant', 'Descendant', 'Inferred'

Returns: "level" (rank from the ORPHAcode node, optional),"parents" / "childs", "OrphaCode= {value}, Name= "{label of clinical entity}"
Expected input:
http://155.133.131.171:8080/Mapper/{path}/{ORPHAcode}/{Depth}

### Set of examples
http://155.133.131.171:8080/Mapper/Inferred/{ORPHAcode}
ex: ORPHAcode 558 (Marfan syndrome)
[http://155.133.131.171:8080/Mapper/Inferred/558]
return both parents/childs of this ORPHAcode, based on inferrence from ORDO

http://155.133.131.171:8080/Mapper/Ascendant/{ORPHAcode}
[http://155.133.131.171:8080/Mapper/Ascendant/558] 
return all levels of "parents" 

http://155.133.131.171:8080/Mapper/Ascendant/{ORPHAcode}/{level}

[http://155.133.131.171:8080/Mapper/Ascendant/558/2]
return "parents" of the node to level 2 max.

http://155.133.131.171:8080/Mapper/Descendant/{ORPHAcode}
[http://155.133.131.171:8080/Mapper/Descendant/558] 
return all levels of "Childs" 

http://155.133.131.171:8080/Mapper/Descendant/{ORPHAcode}/{level}

[http://155.133.131.171:8080/Mapper/Descendant/558/2]
return "parents" of the node to level 2 max. (only level 1 is available in that particular case)
