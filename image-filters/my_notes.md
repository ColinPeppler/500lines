## Preview notes
**Problem definition**: A user friendly application to visualize and create custom image filters

#### Design considerations
* Usability - the app must be simple to use

#### Design constraints
* Usability - will dictate the design of the application
* Testability - there will be limitations to balance usability and testability

## Reading notes
#### Overview
* Integration testing is used to test connected components
* To test a class that can't be tested directly, create a thin wrapper class to mock
  * Could have made a heavier wrapper class but it's intentionally lightweight since usability is the priority 
* Classes should be immutable unless there's a good reason to be mutable
* Prototyping allows you to explain to business partners your ideas and what the app would do

#### Architecture
* `ImageFilterApp` - handles app layout, user interaction and should be as small as possible for testability
* `ImageState` - is the model that stores the image and what levels and filters should be applied to the image
* `ColorHelper` - where the image processing and filtering logic takes place 

#### Requirement statisfaction
* Usability - keeping `ImageFilterApp` as small as possible; only including necessary code for layout and to call the model methods
* Testability - using a thin wrapper class to test encapsulated methods of the model and controller
