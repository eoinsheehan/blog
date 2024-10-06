# Blocks

I don't think I really get the significance of passing a block to a method in ruby.

Questions:
What is the difference between an argument and passing a block?
Can you pass a block as an argument?
What is the relationship with a proc object?

using &block makes it clear in a method that a block is expected.

Using yield unless you check with block_given? then it will raise an error.

Blocks allow you to pass in custom behavior

i.e. you can pass in a bunch of ruby code that will get evaluated as opposed to just variables.
I suppose these are essentially just functions to run at a point in time which is in fact where it ties in with the proc.

I think I have some good readings on this:weq

