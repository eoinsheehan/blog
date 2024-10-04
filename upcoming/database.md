# Database

Chat about persistance and the comparison with memory in a Von Neumann architecture.

NoSQL vs SQL

need to do some stuff on indices.

Seems like there are many different types of indices in Mongo for example.
It also seems that it may be best for the index to be able to be stored in ram somehow to prevent the need to read from disk.

Comparison of index practices in SQL vs Mongo

Watched a decent few of Hussein Nasser's videos on indexing over the weekend which were actually very good.
They also made going back and reading use the index luke make a lot more sense.

It's all pretty straightforward really.

Then would just have to link in the search solution (in my case Elastic more than likely), compare the use cases for indexing and see which works best.

Note:
worth making note of the discussion with Gus that the indexes are loaded into memory of the database application.


What is the deal with SSD and how it differs both from HDD and RAM

Question:
What is an ORM?
Why is it needed?
This could well relate to the requirement for serializing objects?
How are tables segmented on MySQL.
How do joins and clauses work?
