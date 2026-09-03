# 04 — Database and DBMS

**Folder:** `docs/01-introduction/`
**File:** `04-database-and-dbms.md`
**Topics Covered:** Database (definition, advantages, disadvantages, applications), DBMS (definition, functions, components, users, DBA)

---

## Part A — Database

### 1. Definition

According to **Korth, Silberschatz, Sudarshan** (*Database System Concepts*):
> A database is a collection of interrelated data and a set of programs to access those data. The collection of data, usually referred to as the database, contains information relevant to an enterprise.

According to **Elmasri & Navathe** (*Fundamentals of Database Systems*):
> A database is a collection of related data. Data means known facts that can be recorded and that have implicit meaning.

Navathe further specifies that a database has these **implicit properties**:
1. A database represents some aspect of the real world, sometimes called the **mini-world** or the **Universe of Discourse (UoD)**. Changes to the mini-world are reflected in the database.
2. A database is a **logically coherent collection of data** with some inherent meaning. A random assortment of data cannot correctly be referred to as a database.
3. A database is **designed, built, and populated with data** for a specific purpose and intended group of users.

---

### 2. Key Characteristics of a Database

- Represents a **mini-world** (real-world enterprise/scenario)
- Data is **logically related and coherent** (not random)
- Built with a **specific purpose** and target audience in mind
- Can vary in size and complexity — from a small personal list to massive enterprise systems

---

### 3. Advantages of Database (over File Processing System)

*(These directly counter the 8 FPS problems from the previous chapter)*

| # | Advantage | Solves FPS Problem |
|---|---|---|
| 1 | **Controlling Redundancy** — centralized data storage avoids duplication | Data Redundancy & Inconsistency |
| 2 | **Restricting Unauthorized Access** — centralized security/authorization | Security Problems |
| 3 | **Providing Persistent Storage for Program Objects** | Data Isolation |
| 4 | **Providing Storage Structures for Efficient Query Processing** | Difficulty in Accessing Data |
| 5 | **Providing Backup and Recovery** | Atomicity Problems |
| 6 | **Providing Multiple User Interfaces** (query languages, GUIs, forms) | Difficulty in Accessing Data |
| 7 | **Representing Complex Relationships Among Data** | Data Isolation |
| 8 | **Enforcing Integrity Constraints** centrally | Integrity Problems |
| 9 | **Permitting Inferencing and Actions Using Rules** (e.g., triggers) | Integrity Problems |
| 10 | **Concurrency Control** — coordinated multi-user access | Concurrent Access Anomalies |

---

### 4. Disadvantages / Limitations of Database

1. **High Cost** — hardware, software licenses, and skilled personnel (DBA) are expensive
2. **Complexity** — DBMS software itself is complex to design, understand, and manage
3. **Performance Overhead** — additional processing needed for security, integrity checks, concurrency control, and recovery mechanisms
4. **Need for Specialized Staff** — requires trained Database Administrators (DBA) and skilled programmers
5. **Conversion Cost** — migrating from an old FPS-based system to a DBMS-based one involves significant time, cost, and risk

---

### 5. Applications of Database

| Sector | Example Use |
|---|---|
| **Banking** | Customer accounts, transactions, loans |
| **Airlines** | Reservations, schedules, ticketing |
| **Universities** | Student registration, grades, courses |
| **E-commerce** | Product inventory, orders, customer data |
| **Telecommunications** | Call records, billing |
| **Manufacturing** | Production tracking, supply chain, inventory |
| **Human Resources** | Employee records, payroll, attendance |
| **Healthcare** | Patient records, prescriptions, billing |

---

## Part B — DBMS (Database Management System)

### 1. Definition

According to **Korth, Silberschatz, Sudarshan**:
> A Database Management System (DBMS) consists of a collection of interrelated data and a set of programs to access that data. It is a general-purpose software system that facilitates the process of defining, constructing, manipulating, and sharing databases among various users and applications.

According to **Elmasri & Navathe**:
> A DBMS is a collection of programs that enables users to create and maintain a database. The DBMS is hence a general-purpose software system that facilitates the processes of defining, constructing, manipulating, and sharing databases among various users and applications.

**Core Idea:**
```
DBMS = Database (the data) + Set of Programs (software to manage it)
```

---

### 2. The Four Main Operations of a DBMS (Navathe)

