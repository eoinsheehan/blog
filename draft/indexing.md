# Indexing

Ok so I actually have quite a bit to add on this one to refine at a layer date.

I think I had overlooked the fact that a database is an aplication and thay it is distinct from disk. in my head these were inextricably linked and I think that added to the confusion.

What is indexing?
this is a means of segmenting the data in a balanced means to make lookups time as short as possible.

How does it work?
An index can be created on a field in the database with a reference to the rows in the table (in the case of sql anyways) where this entry is found.

A B tree structure can be used to achieve this (although others can also). 
Need to go into some of the inner workings of this data structure and why its used here.

this will be combining my notes on use the index luke which is index specific.

Comparison with how it works between MySQL, Postgresql and Mongo.

