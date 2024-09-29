# Introduction to NoSQL


## What is a NoSQL database?

**NoSQL** is a type of database management system (DBMS) that is designed to handle and store large volumes of unstructured and semi-structured data. Unlike traditional relational databases that use tables with pre-defined schemas to store data, NoSQL databases use flexible data models that can adapt to changes in data structures and are capable of scaling horizontally to handle growing amounts of data.

1. They are schema free.
2. Data structures used are not tabular, they are more flexible, has the ability to adjust dynamically.
3. Can handle huge amount of data (big data).
4. Most of the NoSQL are open sources and has the capability of horizontal scaling.
5. It just stores data in some format other than relational.


## History of NoSQL


!!! quote "History of NoSQL"
	- In 2000s, hardware was really expensive, so to store data in DB, we were required to minimize space and store them effectively. This lead to development of least redundancy and normalization concepts.
	- Over time, hardware prices dropped and now space is not a big concern, but serving customer without latency is the real challenge.
	- To tackle this, new kind of DBs emerged with the intention to minimize the latency and maximize scalability, be it at the cost of data redundancy.
	- These DBs were **NoSQL (`No only SQL`)**.
	- Cloud computing also rose in popularity, and developers began using public clouds to host their applications and data. They wanted the ability to distribute data across multiple servers and regions to make their applications resilient, to scale out out instead of scale up, and to intelligently geo-place their data. Some NoSQL databases like MongoDB provide these capabilities.



## NoSQL DB advantages

!!! success ""
	- **Flexible Schema**
	- **Horizontal scaling (`scale out`)**.
    	- **This is difficult with relational databases due to the difficulty in spreading out related data across nodes. With non-relational databases, this is made simpler since collections are self-contained and not coupled relationally. This allows them to be distributed across nodes more simply, as queries do not have to “join” them together across nodes**.
	- Scaling horizontally is achieved through Sharding OR Replica-sets.
	- High availability
	- **Easy insert and read operations**
    	- Queries in NoSQL databases can be faster than SQL databases. Why? Data in SQL databases is typically normalized, so queries for a single object or entity require you to join data from multiple tables. As your tables grow in size, the joins can become expensive. However, data in NoSQL databases is typically stored in a way that is optimized for queries.
    	- The rule of thumb when you use MongoDB is data that is accessed together should be stored together. Queries typically do not require joins, so the queries are very fast.
    	- But **difficult delete or update operations**.
	- Caching mechanism
	- NoSQL use case is more for **cloud application**




## NoSQL DB Disadvantages ⚠️

!!! warning ""
	1. Data Redundancy
	2. Since data models in NoSQL databases are typically **`optimized for queries and not for reducing data duplication`**, NoSQL databases can be larger than SQL databases. Storage is currently so cheap that most consider this a minor drawback and some NoSQL databases also support compression to reduce the storage footprint.
	3. **Update & Delete operations are costly**.
	4. All type of NoSQL Data model doesn’t fulfil all of your application needs
	5. Depending on the NoSQL database type you select, you may not be able to achieve all of your use cases in a single
	database. For example, graph databases are excellent for analyzing relationships in your data but may not provide what you need for everyday retrieval of the data such as range queries. When selecting a NoSQL database, consider what your use cases will be and if a general purpose database like MongoDB would be a better option.
	6. **Doesn’t support ACID properties in general (`mongodb exception`)**.
	7. **Doesn’t support data entry with consistency constraints**. But, is **eventually consistent**.




## When to use NoSQL?

!!! tip ""
	1. When a huge amount of data needs to be stored and retrieved.
    2. The relationship between the data you store is not that important
    3. The data changes over time and is not structured.
    4. Support of Constraints and Joins is not required at the database level
    5. The data is growing continuously and you need to scale the database regularly to handle the data.
	6. Modern application paradigms like micro-services and real-time streaming.

---



## NoSQL DB Misconceptions

??? warning "Relationship data is best suited for relational databases!"
	A common misconception is that NoSQL databases or non-relational databases don’t store relationship data well. NoSQL databases can store relationship data — they just store it differently than relational databases do.

	- In fact, when compared with relational databases, many find modelling relationship data in NoSQL databases to be easier than in relational databases, because related data doesn’t have to be split between tables. NoSQL data models allow related data to be nested within a single data structure.

??? warning "NoSQL databases don't support ACID transactions"
	Another common misconception is that NoSQL databases don't support ACID transactions.

	- Some NoSQL databases like MongoDB do, in fact, support ACID transactions.


---


## Types of NoSQL data models


- **Key-Value store**
!!! tip ""
	- use cases: `user preferences`, and `user profiles`.
	- e.g., **Oracle NoSQL**, **Amazon DynamoDB**, **MongoDB** also supports Key-Value store, **Redis**.


---


- **Column-Oriented / Columnar / C-Store / Wide-Column**

!!! tip ""
	- The data is stored such that each row of a column will be next to other rows from that same column.
	- While a relational database stores data in rows and reads data row by row, a column store is organized as a set of columns.
	- This means that when you want to run analytics on a small number of columns, you can read those columns directly without consuming memory with the unwanted data.
	- Columns are often of the same type and benefit from more efficient compression, making reads even faster.
	- Columnar databases can quickly aggregate the value of a given column (adding up the total sales for the year, for example).
	- **Use cases include analytics**.
	- e.g., **Cassandra**, **RedShift**, **Snowflake**.


---


- **Document based store**


!!! tip ""
	- store data in documents similar to JSON
	- Use cases include e-commerce platforms, trading platforms, and mobile app development across industries.
	- `Supports ACID` properties hence, suitable for Transactions.
	- e.g., **MongoDB**, **CouchDB**.


---


- **Graph based models**


!!! tip ""
	- A graph database focuses on the relationship between data elements. Each element is stored as a node (such as a person in a social media graph). The connections between elements are called links or relationships. In a graph database, connections are first-class elements of the database, stored directly. In relational databases, links are implied, using data to express the relationships.
	- A graph database is optimized to capture and search the connections between data elements, overcoming the overhead associated with JOINing multiple tables in SQL.
	- Very few real-world business systems can survive solely on graph queries. As a result graph databases are usually run alongside other more traditional databases.
	- Use cases include fraud detection, **social networks**, and **knowledge graphs**.
	- e.g., **Neo4J**