1. **Defining** — specifying data types, structures, and constraints (via DDL)
2. **Constructing** — the process of storing the actual data on a storage medium
3. **Manipulating** — includes querying, updating, and generating reports (via DML)
4. **Sharing** — allowing multiple users/programs to access data concurrently

---

### 3. Functions of DBMS

1. **Data Definition** — via Data Definition Language (DDL); defines schema, structure, constraints
2. **Data Manipulation** — via Data Manipulation Language (DML); insert, update, delete, retrieve
3. **Data Security and Authorization** — controls who can access/modify what
4. **Data Integrity** — enforces constraints (e.g., primary key, foreign key, domain constraints)
5. **Concurrency Control** — manages simultaneous access by multiple users
6. **Backup and Recovery** — restores data to a consistent state after failure
7. **Data Dictionary Maintenance** — stores metadata (data about data)

---

### 4. Components of DBMS

| Component | Description |
|---|---|
| **Hardware** | Physical devices — computers, storage disks |
| **Software** | The DBMS software itself, plus OS and network software |
| **Data** | The actual data + metadata stored in the database |
| **Procedures** | Instructions/rules for designing and using the database |
| **Database Access Language** | Query languages like SQL |
| **Users** | People who interact with the database (see below) |

---

### 5. Types of DBMS Users

1. **Naive / Parametric Users**
   - Interact with the system through pre-written application programs
   - Example: Bank tellers, ATM users — they only fill forms/press buttons, no knowledge of underlying database

2. **Application Programmers**
   - Write application programs using programming languages (Java, Python, C++) combined with embedded DML statements
   - Build the interfaces that naive users interact with

3. **Sophisticated Users**
   - Interact with the system without writing full programs; instead they use query languages directly
   - Example: Data analysts, business users running SQL queries

4. **Specialized Users**
   - Write specialized database applications that don't fit the traditional data-processing framework
   - Example: CAD systems, knowledge-based/expert systems

5. **Database Administrator (DBA)**
   - Has **central control** over both the data and the programs that access it (detailed below)

---

### 6. Database Administrator (DBA) — Responsibilities

1. **Schema Definition** — creates the original database schema by writing DDL statements
2. **Storage Structure and Access Method Definition**
3. **Schema and Physical Organization Modification** — alters schema/storage as requirements evolve
4. **Granting of Authorization for Data Access** — controls which users can access which parts of the data
5. **Routine Maintenance** — includes:
   - Periodically backing up the database
   - Ensuring enough disk space is available
   - Monitoring jobs running and ensuring performance is not degraded

---

### 7. Advantages of DBMS (Recap)

- Reduced data redundancy
- Improved data consistency and integrity
- Improved data sharing among multiple users/applications
- Improved data security via centralized authorization
- Enforced standardization
- Facilitated backup and recovery

### 8. Disadvantages of DBMS

- Increased complexity of the overall system
- Higher cost (software, hardware, trained personnel)
- Performance overhead due to added generality (security, integrity checks)
- Higher impact of failure — since the system is centralized, a failure can affect all applications and users simultaneously

---

## Summary Table — Database vs DBMS

| Basis | Database | DBMS |
|---|---|---|
| **What it is** | The actual collection of related data | The software system managing that data |
| **Nature** | Data (passive) | Program/Software (active) |
| **Example** | Student records, bank account data | MySQL, Oracle, PostgreSQL, SQL Server |
| **Relationship** | Database is *stored inside/managed by* the DBMS | DBMS is the *tool* used to create/manage the database |

---

## 📝 GATE Exam Angle — Summary Points

1. **Database = Data**; **DBMS = Software to manage that data** — this distinction is a common 1-mark conceptual question.
2. Know the **4 core DBMS operations**: Define, Construct, Manipulate, Share.
3. **DBA responsibilities** are occasionally tested directly (matching-type questions) — remember: Schema definition, Storage/access method definition, Authorization granting, Routine maintenance.
4. **Types of users** (Naive, Application Programmer, Sophisticated, DBA) — classification-based questions are common; know to identify a user type from a given scenario.
5. Advantages/Disadvantages of DBMS map directly to Problems of FPS (previous chapter) — study them together, not in isolation.

---

## 🔗 Conceptual Link
This chapter builds the foundation for understanding **how** a DBMS is structured internally — covered next in **Database Environment** (`05-database-environment.md`) and then **Three-Level Architecture** (`06-three-level-architecture.md`).

---

**Previous:** [`03-problems-with-fps.md`](./03-problems-with-fps.md)
**Next:** [`05-database-environment.md`](./05-database-environment.md)
