# OOD

I was was at the point in my developer journey where I was comfortable with completing daily tasks in ruby. While I’ve come to learn to say no to inertia, and move forward in the best way I knew how, I still felt that there was something missing.

What was missing was actually very apparent. A lack of practical knowledge for developing in an object oriented paradigm. I was fully aware of the principles of OOP, and well capable of working in an existing codebase, but when I was staring at a blank sheet of paper before me it was a different story.

That’s the state of affairs that led to me seeking, finding and reading Practical Object Oriented Design by Sandi Metz. Why this book? I’m working in ruby and it came well recommended by trusted senior colleagues as well as on the ultimate source of truth that is Reddit.

As with all of these notes they are as much a reference for myself as for public consumption. A means of documenting my learnings in public and encouraging myself to build something useful at the same time. - move this to a more generic about page or whatever.

I really liked how Metz makes it clear that as a junior dev starting out you will attempt to implement the guidance in the book incorrectly and in the wrong place but that over time the application of these principles will become more refined.

The following is a breakdown and distillation of the main points that I took note of in the book which I hope can provide a good reference for improving my Object oriented design.

## OOP 101
Before I get into the details I am assuming a decent level of experience with OOP but the basics will be:
- OOP provides a blueprint for the construction of similar objects.
- The foundation of OOP is a measage based system where methods are invoked by sending messages.
- Ruby comes with a number of core classes predefined such as String, Array, Hash etc.

One of the challenges to object oriented design is that while there is guidance it is still open to interpretation. However it is highlighted that the methods outlined in this book have been shown to improve code quality against a number of reliable metrics. 

## Postponing design decisions

> "When the future cost of doing nothing is the same as the current cost, postpone the decision."

Some advice that was initially surprising was that it can be better to delay design decisions. Even when there are some initial warning signs it can often be better to make a decision from a more informed viewpoint. In an environemnt where you are working towards an unknown future state a useful benchmark could be to be good enough rather than perfect. Then when the time comes to implement best practice this can have a subsequent benefit of revealing good design also.

If the cost of delaying the decision is similar to the cost of changing right now then it is best to delay. A good example of this is if you have a method where the flow of control is managed based on the class of an object.

## Dependencies
The issue that can arise from the delaying design decision for too long is that the costs of change will have become very high. The more dependencies that an object has the more likely it is that changing such an object will be harder. When objects know too much they have expectations about the world they live in. 

### Look to simplify the dependency
> Just as you can use a method to wrap an instance variable, you can use the Ruby Struct class to wrap a structure.

If an object is dependent on the position of an argument in an array then it is highly dependent. Much like the previous suggestion of delaying decision making radical changes need not be introduced immediately and instead a step can be made in the right direction. This could be as simple as wrapping such a structure in a Struct object as opposed to an Array. This is a step towards a dedicated class with a lightweight approach and will make it easier to identify where changes are required when the time arrives.

A logical next step could then be that a dedicated class is required in the future.

### Isolate Dependencies

> "Quarantine each dependency"

Isolating dependencies will keep your code loosely coupled and open to change. The following is a number of ways of achieving greater isolation. Encapsulation will prevent elements of a class from spreading at will. One of the benefits of using an interpreted language is that the dependency is on a class that implements an interface which is much more flexible.
If you are mindful of dependencies and develop a habit of routing injecting them, your classes will naturally be loosely coupled.

Keyword arguments can be used in place of positional arguments which are less likely to lead to confusion as all arguments of the method are visible on the sender as well as thereceiver.

Dependency injection (DI) will remove reference to a class by name which is itself a subtle dependency much like positional arguments.
This will also have benefits in testing as an mock object can stand in for a concrete implementation.

> "If you let class references fall where they may then your classes will resemble a woven mat rather than independent objects"

Its important to be particularaly concious of classes that have lots of dependents and are likely to change.
The following graph provides a good abtract summary of the signs to look out for and equally the cases which are not as worrying. 

-- Insert sketch of graph from book --

The goal is to look to avoid situations in the top right where classes that are likely to change have many dependencies. Whereas all other states are more likely not as much of an issue as they do not have this dangerous combination.

> "Depend on things that change less often that you do."

## Single Responsibility
A class should be cohesive in that everything the class does should be highly related to its purpose. Methods, like classes, should have a single responsibility. by keeping single responsibility with methods will assist when the time comes to make a new class. There is a link between single responsibility and dependencies. By virtue of the fact that classes have a single responsibility they will have to communicate with each other.

## Interface Segregation
> "The conversation between objects takes place using their interfaces"

The conversation between objects takes place using their interfaces;
In Solid principles the "I" stands for interface segregation. i.e. that larger interfaces should be split into smaller ones. Deciding on the messages that an object public responds to should be carefully considered. The more messages that it responds to, the more that can be sent to it and, back to our friend of dependencies once more, this will make things more likely to get out of hand.
- Interfaces should reveal it's primary responsibilies, and that in itself should encompass a Single responsibility
- private interfaces on the other hand handle implementation details which the sender does not need to know
- public interfaces should be throughly documented in tests.
"You don’t send messages because you have objects, you have objects because you send messages."
- in line with the public interface framing the sender should not be concerned with the internal implementation details rather that they get what they want at the end.

## Abstraction

> Duck typing reveals underlying abstractions that might otherwise be invisible.

By implementing interfaces we may be able to arrive at a truly representative abstraction of a number of classes.
-- check if abstraction applies across a number of types rather than being just top of the tree --
To be considered a good representative it is often best to have a number of sample cases that implement this abstraction rather than looking to build the abstraction prematurely.
The wonderful thing about abstraction is that they represent common, stable qualities. Abstractions by their very nature tend to have many dependencies but will not change very much.

When it comes to abstractions it is better to have a sample of a number of similar classes to inform the creation of
the abstract class.

## Things to look out for
The following a some techniques to keep top of mind when looking to keep objects loosely coupled and open to change:

- DRY code tolerates change because any change in behavior can be made by changing code in just one place.
- If you feel that a comment isnecessary this could be a candidate for moving behaviour into a dedicated method.
- Either do not test private methods or, if you must, segregate those tests from the tests of public methods.
- Strongly consider when chaining methods together to stay in line with the Law of Demeter ("only talk to your neighbour")
- violations of the law of demeter are an indication that your public interfaces are lacking

Inheritence is a specialisation
- User inheritance for is-a relationship
- Use duck types/modules for behaves-like-a relationship
   - if it the implementations have many common features then modules can be used to share this across clases.
   - Ruby's version of multiple inheritance I suppose.
- Use composition for has-a relationship

