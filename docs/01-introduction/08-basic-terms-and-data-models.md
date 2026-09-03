# 08 — Basic Terms and Database Models

**Folder:** `docs/01-introduction/`
**File:** `08-basic-terms-and-data-models.md`
**Topics Covered:** Basic DBMS Terminology, Database (Data) Models

> This is the **final chapter** of the Introduction section — it bridges into the next section, **ER Model** (`02-er-model/`).

---

## Part A — Basic Terms

### 1. Entity
**Definition (Elmasri & Navathe):**
> An entity is a "thing" or "object" in the real world that is distinguishable from all other objects.

> **Example:** A specific student, e.g., "Raj Kumar with RollNo 101," is an entity.

---

### 2. Attribute
**Definition:**
> An attribute is a property or characteristic of an entity that describes it.

> **Example:** For a Student entity — `Name`, `RollNo`, `CGPA`, `Address` are all attributes.

**Types of Attributes** *(will be detailed further in the ER Model chapter)*:
- Simple vs Composite
- Single-valued vs Multi-valued
- Stored vs Derived

---

### 3. Entity Set
**Definition:**
> An entity set is a collection of entities of the same type that share the same attributes.

> **Example:** The entity set `Student` includes all individual student entities (Raj, Amit, Priya, etc.)

---

### 4. Relationship
**Definition:**
> A relationship is an association or connection among two or more entities.

> **Example:** A Student "enrolls in" a Course — `enrolls in` is a relationship between the `Student` entity set and the `Course` entity set.

---

### 5. Tuple
**Definition (Korth):**
> A tuple is a single row of a relation (table) — it represents one instance/record of an entity.

> **Example:** `(101, "Raj", "CSE", 8.5)` is one tuple in the Student relation.

---

### 6. Domain
**Definition:**
> A domain is the set of allowable/permitted values that an attribute can take.

> **Example:** The domain of `CGPA` might be defined as decimal values between 0.0 and 10.0.

---

### 7. Degree
**Definition:**
> The degree of a relation is the number of attributes (columns) it contains.

> **Example:** If the Student relation has 4 attributes (RollNo, Name, Dept, CGPA), its degree is **4**.

---

### 8. Cardinality
**Definition:**
> The cardinality of a relation is the number of tuples (rows) it contains at a given time.

> **Example:** If the Student relation currently has 500 rows, its cardinality is **500**.

> **GATE Tip:** **Degree = columns (structural, fixed)**; **Cardinality = rows (data-dependent, changes with instance)**. This distinction connects directly back to the **Schema vs Instance** concept from Chapter 7 — Degree is a schema-level property, Cardinality is an instance-level property.

---

## Summary Table — Basic Terms

| Term | Meaning | Example |
|---|---|---|
| Entity | A distinguishable real-world object | One student, "Raj" |
| Attribute | A property of an entity | Name, RollNo, CGPA |
| Entity Set | Collection of entities of same type | All students |
| Relationship | Association between entities | Student "enrolls in" Course |
| Tuple | A single row/record | (101, "Raj", "CSE", 8.5) |
| Domain | Set of allowed values for an attribute | CGPA ∈ [0.0, 10.0] |
| Degree | Number of attributes (columns) | 4 |
| Cardinality | Number of tuples (rows) | 500 |

---

## Part B — Database (Data) Models

### Definition
According to **Elmasri & Navathe**:
> A data model is a collection of concepts that can be used to describe the structure of a database — the data types, relationships, and constraints that should hold on the data. Most data models also include a set of basic operations for specifying retrievals and updates.

**Key Idea:** A data model provides the **conceptual tools** to describe *how* data is organized and related within a database.

---

### 1. Hierarchical Model
- Organizes data in a **tree-like structure** with a parent-child relationship
- Each **parent** node can have **multiple children**, but each **child** has only **one parent** (1:N relationship only)
- **Example:** An organizational structure where a Department has multiple Employees, but each Employee belongs to only one Department

```
        Department
        /    |    \
   Emp1   Emp2   Emp3
```

**Limitation:** Cannot naturally represent many-to-many relationships.

---

