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

there are four measurements of architecture: 
1 LCOM 
- LCOM measures the extent to which methods of a class share instance variables
2 abstractness
- abstractness is a ratio of abstract methods to the total number of abstractions + implementations 
3 instability
-  instability is a measure of outward coupling 
4 distance from the main sequence 
- distance from the main sequence is an X Y axis measuring abstraction and coupling with abstraction on the Y axis and coupling on the X axis; in the top right hand corner, you have pure abstraction plus coupling in the bottom left-hand corner you have zero abstraction zero coupling


> Cyclomatic Complexity 
> - cycle refers to graph of control flow in a program
	- more paths through the code base means harder to understand
	- essential v accidental
	- governance and fitness functions (to test the above)

> Kanaisance
> - how things must be changed together (coupling)
> - static v dynamic

### Static Kanaisance
- range of kanaisance (from best to worst coupling)
- name
	- update all variables/methods with the same name - easy to change
- type
	- update all types of methods/variables
- meaning
	- hardcoded numbers rather than constants (eg true is 1 and false is 0)
- position
	- function arg position
- algorithm
	- security hash that must run on both server and client to produce identical results to authenticate the caller

Dynamic Kanaisance
- execution
	- order of execution (eg code that sends an email needs to have subject line set first)
- timing
	- timing of execution (eg race condition between 2 competing threads)
- values
	- several values relate and must change together (eg distributed systems transactions; multiple databases must be updated together)