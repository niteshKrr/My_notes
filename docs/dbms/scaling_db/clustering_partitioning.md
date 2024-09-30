# Clustering & Partitioning


## Clustering

**Clustering** refers to grouping multiple servers or nodes to work together as a single system. In the context of databases, clustering is used to distribute data and workload across multiple servers, allowing the system to handle larger datasets and more users.


!!! success "Purpose"

    * **Scalability:** By distributing data and requests across multiple servers, clustering allows systems to handle larger loads and improve performance.

    * **High Availability:** Clustering can also be used to ensure that if one node fails, others can take over, improving fault tolerance.


**How It Works**

* In a cluster, data is often sharded (split into smaller pieces) and distributed across different nodes.

* Each node may handle a portion of the data and workload, enabling the system to process larger datasets and handle more requests.

* Clustering is about **horizontal scaling**, meaning you can add more machines to handle increased load.


!!! success ""
    **Example**

    In a **sharded cluster** (like MongoDB), data is split into smaller chunks (shards), and each node holds only a portion of the total data. Requests are distributed across the cluster to balance the load.



---


## Partitioning

* A big problem can be solved easily when it is chopped into several smaller sub-problems. That is what the **partitioning** technique does.

* It divides a big database containing data metrics and indexes into smaller and handy slices of data called partitions.

* The partitioned tables are directly used by SQL queries without any alteration.

* Once the database is partitioned, the data definition language can easily work on the smaller partitioned slices, instead of handling the giant database altogether.

* This is how partitioning cuts down the problems in managing large database tables.


**Partitioning** is the process of dividing a large database or table into smaller, more manageable pieces called partitions. Each partition contains a subset of the data, making it easier to manage, query, and maintain.



!!! bug "Relational V/s NOSQL DB on partitioning"
    - When we horizontally scale our machines/servers, we know that it gives us a **challenging time dealing with relational databases as it’s quite tough to maintain the relations**.
    - For performing joins, we will be required to fetch data from multiple servers and then perform join, which will be time-consuming.
    - If instead, we used **NOSQL DB**, data that will be required together will be stored together. Also, we don't care much about normalization in NOSQL, which eventually leads to **better performance and availability**.



---

### Vertical Partitioning

- Slicing relation vertically / column-wise.
- Need to access different servers to get complete tuples.

---

### Horizontal Partitioning

- Slicing relation horizontally / row-wise.
- Independent chunks of data tuples are stored in different servers.

---

## When Partitioning is Applied?

- Dataset become much huge that managing and dealing with it become a tedious task.
- the number of requests are enough larger that the single DB server is taking huge time and hence the system's response time become high.

---


## Benefits of Partitioning


!!! success ""

    * **Improved Query Performance :-**
    SQL queries can target specific partitions rather than scanning the entire table. This reduces the amount of data the database engine has to process, leading to faster query execution.

    * **Easier Data Management :-**
    Maintenance tasks like backups, archiving, and deleting old data become simpler because these operations can be done on individual partitions instead of the entire database.

    * **Reduced Index Size :-**
    Since partitions hold smaller portions of data, the indexes on each partition are also smaller, making index scans and lookups faster.

    * **Parallel Processing :-**
    Some databases support processing partitions in parallel, meaning multiple partitions can be read or written simultaneously. This improves the overall throughput of queries and operations.

    * **Scalability :-**
    As data grows, partitioning allows the system to handle more data without significantly degrading performance. It makes it easier to manage the continuous growth of large datasets.


---

## Scaling Up Vs Scaling Out

!!! success ""
    - **Scaling up** => **Vertical scaling** (adding more resources (ram, cpu, etc.))
    - **Scaling out** => **horizontal scaling** (adding more servers)


---


## Distributed database

- A single logical database that is spread across multiple locations (servers) and logically interconnected by network.
- This is the product of applying DB optimization techniques like, `Clustering`, `Partitioning` & `Sharding`.


!!! tips "Why is it needed?"
    - Dataset become much huge that managing and dealing with it become a tedious task.
    - the number of requests are enough larger that the single DB server is taking huge time and hence the system's response time become high.



