# Introduction to DBMS — Complete Notes
### (Reference: Korth & Sudarshan, Navathe & Elmasri, GATE Perspective)

---

## 1. Data

**Definition:** Data is a collection of raw, unprocessed facts and figures that have no meaning by themselves until processed or organized. It can be in the form of numbers, characters, symbols, or images.

> Example: 21, "Himanshu", "IT" — individually these are raw values with no context.

**Types of Data:**
- **Structured Data** – follows a fixed format/schema (e.g., tables in RDBMS)
- **Semi-structured Data** – some structure but no rigid schema (e.g., XML, JSON)
- **Unstructured Data** – no fixed format (e.g., images, videos, plain text)

**Data Hierarchy:** Bit → Byte → Field → Record → File → Database

---

## 2. Information

**Definition:** Information is processed, organized, and meaningful data that helps in decision-making. It is derived by applying context, structure, or interpretation to raw data.

> Example: "Himanshu is 21 years old and studies in IT" — this is information, derived from data.

**Data vs Information:**

| Data | Information |
|---|---|
| Raw facts | Processed data |
| No meaning by itself | Has meaning/context |
| Input to a system | Output of a system |
| Example: 21, "Himanshu" | Example: "Himanshu is 21 years old" |

**Characteristics of good information:** Accuracy, Timeliness, Relevance, Completeness.

---

## 3. File Processing System (FPS)

**Definition:** A File Processing System is a method of storing and organizing data in computer files (flat files) where each application program has its own set of data files, and there is no centralized control over the data.

**Structure:**
- Data is stored in separate files (e.g., `.txt`, `.dat`) managed directly by application programs using a file system (OS-level).
- Each department/application (e.g., Payroll, Inventory) maintains its own files independently.

**Example:** Before DBMS, a university might maintain separate files for Student Records, Fee Records, and Library Records — each accessed by a different program with no shared structure.

---

## 4. Problems with File Processing System

According to Korth and Navathe, the major drawbacks of FPS are:

1. **Data Redundancy and Inconsistency**
   - Same data stored in multiple files (duplication) → leads to inconsistency when one copy is updated but not others.

2. **Difficulty in Accessing Data**
   - No general-purpose querying facility; a new program must be written for every new type of request.

3. **Data Isolation**
   - Data scattered in various files, possibly in different formats, making it hard to write programs to retrieve appropriate data.

4. **Integrity Problems**
   - Data values must satisfy certain consistency constraints (e.g., account balance > 0). Enforcing these across scattered files requires hardcoding in every program.

5. **Atomicity Problems**
   - A failure during a transaction (e.g., fund transfer) may leave data in an inconsistent state — no rollback mechanism.

6. **Concurrent Access Anomalies**
   - Multiple users accessing/updating data simultaneously can lead to inconsistent results if not properly controlled.

7. **Security Problems**
   - Difficult to enforce access control since every application program needs to implement security independently.

8. **Lack of Flexibility and Data Independence**
   - Any change in file structure requires changes in all application programs using that file.

> **GATE Tip:** These 7-8 problems are the classic **"Why DBMS over FPS"** motivation — frequently asked as short-answer/MCQ concept questions.

---

## 5. Database

**Definition (Silberschatz/Korth):** A database is an organized/structured collection of interrelated data that is stored and accessed electronically, designed to model a real-world enterprise.

**Definition (Elmasri/Navathe):** A database is a collection of related data with the following implicit properties:
- Represents some aspect of the real world (**mini-world/universe of discourse**)
- Logically coherent collection with inherent meaning
- Designed, built, and populated with data for a specific purpose

**Key Characteristics of a Database:**
- Represents some aspect of real world (mini-world)
- Logically coherent collection of data
- Built for a specific purpose/audience

---

## 6. All About Database — Advantages, Disadvantages, Limitations, Applications

### Advantages of Database (over FPS)
1. Controlling redundancy
2. Restricting unauthorized access
3. Providing persistent storage for program objects
4. Providing storage structures for efficient query processing
5. Providing backup and recovery
6. Providing multiple user interfaces
7. Representing complex relationships among data
8. Enforcing integrity constraints
9. Permitting inferencing and actions using rules

### Disadvantages / Limitations of Database
1. High cost of hardware, software, and skilled personnel (DBA)
2. Complexity — DBMS software is complex to understand and manage
3. Overhead for providing security, concurrency, recovery
4. Requires specialized staff (DBA, trained programmers)
5. Conversion cost from old (FPS) system to DBMS is high