### 2. Network Model
- A **generalization** of the hierarchical model
- Data is represented as **records connected via links** (graph structure instead of tree)
- A record (child) can have **multiple parent records**, unlike the hierarchical model
- Represented using a graph rather than a strict tree

**Example:** A Student can be linked to multiple Courses, and a Course can be linked to multiple Students — represented via explicit links/pointers.

---

### 3. Relational Model
- Proposed by **E. F. Codd in 1970** — the foundation of modern RDBMS
- Data is organized into **relations (tables)** consisting of **rows (tuples)** and **columns (attributes)**
- The most widely used data model today; forms the basis of **SQL**

**Key Features:**
- Data represented simply as tables — easy to understand
- Strong theoretical foundation (relational algebra, relational calculus)
- Supports powerful query languages (SQL)

> **GATE Tip:** "Who proposed the Relational Model, and in which year?" → **E. F. Codd, 1970** — a commonly asked factual recall question.

---

### 4. Entity-Relationship (ER) Model
- Represents data in terms of **Entities**, **Attributes**, and **Relationships**
- Primarily used as a **conceptual design tool** — represented visually through **ER Diagrams**
- Acts as a bridge between real-world requirements and the relational database schema (ER diagrams are later converted into relational tables)

*(This model is covered in full depth in the next section: `docs/02-er-model/`)*

---

### 5. Object-Oriented Data Model
- Represents data as **objects**, similar to object-oriented programming
- Combines **data** and the **behavior/methods** that operate on that data, into a single unit
- Supports OOP concepts: **Encapsulation, Inheritance, Polymorphism**
- Useful for complex data types (multimedia, CAD/CAM applications)

---

### 6. Object-Relational Model
- A **hybrid model** combining features of the Relational Model and the Object-Oriented Model
- Allows relational databases to support complex/object-like data types while retaining SQL-based querying

---

## Summary Table — Data Models

| Model | Structure | Relationship Support | Key Point |
|---|---|---|---|
| Hierarchical | Tree | Only 1:N | Each child has exactly one parent |
| Network | Graph | M:N supported | Generalization of hierarchical model |
| Relational | Tables (rows & columns) | M:N (via extra tables) | Proposed by Codd (1970); basis of SQL |
| ER Model | Entities, attributes, relationships | Conceptual — all types | Used for conceptual design (ER diagrams) |
| Object-Oriented | Objects (data + methods) | Complex relationships | Based on OOP principles |
| Object-Relational | Hybrid (tables + objects) | Complex + relational | Combines relational and OO features |

---

## 📝 GATE Exam Angle — Summary Points

1. **Degree vs Cardinality**: Degree = number of columns (attributes); Cardinality = number of rows (tuples). Very frequently tested.
2. **Relational Model** was proposed by **E. F. Codd in 1970** — remember this fact.
3. **Hierarchical Model**: strict tree, 1:N only, each child has ONE parent.
4. **Network Model**: graph-based, allows a child to have MULTIPLE parents (generalization of hierarchical).
5. The **ER Model** is a conceptual design tool (not used for actual storage) — it gets converted into the Relational Model for implementation. This conceptual→logical mapping is a key theme carried into the next section.
6. Know to classify a given real-world scenario into the correct basic term (Entity vs Attribute vs Relationship) — this skill is essential preparation for the ER Model chapters ahead.

---

## 🎉 End of Introduction Section

This completes all 8 chapters of `docs/01-introduction/`:
1. Data and Information
2. File Processing System
3. Problems with FPS
4. Database and DBMS
5. Database Environment
6. Three-Level Architecture
7. Schema, Instance, and View
8. Basic Terms and Data Models

---

## 🔗 What's Next
The next section of the handbook, **`docs/02-er-model/`**, begins with a deep dive into the **Entity-Relationship (ER) Model** — covering entities, attributes (in full detail: simple/composite, single/multi-valued, derived), relationships, ER diagram notations, keys, and eventually Enhanced ER (EER) concepts like generalization and specialization.

---

**Previous:** [`07-schema-instance-view.md`](./07-schema-instance-view.md)
**Next:** `docs/02-er-model/01-entities-attributes-relationships.md` *(to be created)*
