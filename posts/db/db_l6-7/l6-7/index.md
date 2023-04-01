# Data base system - L6-7


***这篇文章展示了数据库系统的学习记录***


<!--more-->
---
# 1 Disk Storage Devices
- Data stored as magnetized areas on magnetic disk surfaces. 
- A *disk pack* contains several magnetic disks connected to a rotating spindle.
-  Disks are divided into concentric circular ***tracks*** on each disk ***surface***. Track capacities vary typically from 4 to 50 Kbytes.
-  A track is divided into ***blocks*** (In some systems, there is an intermediate unit called ***sectors***). The block size B is fixed for each system. Typical block sizes range from B=512 bytes to B=4096 bytes.
- Whole blocks are transferred between disk and main memory
for processing.

![](/posts/db/db_l6-7/pic/sector_disk.png)

- A ***read-write*** head moves to the track that contains the block to be transferred. Disk rotation moves the block under the read-write head for reading or writing 
- A physical disk block address consists of a surface number, track number (within surface), and block number (within track)
- ***Reading or writing a disk block is time consuming*** because of the *seek time* $s$ and *rotational delay (latency)* $rd$
- Double buffering can be used to speed up the transfer of contiguous disk blocks

![](/posts/db/db_l6-7/pic/read-write_head.png)

---
# 2.1 File of Records
- A file is sequence of records, where each record is a collection of data values or items.
  - A *file descriptotr or header* includes information that describes the file, such as the *field names* and their *data tpyes*, and the addressseds of the file blocks on the disk.
  - Records are stored on disk blocks. The ***blocking factor*** **bfr** for a file is the (average) number of file records stored in a disk block. 
  - A file can have ***fixed-length*** records or ***variable-length*** records.

- File records can be
  - *unspanned*: no record can span two blocks
  - *spanned*: a record can be stored in more than one block
- In a file of **fixed-length** records, all records have the ***same*** format. Usually, unspanned blocking is used with such files. 
- Files of **variable-length** records require additional information to be stored in each record. Usually spanned blocking is used with such files. 
- The records of a file can be ***contiguous***, ***linked***, or ***indexed***.

---
## 2.2 Operation on Files

![](/posts/db/db_l6-7/pic/operation_file_1.png)

![](/posts/db/db_l6-7/pic/operation_file_2.png)

---
## 2.3 Unordered Files & ordered Files
- *Unordered Files*: also called *pile* file
- New records are insterted at the ***end*** of the file
- ***Linear search*** through the file is necessary, which requires reading and searching half the file blocks on the average. **QUITE EXPENSIVE**.
- Insertion is quite efficient
- Reading the records in order of a particular field requires sorting the file records.

|9|16|50|2|10|4|8|12|60|100|
|---|---|---|---|---|---|---|---|---|---|
---
- *Ordered Files*: also called *sequential* file
- File records are kept sorted by the values of an ordering field. 
- **Insertion is expensive**: records must be inserted in the correct position. It is common to keep a separate unordered overflow file for new records to improve insertion efficiency; this is periodically merged with the main ordered file
- A binary search can be used to search for a record on its ordering field value. This requires reading and searching ${log_2}^{n}$ of the file blocks on the average.
- Reading the records according to the order of the ordering field is quite efficient.

|2|4|6|14|18|50|100|5000|9000|100000|
|---|---|---|---|---|---|---|---|---|---|

---
## 2.4 Hashed Files
- Hashing for disk files is called **External Hashing** 
- ***Collisions*** occur when a new record hashes to a bucket that is
already full 
  - an **overflow** file is kept for storing such records;
  - *overflow* records that hash to each bucket can be linked together.

*[Resolution]*
  - **Open addressing**: Proceeding from the occupied position specified by the hash address, the program checks the subsequent positions in order until an unused (empty) position is found.
    - ***Linear Prob***: If collide, try Bucket_id+1, Bucket_id+2, …
    - ***Quadratic Prob***: If collide, try Bucket_id+1, Bucket_id+4,…(try to not affect the close neighbors like linear probing)

![](/posts/db/db_l6-7/pic/resolution_collision.png)

![](/posts/db/db_l6-7/pic/hashed_overflow_handle.png)

> Main disadvantagesof static external hashing:
> Fixed number of buckets M is a problem when the number of records in the file grows or shrinks.

---
## 2.5 Dynamic and Extendible Hashing Techniques
- Both **dynamic** and **extendible** hashing use the ***binary representation*** of the hash value h(K) in order to access a **directory**.
  - In dynamic hashing the directory is a binary tree. 
  - In extendible hashing the directory is an array of size $2^d$ where d is called the **global depth**.