### Applications of Database
- Banking (transactions, accounts)
- Airlines (reservations, schedules)
- Universities (registration, grades)
- E-commerce (inventory, orders)
- Telecommunications (call records)
- Manufacturing (production, supply chain, inventory)
- Human Resources (employee records, payroll)

---

## 7. DBMS (Database Management System)

**Definition (Korth):** A Database Management System (DBMS) is a collection of interrelated data and a set of programs to access that data. It is a software system that allows users to define, create, maintain, and control access to the database.

**Definition (Elmasri/Navathe):** DBMS is a collection of programs that enables users to create and maintain a database, providing an environment that is both convenient and efficient for users to store, retrieve, and process information.

**Core Idea:** DBMS = Database + Set of Programs (software) to manage it.

---

## 8. All About DBMS

### Functions of DBMS
1. Data Definition (via DDL)
2. Data Manipulation (via DML)
3. Data Security and Integrity
4. Data Recovery and Concurrency Control
5. Data Dictionary Maintenance
6. Performance (efficient query processing)

### Components of DBMS
- Hardware
- Software (DBMS software itself)
- Data
- Procedures
- Database Access Language (SQL)
- Users (DBA, Application Programmers, End Users, Sophisticated Users)

### Types of DBMS Users
1. **Naive/Parametric users** — use pre-written application programs (e.g., ATM users)
2. **Application Programmers** — write application programs using languages like Java, Python with embedded DML
3. **Sophisticated users** — interact via query language directly (analysts)
4. **DBA (Database Administrator)** — has central control over the system

### DBA Responsibilities
- Schema definition
- Storage structure & access method definition
- Schema and physical organization modification
- Granting authorization for data access
- Routine maintenance (backup, security patches, storage management)

### Advantages of DBMS (recap over FPS)
- Reduced redundancy, improved data consistency, data sharing, improved data security, improved data integrity, enforced standards.

### Disadvantages of DBMS
- Complexity, cost, performance overhead, higher impact of failure (centralized).

---

## 9. Database Environment

The **database environment** refers to the complete set of components that surround and support a DBMS.

**Components of Database Environment (Connolly & Begg style, referenced in Navathe too):**
1. **Hardware** — computers, storage devices
2. **Software** — DBMS software, OS, application programs, network software
3. **Data** — the actual raw and meta data
4. **Procedures** — instructions/rules for design and use of database
5. **People** — DBA, Database Designers, Application Programmers, End Users

This is essentially the ecosystem in which the DBMS operates — combining software, hardware, data, procedures, and people together.

---

## 10. Three Levels of Data Abstraction (ANSI/SPARC Architecture)

DBMS provides **data abstraction** to hide complexity from users. Given by ANSI/SPARC committee, referenced in Korth as the **Three-Schema Architecture**.

### (i) Physical Level (Internal Level)
- Lowest level of abstraction
- Describes **how** data is actually stored (physical storage structures, file organization, indexing, access paths)

### (ii) Logical Level (Conceptual Level)
- Describes **what** data is stored and the relationships among that data
- Database administrators use this level to decide what information to keep
- Users at this level need not know physical storage details

### (iii) View Level (External Level)
- Highest level of abstraction
- Describes only **part** of the entire database relevant to a particular user/group
- Multiple views can exist for the same underlying database, for security and simplicity

**Diagrammatic order (bottom to top):**
```
View Level (External) → Logical Level (Conceptual) → Physical Level (Internal)
```

> **GATE Tip:** Order and direction of abstraction (top-down: View → Logical → Physical) is a common one-line MCQ.

---

## 11. DBMS Architecture (Three-Schema Architecture / ANSI-SPARC Architecture)

**Purpose:** To achieve **Data Independence** by separating user applications from the physical database.

### Three Schemas:
1. **External Schema (View level)** — Describes multiple user views of the database
2. **Conceptual Schema (Logical level)** — Describes structure of whole database for a community of users (entities, data types, relationships, constraints)
3. **Internal Schema (Physical level)** — Describes physical storage structure of database (file organization, indexes, storage allocation)

### Mappings between Schemas:
1. **External/Conceptual Mapping** — defines correspondence between a particular external view and conceptual schema
2. **Conceptual/Internal Mapping** — defines correspondence between conceptual schema and internal schema, enables logical data independence to work with physical storage

---

## 12. Explanation of All Levels — Schema, Instance, and Views

### Schema
**Definition:** The overall design/structure of the database, which remains fairly static (does not change frequently) — analogous to variable declarations in a program.

