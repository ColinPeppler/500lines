These are my notes for this book. I will focus on the design decisions and tradeoffs made in each project to improve my ability to make the same decisions when creating systems myself.

For each chapter I read, I should:
1. Identify design considerations & constraints
2. Create a high level architecture diagram (before and during)
3. Identify anything that surprises me as I read

## Design characteristics
### External characteristics
* Correctness: degree to which a system matches its specification
* Usability: easy which users can use & learn
* Efficiency: minimal use of resources
* Reliability: long delta (in times) between failures
* Integrity: prevent unauthorized access
* Adaptability: extent a system can be used in other systems
* Accuracy: free from error; how well it does its job (think of ML accuracy)
* Robustness: the extent system handles invalid inputs and stress

### Internal characteristics
* Maintainability: easy a system can be modified
* Flexibility: extent to modify a system for another use case
* Portability: easy to modify to use in another environment
* Reusability: extent parts can be re-used
* Readability: ease to read/understand code
* Testability: degree to unit and system test the requirements
* Understandability: easy to comprehend logic
