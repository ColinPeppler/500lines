## Preview notes
**Problem definition**: Schedule a set of jobs (a job is a series of tasks) on a set of machines (1st machine can do task 1, etc.) s.t. the time to complete all jobs is minimized.

#### Design considerations
* Efficiency - we need to define an algorithm that work with large N
* Usability - how can we verify the solution is a good solution

#### Design constraints
* Efficiency - need an efficient algorithm

## Reading notes
#### Flow Scheduling Problem
* a permutation of the jobs is a candidate
<img src="flow-shop/flow-shop-images/example1.png">
<img src="flow-shop/flow-shop-images/example2.png">

#### Local Search
* Job: solve intractable optimization problems where the optimal solution is too hard to compute
* Intuition: Move from one good solution to another solution that's better
* A **neighborhood** is the set of solutions similar to the current solution
* Since a permutation of jobs is a candidate solution, simply shuffling the jobs around is a way to explore the search space. More formally we should ask:
  * Where should we start?
  * What neighboring solutions should be considered?
  * Given a set of candidate neighbors, which one should we consider moving to next?

#### Neighborhood
* Job: returns a set of candidates
* Random - adds exploration into the search space at the cost of possibly illogical candidate selection
* Swap 2 jobs - candidates are closely similar to current solution
* Permutation of top k most idle jobs - Sort by idle time, compute permutations of the top k most idle jobs
  * considered Large Neighborhood Search (LNS) since it can find more neighborhoods by compution a permutation on a small subset in isolation
  * use a parameter to limit the number of permutations to search through   
  * the candidates are only the top k most idle jobs (only a subset of the current solution)

#### Heuristic
* Job: evaluates a set of candidates and returns the selected candidate
* Random - randomly pick a candidate
* Lowest timespan first - pick candidate with lowest makespan
* Random + Lowest timespan - pick best candidate 50% of the time, second best 25% of the time and so on
  * Introducing randomness allows us to be more open to explore the search space 

#### Dynamic Strategy Selection
* Pick a permutation of the neighborhood and heuristic strategy dynamically throughout the solving process
  * can use Roullette Wheel Selection Genetic Algorithm to select a permutation that's biased towards high performing strategies
  * strategy value is calculated by `strategy improvement / strategy time-spent` and weight is added according to the value
  * unused strategies need to be bumped up periodically since a strategy may perform better later in the search

#### Requirement statisfaction
* Efficiency - the algorithm can mix and match strategies to dynamically select a strategy that will maximize improvement and minimize time spent but also open to exploring the search space
* Usability - the solver prints solution stats and makes it easy for the user to run the solver (minimal program arguments and parser interaction)
