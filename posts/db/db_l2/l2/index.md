# Data base system - L2


***这篇文章展示了数据库系统的学习记录***


---

<!--more-->
# 1 Rational Data Model (record-based logical model)
---
## 1.1 Basic structure
* Relations:
  *  Data stored as tables (called relations); each has a unique name
  * A relation consists of rows (called tuples) and columns (called attributes)

* Attributes:
  * An attribute has a "domain" 

* Record:
  * Each row/tuple in a relation is a record (an entity)
  * Each attribute in a relation corresponds to a particular filed of a record

![](/posts/db/db_l2/pic/Rational_data_model.png)

> DB Schema: relatively ***static***, the whole structure
> DB instance: ***dynamic***, data & structure

---
## 1.2 Key

> Candidate and primary keys are also defined by relational data model
> Super keys are similar to candidate/primary keys, but are not required to be minimal. (可以有其他属性)
---
## 1.3 Characteristic of Relations

* Ordering of tuples in a relation r(R): The tuples are
***not considered to be ordered***, even though they appear
in order in the table form.

* Ordering of attributes in a relation schema R (and of
values within each tuple): We will consider the attributes
in R(A1, A2, ..., An) and the values in t=<v1, v2, ..., vn>
to be ***ordered*** .

* Values in a tuple: All values are considered atomic (indivisible). A special ***null*** value is used to represent values that are unknown or inapplicable to certain tuples.

> **Can a key attribute contain NULL values? Why?**
> *No, since a key attribute is a unique data to identify an entity in an entity set, if the key is null, which is meaningless.*

---
# 2 ER vs. Rational Data Model
---
## 2.1 Mapping ER Diagrams into Tables
---
### 2.1.1 Repersentation of Entity(Strong) sets
![](/posts/db/db_l2/pic/map1.png)

---
### 2.1.2 Repersentation of Weak Entity sets
![](/posts/db/db_l2/pic/map2.png)

---
### 2.1.3 Repersentation of M:N Relationship Sets
![](/posts/db/db_l2/pic/map3.png)

---
### 2.1.4 ER to relational schema
***Relation Table & Entity Table***
- **Relation table**
> *Strong relation*
> |primary keys of connecting entities|relation attributes(if any)|
> |---|---|
> *Weak relation*
> |primary keys of connecting strong entities|all attributes of all weak entities|
> |---|---|

- **Entity table**
> *Strong entity*
> |all attributes (sign the key attribute(s))|
> |---|
> *Weak entity*
> |all primary keys of corresponding strong entity|all attributes of weak entity|
> |---|---|

---
## 2.2 (min,max) notation
- (min,max) notation replaces the cardinality ratio(1:1,1:N,M:N) and single/double-line notation for participation constraints;
- Definition: 
> For **EACH** entity e in E, e **MUST participate** in **at least** $min$ and **at most** $max$ relationship instances in R at any point in time.
- Conver it into English: for a particular entity(e.g. Stundet A in Student Entity), MUST appear(participate) in **at most** $max$ & **at least** $min$ tuples in the table(relation R).
- As a result
  - For $min$
    - $min = 0\to$ **partial participation** - single line, not all entities participate
    - $min>0\to$ **total paricipation** - double line, all entities MUST appear in rows
  - For $max$
    - For a entity, it MUST appear in **at most** $max$ rows in a table

**[Example]**

![](/Y2S1/COMP2411/L2/pic/min_max_no.png)

---
**Translation** between Cardinality ratio and (min,max) notation:
1. Cardinality ratio **1:1** $\to$ (min,max): $(x,1)$;$(1,x)$
   - $x=0$, the entity has **partial** participation
   - $x=1$, the entity has **total** participation 

**Example**:

ID === HAS === Student
**Cardinality ratio 1:1**: double lines mean **total** participation
   - For every ID, it MUST be hold by one and only one student
   - For each student, he/she MUST has one and only one ID


ID =(1,1)= HAS =(1,1)= Student
**(min,max) notation**: in HAS tabke
  - Each student MUSt appear in the table one and only one row
  - Each ID MUSt appear in the table one and only one row

---
2. Cardinality ratio **1:N** $\to$ (min,max): $(x,N)$;$(1,x)$
   - $x=0$, the entity has **partial** participation
   - $x=1$, the entity has **total** participation
3. Cardinality ratio **N:1** $\to$ (min,max): $(x,1)$;$(N,x)$
   - $x=0$, the entity has **partial** participation
   - $x=1$, the entity has **total** participation

**Example**
Employee === WORKS_FOR === Department
**Cardinality ratio 1:N**: double lines mean **total** participation
   - One employee must work for one and only one department
   - One department must has at least one employee working for it

**(min,max) notation**: =(1,1)= WORKS_FOR =(1,N)= Department
  - Each employee MUST appear in the table one and only one row
  - Each department MUST appear in the table at least one row, **at most** N rows

---
4. Cardinality ratio **M:N** $\to$ (min,max): $(x,N)$;$(x,M)$
   - $x=0$, the entity has **partial** participation
   - $x=1$, the entity has **total** participation


---
# 3 SQL

## 3.1 Basic syntax (structure) of SQL
```SQL
SELECT [DISTINCT] attribute1,...
FROM table1 [name1], tabel2 [name2],...
    [WHERE requirement]
    [GROUP BY (attribute) HAVING requirement];

```

