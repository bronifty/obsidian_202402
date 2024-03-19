# Patterns that Matter

1 Fundamentals of Software Architecture
### cohesion, coupling, kanaisance
#### cohesion
- definition: to what extent parts of a module should be contained together (how related the parts are in a module); attempting to divide a cohesive module would result in increased coupling

##### range of cohesion:
	1 functional: module contains everything and nothing but what it needs to function
	2 sequential: modules interact where one outputs data that becomes input to another
	3 communication: modules participate in a comms chain where to contribute to some output (eg add db record and send email update about it)
	4 procedural: modules execute in a particular order
	5 temporal: modules are related based on timing dependencies (eg docker compose web app depends on db)
	6 logical: modules data are related logically but not functionally (eg util package for operating on a data type; they all logically work on the same thing, but are otherwise unrelated)
	7 coincidental: parts in module only relate in that they exist in the same file