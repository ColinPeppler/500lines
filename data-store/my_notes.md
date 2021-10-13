## Preview notes
**Problem definition**: A data store that has atomic transactions and guarantees the durability of the data (remains safe even in the case of failures).

#### Design considerations
* Correctness - other developers will use this system as a data store for their application
* Usability - the interface should be simple to use

#### Design constraints
* Usability - keeping the interface simple will dictate the design of the system

## Reading notes
#### Organisational Units
* modules are listed in order of what program the user will likely need to know more about
* note each class has a single responsibility
* `tool.py` - a CLI for exploring a database
* `interface.py` - a module that provides the database class for access in a py program
* `logical.py` - logical layer; abstraction for a KV store
  * `LogicalBase` - API for logical updates such as get(), set() and commit()
  * `ValueRef` - a Python object to reference a binary blob in the database
* `binary_tree.py` - concrete binary tree algorithm below the logical layer
  * `BinaryTree` - concrete implementation of a binary tree
  * `BinaryNode` - concrete implementation of a node in a binary tree
  * `BinaryNodeRef` - specialized `ValueRef` that can ser/deser a `BinaryNode`
* `physical.py` - physical layer
  * `Storage` - provides persistent and (mostly) append-only record storage    

#### Requirement statisfaction
* Correctness
  * Atomic operations - Customers will only see the data of an old tree or the new tree, never the data of a mix between the old tree and new tree. 
    * This makes commits atomic b/c customers can't read partial changes only full changes.
    * Also, data of a new tree is written to disk before the address of the root of a new tree is published.
  * Durability - Once the address of the root of a new tree is published, then we can ensure the data is on disk already since data was written to disk before the address update.
  * the best way to test correctness is to test the interface not the implementation
* Usability - The user will only need to interact with the CLI or database module; the implementation is abstracted away.
