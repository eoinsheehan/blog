# Practical Object-Oriented Design: An Agile Primer Using Ruby - Sandi Metz

When presented with a blank page (or the dev equivalent of an empty project) I found myself somewhat stuck. While I’ve come to learn to say no to inertia and move forward in the best way I knew how I still felt that there was something missing.

What was missing was actually very apparent. A complete lack of practical knowledge for developing in an object oriented paradigm. I was fully aware of the principles of OOP, and well capable of working in an existing codebase, but when I was staring at a blank sheet of paper before me it was a different story.

That’s the state of affairs that led to me seeking, finding and reading Practical Object Oriented Design by Sandi Metz. Why this book? I’m working in ruby and it came well recommended by trusted senior colleagues as well as on the ultimate source of truth that is Reddit.

As with all of these notes they are as much a reference for myself as for public consumption. A means of documenting my learnings in public and encouraging myself to build something useful at the same time. - move this to a more generic about page or whatever.

I really liked how Metz makes it clear that as a junior dev starting out you will attempt to implement the guidance in the book incorrectly and in the wrong place but that over time these somewhat subjective skills will be fine tuned.

Ok that’s enough of a background let’s jump in to what I learned…

The following is a breakdown and distillation of the main points that I took note of in the book which I hope can provide a good reference for improving my Object oriented design.


## Art vs Science - Motivation
There are many points at which you can make decisions which have consequences for the future.
Given this it is better to make bigger decisions from a place of greater knowledge.
For example - the case with the switch statements for splitting out into dedicated class
While there is flexibility in decision making following guiding principles such as those set out in this book is more likely to be a good thing than
not having anything to follwo
These techniques have been shown to improve performance in tests which measure the quality of code

## Object oriented design
- Provides a blueprint for the construction of similar objects
- Methods get invoked in response to messages.
- Ruby comes with a number of predefined classes e.g String, Hash, Array
- The foundation of an object-oriented system is the message

However the design emphasis will shift from classes to messages w
The classes you create will affect how you think about your application forever.
- They define a virtual workd
- The consequences of change should be obvious - Make a more informed decision

## Dependencies ( related to "D" in SOLID of Dependency Inversion )
### Unmanaged dependencies
This is such a key thing as it will affect the ability for you to iteratively improve the design of the application.
- objects know too much about one another
- changing one forces change in another
- which results in inertia.
- when objects know too much they have expectations about the world in which they reside
- Isolate dependencies
- A step on this road was achieved by moving from a data structure to using a Struct to portray an object.
By doing this it will make it easier to identify where changes can be made when the time arrives
Look to simplify the dependency. Depending on an instance variable is bade but depending on a complicated data structure is worse.
e.g. needing to know the index of an array at which data is stored
When you have data in an array, it’s not long before you have references to the array’s structure all over. The references are leaky.
They escape encapsulation and insinuate themselves throughout the code.

You can use a method to wrap an instance variable you can also use a Ruby Struct to wrap a structure
A struct is a lightweight means of moving towards a dedicated class. It gives you accessors out of the box.
dependency injection
with dependency injection the depedency is on something more abstract i.e. that an object responds to a message rather that a particular class.
The following highlights that point rather well...
- One of the benefits of using an interpreted language is that the dependency is on a class that implements an interface which is much more flexible
- If you are mindful of dependencies and develop a habit of routing injecting them, your classes will naturally be loosely coupled
If you let class references fall where they may then your classes will resemble a woven mat rather than independent objects.
Need to keep things loose and flexible to make it easier to complete the enivatable refactoring without a terribly high cost.
- Quarantine dependencies.
- subtle dependency - order of arguments
- look to use keyword arguments to remove this dependency
- keyword arguments may be passed in any order and there is a description of parameters with the sender as well as the receiver (where the method is defined)

## Single Responsibility ( "S" in SOLID )
A class should be cohesive in that everything the class does should be highly related to its purpose
- Methods, like classes, should have a single responsibility.
by keeping single responsibility with methods will assist when the time comes to make a new class.
There is a link between single responsibility and dependencies.
By virtue of the fact that classes have a single responsibility they will have to communicate with each other.

