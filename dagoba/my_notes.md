## Preview notes
**Problem definition**: Design a highly usable graph database with high code reusability.

#### Design considerations
* **Usability** - the graph database should be easy to pick up and query from
* **Reusability** - the code should be compact

#### Design constraints

## Reading notes
#### Overview

#### Build a Better Graph
* Uses simple data structures, edge list, vertices list and vertexIndex map for lookup optimization
* Let users provide a vertex-like object to add to the graph
  * object must have id, in-edges and out-edges
  * this reduces space by avoiding needing to create a Node impl object 
  * if a specific Vertex instance was accepted then the user could use a pointer to manipulate it at runtime and break invariants

#### Enter the Query
* Since a query goes through a series of transformations, we'll want to follow the data's state at each transformation step
  * this implemented with an array of gremlins (data's state at each step) and an array of executed functions + args
  * this will help with debugging and reproduction

#### Ramifications of Evaluation Strategy on our Mental Model
* Keep a simple mental model for the users
  * but we may need to think about switching to a more complex mental model for better performance
* Some factors to wrestle with the above decision is
  * the cognitive difficulty for learning the simple vs complex model
  * amount of additional cognitive load to first learn the simple then the complex model 
  * the subset of users required to make the transition

#### Pipetypes
* Allowing runtime modifications of existing pipetypes
  * Good if users want to iterate on their pipetypes, Bad if it isn't common b/c it's prone to human errors
  * I think it will be fine as long as we add a warning for potential human errors 
* Too little structure and the mental load is high, too much structure and the cost for boilerplate and abstraction complexity is high
  * high structure is better for greater number of moving pieces 
* We might want to continue the query after an error has been encountered because 
  * it gives the users some relevant result that the programmer can fix
  * and we want to avoid presenting a grave error message for web apps

#### Query Transformers
* Greedy local optimizations may make more impactful global optimizations unavailable
  * As software design should be, iterate and add optimizations if necessary (after impl simple code) 
#### Requirement statisfaction

Questions
* What is this prototype inheritance?
* Why do we need unique refefences?
