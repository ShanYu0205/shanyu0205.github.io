# Data base system - L4


***这篇文章展示了数据库系统的学习记录***

<!--more-->
---
# Relational Algebra
![](/posts/db/db_l4/pic/whole_table.png)


---
## 1.1 SELECT σ and PROJECT π

### 1.1.1 SELECT
- SELECT operation (denoted by **σ**):
  - Form of the operation: $σ_{c}(R)$
  - Selects the tuples (rows) from a relation R that satisfy a certain ***selection condition c***.
  - The condition c is an arbitrary Boolean expression on the attributes of R 
  - Resulting relation has the ***same attributes*** as R.

![](/posts/db/db_l4/pic/select.png)

---
### 1.1.2 PROJECT
- PROJECT operation (denoted by **π**):
  - Form of the operation: $π_{L}(R)$
  - Keeps only certain attributes (columns) from a relation R specified in an ***attribute list L***.
  - Resulting relation has only those attributes of R specified in L(***subtable of R***).

![](/posts/db/db_l4/pic/project.png)

---
## 1.2 Select & Project

![](/posts/db/db_l4/pic/select&project.png)
![](/posts/db/db_l4/pic/ex_s&p.png)
![](/posts/db/db_l4/pic/ex1_p.png)
> *Not allow any duplicated for a **combined attribute** value* (e.g. $\pi_{Sex,Salary}$ not allow the same **combined attribute(Sex,salary)**, so the (F,25000) appears only once)

---
### 1.2.1 Combined Select and Project Operation
- Several operations can be combined to form a relational algebra expression (query)
> EX: Retrieve the names and salaries of employees whon work in department 4
> $π_{FNAME,LNAME,SALARY}(σ_{DNO=4}(EMPLOYEE))$
> We also can specify explicitly:
> DEPT4_EMPS$\leftarrow$$σ_{DNO=4}(EMPOYEE)$
> R$\leftarrow$ $π_{FNAME,LNAME,SALARY}$(DEPT4_EMPS)

---
### 1.2.2 Rename

![](/posts/db/db_l4/pic/rename.png)
![](/posts/db/db_l4/pic/table_rename&combined.png)

---
## 2.1 Set Operation

- For $\cap, \cup, - $
  - The operand must have the ***same number of attributes***
  - The *domain* of corresponding attributes must be compatible(union compatibility)
  - The *resulting relation* for $\cap, \cup, -$ has the same attribute names as the *first relation R1*

![](/posts/db/db_l4/pic/set_operation.png)

---
### 2.1.1 CARTESIAN PRODUCT
- R(A1,A2,A3,...,B1,B2,B3,...)$\leftarrow$R1(A1,A2,A3,...,Am) X R2(B1,B2,B3,...,Bm)
- If R1 has n1 tuples and R2 has n2 tuples, then R will have $n1*n2$ tuples.

> *CARTESIAN PRODUCT* is a ***meaningless operation*** on its own. It can *combine related tuples* from two relations if followed by the ***appropriate SELECT operation***.

> ![](/posts/db/db_l4/pic/car_pro.png)
> ![](/posts/db/db_l4/pic/ex_car_pro.png)
> The table *EMP_DEPENDENTS* has ***(3 x 7)21*** tuples. 
> To find the tuple which ***ESSN=SSN***

---
## 3.1 JOIN OPERATION
![](/posts/db/db_l4/pic/Join_operation&car.png)

---
### 3.1.1 Equal Join and Theta Join
- *Theta Join*:
  - Similar to a ***Cartesian Product followed by a Select***. The condition c (often use θ) is called a *join condition*.

- *Equal Join*:
  - The join condition c includes one or more equality conparisons involving arrtibutes from R1 and R2.

![](/posts/db/db_l4/pic/equijoin.png)

---
### 3.1.2 Natural Join
![](/posts/db/db_l4/pic/natural_join.png)
- There shoule be some column have same attribute(s)
  - Based on the same value of attributes, adding two table tigether directly
  - Delet the column which has same attribute value

![](/posts/db/db_l4/pic/ex1_natural_join.png)




---
***学习笔记，仅供参考***
