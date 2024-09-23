# Ruby (some of the more interesting parts) 
Discuss some of the key features
- what are symbols
unique identifiers
need to check also but they actually point to a value and not a reference I think?
they are scoped to their classes so that methods woth the same name in different classes can be stored as symbols.
similarly different hashes can have the save key values as symbols which woild have to be scoped also?
- discuss that what MRI is and YARV
- Blocks in ruby (Passing execution control and how it works)
- There is like the pretzel operator or whatever too
- What is the enumerable class
- Inheritance in Ruby (Multiple inheritence is somewhat available via modules)
- The Class hierarchy diagram or whatever it's called
- chat about the metaprogramming aspects a little and reference Paolo Perrotta's book

Some of the good reaources were the rubyapi.org documentation for exploring the fratures of the language.


Ruby Object Model
Exploring the docs that are available at rubyapi.org my lack of hnderstanding of the class hierarchy in the ruby onject model became apparent. 
I dabbled somewhat with Paolo Perrottas Meta Programming book. The cyclical like relationship between class and Module was challenging and it was also interesting to note that all user defined classes inherit from the Object class. The other main learning I had was that there can be a disconnection between inheritance and the ancestor of an object??
These learnings from metaprogramming were all from the beginning of the book but I felt that the more advanced topics would not be the best use of my time right now and that would be better held off for a future date.

Out of Metaprogramming the main learning was a more solid understanding of the class hierarchy in the ruby object model. 
Constant lookup
Chapter 6 of Ruby under a microscope provided a detailed breakdown of constant lookup in ruby. Starting out using ruby on rails had meant that some of these features of the language were hidden using the autoloading feature of rails.

Reference of self depends on the context.
within an instance method it refers to the object
within a class method it refers to the class.

Funky syntax:
& operator does bitwise operation on integer and the like but actually does set like operations on sets and arrays.

## Rails
- What is MVC at a high level
- Some of the key components of the rails frameworks
- Some of the key commands
- The startup process in rails
- The lifecycle of a request in rails
- Database chat
   - Discuss how this is configured and then it is all pretty straightforward after this

