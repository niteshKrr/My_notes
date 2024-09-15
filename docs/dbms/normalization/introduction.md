# Introduction to Normalization


## What is a Normalization?

**Normalization** is the process of organizing the data and the attributes of a database. It is performed to reduce the data redundancy in a database and to ensure that data is stored logically.


**Data redundancy in DBMS** means having the same data but at multiple places. It is necessary to remove data redundancy because it causes anomalies in a database which makes it very hard for a database administrator to maintain it.



## Why Do We Need Normalization?

Normalization is used to reduce data redundancy. It provides a method to remove the following anomalies from the database and bring it to a more consistent state:


* **Insertion anomalies :-** This occurs when we are not able to insert data into a database because some attributes may be missing at the time of insertion.

* **Updation anomalies :-** This occurs when the same data items are repeated with the same values and are not linked to each other.

* **Deletion anomalies :-** This occurs when deleting one part of the data deletes the other necessary information from the database.



## Normal Forms

There are four types of normal forms that are usually used in relational databases.


![loading...](../../images/dbms/normalization/normal_forms.webp)