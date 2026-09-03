# 06 — Three-Level Architecture (ANSI-SPARC Architecture)

**Folder:** `docs/01-introduction/`
**File:** `06-three-level-architecture.md`
**Topics Covered:** Three Levels of Data Abstraction, DBMS Architecture, Data Independence (Logical & Physical)

> **Note:** This is one of the **most heavily tested topics** in GATE DBMS Introduction. Read carefully.

---

## Part A — Three Levels of Data Abstraction

### 1. Why Data Abstraction?

According to **Korth, Silberschatz, Sudarshan**:
> A major purpose of a database system is to provide users with an *abstract* view of the data. The system hides certain details of how the data are stored and maintained.

In simple terms: different users of a database have different needs. A DBA needs to know physical storage details; an end user just wants to see relevant information without worrying about *how* it's stored. **Data abstraction** provides different "levels" of viewing the same underlying data.

---

### 2. The Three Levels of Abstraction

#### (i) Physical Level (Internal Level)
- The **lowest** level of abstraction
- Describes **how** the data is actually stored on the storage medium
- Deals with: file organization, storage structures, indexing methods, access paths, compression, encoding

> **Example:** "The student record is stored as a sequence of consecutive bytes; the Roll_No field starts at byte offset 0 and occupies 4 bytes."

---

#### (ii) Logical Level (Conceptual Level)
- The **middle** level of abstraction
- Describes **what** data is stored in the database and the **relationships** among that data
- The entire database is described in terms of a small number of relatively simple structures
- Database Administrators use this level to decide what information should be kept in the database
- Users at this level **do not need to know** the physical storage details

> **Example:** "A Student has RollNo, Name, and CGPA; each Student is enrolled in one Department."

---

#### (iii) View Level (External Level)
- The **highest** level of abstraction
- Describes only **part** of the entire database, relevant to a **particular group of users**
- Multiple views can exist for the same underlying database — different users see different subsets/perspectives
- Used to simplify user interaction and enhance security (users only see what they need to see)

> **Example:** An Accounts clerk's view might show `Name, RollNo, FeeStatus` only, hiding academic details like CGPA.

---

### 3. Diagram — Direction of Abstraction

```
        ┌─────────────────────────┐
        │      VIEW LEVEL          │   <-- Highest (multiple external views)
        │   (External Schema)      │
        └───────────┬─────────────┘
                     │
        ┌─────────────────────────┐
        │     LOGICAL LEVEL        │   <-- Middle (single conceptual schema)
        │   (Conceptual Schema)    │
        └───────────┬─────────────┘
                     │
        ┌─────────────────────────┐
        │     PHYSICAL LEVEL       │   <-- Lowest (internal storage details)
        │    (Internal Schema)     │
        └─────────────────────────┘
```

> **GATE Tip:** Order (top → bottom): **View → Logical → Physical**. This is a very common one-line MCQ ("which is the highest/lowest level of abstraction?").

---

## Part B — DBMS Architecture (Three-Schema Architecture / ANSI-SPARC Architecture)

### 1. Purpose

The **Three-Schema Architecture** (proposed by the ANSI/SPARC committee) is the standard architectural framework that implements the three levels of abstraction described above. Its main goal is to achieve **Data Independence** — separating user applications from the physical database.

---

### 2. The Three Schemas

| Schema | Corresponds to | Description |
|---|---|---|
| **External Schema** | View Level | Describes multiple user views of the database; each external schema describes the part of the database that a particular user group is interested in |
| **Conceptual Schema** | Logical Level | Describes the structure of the *whole* database for the entire community of users — entities, data types, relationships, and constraints; hides physical storage details |
| **Internal Schema** | Physical Level | Describes the physical storage structure of the database — file organization, indexes, storage allocation |

> Note: There is only **ONE** conceptual schema and **ONE** internal schema per database, but there can be **MANY** external schemas (one or more per user group).

---

### 3. Mappings Between Schemas

To connect the three schemas, the DBMS maintains **mappings**:

1. **External/Conceptual Mapping**
   - Defines the correspondence between a particular external view and the conceptual schema
   - Allows the DBMS to transform requests/results between the external view and the conceptual level

2. **Conceptual/Internal Mapping**
   - Defines the correspondence between the conceptual schema and the internal schema
   - Enables the DBMS to find the actual physical record(s) that correspond to a conceptual-level record
   - This mapping is what allows **physical data independence** to work

