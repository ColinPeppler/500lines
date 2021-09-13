## Preview notes
**Problem definition**: Implementing a protocol to support reliable computation on a distributed system. With a concrete example, if you transfer money to another person and the server hosting your account withdrew the money but the server hosting the other account failed then this is unreliable.

#### Design considerations
* **Reliability** - the system should be able to avoid computation failures as much as possible throughout its lifespan
* **Accuracy** - the should should be able to execute the computation perfectly

#### Design constraints
* **Reliability** - failures must be prevented 

## Reading notes
##### Deterministic State Machines
* If servers use local state to perform operations then there can be race conditions. 
* The solution is to use a **distributed deterministic state machine**.

#### Consensus by Paxos
* Simple Paxos (or Synod protocol): a way for servers to agree on a single value
  * Guarantees that there will be no conflicts on a consensus since it's a distributed state machine 
* Multi-Paxos: a way for servers to agree on a numbered sequence of values, one at a time.

#### Requirement satisfaction
* **Accuracy** - a Deterministic State Machine will always produce the same output given the same input

