# AWS Solution Support Architect — NoSQL Notes

## 1. Key-Value Stores

I understand **Key-Value databases** like a giant **HashMap**.

Example:

```java
Map<String, String> map = new HashMap<>();
```

Database version:

```text
Key       → Value
Name      → Devanshi
Birthday  → 11-12-1985
Hobbies   → Archery
```

### How it works
- Every value has a unique key
- I access data directly using the key
- Very fast lookup (**O(1)** average)

### Best for
- Caching
- Session storage
- User profiles
- Shopping carts

### Popular examples
- Redis
- Amazon DynamoDB
- Apache Cassandra
- Couchbase
- Riak
- Voldemort

### Companies using it
- Instagram
- Amazon
- Twitter
- LinkedIn

---

## 2. Graph Databases

I use Graph DB when **relationships matter more than rows**.

Example:

```text
Devanshi → friend → Rahul
Rahul → buys → Product
```

### Components
- **Node** = object/entity
- **Edge** = relationship
- **Attribute** = properties

Example:

```text
Node: Devanshi
Attribute: Age = 21
Edge: Friend of Rahul
```

### Best for
- Social networks
- Recommendation engines
- Fraud detection
- Route optimization

### Example
- Neo4j

---

## 3. Column-Oriented Stores

Traditional SQL stores by rows:

```text
Row1 → full row
Row2 → full row
```

Column DB stores by columns:

```text
Name column
Price column
Date column
```

### Benefits
- Faster analytics
- Reads only needed columns
- Avoids storing many nulls
- Better compression

### Best for
- Big data
- Analytics
- Log processing

### Examples
- Google Bigtable
- Apache HBase

---

# Characteristics of NoSQL

NoSQL follows **BASE**, not ACID.

---

## BASE

### B = Basically Available
System tries to remain available.

---

### S = Soft State
Data can temporarily change.

---

### E = Eventually Consistent
Data becomes consistent after some time.

Example:
Server A updated now → Server B updates after a few seconds.

---

# CAP Theorem

I cannot maximize all 3 together.

```text
C = Consistency
A = Availability
P = Partition Tolerance
```

I can choose only **2 out of 3**.

---

## 1. Consistency
All users see same data.

Example:
Balance = ₹100 everywhere

---

## 2. Availability
System always responds.

Even if slightly old data is returned.

---

## 3. Partition Tolerance
System continues even if network fails.

Critical for cloud systems.

---

# Example with DynamoDB

Amazon DynamoDB usually chooses:

✅ Availability  
✅ Partition Tolerance  

Slight compromise on immediate consistency.

---

# Quick Comparison Table

| Type | Stores | Best For | Example |
|------|--------|----------|---------|
| Key-Value | key → value | caching/session | Redis |
| Graph | nodes + edges | relationships | Neo4j |
| Column | columns | analytics | HBase |
| Document | JSON docs | flexible apps | MongoDB |

---

# Final Understanding

I use **NoSQL** when I need:

- Huge scalability
- Flexible schema
- Fast performance
- Distributed architecture
- Real-time applications

**NoSQL is built for modern cloud applications.**