*[Example]*
> Following relational schema:
> Customer (cname, street, city)
> Branch (bname, assets, b-city) 
> Borrow (bname, loan#, cname, amount) 
> Deposit (bname, acct#, cname, balance)

- E1: Find all customers of the Sai Kong branch

```sql
(SELECT cname
FROM Deposit
WHERE bname = 'Sai Kong') -- 注意是单引号
UNION -- not only Deposit customres, but borrow customers
  (SELECT cname
  FROM Borrow
  WHERE bname = 'Sai Kong');
```

- E2: Find the name and city of all customers having a loan at the
Sai Kong branch
```sql
SELECT DISTINCT Customer.cname,city
FROM Borrow,Customer
WHERE Borrow.cname = Customer.cname
  AND Borrow.bname = 'Sai Kong';
```

- E3: Find the names of all customers whose street has the substring
‘Main’ included
```sql
SELECT cname
FROM Customer
WHERE Customer.street LIKE '%Main%';
```

- E4: Find all customers who have an account at some branch in
which Jones has an account
```sql
SELECT DISTINCT S1.cname
FROM Deposit S1
WHERE S1.bname IN
  (SELECT bname
   FROM Deposit S2
   WHERE S2.cname = 'Jones')
   AND S1.cname != 'Jnoes';
``` 
```sql
SELECT DISTINCT S2.cname
FROM Deposit S1,Deposit S2
WHERE S1.cname = 'Jnoes' 
AND S1.bname = S2.bname
AND S1.cname != S2.cname;
```

- E5: Find branches having greater assets than all branches in N.T.
```sql
SELECT B1.bname
FROM Branch B1
WHERE B1.assets > ALL (SELECT B2.assets
                       FROM Branch B2
                       WHERE B2.b-city = 'N.T.'
                       );
```
```sql
SELECT B1.bname
FROM Branch B1
WHERE NOT EXISTS
  (SELECT *
   FROM Branch B2
   WHERE B2.assets >= B1.assets
   AND B2.b-city = 'N.T.'
  ); 
```

- E6: Find names of all branches that have greater assets than some
branch located in Kowloon
```sql
SELECT bname
FROM Branch
WHERE assets > SOME 
  (SELECT assets
   FROM Branch
   WHERE b-city = 'Kwoloon');
```
```sql
SELECT bname
FROM Branch B1,Branch B2
WHERE B1.assets > B2.assets
AND B2.b-city = 'Kwoloon';
```

- E7: Find all customers who have a deposit account at allbranches located in Kowloon
```sql
SELECT DISTINCT S.cname
FROM Deposit S
WHERE 
 (SELECT T.bname
  FROM Deposit T account
  WHERE S.cname = T.cname) -- the set of branches he/she has a deposit account
CONTAINS
 (SELECT bname
  FROM Branch 
  WHERE b-city = 'Kowloon'); -- the set of branches on Kwoloon
```

- E8: Find all customers of Central branch who have an account there but no loan there
```sql
SELECT C.cname
FROM Customer C
WHERE EXISTS 
  (SELECT *
   FROM Deposit D 
   WHERE D.cname = C.cname
   AND D.bname = 'Central')
   AND NOT EXISTS
      (SELECT *
       FROM Borrow B
       WHERE B.cname = C.cname
       AND B.bname = 'Central');

```

- E9: Find all customers who have a deposit account at ALL branches located in Kowloon
```sql
SELECT DISTINCT S.cname
FROM Deposit S
 WHERE NOT EXISTS(
  (SELECT bname
   FROM Branch 
   WHERE b-city = 'Kowloon')
MINUS
  (SELECT T.bname customer S 
   FROM Deposit T
   WHERE S.cname = T.cname));
```

- E10: List in alphabetic order all customers having a loan at
branches in Kowloon
```sql
SELECT DISTINCT cname
FROM Borrow
WHERE b-city = 'Kowloon'
ORDER BY cname;  --By default, in ascending order.
```

- E11: List the entire borrow table in descending order of amount, and if several loans have the same amount, order them in ascending order by loan#
```sql
SELECT *
FROM Borrow
ORDER BY amount DESC, loan# ASC; -- when the <amount> is the same, order aomunt by <loan#> in ascending, and so on.
```

---
## 3.2 NULL Value
- ***All comparisons involving Null become FALSE!!!***
- ***A modification is permitted through a view ONLY IF the view is defined in terms of ONE base/physical relation(whether all the values of tuple are full).***

- In most SQL-based DBMSs, the special keyword NULL may be used to test for a null value.
  
*[like]*
```sql
SELECT c-name 
FROM Deposit 
WHERE balance IS NOT NULL;
```

---
## 3.3 Aggregate Function
-  Compute functions on groups of tuples using the `group by` clause 
   - Tuples with the *same value* on all attributes in the group by clause are placed in one group 
   - Aggregate function includeds: `avg`, `sum`, `min`, `count`, `max`

- E1: Find the average account balance at each branch:
```sql
SELECT b-name, AVG(balance) 
FROM Deposit 
GROUP BY b-name;
```

- E2:  If only interested in branches where average balance is > $12000:
```sql
SELECT b-name, AVG(balance)
FROM Deposit
GROUP BY b-name
HAVING AVG(balance) > 12000;
```

- E3:  Find those branches with the highest average balance:
```sql
SELECT b-name 
FROM Deposit 
GROUP BY b-name 
HAVING AVG(balance) = SELECT MAX(AVG(balance))
                      FROM Deposit 
                      GROUP BY b-name);
```

- E4: Find the average balance of all depositers who live in Laguna city and have at least 3 accounts:
```sql
SELECT AVG(balance) 
FROM Deposit, Customer 
WHERE Deposit.c-name = Customer.c-name 
AND city = 'Laguna' 
GROUP BY Deposit.c-name HAVING COUNT(DISTINCT acct#) >= 3;
```
---
***学习笔记，仅供参考***