---

### 4. Full Architecture Diagram

```
   ┌───────────┐   ┌───────────┐   ┌───────────┐
   │  View 1   │   │  View 2   │   │  View 3   │      <- External Schemas
   └─────┬─────┘   └─────┬─────┘   └─────┬─────┘
         │               │               │
         └───────────────┼───────────────┘
                          │  (External/Conceptual Mapping)
                          ▼
                ┌───────────────────┐
                │  Conceptual Schema │                <- Single Logical View
                └──────────┬─────────┘
                           │  (Conceptual/Internal Mapping)
                           ▼
                ┌───────────────────┐
                │   Internal Schema  │                <- Physical Storage
                └───────────────────┘
```

---

## Part C — Data Independence

### 1. What is Data Independence?

**Definition:** Data independence is the capacity to change the schema at one level of the database system without having to change the schema at the next higher level.

There are **two types**, corresponding to the two mappings above:

---

### (a) Logical Data Independence

- The ability to change the **conceptual schema** without changing the **external schemas** or application programs
- **Example:** Adding a new attribute or entity to the conceptual schema (e.g., adding a "Scholarship" entity) should not require changes to existing user views that don't need it.
- **Harder to achieve** than physical data independence, because external views are closely tied to the conceptual structure.

### (b) Physical Data Independence

- The ability to change the **internal schema** (storage structures, file organization, indexes) without changing the **conceptual schema**
- **Example:** Switching from sequential file storage to a B+ Tree indexed structure, or moving data to a different storage device, should not affect how the conceptual schema or user applications see the data.
- **Easier to achieve** than logical data independence, since it only affects the storage layer.

> **GATE Tip:** A very common question format: *"Which type of data independence is easier to achieve?"* → **Answer: Physical Data Independence.**

---

## Part D — Advantages of the Three-Level (Three-Schema) Architecture

1. **Data Abstraction** — hides implementation and storage details from users
2. **Achieves Data Independence** — both logical and physical, reducing maintenance costs when structure changes
3. **Supports Multiple Views** — same conceptual/internal schema can support many different external views for different users simultaneously
4. **Simplifies User Interaction** — users only deal with their relevant view, not the entire complex database
5. **Enhances Security** — users only see the portion of data permitted to them via their view
6. **Enables Schema Evolution** — the conceptual or internal schema can evolve over time without breaking existing applications

---

## Summary Table

| Level / Schema | Abstraction Level | Scope | Who Uses It |
|---|---|---|---|
| External Schema | View Level | Partial (subset for specific users) | End users, specific user groups |
| Conceptual Schema | Logical Level | Entire database (logical structure) | DBA, database designers |
| Internal Schema | Physical Level | Entire database (physical storage) | DBA, system-level administrators |

| Data Independence Type | Protects Against Changes In | Difficulty |
|---|---|---|
| Logical Data Independence | Conceptual Schema | Harder to achieve |
| Physical Data Independence | Internal Schema | Easier to achieve |

---

## 📝 GATE Exam Angle — Summary Points

1. **Three Levels (bottom to top):** Physical → Logical → View; abstraction increases going up.
2. **Three Schemas:** External (many), Conceptual (one), Internal (one).
3. **Two Mappings:** External/Conceptual and Conceptual/Internal.
4. **Two types of Data Independence:**
   - Logical (conceptual schema changes hidden from external schema) — **harder**
   - Physical (internal schema changes hidden from conceptual schema) — **easier**
5. This architecture's entire purpose = achieving **data independence**, which directly solves the "Lack of Flexibility / Data Dependence" problem of FPS (Chapter 3, Problem #8).
6. Common GATE trap: confusing which mapping enables which independence — remember, **Conceptual/Internal mapping → Physical Independence**, and **External/Conceptual mapping → Logical Independence**.

---

## 🔗 Conceptual Link
The next chapter, **Schema, Instance, and View**, dives deeper into what exactly a "schema" is at each of these three levels, and introduces the important distinction between schema (structure) and instance (actual data/snapshot) — a frequently confused GATE topic.

---

**Previous:** [`05-database-environment.md`](./05-database-environment.md)
**Next:** [`07-schema-instance-view.md`](./07-schema-instance-view.md)
