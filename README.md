# 📘 DBMS GATE Handbook

A structured, topic-wise handbook for **Database Management Systems (DBMS)**, prepared from standard reference books — *Database System Concepts (Korth, Sudarshan)*, *Fundamentals of Database Systems (Elmasri & Navathe)*, and *Database Management Systems (Ramakrishnan)* — with a strong focus on **GATE exam preparation**.

---

## 📂 Repository Structure

```
dbms-gate-handbook/
│
├── README.md
├── LICENSE
│
├── docs/
│   ├── 01-introduction/
│   ├── 02-er-model/
│   ├── 03-relational-model/
│   ├── 04-sql/
│   ├── 05-normalization/
│   ├── 06-transactions/
│   ├── 07-concurrency-control/
│   ├── 08-recovery/
│   ├── 09-indexing-file-organization/
│   └── 10-query-processing/
│
├── pyqs/
│   └── gate-pyqs-topicwise.md
│
├── assets/
│   └── images/
│
└── resources/
    └── reference-books.md
```

---

## 📑 Chapter-wise File List

### `docs/01-introduction/`
| File Name | Topic |
|---|---|
| `01-data-and-information.md` | Data, Information, Data vs Information |
| `02-file-processing-system.md` | File Processing System (FPS) |
| `03-problems-with-fps.md` | Problems/Limitations of FPS |
| `04-database-and-dbms.md` | Database, DBMS definitions, advantages/disadvantages |
| `05-database-environment.md` | Components of Database Environment |
| `06-three-level-architecture.md` | 3 Levels of Data Abstraction, ANSI-SPARC Architecture |
| `07-schema-instance-view.md` | Schema, Instance, View — explained |
| `08-basic-terms-and-data-models.md` | Entity, Attribute, Relation, Data Models |

### `docs/02-er-model/`
| File Name | Topic |
|---|---|
| `01-entities-attributes-relationships.md` | ER Model basics |
| `02-er-diagram-notations.md` | ER Diagram symbols and notations |
| `03-eer-generalization-specialization.md` | EER — Generalization, Specialization, Aggregation |

### `docs/03-relational-model/`
| File Name | Topic |
|---|---|
| `01-relational-model-basics.md` | Relations, Tuples, Attributes, Domains |
| `02-keys-constraints.md` | Super key, Candidate key, Primary key, Foreign key, Constraints |
| `03-relational-algebra-calculus.md` | Relational Algebra & Relational Calculus |

### `docs/04-sql/`
| File Name | Topic |
|---|---|
| `01-ddl-dml-dcl-tcl.md` | SQL Command Categories |
| `02-joins-subqueries.md` | Joins, Nested Queries |
| `03-aggregate-functions-grouping.md` | GROUP BY, HAVING, Aggregate Functions |

### `docs/05-normalization/`
| File Name | Topic |
|---|---|
| `01-functional-dependency.md` | Functional Dependencies, Armstrong's Axioms |
| `02-normal-forms-1nf-to-bcnf.md` | 1NF, 2NF, 3NF, BCNF |
| `03-4nf-5nf-decomposition.md` | 4NF, 5NF, Lossless Decomposition |

### `docs/06-transactions/`
| File Name | Topic |
|---|---|
| `01-transaction-states-properties-acid.md` | Transaction States, ACID Properties |
| `02-schedules-serializability.md` | Schedules, Conflict/View Serializability |

### `docs/07-concurrency-control/`
| File Name | Topic |
|---|---|
| `01-locking-protocols.md` | Lock-based Protocols, 2PL |
| `02-timestamp-validation-protocols.md` | Timestamp Ordering, Validation-based Protocols |

### `docs/08-recovery/`
| File Name | Topic |
|---|---|
| `01-log-based-recovery-checkpoints.md` | Log-based Recovery, Checkpoints, Deferred/Immediate Update |

### `docs/09-indexing-file-organization/`
| File Name | Topic |
|---|---|
| `01-file-organization-methods.md` | Sequential, Heap, Hashed File Organization |
| `02-indexing-b-trees-hashing.md` | B-Tree, B+ Tree, Static/Dynamic Hashing |

### `docs/10-query-processing/`
| File Name | Topic |
|---|---|
| `01-query-optimization-basics.md` | Query Processing Steps, Optimization Basics |

### `pyqs/`
| File Name | Topic |
|---|---|
| `gate-pyqs-topicwise.md` | GATE Previous Year Questions, topic-wise |

### `resources/`
| File Name | Topic |
|---|---|
| `reference-books.md` | List of reference books used (Korth, Navathe, Elmasri, Ramakrishnan) |

---

## 🎯 Purpose
This handbook is built for **GATE CS/IT aspirants** who want concise, book-referenced notes on DBMS instead of scattered internet material. Each `.md` file follows a consistent format:
- Definition (as per reference book)
- Key Points
- Diagrams (where applicable, stored in `assets/images/`)
- GATE Tips / Common Question Patterns

## 📚 Reference Books
- *Database System Concepts* — Silberschatz, Korth, Sudarshan
- *Fundamentals of Database Systems* — Elmasri & Navathe
- *Database Management Systems* — Raghu Ramakrishnan

## 🚧 Status
Work in progress — chapters are being added topic-wise as the study progresses.

---

## 🤝 Contribution
This is a personal study handbook, but suggestions/corrections are welcome via issues or pull requests.
