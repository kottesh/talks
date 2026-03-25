---
title: "Key-Value Databases"
subtitle: "ADBMS (20MSSE07)"
author: "Shree Kottes J (7176 22 31 050)"
theme: "default"
header-includes:
  - \usepackage{graphicx}
  - \usepackage{booktabs}
---

# Introduction to Key-Value Stores

- **Definition**: A simple hash table where all access is via a primary key.
- **Analogy**: Similar to a two-column RDBMS table (ID, Name), but the "Name" (value) is an unrestricted blob.
- **Core Operations**:
  - `GET`: Retrieve value for a key.
  - `PUT`: Store/Overwrite value for a key.
  - `DELETE`: Remove key-value pair.
- **Philosophy**: The database is "schema-agnostic" regarding the value; the application is responsible for understanding the content.

# Terminology Comparison

| Oracle (RDBMS) | Riak (Key-Value) |
| :--- | :--- |
| Database Instance | Riak Cluster |
| Table | Bucket |
| Row | Key-Value Pair |
| RowID | Key |

# Storing Data in Key-Value Stores

- **Buckets**: Flat namespaces used to segment keys and reduce collisions.
- **Aggregation Strategies**:
  - **Single Object**: Storing all related data (Session, Profile, Cart) under one key.
  - **Key Segmentation**: Appending object names to keys (e.g., `sessionID_userProfile`).
  - **Domain Buckets**: Using separate buckets for different object types to handle serialization automatically.

# Data Storage Comparison

::: columns
:::: {.column width="50%"}
**Single Bucket Strategy**
\begin{figure}
\centering
\includegraphics[width=0.8\textwidth]{storing_all_data_in_single_bucket.png}
\caption{All data in one aggregate}
\end{figure}
::::
:::: {.column width="50%"}
**Segmented Key Strategy**
\begin{figure}
\centering
\includegraphics[width=0.8\textwidth]{segment_data_in_single_bucket.png}
\caption{Segmented keys within a bucket}
\end{figure}
::::
:::

---

\vfill
\begin{center}
\usebeamercolor[fg]{frametitle}
\textbf{Features of KV Databases}
\end{center}
\vfill
---

# Consistency

- **Scope**: Consistency is applicable only for operations on a **single key**.
- **Distributed Model**: Distributed K-V stores (like Riak) typically implement an **eventually consistent** model.
- **Conflict Resolution**:
  - **Last Write Wins (LWW)**: Newest write wins and older writes are lost.
  - **Siblings**: Multiple versions are returned, allowing the client to resolve the conflict.
- **Quorum Control**:
  - `nVal`: Number of replicas for the data.
  - `w`: Number of nodes that must respond for a successful write.
  - `r`: Number of nodes that must respond for a successful read.

# Transactions

- **Guarantees**: Generally, there are no multi-key ACID guarantees.
- **Quorum-based Writes**: Riak uses Quorum ($W$ value) to implement a form of transaction for single-key writes.
- **Write Tolerance**:
  - If Replication Factor ($N$) = 5 and $W$ = 3, the cluster can tolerate 2 nodes being down for write operations ($N - W = 2$).
- **Limitations**: If you need to save multiple keys and rollback on failure, standard K-V stores are not ideal.

# Query Features

- **Primary Method**: Query by Key.
- **Metadata Search**: Extensions like **Riak Search** allow querying data using Lucene-style indexes.
- **Key Design**:
  - Keys can be generated using algorithms or provided by users (email, userId).
  - Derived from timestamps or other external data.
- **Expiration**: Many stores support `expiry_secs` to automatically expire keys (e.g., sessions).

# Structure of Data

- **Schema-less**: Key-value databases don't care what is stored in the value part.
- **Formats**: Values can be Blobs, Text, JSON, XML, etc.
- **Advanced Types**: Stores like **Redis** support specialized data structures:
  - Lists
  - Sets
  - Hashes
  - Strings
- **Content-Type**: In Riak, the `Content-Type` header can be used to specify the data format (e.g., `application/json`).

# Scaling

- **Sharding**: K-V stores scale by distributing data across multiple nodes.
- **Shard Key**: The value of the key determines its physical storage node.
- **CAP Theorem Control**:
  - Users can fine-tune $N, R, W$ values at the bucket level.
  - Higher $W$ = Better Consistency, Lower Performance.
  - Higher $R$ = Better Consistency, Lower Availability.
- **Impact**: Adding nodes increases performance, but node failure can make specific key ranges unavailable.

# Suitable Use Cases

1. **Session Information**:
   - Web sessions are unique and indexed by `sessionid`.
   - Fast, single-request operations for session recovery.
2. **User Profiles and Preferences**:
   - Unique `userId` as the key.
   - Entire preference object retrieved in one `GET` call.
3. **Shopping Cart Data**:
   - Tied to `userid`.
   - Ensures cart availability across different devices and sessions.

# When NOT to Use

- **Relationships among Data**: If you need to correlate data between different sets of keys.
- **Multi-operation Transactions**: If you need ACID properties or "rollbacks" across multiple keys.
- **Query by Data**: If you need to search for values based on internal attributes.
- **Operations by Sets**: If you need to operate on multiple keys simultaneously (must be handled client-side).

---

\vfill
\begin{center}
{\usebeamerfont{title}\usebeamercolor[fg]{title} Thank you}
\end{center}
\vfill