**Types of Schema:**
- **Physical Schema** — database design at physical level
- **Logical Schema** — database design at logical level (most important for programmers)
- **View Schema/Subschema** — database design at view level

### Instance
**Definition:** The actual content/data of the database at a particular point in time. Also called **database state** or **snapshot**. Instance changes very frequently as data is inserted/updated/deleted.

> Schema = structure (rare changes) ; Instance = content (frequent changes)

### View
**Definition:** A view is a virtual table derived from one or more base tables (or other views), which does not store data itself but presents a customized/restricted picture of the data for a specific user or application. Achieved at the External Level.

---

## 13. Advantages and All About Three-Level (Three-Schema) Architecture

### Purpose: Data Independence

**(a) Logical Data Independence**
- Ability to change the conceptual schema without changing external schemas or application programs.
- Example: Adding a new attribute/entity to conceptual schema shouldn't affect existing views.
- **Harder to achieve** than physical data independence.

**(b) Physical Data Independence**
- Ability to change the internal schema (storage structures, indexes) without changing the conceptual schema.
- Example: Changing file organization or storage device shouldn't affect logical structure.
- **Easier to achieve** than logical data independence.

### Advantages of Three-Level Architecture
1. Provides data abstraction — hides implementation details from users
2. Achieves both logical and physical data independence
3. Same conceptual/internal schema can support multiple external views (multi-user support)
4. Simplifies user interaction (users only deal with their relevant view, not the whole DB)
5. Enhances security (users only see permitted views)
6. Enables schema evolution without disturbing existing applications

---

## 14. Basic Terms and Database Models

### Basic Terms
- **Entity:** A real-world object/thing distinguishable from other objects (e.g., a Student)
- **Attribute:** A property/characteristic of an entity (e.g., Name, Roll No.)
- **Entity Set:** A collection of similar entities (e.g., all Students)
- **Relationship:** An association among two or more entities
- **Tuple:** A single row/record in a relation (table)
- **Domain:** The set of allowable/permitted values for an attribute
- **Degree:** Number of attributes in a relation
- **Cardinality:** Number of tuples in a relation

### Database Models (Data Models)
A **data model** is a collection of conceptual tools for describing data, relationships, semantics, and constraints.

1. **Hierarchical Model** — Data organized in tree-like structure (parent-child relationship); one parent can have many children, but a child has only one parent.

2. **Network Model** — Data represented as records connected via links; a record can have multiple parent and child records (graph structure) — generalization of hierarchical model.

3. **Relational Model** (Codd, 1970) — Data organized in tables (relations) consisting of rows (tuples) and columns (attributes). Most widely used model today (basis of SQL/RDBMS).

4. **Entity-Relationship (ER) Model** — Data represented in terms of entities, attributes, and relationships; used mainly for conceptual design (ER diagrams).

5. **Object-Oriented Model** — Data represented as objects, combining data and its behavior (methods), supports inheritance, encapsulation.

6. **Object-Relational Model** — Hybrid of relational and object-oriented models.

> **GATE Tip:** Relational Model and ER Model are the most heavily tested; know Codd's contribution (1970, relational model) as a factual recall point.

---

## Quick Revision Table

| # | Topic | One-line Recall |
|---|---|---|
| 1 | Data | Raw facts, no meaning |
| 2 | Information | Processed, meaningful data |
| 3 | FPS | Data stored in independent flat files |
| 4 | Problems with FPS | Redundancy, inconsistency, isolation, integrity, atomicity, concurrency, security |
| 5 | Database | Organized, related collection of data (mini-world) |
| 6 | Database pros/cons | Controls redundancy vs high cost/complexity |
| 7 | DBMS | Software + Data to manage database |
| 8 | All about DBMS | Functions, components, users, DBA role |
| 9 | Database Environment | HW + SW + Data + Procedures + People |
| 10 | 3 Levels of Abstraction | View → Logical → Physical |
| 11 | DBMS Architecture | External, Conceptual, Internal schema + mappings |
| 12 | Schema/Instance/View | Schema = structure; Instance = snapshot; View = virtual table |
| 13 | 3-level Architecture Advantages | Logical & Physical Data Independence |
| 14 | Basic Terms & Models | Entity, Attribute, Relation + Hierarchical/Network/Relational/ER/OO models |

---

*References: Database System Concepts – Silberschatz, Korth, Sudarshan; Fundamentals of Database Systems – Elmasri & Navathe; Database Management Systems – Raghu Ramakrishnan (supplementary).*
