# 02 — File Processing System (FPS)

**Folder:** `docs/01-introduction/`
**File:** `02-file-processing-system.md`
**Topics Covered:** File Processing System (Traditional File-Based Approach)

---

## 1. What is a File Processing System?

### Definition
According to **Korth, Silberschatz, Sudarshan** (*Database System Concepts*):
> Before the advent of DBMS, organizations typically stored information in a file-processing system, using a collection of files stored on a fixed disk, maintained by application programs written specifically for those files.

According to **Elmasri & Navathe** (*Fundamentals of Database Systems*):
> A File Processing System is a system where each application program defines and manages its own data, storing it in permanent files (also called flat files), and each program has its own logic to access and manipulate that data.

In simple terms — before DBMS existed, data was stored directly in **files** (like `.dat`, `.txt`) on the operating system, and every application had its own separate files with its own program logic to read/write them. There was **no centralized management** of data.

---

## 2. Structure of a File Processing System

```
┌─────────────────────┐      ┌─────────────────────┐
│  Application 1       │----->│  File 1 (own format) │
│  (e.g., Payroll)      │      └─────────────────────┘
└─────────────────────┘

┌─────────────────────┐      ┌─────────────────────┐
│  Application 2       │----->│  File 2 (own format) │
│  (e.g., Inventory)    │      └─────────────────────┘
└─────────────────────┘

┌─────────────────────┐      ┌─────────────────────┐
│  Application 3       │----->│  File 3 (own format) │
│  (e.g., Library)      │      └─────────────────────┘
└─────────────────────┘
```

- Each **application program** directly accesses its **own dedicated file(s)**.
- Data definitions (field names, formats) are **hardcoded inside the application program**, not stored separately.
- There is **no shared/common access mechanism** across applications.

---

## 3. Real-World Example

Consider a **University** before DBMS was adopted:

| Department | File Maintained | Program Used |
|---|---|---|
| Accounts | `fee_records.dat` | Custom COBOL/C program for fee processing |
| Examination | `result_records.dat` | Separate program for result processing |
| Library | `book_issue.dat` | Separate program for issue/return tracking |

Notice: A student's **Name** and **Roll Number** might be stored **separately in all three files**, maintained independently — this duplication is the root of most FPS problems (covered in the next chapter).

---

## 4. Key Characteristics of File Processing Systems

1. **Application-specific files** — each program has its own file(s); no sharing.
2. **Data definitions embedded in program code** — file structure (field types, lengths) is defined within the application, not centrally.
3. **No standard query language** — retrieving data requires writing new code for every new type of request.
4. **Manual data integrity enforcement** — every constraint (e.g., "salary > 0") must be coded individually in each program.
5. **Limited or no concurrency control** — multiple users accessing the same file simultaneously can cause conflicts.
6. **File organization types typically used:**
   - Sequential file organization
   - Indexed file organization
   - Direct/Random file organization
   *(these are covered in detail later, in `09-indexing-file-organization/`)*

---

## 5. Why FPS Was Used Historically

Before centralized database systems existed (pre-1970s, before Codd's relational model), FPS was the **only available approach** because:
- Storage and processing power were limited
- Organizations had smaller, simpler data-processing needs
- Programming languages (COBOL, FORTRAN) directly supported file handling

As organizational data needs grew more complex (more applications sharing overlapping data), FPS's limitations became a major bottleneck — which directly led to the **development of DBMS** (this evolution is important conceptually and appears often as a "why DBMS was introduced" question).

---

## 📝 GATE Exam Angle — Summary Points

1. FPS = data stored in **independent flat files**, each managed by a separate application program.
2. **No central control** over data — data definitions live inside program code.
3. FPS predates DBMS; DBMS was developed specifically to solve FPS's core issues (redundancy, inconsistency, poor querying, etc. — see next chapter).
4. Common file organizations used in FPS: Sequential, Indexed, Direct/Random.
5. Understanding FPS is essential as a **contrast baseline** — most "advantages of DBMS" questions are actually testing "problems of FPS" in reverse.

---

## 🔗 Conceptual Link
This chapter sets up the motivation for the next one — **Problems with File Processing System** — which is one of the most frequently tested conceptual topics in GATE DBMS (redundancy, inconsistency, isolation, integrity, atomicity, concurrency, security).

---

**Previous:** [`01-data-and-information.md`](./01-data-and-information.md)
**Next:** [`03-problems-with-fps.md`](./03-problems-with-fps.md)
