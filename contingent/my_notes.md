## Preview notes
**Problem definition**: To precisely rebuild documents from source with the fewest amount of build operations.

#### Design considerations
* **Accuracy** - must produce the correct output with no error
* **Efficiency** - require minimal time to rebuild the document

#### Design constraints
* **Efficiency** - need to ensure we're using the fewest amount of build steps

## Reading notes
#### Overview
* The idea is to represent rebuild steps as tasks in a graph.
* To rebuild a document, we'll only execute the required tasks.

#### Representing the build task as a graph
* Downstream tasks for a node are on the other end of the node's outgoing edges
* Upstream tasks for a node are on the other end of the node's incoming edges

#### Learning operation dependencies using a stack
* See a new task then:
* Add a dependency edge between the new task and the task from _stack.top()_
* Add new task to stack; _stack.push(new-task)_
* Execute task

#### Finding dependencies
* Using DFS + Topological sort we can have a great illustration of the dependency graph
* Use a cache to avoid re-computation of tasks that will produce the exact same output with the exact same input
  * _get_dependencies()_ will return the task and its dependencies
  * _todo_ is a set of tasks to re-execute (only marked if at least one of the task's inputs have changed)
  * _cache_ is a dict of <task-name, return value (eg. string> (only works for deterministic tasks)

#### Requirement statisfaction
* **Accuracy** - Using the stack we can find the exact dependencies between each task, this will ensure the necessary tasks are executed upon a build operation
* **Efficiency** - For fast upstream/downstream tasks look-up, incoming edges and outgoing edges are stored in separate data structures. This redundancy enables O(1) look-up.
