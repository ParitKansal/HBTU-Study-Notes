<img src="https://github.com/ParitKansal/Database/blob/main/src/data_info_database_dbms.png" alt="A descriptive caption for the image" width="400">

- "File system" can be used to manage and access the database, but file system fails to do the task efficiently if database is too large.
- Database files are stored in the non-volatile memory, i.e., secondary memory.
- Unit of transfer between secondary memory and main memory is "one disk block".
- **IO Cost:** The IO cost of a "record access" can be defined as the number of secondary memory disk blocks that need to be transferred from secondary memory to main memory in order to access that record from the database.

| Basis for Comparison | File System | DBMS (Database Management System) |
| :--- | :--- | :--- |
| **Data Access & Details** | Requires knowledge of the physical details of the file to access records programmatically. | Hides physical details from the user through data abstraction and data independence (provided by its 3-tier architecture). |
| **I/O Cost** | Higher I/O cost to access data. | Lower I/O cost due to optimization techniques like indexing. |
| **Concurrency** | Provides low concurrency, as locking happens at the entire file level. | Provides high concurrency, as locking can be managed at the individual record level. |

### **Functional dependency (FD)**

In functional dependency **X → Y**, {it is read as 'X determines Y'}

'X' is called **determinant**, & 'Y' is called **dependent**.

If we know X, then we can determine Y. **Converse of the implication need not be true.** i.e. "If we know Y, then we can determine X" need not be true.


A **Functional dependency X → Y** exists in a relation **R** only if:

For every pair of tuples **t1, t2 ∈ R**,
If **t1.X = t2.X** then **t1.Y = t2.Y**.

This means that if the functional dependency **X → Y** exists in a relation **R**, then whenever the values for the attribute set **X** are the same in two tuples, the corresponding values for **Y** must also be the same in those tuples.


* If the necessary condition for the functional dependency "X → Y" does not hold true based on a given relation instance, then the functional dependency "X → Y" can **never exist** in the given relation.
* Even if the necessary condition for the functional dependency "X → Y" does hold true based on a given relation instance, we still cannot be sure whether the functional dependency X → Y exists in the relation or not, because it is just the relational instance (it may change based on time).
* Functional dependencies that **hold true** in a relation are always identified by the database designer based on the properties of the attribute.
