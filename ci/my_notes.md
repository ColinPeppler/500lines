**Problem definition**: Testing new code changes in a distributed, accurately and robust manner to ensure the changes will not break production servers.

#### Design considerations
* **Accuracy** - this system should be able to consistently determine whether a commit will or will not break tests
* **Robustness** - if failures occurs, the system should be able to recover and continue testing new commits
* **Efficiency** - the system must be able to handle many commits at once to avoid being a bottleneck in the push process

#### Design constraints
* **Efficiency** - handle high load well
* **Be fast** - quickly return tests results
