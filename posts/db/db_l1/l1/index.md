# Data Base system - L1


***这篇文章展示了数据库系统的学习记录***

---

<!--more-->
## 1.1 What is Database(DB)?

> A **non-redundant**, **persistent**(like store in hard disk) collection of **logically related** records/files that are *structured* to support various **processing and retrieval needs**.


---
## 1.2 Database Management System

> A set of software programs for creating, storing, updating, and accessing the data of a DB.

---
## 1.3 Basic concept and terminologies
* instance *(compared to the instance in oop)*
  * the collection of data (information) stored in the DB at a particular moment (ie, a snapshot)
  * The data in the database at **a particular moment in time** is called a database state or snapshot. It is also called the current set of occurrences or **instances** in the database.
  
* scheme/schema
  *  the overall structure (design) of the DB -- relatively static

![](/posts/db/db_l1/schema.png)

---
## 1.4 Data Abstraction: 3-level architecture
![](/posts/db/db_l1/3-level.png)

* ***Internal/Physical Level***: the complete details of data storage and access paths for the database. (i.e., SSD,Cloud,disk)(**how** data are actually stored)
  * *Internal level has an internal schema, which describes the physical storage structure of the database.*
  
* ***Conceptual Level***: which describes the structure of the whole database. For a 2D array, it will be stored as a "**table**" in database. It hides the detail of internal level.(**what** data are actually stored)
  * *The conceptual schema hides the details of physical storage structures and concentrates on **describing entities, data types, relationships, user operations, and constraints.(data model)***

* ***External Level***: It only privides the data which the user wants and hide the rest of the datbase. 

> Consider a two-dimensional integer array of size n*m
> - The *physical level* would simply be n × m (probably consecutive) storage locations
> - The *conceptual level* is a grid of boxes, each possibly containing an integer, which is n boxes high by m boxes wide.
> - There are $2^{n×m}$ possible views (*external level*). For example, a view might be the entire array, or may be a part of array.

---
## 1.5 Data Independence
  * The ability to modify a schema definition in one level *without* affecting a schema in the next higher level 

  - Physical data independence: capacity to change the *internal schema* **without** having to change the *conceptual schema*
  - Logical data independence: the capacity to change the *conceptual schema* **without** having to change *external schemas or application programs*.



> DB System Architecture
> ![](/posts/db/db_l1/DB_Sys_Arch.png)
---
# 2 The Entity-Relationship Model(实体关系模型)

## 2.1 Basic Definition
---
### 2.1.1 ER模型的作用
  * 数据库设计的第一步是需求分析阶段，也是最重要的一步
  * 概念建模也就是ER建模,将需求以ER图的方式进行可视化
  * ER图可以描述一个数据库的逻辑结构

---
### 2.1.2 ER模型的组成

#### 2.1.2.1 entity
  * **entity(实体)**: a distinguishable object with *an* independent existence 
    > * 一个entity可以是具体的(如：人，书，CityU), 也可以是抽象的(如：假期)

  * **entity set**: a set of entities of the same type
    > * Like: Student Bank......

---
#### 2.1.2.2 attribute
  * **attribute**(属性): 一个entity用一组attributes来表示，每一个attribute有一个对应的值，比如一个人可以有**name，SSN，gender，phone number**等attributes
    * *Different type of Attributes*: 
      * **Simple**:  Each entity has a single atomic value for the attribute. *For example SSN or Sex*
      * **Composite**: The attribute may consist of several components. *For example, Name(FirstName, MiddleName, LastName).*
      * **Multi-valiue**: An entity may have multiple values for that attribute. *For example, Color of a CAR, denoted as {Color}.*
      >  In general, composite and multi-valued attributes may be nested.
    * **Domain**: 一个attribute的domain是这个attribute值的有效范围 
    * Formally, an attribute **A** is a function which maps from an entity set **E** into a domain **D**:
    $$A: E\to D$$

