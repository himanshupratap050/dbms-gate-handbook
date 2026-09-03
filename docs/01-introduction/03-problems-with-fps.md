# 03 — Problems with File Processing System (FPS)

**Folder:** `docs/01-introduction/`
**File:** `03-problems-with-fps.md`
**Topics Covered:** Limitations/Drawbacks of File Processing System

---

## Introduction

According to **Korth, Silberschatz, Sudarshan** (*Database System Concepts*), keeping organizational information in a file-processing system has several major disadvantages. These drawbacks are exactly what motivated the development of the **Database Management System (DBMS)**.

> **GATE Importance:** This is one of the **most frequently tested conceptual topics** in DBMS — often appears as MCQs, match-the-following, or "which of the following is NOT a problem of FPS" type questions.

---

## 1. Data Redundancy

### Definition
When the **same data is stored at multiple places/files**, it is called **Data Redundancy**.

**Example:**  
A student's name and address are stored in the **Fee, Library, and Examination files**.

**Problem:**  
→ Same data is unnecessarily repeated.  
→ **Storage wastage** happens.

---

## 2. Data Inconsistency

### Definition
When the **same data has different values at different places/files**, it is called **Data Inconsistency**.

**Example:**  
If a student's address is changed in the **Fee file** but not in the **Library file**, then both files contain different addresses.

**Problem:**  
→ Data becomes **incorrect/conflicting**.  
→ Different files show **different values for the same data**.

---

## 3. Difficulty in Accessing Data

### Explanation
FPS environments do not provide a general-purpose, flexible way to retrieve data. If a new type of data request arises that wasn't anticipated when the original programs were written, a **new application program must be written from scratch** to satisfy it.

> **Example:** If the original program only supports "list all students in CSE," but now someone wants "list all students in CSE with CGPA > 8," an entirely new program must be coded — there's no query language to just ask for it.

### Consequence
- Highly inefficient and time-consuming for ad-hoc/unplanned queries
- Heavy dependency on programmers for even simple data retrieval needs

---

## 4. Data Isolation

### Explanation
Data is scattered across various files, and these files may be in **different formats**, written using different programs/languages. This makes it difficult to write new application programs that need to retrieve data from multiple sources together.

### Consequence
- Related data cannot easily be combined/cross-referenced
- Integration of data from multiple files requires significant custom coding effort

---

## 5. Integrity Problems

### Explanation
Data values stored in the database must often satisfy certain **consistency/integrity constraints**.

> **Example:** "Account balance must not go below ₹0" or "CGPA must be between 0 and 10."

In FPS, such constraints are **not centrally enforced**. Instead, they must be hardcoded into the logic of *every single application program* that touches that data.

### Consequence
- If a new constraint needs to be added later, **every relevant program must be modified individually**
- High risk of constraints being missed or inconsistently applied across programs

---

## 6. Atomicity Problems

### Explanation
A computer system, like any mechanical/electrical device, is subject to failure (power failure, hardware crash, etc.). In such cases, it is essential that the data be restored to a consistent state.

> **Example:** Consider transferring ₹5000 from Account A to Account B.
> This requires **two steps**:
> 1. Debit ₹5000 from A
> 2. Credit ₹5000 to B
>
> If a system failure occurs **after step 1 but before step 2**, the transaction is left **incomplete** — money has vanished from A but never reached B.

### Consequence
- FPS has **no built-in mechanism** to guarantee that a transaction either completes fully or not at all (this "all-or-nothing" property is called **Atomicity**)
- Leads to data corruption/loss in case of failures

---

## 7. Concurrent Access Anomalies

### Explanation
When multiple users/programs access and update the same data **simultaneously**, without proper coordination, it can lead to **inconsistent results**.

> **Example:** Two clerks simultaneously try to book the last available seat on a train. Both read "1 seat available" at the same time, both book it — resulting in **overbooking** (double allocation of the same seat).

### Consequence
- FPS typically lacks **concurrency control mechanisms**
- Leads to lost updates, dirty reads, and other anomalies when multiple users work on shared data at once

---

## 8. Security Problems

### Explanation
Not every user of the system should be allowed to access all the data. For example, in a university system, payroll staff should not be able to access student examination results, and vice versa.

Since FPS has **no centralized access control**, security must be enforced **individually within every application program** — which is inconsistent and prone to gaps.

### Consequence
- Difficult to enforce a uniform security policy across the system
- High risk of unauthorized access due to inconsistent implementation

---

## 9. Lack of Flexibility / Data Dependence

### Explanation
In FPS, application programs are tightly coupled to the **physical structure** of the files they use (field names, order, data types, storage format).

### Consequence
- Any change to file structure (e.g., adding a new field, changing a data type) requires **modifying every application program** that accesses that file
- This lack of **Data Independence** makes the system rigid and expensive to maintain

---

## Summary Table

| # | Problem | Core Issue | Real-World Impact |
|---|---|---|---|
| 1 | Data Redundancy | Same data stored in multiple files | Wasted storage space due to unnecessary duplication |
| 2 | Data Inconsistency | Same data has different values in different files | Conflicting or incorrect data |
| 3 | Difficulty in Accessing Data | No easy way to query or retrieve data | New program needed for new data requests |
| 4 | Data Isolation | Data scattered across different files and formats | Difficult to combine and access related data |
| 5 | Integrity Problems | Data constraints handled separately by programs | Constraints may be missed or applied inconsistently |
| 6 | Atomicity Problems | No all-or-nothing transaction guarantee | Data may become incorrect if a failure occurs during an operation |
| 7 | Concurrent Access Anomalies | No proper control over simultaneous data access | Lost updates and incorrect results may occur |
| 8 | Security Problems | No centralized access control | Unauthorized users may access or modify data |
| 9 | Lack of Flexibility (Data Dependence) | Programs depend on the physical file structure | Changes in file structure require program modifications |

---

## 📝 GATE Exam Angle — Summary Points

1. These **8 problems are the direct motivation for DBMS** — nearly every "advantage of DBMS" question is testing the reverse of one of these points.
2. **Atomicity** and **Concurrency** problems are especially important — they connect directly to later chapters on **Transactions** (`06-transactions/`) and **Concurrency Control** (`07-concurrency-control/`).
3. **Data Independence** (lack of it in FPS) connects directly to the **Three-Level Architecture** chapter (`06-three-level-architecture.md`), where DBMS solves this exact problem.
4. Common trick in MCQs: distinguishing between **Data Redundancy** (duplication) vs **Data Inconsistency** (conflicting duplicated values) — redundancy is the *cause*, inconsistency is often the *effect*.
5. Remember the money-transfer example for Atomicity — it's the most commonly used illustration in textbooks and exams.

---

## 🔗 Conceptual Link
This chapter completes the "problem" side of the introduction. The next chapter, **Database and DBMS**, introduces the **solution** — showing how a Database and DBMS directly address each of these 8 problems.

---

**Previous:** [`02-file-processing-system.md`](./02-file-processing-system.md)
**Next:** [`04-database-and-dbms.md`](./04-database-and-dbms.md)
