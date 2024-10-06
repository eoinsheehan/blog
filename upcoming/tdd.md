# TDD

Technically we do BDD with RSpec I think.

Chat about the features of RSpec.
- The types of test we look to write
Model, request and feature tests should have you coverred
- I could also do with discussing the use case of FactoryBot vs Mocking of objects using the double and instance_double methods of rspec-mocks.

Questions:
- Why request specs are preferable to Controller.
controller tests test the controller in isolation without sending http request (and there is a couple of other things too..)
- What is the difference between stubbing and mocking
   - when to use the above (i.e. if it
- What is the difference between double, stubbing and mocking?
   - It seems like stubbing and mocking are sub types of a test double
- difference between double and instance_double in rspec?
double is needed in two cases:
1. The object doesn't yet exist in the system so there is no instance_double to rely on.
this could be suitable for cases early in development when the class is not yet fully defined.
- when to use stubbing over mocking?

## Mocking
Using the rspec-mocks gem gives access to these.
Allows to test an object without testing the behaviour of dependencies.

## Method stubs
A method stub is an instruction to an object (real or test double) to return a specific value in response to a message. 
- Can be good  to check that a dependent object is receiving the expected parameters also.

Working on my current story adding an endpoint to the api:
- What is the use of double?
mocks and stubs are each special types of test doubles.
For example think of a stunt double. It is meant to be able to do a specific behaviour of the actor.
Similar can be said for the test double. It can carry out specific actions of the actual object.

instance_doubles are known as verifying doubles.
- they do some checking against an actual instance of the object.
- they will throw no method error in the instance_double

Random
- There metadata available on each example e.g. where the test is invoked and the description
- The described class is the class which has been labelled in the RSpec.describe method.
- RSpec has a number of gems on offer e.g. rspec-core rspec-rails and rspec-mocks.

Sources:
This had the good analogy for test double
https://www.honeybadger.io/blog/rspec-mocks/

struggles:
Today I found that I was trying to encapsulate some things in a factory which just added to the confusion.
In this instance it seemed that being a little more verbose was more valuable

I just discovered what the .rspec file does so I should mention that and it just slightly cleans up writing the rspec files

also I think there is an option for a .rspec-local file which could be added to the .gitignore file and have like nice personal config.