---
#### 2.1.2.3 relationship
  * **Relationship**: the relationship(association) among several entities

    > An attribite *$A:E\to D$* is a "simplified form of a relationshihp"
    > * if we allow **D** to be an Entity Set, then **A** becomes a relationship
    
    > A realtionship can carry attribute  
    > * Example: Patrick takes cs2450 with a grade of B+.
    > "takes" is relationship bteween "Patrick" and "CS2450", "B+" is the attribute of this relationship, since "B+" is neither the attribute of "Patrick" nor "CS2450", which is **"Patrick takes cs2450"**

    * The **degree** of a relationship set/type is the number of participating entity sets/types.
      * Both *MANAGES* and *WORKS_ON* are **binary** relationships.
      * In general, an n-ray relationship is **not equialent** to n binary relationships.
    * The relationship has participation constraint
      * partial participation: **single line** (not all entity participate)
      * total participation: **double line** (every entity participate)

![](/posts/db/db_l1/total_participation.png)

  * (min,max) notation for relationship
    * Specified on each participationof an entity set E
in a relationship set R 
    * Specifies that each entity e in E participates in at
**least** min and at **most** max relationship instances in R 
    * Default (no constraint): min=0, max=n ! Must have: $min<=max,min>=0,max>=1$

![](/posts/db/db_l1/min_max_no.png)
![](/posts/db/db_l1/ternay_rela.png)

  > (a) is not equivalent to (b) but to (c).
---
## 2.3 ER diagram  

---
### 2.3.1 ER图的基本构成

* Rectangles(正方形): Entity Sets
* Ellipses(椭圆形): Attributes
* Diamonds(菱形): Relationship Sets
* Lines: Attributes to Entity/ Relationship Sets or, Entity Sets to Realtionship Sets

![](/posts/db/db_l1/ER_Diagram.png)

* 不同的键(Key): to distinguish individual entities or relationships
  * *Superkey* (超键): a set of one or more **attributes** which, taken together, identify uniquely an entity in an entity set
    * 在关系中能**唯一标识**元组的属性集称为关系模式的超键
    * Example: 一般来说，学号是标识学生实体的唯一标识，所以该元组的超键就为学号。我们可以将学号和其他属性结合起来，(学号，性别)，(学号，年龄)等也为超键。
  ---
  * *Candiaite key*(候选键): minimal set of attributes which can identify uniquely an entity in an entity set
    * 最小的超键，仅包括独一标识实体所必需得**最小属性的数量**，即不含多余属性的超键为候选键
    * Example: stident ID identify a student, but Name is not a candidate key
> **候选键是超键的子集**

  ---
  * *Primary key*(主键):  a **candidate key** chosen by the DB designer to identify an entity in an entity set
    * 是从候选码(candidate key)中人为挑选的一个
  * *Foreign key*: FK is a set of attributes of R1, which refers to the PK(primary key(s)) of R2
    * Domain of FK should be the same as PK
    * t1[FK] in R1 either occurs as a value of t2[PK] in R2 or is NULL.

---
* 实体间的联系
* Integrity Constraints
  * *One-to-one*(一对一): 例如班级和班长之间就是一对一联系，一个班级只有一个班长

![](/posts/db/db_l1/1-to-1.png)

  * *One-to-many*(一对多/多对一): 例如一个班级有一个辅导员，但担任辅导员的老师可以同时担任其他班级的辅导员，所以辅导员和班级之间就是一对多联系

![](/posts/db/db_l1/1-to-many.png)

  * *Many-to-many*(多对多): 例如一个学生可以学习多门课程，每门课程也可以有多个学生，那么学生和课程之间的关系就是多对多联系

---
* *Weak Entity Set*
  * An entity set that does NOT have enough attributes to form a primary/candidate key

![](/posts/db/db_l1/Weak_entity_set.png)

---
![](/posts/db/db_l1/ER-example.png)

![](/posts/db/db_l1/ER-Notation.png)

---
***学习笔记，仅供参考***
