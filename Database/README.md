# DBMS

## Introduction to DBMS

### **Database**
- **Definition**: A structured system for storing, accessing, updating, and managing data efficiently.

### **Database Management System (DBMS)**
- **Components**:
  - **Database**: Collection of interrelated data.
  - **Set of Programs**: For accessing, storing, updating, and deleting data.

![DBMS](https://i.ibb.co/kmNHLFL/dbms.png)

### **Tasks of a DBMS**
1. **Definition**: Defines data structures for storage.
2. **Insertion**: Adds new data.
3. **Updation**: Modifies existing data.
4. **Retrieval**: Fetches data.
5. **Administration**: Manages and maintains the database.

### **Disadvantages of DBMS**
1. **Cost**: Requires investment in specialized hardware and software.
2. **Size**: Needs significant storage space and resources.
3. **Complexity**: Requires trained personnel.
4. **Higher Impact of Failure**: Failures can have significant consequences.

### **Disadvantages of File Systems**
1. **Data Redundancy**: Multiple copies of data.
2. **Difficulty in Accessing**: Custom programs needed for access.
3. **Data Isolation**: Challenges in extracting data from different files.
4. **Integrity**: Difficulty in applying constraints.
5. **Atomicity**: Issues with rollbacks if transactions fail.
6. **Concurrent Access**: Problems with multiple users accessing data.
7. **Security Problems**: Vulnerabilities in data security.

### **File System vs DBMS**

<img src="https://github.com/ParitKansal/Database/blob/main/src/data_info_database_dbms.png" alt="File System vs DBMS" width="400">

- A file system can be used to manage and access a database, but fails to do so efficiently when the database is too large.
- Database files are stored in non-volatile (secondary) memory.
- The unit of transfer between secondary memory and main memory is one **disk block**.
- **IO Cost**: The number of disk blocks that must be transferred from secondary memory to main memory to access a record.

| Basis for Comparison | File System | DBMS |
| :--- | :--- | :--- |
| **Data Access** | Requires knowledge of physical file details to access records programmatically. | Hides physical details through data abstraction and data independence (3-tier architecture). |
| **I/O Cost** | Higher I/O cost to access data. | Lower I/O cost due to optimization techniques like indexing. |
| **Concurrency** | Low concurrency — locking happens at the entire file level. | High concurrency — locking can be managed at the individual record level. |

---

## **Database Users**

1. **Native Users**:
   - Use existing applications to interact with the database.
   - **Examples**: Online library systems, ticket booking systems, ATMs.

2. **Application Programmers**:
   - Develop applications interacting with the database using DML queries.
   - **Languages**: C, C++, Java.

3. **Sophisticated Users**:
   - Directly use SQL for database interactions.
   - **Examples**: Scientists, engineers, analysts.

4. **Specialized Users**:
   - Develop complex database applications.

### **Database Administrator (DBA)**
- **Functions**:
  1. Schema definition.
  2. Storage structure and access methods.
  3. Schema and physical organization modification.
  4. Authorization control.
  5. Routine maintenance.

---

## **Instance and Schema**

### **Instance**
- **Definition**: The collection of information stored in the database at a specific moment.

### **Schema**
- **Definition**: The structural description of the database.

---

## **Three Schema Architecture**

- **Levels of Abstraction**:
  1. **Physical Level**: Describes how data is physically stored.
  2. **Logical/Conceptual Level**: Describes database design, including data types and relationships.
  3. **View/External Level**: Describes the part of the database that a particular user group interacts with.

![Three Schema Architecture](https://i.ibb.co/4SPTpMJ/three-level.png)

---

## **DDL and DML**

1. **Data Definition Language (DDL)**:
   - Defines the database schema.

2. **Data Manipulation Language (DML)**:
   - Handles data queries and modifications.
   - **Procedural DML**: Specifies what data is needed and how to get it.
   - **Non-Procedural DML**: Specifies what data is needed without detailing how to get it.

![DBMS Architecture1](https://i.ibb.co/tLsWczG/dbms-archi-1.png)
![DBMS Architecture2](https://i.ibb.co/HnqNg79/dbms-archi-2.png)

---

## **Data Models**

### **Relational Model**
- **Tables**: Represent data and relationships.
- **Attributes**: Columns in tables.
- **Record-based model**: Fixed-format records.

![Relational Model](https://i.ibb.co/jGJs7m9/rational-database.png)

### **Entity-Relationship Model**
- **Entities**: Basic objects with attributes.
- **Relationships**: Connections among entities.

### **Hierarchical Model**
- Data elements linked in a tree structure with a single root.

### **Network Model**
- Extension of the hierarchical model with multiple parent-child relationships.

### **Object-Oriented Model**
- Defines data in terms of objects and classes.

---

## **Keys**

- **Super Key**: Any set of attributes that uniquely identifies a tuple.
- **Candidate Key**: A minimal super key — no proper subset of it is also a super key.
- **Primary Key**: The candidate key chosen to uniquely identify tuples in the table.
- **Alternate Key**: Candidate keys not selected as the primary key.
- **Foreign Key**: An attribute that references the primary key of another table, enforcing referential integrity.

---

## ER Diagram Overview

### **Entities**
- **Strong Entity**: Can be uniquely identified.
- **Weak Entity**: Cannot be uniquely identified.

![Strong vs Weak Entity](https://techdifferences.com/wp-content/uploads/2016/12/Strong-Entity-Vs-Weak-Entity.jpg)

### **Entity Set**
- A set of entities with the same properties or attributes.

---

## **Types of Attributes**

| **Type**               | **Description**                                   | **Image**                                                                                                            |
|------------------------|---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|
| **Simple**             | Cannot be divided further.                       | ![Simple](https://i.ibb.co/xJPxbDT/simple-1.png)                                                                     |
| **Composite**          | Can be divided into multiple attributes.         | ![Composite](https://i.ibb.co/znN9RPd/composite-1.png)                                                               |
| **Single Valued**      | Holds a single value.                            | ![Single Valued](https://i.ibb.co/xJPxbDT/simple-1.png)                                                              |
| **Multi-Valued**       | Can hold multiple values.                        | ![Multi Valued](https://i.ibb.co/c626nGF/multivales-1.png)                                                           |
| **Derived**            | Derived from other attributes.                   | ![Derived](https://i.ibb.co/QYtvSsk/primary-1.png)                                                                   |
| **Primary Key Attribute** | Uniquely identifies an entity.                   | ![Primary Key Attribute](https://i.ibb.co/59WM8w1/weak-1.png)                                                        |
| **Weak Key Attribute** | Part of a weak entity key.                       | ![Weak Key Attribute](https://i.ibb.co/S5NkLzS/derived-1.png)                                                        |

---

## **Strong and Weak Relationships**

| **Strong Relationship** | **Weak Relationship** |
|-------------------------|------------------------|
| ![Strong](https://i.ibb.co/pf1Wsn4/strong-relation-1.png) | ![Weak](https://i.ibb.co/znXBwtH/weak-relation-1.png) |

---

## **Degree of Relationship**

| **Degree** | **Type**          | **Image**                                                                                           |
|------------|-------------------|-----------------------------------------------------------------------------------------------------|
| 1          | **Unary (1 Degree)**       | ![Unary](https://media.geeksforgeeks.org/wp-content/uploads/20231030173427/unary.jpg)               |
| 2          | **Binary (2 Degrees)**     | ![Binary](https://media.geeksforgeeks.org/wp-content/uploads/20231030173529/binary.jpg)             |
| 3          | **Ternary (3 Degrees)**    | ![Ternary](https://media.geeksforgeeks.org/wp-content/uploads/20231030173612/tarnary.jpg)          |
| 4          | **N-Ary (n Degrees)**      | ![N-Ary](https://media.geeksforgeeks.org/wp-content/uploads/20231030173925/nary.jpg)               |

---

## **Relationship Constraints**

### **Mapping Cardinality**
- One to One
- One to Many
- Many to One
- Many to Many

### **Participation Constraints**
- **Total**: Each entity must be involved in at least one relationship instance.
- **Partial**: Not all entities are involved in relationship instances.

**Note**: Weak entities have a total participation constraint, meaning every instance must be associated with a strong entity.

---

## **Extended ER Features**

### **1. Specialization**
- **Top-Down Approach**

### **2. Generalization**
- **Bottom-Up Approach**

![Specialization vs Generalization](https://www.tutorialspoint.com/assets/questions/images/113346-1532408376.png)

### **3. Aggregation**
- Treating a relationship as a higher-level entity (abstract entity).

![Aggregation](https://i.ibb.co/B4f7K2v/aggeregation.png) 

---

## **Constraints**

| **Constraint**   | **Type**         | **Description**                                                                                       |
|------------------|------------------|-------------------------------------------------------------------------------------------------------|
| **Membership**   | **Attribute Defined** | Based on explicit attribute conditions. |
|                  | **User Defined** | Assigned manually by users.   |
| **Disjointness** | **Disjoint**        | An entity can belong to only one lower-level set. |
|                  | **Overlapping**     | An entity can belong to multiple lower-level sets. |
| **Completeness** | **Totalness**       | Every higher-level entity must belong to at least one lower-level set. |
|                  | **Partial**         | Some higher-level entities may not belong to any lower-level set.|

---

## **Integrity Constraints**

- **Domain Constraints**: Define the permissible values for an attribute.
- **Entity Integrity Constraint**: Ensures that the primary key value cannot be null.
- **Referential Integrity Constraints**: Ensures that a foreign key must either refer to a valid primary key or be null.
- **Key Constraint**: Ensures that all primary key values are unique.

---

## **Reduction of ER Diagrams to Tables**

| **Type**                              | **Description**                                 |
|---------------------------------------|-------------------------------------------------|
| 1. Weak Entity                        | ![Weak Entity](https://i.ibb.co/xXKgRjX/1-1.png) |
| 2. Composite Attributes               | ![Composite Attributes](https://i.ibb.co/n1pZ3RV/2-1.png) |
| 3. Multi-Valued Attributes            | ![Multi-Valued Attributes](https://i.ibb.co/9sHf14j/3-1.png) |
| 4. Many-to-Many Relationship          | ![Many-to-Many](https://i.ibb.co/7Y6GS0P/4-1.png) |
| 5. One-to-Many Relationship           | ![One-to-Many](https://i.ibb.co/YR1sqpB/5-1.png) |
| 6. Aggregation                        | ![Aggregation](https://i.ibb.co/1QrspC9/6-1.png) |
| 7. Unary One-to-Many Relationship     | ![Unary One-to-Many](https://i.ibb.co/YLSnxc9/7-1.png) |
| 8. Unary One-to-One Relationship      | ![Unary One-to-One](https://i.ibb.co/rpBvVmb/8-1.png) |
| 9. Unary Many-to-Many Relationship    | ![Unary Many-to-Many](https://i.ibb.co/rmwpqR2/9-1.png) |

---

## **Functional Dependency and Normalization**

### 1. Functional Dependency (FD)

**Definition:**  
For a relation $R$ and attributes $A$ and $B$ in $R$, $B$ is functionally dependent on $A$ (denoted $A \rightarrow B$) if each value of $A$ is associated with exactly one value in $B$ in $R$.

In $X \rightarrow Y$, $X$ is called the **determinant** and $Y$ is called the **dependent**. If we know $X$, we can determine $Y$. The converse need not be true.

**Formal definition:** $X \rightarrow Y$ holds in relation $R$ if and only if for every pair of tuples $t_1, t_2 \in R$: if $t_1.X = t_2.X$ then $t_1.Y = t_2.Y$.

> **Note:** If the necessary condition for $X \rightarrow Y$ does not hold in a given instance, the FD can **never** exist. Even if it does hold in an instance, we cannot be certain the FD truly exists — a relation instance may change over time. FDs that hold in a relation are always identified by the database designer based on the semantics of the attributes.

**Examples:**

<div style="text-align: center;">

<table style="margin-left: auto; margin-right: auto;">
  <tr>
    <th>Functional Dependency Holds (✅)</th>
    <th>Functional Dependency Doesn't Hold (❌)</th>
  </tr>
  <tr>
    <td>
      <table style="margin-left: auto; margin-right: auto;">
        <tr>
          <th>A</th>
          <th>B</th>
        </tr>
        <tr>
          <td>A1</td>
          <td>B1</td>
        </tr>
        <tr>
          <td>A2</td>
          <td>B2</td>
        </tr>
        <tr>
          <td>A1</td>
          <td>B1</td>
        </tr>
      </table>
    </td>
    <td>
      <table style="margin-left: auto; margin-right: auto;">
        <tr>
          <th>A</th>
          <th>B</th>
        </tr>
        <tr>
          <td>A1</td>
          <td>B1</td>
        </tr>
        <tr>
          <td>A2</td>
          <td>B2</td>
        </tr>
        <tr>
          <td>A1</td>
          <td>B2</td>
        </tr>
      </table>
      <p>Because A1 is associated with more than one value in B</p>
    </td>
  </tr>
</table>

</div>

### 2. Functional Dependency with Keys

- If $\alpha$ is a key, then $\alpha \rightarrow \beta$ always holds for any attribute $\beta$.

### 3. Closure of an Attribute

Given relation $R(A, B, C, D)$ with functional dependencies: { $A \rightarrow B$, $A \rightarrow D$, $B \rightarrow C$ }:

- $A^+ = \{A, B, C, D\}$
- $B^+ = \{B, C\}$
- $C^+ = \{C\}$
- $D^+ = \{D\}$

### 4. Trivial Functional Dependency

- A functional dependency $A \rightarrow B$ is **trivial** if $B \subseteq A$ (e.g., $\{A, B\} \rightarrow A$). Trivial FDs always hold.

### 5. Armstrong’s Axioms

- **Reflexivity Rule:** $A \rightarrow B$ holds if $B \subseteq A$.
- **Augmentation Rule:** If $A \rightarrow B$, then $\alpha A \rightarrow \alpha B$ holds for any set $\alpha$.
- **Transitivity Rule:** If $A \rightarrow B$ and $B \rightarrow C$, then $A \rightarrow C$ holds.

### 6. Additional Rules

- **Union Rule:** If $A \rightarrow B$ and $A \rightarrow C$, then $A \rightarrow BC$ holds.
- **Decomposition Rule:** If $A \rightarrow BC$, then $A \rightarrow B$ and $A \rightarrow C$ hold.

### 7. Closure of a Set of Functional Dependencies

- To find all possible functional dependencies from a given set, compute the closure of the attribute sets using Armstrong’s axioms and additional rules.

---

## **Normalization**

**Definition:**  
Normalization is the process of minimizing redundancy and avoiding anomalies in a relational database by organizing data into well-structured relations. Each relation should represent a single theme or entity.

**Anomalies eliminated:** insertion, deletion, and update anomalies.

---

### Normalization Forms

| **Normal Form** | **Eliminates** | **Condition** |
|---|---|---|
| **Unnormalized (UNF)** | — | Relations may have repeating groups or non-atomic values |
| **1NF** | Repeating groups | Every column must contain atomic (indivisible) values |
| **2NF** | Partial dependency | No non-prime attribute depends on only part of a composite key |
| **3NF** | Transitive dependency | No non-prime attribute transitively depends on the primary key |
| **BCNF** | Overlapping candidate keys | For every FD $A \rightarrow B$, $A$ must be a superkey |
| **4NF** | Multi-valued dependency | No independent multi-valued facts about an entity in one relation |
| **5NF** | Join dependency | Every join dependency is implied by the candidate keys |

---

## **Types of Decomposition**

- **Lossless Decomposition:**  
  Ensures that the original relation can be perfectly reconstructed from the decomposed relations.  
  $R = R1 \bowtie R2 \bowtie R3 \bowtie \ldots \bowtie Rn$

- **Lossy Decomposition:**  
  May not preserve all information from the original relation.  
  $R \neq R1 \bowtie R2 \bowtie R3 \bowtie \ldots \bowtie Rn$

> **Note:** Decompositions up to 3NF are lossless. Beyond 3NF, decompositions may be either lossy or lossless.

### Dependency Preserving Decomposition

A decomposition is dependency preserving if:

(F1 ∪ F2 ∪ ... ∪ Fn)<sup>+</sup> = F<sup>+</sup>

Where:
- $F1, F2, \ldots, Fn$ are the functional dependencies derived from the decomposed relations $R1, R2, \ldots, Rn$.
- F<sup>+</sup> is the closure of the original functional dependencies F.

---

## **Relational Algebra**

### **1. Basic Operators**

- **Comparison Operators**: `=`, `≥`, `≤`, `<`, `>`, `≠`
- **Logical Operators**: `∧` (AND), `∨` (OR), `¬` (NOT)

### **2. Select (σ)**

- **Syntax**: σ<sub><selection-condition></sub>(Relation_name)
- **Description**: Selects rows from the relation that meet the specified condition.

### **3. Project (Π)**

- **Syntax**: Π<sub>col<sub>1</sub>, col<sub>2</sub>, ... col<sub>n</sub></sub>(Relation_name)
- **Description**: Projects specified columns from the relation and removes duplicate rows.

### **4. Set Operations**

- **Union (∪)**: Combines rows from two relations, removing duplicates.
- **Intersection (∩)**: Retrieves rows common to both relations.
- **Difference (−)**: Retrieves rows in the first relation but not in the second.
- **Product (×)**: Returns the Cartesian product of two relations.

**Notation Examples**:
- Π<sub>x</sub>(R<sub>1</sub> ∪ R<sub>2</sub>) = Π<sub>x</sub>(R<sub>1</sub>) ∪ Π<sub>x</sub>(R<sub>2</sub>)
- Π<sub>x</sub>(R<sub>1</sub> ∩ R<sub>2</sub>) ≠ Π<sub>x</sub>(R<sub>1</sub>) ∩ Π<sub>x</sub>(R<sub>2</sub>)

### **5. Join Operations**

- **Inner Join (⋈)**: Combines rows from two relations based on a condition.
  - **Condition**: R<sub>1</sub> ⋈<sub>condition</sub> R<sub>2</sub>
  - **Equal Join**: R<sub>1</sub> ⋈<sub>equal-condition</sub> R<sub>2</sub>
  - **Natural Join**: R<sub>1</sub> ⋈ R<sub>2</sub>

- **Outer Join**:
  - **Left Join (⟕)**: Includes all rows from the left relation and matched rows from the right relation.
    - **Syntax**: R<sub>1</sub> ⟕<sub>condition</sub> R<sub>2</sub>
  - **Right Join (⟖)**: Includes all rows from the right relation and matched rows from the left relation.
    - **Syntax**: R<sub>1</sub> ⟖<sub>condition</sub> R<sub>2</sub>
  - **Full Outer Join (⟗)**: Includes all rows from both relations, with matched rows where available.
    - **Syntax**: R<sub>1</sub> ⟗<sub>condition</sub> R<sub>2</sub>

### **6. Rename (ρ)**

- **Syntax**: ρ<sub>new_name</sub>(Original_name)
- **Syntax with Columns**: ρ<sub>new_name(col1, col2, ...)</sub>(Original_name)
- **Description**: Renames a relation or its attributes.

### **7. Division (÷)**

- **Syntax**: R<sub>1</sub> ÷ R<sub>2</sub>
- **Description**: Retrieves rows from R<sub>1</sub> where the value of each attribute in R<sub>2</sub> is associated with all values of other attributes.

**Example**:

<table border="1">
   <thead>
      <tr>
         <th>R<sub>1</sub></th>
         <th>R<sub>2</sub></th>
         <th>R<sub>1</sub> ÷ R<sub>2</sub></th>
      </tr>
   </thead>
   <tbody>
      <tr>
         <td>
            <table border="1">
               <tr>
                  <th>A</th>
                  <th>B</th>
                  <th>C</th>
               </tr>
               <tr>
                  <td>A1</td>
                  <td>B2</td>
                  <td>C1</td>
               </tr>
               <tr>
                  <td>A4</td>
                  <td>B5</td>
                  <td>C2</td>
               </tr>
               <tr>
                  <td>A1</td>
                  <td>B2</td>
                  <td>C2</td>
               </tr>
               <tr>
                  <td>A4</td>
                  <td>B5</td>
                  <td>C4</td>
               </tr>
            </table>
         </td>
         <td>
            <table border="1">
               <tr>
                  <th>A</th>
                  <th>B</th>
               </tr>
               <tr>
                  <td>A1</td>
                  <td>B2</td>
               </tr>
               <tr>
                  <td>A4</td>
                  <td>B5</td>
               </tr>
            </table>
         </td>
         <td>
            <table border="1">
               <tr>
                  <th>C</th>
               </tr>
               <tr>
                  <td>C2</td>
               </tr>
            </table>
         </td>
      </tr>
   </tbody>
</table>

**Explanation:** A value of C is included in the result only if it appears paired with **every** (A, B) combination present in R<sub>2</sub>. Here, C2 pairs with both (A1, B2) and (A4, B5), so it is selected. C1 and C4 are not, because they each appear with only one of the two pairs.

---
