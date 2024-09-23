# Indexing

Notes from reading use the index luke

Preface

SQL abstracts the what you want as a user from how this can be achieved by the database.

It turns out that the only thing *developers* need to learn is how to index

 That is because the most important information for proper indexing is not the storage system configuration or the hardware setup. The most important information for indexing is how the application queries the data.

Anatomy of a SQL index

An index is a distinct structure in the database that is built using the `create index` statement.

It requires its own disk space and holds a copy of the indexed table data. That means that an index is pure redundancy. Creating an index does not change the table data; it just creates a new data structure that refers to the table.

A database index is, after all, very much like the index at the end of a book: it occupies its own space, it is highly redundant, and it refers to the actual information stored in a different place.

A database index is, however, more complex than a printed directory because it undergoes constant change

It must process `insert`, `delete` and `update` statements immediately, keeping the index order without moving large amounts of data.

The database combines two data structures to meet the challenge: a doubly linked list and a search tree. These two structures explain most of the database’s performance characteristics.

The index leaf nodes

It is, however, not possible to store the data sequentially because an `insert` statement would need to move the following entries to make room for the new one.

The solution to the problem is to establish a logical order that is independent of physical order in memory.

The logical order is established via a doubly linked list. Every node has links to two neighboring entries, very much like a chain. New nodes are inserted between two existing nodes by updating their links to refer to the new node. The physical location of the new node doesn’t matter because the doubly linked list maintains the logical order.

The data structure is called a *doubly linked list* because each node refers to the preceding and the following node. 

The database uses the space in each block to the extent possible and stores as many index entries as possible in each block. That means that the index order is maintained on two different levels: the index entries within each leaf node, and the leaf nodes among each other using a doubly linked list.

My words: for the above we stack in as much data as possible within the available block at a leaf node.

From the above the indexed filed is column 2 which is used to return any entries meeting this criteria I think? Then somehow the rowID is stored. not very sure on this so far.

**The Search Tree (B-Tree) Makes the Index Fast**

So the underlying structure of the index is a doubly linked list. But to search this quickly we will probably need some metric which is where the B tree comes in (whatever a B tree is)

The index leaf nodes are stored in an arbitrary order—the position on the disk does not correspond to the logical position according to the index order. It is like a telephone directory with shuffled pages. If you search for “Smith” but first open the directory at “Robinson”, it is by no means granted that Smith follows Robinson. A database needs a second structure to find the entry among the shuffled pages quickly: a *balanced search tree*—in short: the B-tree.

[Figure 1.2](https://use-the-index-luke.com/sql/anatomy/the-tree#TreeNodes) shows an example index with 30 entries. The doubly linked list establishes the logical order between the leaf nodes. The root and branch nodes support quick searching among the leaf nodes.

 Each branch node entry corresponds to the biggest value in the respective leaf node

Cool so the branch node relates to everything less than or equal the value in the branch node.

This logic moves down similarly from the root node which contains the highest value that it points to in the branch node.

A branch layer is built up until all leaf node values are covered.

The structure is a balanced tree because the tree depth is equal at every position.

N.B.

Once create the database maintains the index automatically. It applies every insert, delete and update to the index and keeps the tree in balance, thus causing maintenance overhead for write operations.

B-Tree traversal.

each entry is processed in ascending order until a value is greater than or equal to the search term. The database follow the reference to the corresponding branch node and repeats the procedure until the tree traversal reaches a leaf node.

The tree traversal is a very efficient operation so efficient that the author refers to it as the first power of indexing. It works almost instantly - even on a huge data set. That is primarily because of the tree balance, which allows accessing all elements wiht th esame number of steps, and decondly becuase of the logarithmic grows very slowly compared to the number of leaf nodes. Real world indexes with millions of records have a tree depth of four or five.

Logarithmic Scalability.

The logarithm of a number is the exponent to which the base must be raised in order to produce the number. The size of the index is the number of entries per branch node to the power of the depth of the tree. All combinations of the number of checks that would have to be made to get the right entry.

### Slow indexes - Part 1

This is where I’m picking up…
