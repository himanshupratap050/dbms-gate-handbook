# ER Model — Basics (Entities & Attributes)

> **Chapter:** 02 — ER Model
> **File:** 01 — ER Model Basics
> **References:** Elmasri & Navathe (Ch. 3, 7th Ed.), Korth/Silberschatz/Sudarshan (Ch. 6, 7th Ed.), Ramakrishnan & Gehrke (Ch. 2)

---

## 1. Why ER Model? (Context)

Database design ka pehla step hai **conceptual design** — real-world requirements ko ek high-level, implementation-independent model mein represent karna. **Entity-Relationship (ER) Model**, jo Peter Chen ne 1976 mein propose kiya tha, isi purpose ke liye use hota hai.

> **Elmasri & Navathe definition:** The ER model describes data as entities, relationships, and attributes.

ER model ka output ek **ER diagram** hota hai, jise baad mein relational schema mein convert kiya jaata hai (ye mapping Chapter 02 ki file 06 mein cover hogi).

**GATE Perspective:** Is topic se directly diagram-based questions kam aate hain, lekin ER-to-relational mapping aur cardinality/participation constraints wale questions bohot common hain. Concepts clear hone chahiye taaki mapping rules easily apply ho sakein.

---

## 2. Entity and Entity Set

### 2.1 Entity

> **Korth definition:** An entity is a "thing" or "object" in the real world that is distinguishable from all other objects.

Example: Ek specific student, "Rahul Sharma, roll no. 21" — ye ek entity hai.

### 2.2 Entity Set

> **Korth definition:** An entity set is a set of entities of the same type that share the same properties, or attributes.

Example: "STUDENT" entity set — sabhi students ka collection, jinke attributes (name, roll_no, dob) same structure follow karte hain.

**Note:** Elmasri & Navathe entity set ko "entity type" bhi kehte hain, aur us type ke actual entities ke collection ko "entity set" ya "extension" kehte hain. GATE mein dono terms interchangeably use ho sakte hain, isliye confuse mat hona.

| Term | Korth | Elmasri & Navathe |
|---|---|---|
| Category/class of entities | Entity Set | Entity Type |
| Actual collection of entities at a point in time | Entity Set (same term) | Entity Set / Extension |

### 2.3 Entity Types

- **Strong Entity:** Apna khud ka primary key hota hai. Independent existence hoti hai. (e.g., STUDENT, COURSE)
- **Weak Entity:** Apna khud ka sufficient primary key nahi hota; kisi strong (owner/identifying) entity par existence-dependent hota hai. Isko **partial key (discriminator)** ke saath identify kiya jaata hai.
  - Example: DEPENDENT entity (employee ke family members) — apne aap identify nahi ho sakta, EMPLOYEE ke through hi identify hota hai.
  - Weak entity ka relationship jo use owner se connect karta hai use **identifying relationship** kehte hain.

**GATE Tip:** Weak entity ki diagram notation (double rectangle) aur identifying relationship (double diamond) ka notation yaad rakhna — diagram-reading questions mein directly puchha jaata hai.

---

## 3. Attributes

> **Elmasri & Navathe definition:** Attributes are properties that describe an entity.

Har entity ke attributes hote hain jo uske characteristics describe karte hain. Attributes types niche diye gaye hain — ye classification GATE mein bohot important hai.

### 3.1 Simple (Atomic) vs Composite Attributes

- **Simple/Atomic Attribute:** Further divide nahi ho sakta. Example: `roll_no`, `age`.
- **Composite Attribute:** Sub-parts mein divide ho sakta hai, jinka apna meaning hota hai. Example: `Name` → `First_Name`, `Middle_Name`, `Last_Name`. `Address` → `Street`, `City`, `State`, `Pincode`.

### 3.2 Single-valued vs Multivalued Attributes

- **Single-valued:** Ek entity ke liye sirf ek value hoti hai. Example: `date_of_birth`.
- **Multivalued Attribute:** Ek entity ke liye multiple values ho sakti hain. Notation mein double oval/ellipse se represent karte hain. Example: `Phone_Numbers` (ek person ke multiple numbers ho sakte hain), `Degrees` (ek employee ke multiple degrees).
  - Multivalued attributes par **lower and upper bounds** bhi define kiye ja sakte hain — e.g., `{Phone_Number}(1,3)` matlab minimum 1, maximum 3 phone numbers.

### 3.3 Stored vs Derived Attributes

- **Stored Attribute:** Directly database mein store hoti hai. Example: `date_of_birth`.
- **Derived Attribute:** Kisi aur attribute se compute ki jaa sakti hai, isliye store nahi ki jaati. Example: `Age` (derived from `date_of_birth`), `Years_Employed` (derived from `date_of_joining`).
  - Notation: dashed oval/ellipse.

### 3.4 Key Attribute

Wo attribute jiski value har entity ke liye **unique** ho — entity set ke andar entities ko distinguish karne ke liye use hota hai. Diagram mein underline karke represent karte hain.

**GATE Tip:** Composite + multivalued attribute ka combination bhi possible hai — e.g., `Address` composite hai aur agar person ke multiple addresses ho sakte hain to wo multivalued bhi ho sakta hai. Aise nested cases diagram-based MCQs mein aate hain.

---

## 4. Comparison Table — Attribute Types at a Glance

| Attribute Type | Definition | Notation (ER Diagram) | Example |
|---|---|---|---|
| Simple | Not divisible further | Single oval | `Roll_No` |
| Composite | Divisible into sub-parts | Oval with sub-ovals | `Name` → `First`, `Last` |
| Single-valued | One value per entity | Single oval | `DOB` |
| Multivalued | Multiple values allowed | Double oval | `Phone_Numbers` |
| Stored | Directly stored | Single oval | `DOB` |
| Derived | Computed from other attributes | Dashed oval | `Age` |
| Key | Uniquely identifies entity | Underlined | `Roll_No` |

---

## 5. Domain of an Attribute

Har attribute ka ek **domain** hota hai — values ka set jo wo attribute le sakta hai.

> **Korth definition:** For each attribute, there is a set of permitted values, called the domain, or value set, of that attribute.

Example: `Age` attribute ka domain ho sakta hai integers 0–120 tak.

---

## 6. GATE-Specific Tips (Summary)

1. **Weak entity vs strong entity** ka difference — weak entity ka apna primary key nahi hota, sirf partial key hota hai jo owner ke primary key ke saath milke unique banta hai. Isse confuse mat karna ki weak entity ki koi key hi nahi hoti.
2. **Composite + Multivalued attribute** wale diagram-based tricky questions practice karo.
3. **Derived attributes** ko schema mein column ki tarah treat nahi karte — ye ek common conceptual mistake hai jo MCQs mein test hoti hai.
4. Terminology confusion avoid karo: "Entity Type" (Elmasri) = "Entity Set" (Korth) — dono ek hi cheez ke liye use hote hain conceptually, but exam mein jo bhi term diya ho usi context mein samjho.
5. Attribute classification (simple/composite, single/multi-valued, stored/derived) — ye classification khud se ek diagram dekh kar identify karna aana chahiye.

---

**Next file:** `02-relationships-and-cardinality.md` — Relationship types, degree, cardinality ratios, participation constraints.