- The directories can be stored on disk, and they expand or shrink **dynamically**.
- An insertion in a bucket that is full causes the bucket to ***split*** into two buckets and the records are **redistributed** among the two buckets.
- Dynamic and extendible hashing ***do not*** require an **overflow** area.

![](/posts/db/db_l6-7/pic/extendible_hashing.png)

---
# 3 Types of Single-level Indexes
- One form of an index:
    - a file of entries *<field value, ptr to record>*, which is ordered by field value
-  The index is called an ***access path*** on the field 
![](/posts/db/db_l6-7/pic/index_1.png)
![](/posts/db/db_l6-7/pic/index_2.png)

---
## 3.1 Primary Indexes

- Defined on an ordered data file 
- The data file is ordered on a ***key*** field 
- Includes one index entry for each block in the data file; the index entry has the key field value for the *first* record in the block, which is called the *block anchor*
- A similar scheme can use the last record in a block

![](/posts/db/db_l6-7/pic/primary_index_1.png)
![](/posts/db/db_l6-7/pic/primary_index_2.png)

---
## 3.2 Clustering Indexes
- Defined on an ordered data file 
- The data file is ordered on a *non-key* field 
- Includes one index entry for *each distinct value* of the field; the index entry points to the first data block that contains records with that field value

![](/posts/db/db_l6-7/pic/cluster_index_1.png)


---
## 3.3 Secondary Indexes
- A secondary index provides a secondary means of accessing a file for which some primary access already exists 
- The secondary index may be on a **candidate key field** or a **non-key field** 

> There can be many secondary indexes for the same data file.
- The index is an **ordered** file with two fields.
  - The first field is of the same data type as some ***non-ordering field*** (ie.,the indexing field) of the data file. 
  - The second field is either a block pointer or a record pointer 
  -  If we include one entry for each record in the data file, then it is called a *dense index* 


---
## 3.4 Multi-level Indexes
-  Because a single-level index is an ordered file, we can create a primary index to the index itself ; in this case, the original index file is called the *first-level index* and the  index to the index is called the *second-level index*

![](/posts/db/db_l6-7/pic/two-level_index.png)

---
# 4 B-Trees and B+-Trees as Dynamic Multi-level Indexes
- In B Tree and B+ Tree data structures, each node corresponds to a disk block
-  Each node is kept between *half-full* and *completely full*

---
*[An insertion into a node that is not full is quite efficient; if a node is full the insertion causes a split into two nodes]*

*[If a deletion causes a node to become less than half full, it must be merged with neighboring nodes]*

- In a B tree, pointers to data records exist at all levels of the tree 
- In a B+ tree, all pointers to data records exists at the leaf-level nodes 
- Internal pointer ***must*** point to a block

---

- A search tree of order $p$ is a tree such that each node contains at most $p−1$ **search values** and $p$ **pointers**
  - Each internal node has at most $p$ tree **pointers**, $p-1$ **value(s)**.
  - Each internal node, except the root, has at least $⎡(p/2)⎤$ tree **pointers**,  $⎡(p/2)⎤-1$ **value(s)**. The root node has at least two tree **pointers** if it is an internal node.

![](/posts/db/db_l6-7/pic/B-tree_node.png)
![](/posts/db/db_l6-7/pic/B+-tree_node.png)

---

- During the insertion, the node has to be splited when it is full. 
- During the deletion, the node has to be merge when it is too small (number of value < $⎡(p/2)⎤-1$). Normally, we choose the **left leaf node** of the **same subtree** to merge. *(When there exists right or left leaf node within a same subtree, it should be different results.)*



![](/posts/db/db_l6-7/pic/insertion_B+_1.png)
![](/posts/db/db_l6-7/pic/insertion_B+_2.png)
![](/posts/db/db_l6-7/pic/deletion_B+.png)

---
# 5 Physical Database Design Decisions
---
# 5.1 Physical Database Design Decisions 
- Denormalization as a design decision for speeding up queries 
  - The goal of ***normalization*** is to separate the logically related attributes into tables to ***minimize redundancy*** and thereby ***avoid the update anomalies*** that cause an ***extra processing overheard*** to ***maintain consistency*** of the database.
  - The goal of ***denormalizationis*** to improve the performance of ***frequently occurring queries and transactions.*** (Typically the designer adds to a table attributes that are needed for answering queries or producing reports so that a join with another table is avoided.)

---
## 5.2 Tuning
- Goal:
  - To make application run faster
  - To lower the response time of queries/transactions
  - To improve the overall throughput of transactions

- Tuning Index
- Tuning Queries

---
***学习笔记，仅供参考***