## Abstraction
The wonderful thing about abstraction is that they represent common, stable qualities.
Abstractions by their very nature tend to have many dependencies but will not change very much
Duck typing reveals abstractions that may otherwise not be visible
  
## Interface Segregation ( I in SOLID)
The conversation between objects takes place using their interfaces;
In Solid principles the "I" stands for interface segregation. i.e. that larger interfaces should be split into smaller ones
Deciding on the messages that an object public responds to should be carefully considered.
The more messages that it responds to, the more that can be sent to it and, back to our friend of dependencies once more, this will make things more likely to get out of hand.
- Interfaces should reveal it's primary responsibilies, and that in itself should encompass a Single responsibility
- private interfaces on the other hand handle implementation details which the sender does not need to know
- public interfaces should be throughly documented in tests.
"You don’t send messages because you have objects, you have objects because you send messages."
- in line with the public interface framing the sender should not be concerned with the internal implementation details rather that they get what they want at the end.

## Techniques to use
### making a change
- Making a change - the cost of any change should be proportional to the benefits the change achieves
- if you could tell what the future would look like then you would make the perfect design decisions today.
- but you don't so don't get too caught up or attached to making the perfect design decision.
Ok and then this is a key one really - when the future cost of doing nothing is the same as the current cost, postpone the decision
Even though I had read this book I still have to bring myself back to this when trying to implement some of the findings.
It is all well and good to be aware where changes could be made to improve things but if the future cost is the same as the current cost then postpone.
You will probably have greater context with which to make a more informed decision in the future.
well-known techniques that you can use to create code that embraces change.
DRY code tolerates change because any change in behavior can be made by changing code in just one place.
- Good practices reveal design
- Avoid the need for comments where possible - look to move this into it's own method
- The code is not perfect, but in some ways, it achieves a higher standard: it is good enough.
- Referring to a class by it's name creates a coupling.
as an alternative could this be passed in the message to the class but rather than being tied to the object 
only be concerned if it responsds to certain messages.
- When a class has many dependents alarm bells should be ringing.
note: - there is like a formula mentioned at some point in reference to this kind of thing.
you want to be in a space where the things that change a lot do not have many dependencies.
this is far more important than if there are more dependencies in classes that do not change all that much
- Isolating dependencies allows objects to quickly adapt to unexpected changes, this seems like it can be the first step to prevent having references to other classes 
scattered throughout your definition of the object.
- Injecting dependencies creates loosely coupled objects that can be reused in novel ways as the dependency can be on a class implementing an interface.
- Depending on abstractions decreases the likelihood of facing these changes as these classes tend to be more stable.
- Approach the design of the application from the point of the messages that are being passed not the real world objects that may be easier to concieve.
- Either do not test private methods or, if you must, segregate those tests from the tests of public methods.
- Strongly consider when chaining methods together to stay in line with the Law of Demeter ("only talk to your neighbour")
- violations of the law of demeter are an indication that your public interfaces are lacking
- You can replace the following with ducks:
   - case statements that depend on class
Inheritence is a specialisation
- User inheritance for is-a relationship
- Use duck types/modules for behaves-like-a relationship
   - if it the implementations have many common features then modules can be used to share this across clases.
   - Ruby's version of multiple inheritance I suppose.
- Use composition for has-a relationship


## Notes
#### Struct vs OpenStruct 
Struct is more primative and and give you a quick means of defining a class
Struct attributes are only defined at instantiation whereas OpenStruct is able to continue to be interacted with.

#### Dependency injection
- The instance is passed to the object rather than being created within the class.
This makes it easier for testing

#### Public/Private/Protected
this is mildly interesting
Protected methods allow explicit receivers as long as the receiver is self or an instance of the same class or subclass of self.
implicit receiver is self which is the reference to the class which is in scope in that point in the application.

#### Monkey patching 
Making changes to base classes - normally to be avoided
