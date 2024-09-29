# ACID vs BASE


- **`ACID`**: **Atomicity**, **Consistency**, **Isolation**, **Durability**
- **`BASE`**: **Basically available**, **soft-state** & **eventually consistent**


---


## BASE compliant DBs

!!! info ""
    - **Basically Available**: The system guarantees availability according to the CAP theorem, but without strict guarantees on immediate consistency.
    - **Soft state**: The state of the system may change over time, even without input (due to eventual consistency).
    - **Eventual consistency**: The system will become consistent over time, given that no new updates are made. It is not immediately consistent. Changes will be reflected over time (obviously withing acceptable range).


---


## ACID & BASE

!!! tip ""
    - Most **RDBMS (or SQL DBs) are ACID compliant**.
    - Whereas, **NoSQL (not only SQL) are BASE compliant**. (though, `MongoDB is acid compliant` too)


---


## Difference b/w the two

![loading...](../../images/dbms/transaction_and_acid/acid-vs-base.png)


---


## When to use which one?

!!! success "ACID V/S BASE compliant DBs"
    - For financial & banking systems, where atomicity, consistency and durability is more preferred over availability, ACID compliant DBs should be preferred.

    ---

    - For social media apps, where availability matters over slight delay in the updated value (`comments on a post being reflected after some seconds`), BASE compliant DBs should be preferred.