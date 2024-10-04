# Design Patterns

## Builder Pattern
Builder is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to produce different types and representations of an object using the same construction code.

You might make the program too complex by creating a subclass for every possible configuration of an object.

For example all the different types of houses could result in a crazy amount of subclasses.
Instead we could look to make use of the Builder pattern.

Alternatively you could have a case where the initialization method is very involved.

This could be a sign that a builder pattern could be a good approach.
This creates another problem though where most of the parameters will be unused, making the constructor calls pretty ugly.

### Solution
The builder pattern suggest that you extract the object construction code out of its own class and move it to separate objects called buidlers.
To create an object, you execute a series of these steps ona builder object. The importatnt part is that you don't need to call all of the steps.
You can call only those steps that are necessary for producing a particulaar configuration of the object.

You can call different methods to build the object that you desire and potentially control the order as well if required.

You can go a step further and extracgt a series of calls to the builder steps you can use a construct a product into a separate class called director.
The director class defined the order in which to execute the building steps, while the builder provides the implementation for those steps.

The builder interface declares product construction steps that are common across all types of builders.

- Identify the builder that is required for your object
- invoke get result method for the builder in question
each of the builder methods should be called to add the relevant attributes to the object in question.

