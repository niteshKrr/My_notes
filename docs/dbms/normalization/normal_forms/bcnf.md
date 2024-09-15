# Normal Forms


## Boyce-Codd Normal Form (BCNF)

**Boyce-Codd Normal Form(BCNF)** is an advanced version of 3NF as it contains additional constraints compared to 3NF.


* For a relational table to be in Boyce-Codd normal form, it must satisfy the following rules:

    1. The table must be in the third normal form.
    2. For every non-trivial functional dependency `X -> Y`, X is the superkey of the table. That means X cannot be a non-prime attribute if Y is a prime attribute.


* A **superkey** is a set of one or more attributes that can uniquely identify a row in a database table.


Let us take an example of the following `EmployeeProjectLead` table to understand how to normalize the table to the BCNF:


![loading...](../../../images/dbms/normalization/bcnf_01.png)



??? tip "Explanation"
    The above table satisfies all the normal forms till 3NF, but it violates the rules of BCNF because the **candidate key** of the above table is `{Employee Code, Project ID}`. For the **non-trivial functional dependency**, `Project Leader -> Project ID`, Project ID is a prime attribute but Project Leader is a non-prime attribute. This is not allowed in BCNF.



To convert the given table into BCNF, we decompose it into two tables:


![loading...](../../../images/dbms/normalization/bcnf_02.png)



Thus, we’ve converted the `EmployeeProjectLead` table into BCNF by decomposing it into `EmployeeProject` and `ProjectLead` tables.
