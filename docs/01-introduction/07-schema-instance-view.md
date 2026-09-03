# 07 — Schema, Instance, and View

**Folder:** `docs/01-introduction/`
**File:** `07-schema-instance-view.md`
**Topics Covered:** Database Schema, Database Instance, Views (explained in relation to the Three-Level Architecture)

---

## 1. Schema

### Definition
According to **Korth, Silberschatz, Sudarshan** (*Database System Concepts*):
> The overall design of the database is called the database schema. A database schema, along with the database state at a particular moment in time, are collectively used to describe a database.

According to **Elmasri & Navathe**:
> The description of a database is called the database schema, which is specified during database design and is not expected to change frequently.

**Key Idea:** A schema is like the **blueprint or structure** of the database — it defines *what* data exists, *what type* it is, and *how* it's related, but not the actual data values themselves.

> **Analogy (common in textbooks):** A schema is like variable declarations (along with their data types) in a program — e.g., `int rollNo; String name;` — these declarations don't change often once the program is written.

---

### 2. Types of Schema (Corresponding to the Three-Level Architecture)

Since the database is described at three different levels (Chapter 6), there are correspondingly **three types of schema**:

| Schema Type | Corresponds to | Description |
|---|---|---|
| **Physical Schema** | Internal Level | Describes the database design at the physical storage level (file structures, indexes) |
| **Logical Schema** | Conceptual Level | Describes the database design at the logical level (entities, attributes, relationships) — **most important for programmers**, since programmers work at this level |
| **View Schema (Subschema)** | External Level | Describes the different views/subsets of the database for different user groups |

> **GATE Tip:** Programmers/application developers work primarily with the **Logical Schema** — they don't need to worry about physical storage (thanks to Physical Data Independence) or about every external view (only their relevant one).

---

### 3. Characteristics of Schema

- Represents the **structure/design**, not the content
- Changes **infrequently** (only when the database design is modified — e.g., adding a new table or column)
- Also referred to as the **"intension"** of the database

---

## 4. Instance (Database State)

### Definition
According to **Korth, Silberschatz, Sudarshan**:
> The data stored in the database at a particular moment in time is called a database instance.

According to **Elmasri & Navathe**:
> The actual data in the database at a particular moment in time is called a database state (or snapshot). It is also called the current set of occurrences or instances in the database.

**Key Idea:** An instance is a **snapshot** — the actual values present in the database *right now*. Unlike schema, this changes very frequently, every time data is inserted, updated, or deleted.

> **Analogy:** If schema is like variable declarations (`int rollNo;`), then instance is like the actual value stored in that variable at runtime (`rollNo = 101`).

---

### 5. Schema vs Instance — Comparison Table

| Basis | Schema | Instance |
|---|---|---|
| **Definition** | Overall structure/design of database | Actual data present at a specific point in time |
| **Also Called** | Intension | Extension / Database State / Snapshot |
| **Frequency of Change** | Rarely changes (only on design modification) | Changes very frequently (on every insert/update/delete) |
| **Analogy** | Variable declaration (`int x;`) | Variable's current value (`x = 5`) |
| **Example** | "Student(RollNo, Name, CGPA)" | "101, Raj, 8.5" and "102, Amit, 9.1" (actual rows) |

> **GATE Tip:** This is a **very frequently tested distinction** — questions often describe a scenario and ask "is this schema or instance?" Remember: **structure = schema, actual data = instance.**

---

## 6. View

### Definition
According to **Elmasri & Navathe**:
> A view is a virtual or derived relation/table that is dynamically derived from one or more base relations, and does not necessarily exist in physical form.

**Key Points about Views:**
- A view is achieved at the **External Level** of the Three-Schema Architecture (Chapter 6)
- A view does **not store data itself** — it is a **virtual table**, generated on-the-fly from one or more **base tables** (or other views) using a query
- Used to:
  - Present a **customized/restricted picture** of data to a specific user or application
  - Enhance **security** — users only see the columns/rows relevant/permitted to them
  - Simplify **complex queries** — a view can encapsulate a complicated join/query, and users just query the view directly

> **Example:** A view `StudentFeeStatus` might be created by joining the `Student` table and `Fee` table, showing only `RollNo, Name, FeeStatus` — hiding sensitive academic details like CGPA — for use by the Accounts department.

---

## 7. Relating Schema, Instance, and View to the Three-Level Architecture

```
┌────────────────────────────────────────────────────┐
│  EXTERNAL LEVEL   →  View Schema (Subschema)         │
│                       Realized through VIEWS          │
├────────────────────────────────────────────────────┤
│  CONCEPTUAL LEVEL →  Logical Schema                   │
│                       (main structure programmers use) │
├────────────────────────────────────────────────────┤
│  INTERNAL LEVEL   →  Physical Schema                  │
│                       (storage structures)             │
└────────────────────────────────────────────────────┘

  At ANY point in time, the ACTUAL DATA present
  across these levels = the DATABASE INSTANCE
```

---

## Summary Table

| Concept | What It Represents | Changes? | Level in 3-Schema Architecture |
|---|---|---|---|
| **Physical Schema** | Physical storage design | Rarely | Internal Level |
| **Logical Schema** | Logical structure (entities, relationships) | Rarely | Conceptual Level |
| **View Schema** | User-specific subset of data | Rarely (structure), but views can be redefined | External Level |
| **View** | Virtual table derived from base table(s) | N/A (dynamically generated) | External Level (implementation) |
| **Instance** | Actual data values at a point in time | Frequently | Applies across all levels |

---

## 📝 GATE Exam Angle — Summary Points

1. **Schema = Structure (rare changes)**; **Instance = Data/Content (frequent changes)** — the most tested distinction in this chapter.
2. Schema is also called **"intension"**; Instance is also called **"extension"** or **"database state"/"snapshot."**
3. Three types of schema map directly to the three levels: **Physical Schema ↔ Internal Level**, **Logical Schema ↔ Conceptual Level**, **View Schema ↔ External Level**.
4. A **View** is a **virtual table** — it does not physically store data; it's derived dynamically from base tables. This is a common conceptual MCQ point ("Does a view store data physically?" → **No**).
5. Views are used for **security** and **query simplification** — remember both purposes for application-based questions.
6. Common trap: confusing **View (a specific SQL/relational concept — a derived virtual table)** with **View Level/External Schema (a level of abstraction in the 3-schema architecture)**. They are related but not identical — the View Level is realized *through* views and other external schema constructs.

---

## 🔗 Conceptual Link
This chapter concludes the "architecture" portion of the introduction. The final chapter, **Basic Terms and Database Models**, introduces fundamental terminology (Entity, Attribute, Tuple, etc.) and the different data models (Relational, Hierarchical, Network, ER, Object-Oriented) — setting the stage for the next major section of the handbook: the **ER Model**.

---

**Previous:** [`06-three-level-architecture.md`](./06-three-level-architecture.md)
**Next:** [`08-basic-terms-and-data-models.md`](./08-basic-terms-and-data-models.md)
