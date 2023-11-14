# System Design Concepts:

## Distributed System:
A distributed system is a network of independent computers that work together to achieve a common goal. Key characteristics include concurrency, scalability, and fault tolerance.

## Vertical Scaling vs Horizontal Scaling:
- **Vertical Scaling:** Increasing the capacity of a single machine, suitable for smaller workloads.
- **Horizontal Scaling:** Adding more machines or nodes, enhancing scalability and fault tolerance for larger workloads.

![image](https://github.com/sergiobriito/system-design/assets/64617586/a5d34021-13ad-43fd-bdb9-09a0c2ee4378)

## Caching:
Caching involves storing frequently accessed data temporarily to reduce retrieval latency and improve system performance.

![image](https://github.com/sergiobriito/system-design/assets/64617586/6b4cf538-e5fe-42a7-8075-f4d3a537c54f)


## CDN (Content Delivery Network)

A **CDN (Content Delivery Network)** is a network of distributed servers delivering web content to users based on their geographical location, reducing latency and improving content delivery speed.

![image](https://github.com/sergiobriito/system-design/assets/64617586/94e6afd6-da5d-479e-9900-eef97aece6c9)


### Components of a CDN:

1. **Edge Servers:**
   - Distributed servers storing cached copies of static content like images, stylesheets, and scripts.

2. **PoPs (Points of Presence):**
   - Locations with multiple edge servers strategically placed to serve specific regions.

3. **Cache Servers:**
   - Servers storing static content closer to end-users, reducing data travel distance.

4. **Origin Server:**
   - The original server where web content is hosted.

In summary, a CDN is a crucial infrastructure component for optimizing content delivery, enhancing user experience, and ensuring the performance and availability of web applications and websites.

## DNS (Domain Name System):
DNS translates human-readable domain names into IP addresses, enabling users to access websites using names instead of numeric IP addresses.

![image](https://github.com/sergiobriito/system-design/assets/64617586/77b05ec8-cc3c-436d-8c5d-ece8d45b9002)

## Load Balancer:
A load balancer distributes incoming network traffic across multiple servers to optimize resource utilization and improve system reliability.

![image](https://github.com/sergiobriito/system-design/assets/64617586/7437cdd0-a8c3-4eeb-b3bb-60ed07c7f480)


## Databases (SQL and NoSQL):

### SQL Databases:

- **Structure:** SQL databases organize data into tables with predefined schemas and establish relationships between data through keys.
- **Query Language:** They use SQL for defining, querying, and manipulating data. SQL allows complex queries involving joins, aggregations, and transactions.
- **ACID Properties:** SQL databases typically support ACID (Atomicity, Consistency, Isolation, Durability) properties, ensuring data integrity and reliability.
- **Examples:** MySQL, PostgreSQL, Microsoft SQL Server.
- **When to Use:** SQL databases are suitable for applications requiring structured data, transactions, complex queries, and where data integrity is critical.

### NoSQL Databases:

- **Structure:** NoSQL databases encompass various data models, handling unstructured, semi-structured, or rapidly changing data.
- **Query Language:** NoSQL databases use different querying methods; some have their query languages, while others use APIs for data retrieval and manipulation.
- **Scalability:** Many NoSQL databases are designed for horizontal scalability, efficiently managing large volumes of data across distributed systems.
- **Examples:** MongoDB (document-based), Cassandra (wide-column store), Redis (key-value store).
- **When to Use:** NoSQL databases are suitable for applications with evolving schemas, huge data volumes, distributed systems, and where high scalability and performance are crucial.


### When to Choose Each:

- **SQL Databases** are preferred when:
  - Data has a well-defined structure and relationships.
  - ACID compliance is necessary for data integrity.
  - Complex queries, joins, and transactions are required.

- **NoSQL Databases** are preferred when:
  - Dealing with unstructured, semi-structured, or rapidly changing data.
  - Scalability and high performance in a distributed environment are crucial.
  - Flexibility in schema design and handling diverse data types is needed.


# Database Sharding and Partitioning:
### Database Sharding:
- **Definition:** Sharding involves horizontally partitioning a database by splitting it into smaller, independent databases called shards.
- **Distribution:** Each shard is a self-contained database that can be hosted on a separate server or cluster of servers.
- **Data Distribution:** Sharding distributes the data across multiple servers based on a specific criterion (e.g., range-based, hash-based, or directory-based sharding).
- **Benefits:**
  - Improved scalability and performance as each shard can handle a subset of the overall dataset.
  - Parallel processing of queries across multiple shards.
  - Enhanced fault tolerance since the failure of one shard does not affect the others.

### Database Partitioning:
- **Definition:** Partitioning involves dividing a single database table into smaller, more manageable segments called partitions.
- **Distribution:** Partitions are typically stored on the same server or storage system.
- **Data Distribution:** Partitioning is often done based on a specific column or columns in the table, such as range partitioning (based on a range of values) or hash partitioning (based on a hash function applied to a column's value).
- **Benefits:**
  - Improved query performance for certain types of queries by limiting the amount of data that needs to be scanned.
  - Simplified data management and maintenance tasks, as operations can be performed on individual partitions.

### Key Differences:
- **Scope:**
  - **Sharding:** Involves dividing the entire database into independent shards, each functioning as a separate database.
  - **Partitioning:** Involves dividing a single table within a database into partitions.
- **Independence:**
  - **Sharding:** Each shard is essentially a standalone database, potentially on a separate server or cluster.
  - **Partitioning:** Partitions within a table are typically stored on the same server.
- **Use Cases:**
  - **Sharding:** Often used in distributed databases to improve scalability and performance across multiple servers.
  - **Partitioning:** Commonly employed to enhance query performance and simplify data management within a single database.


## Datacenters:
Datacenters house computer systems, networking equipment, and resources supporting an organization's IT infrastructure.

## Analytics and Monitoring:

This is something that is needed in every system you create. This is a hidden requirement, no one calls it out in the requirement gathering but every interviewer wants this.

User logs in or logs out? Wishlisted an item? Payment failed? It is all the information for us! Anything of importance happens, fire an event and save it in your messaging queue.

You can perform real-time analytics on data or just dump it in a Hadoop cluster to use later. Similarly, if an API call is regularly failing, or if your servers are about to run out of resources, wouldn’t you like to know of it beforehand?

A good knowledge of tools like Grafana, Prometheus can help with you with Analytics and monitoring and also to impress your interviewer during system design interview. Alex Xu has also shared a lot of good information on Monitoring on his book and ByteByteGo course, you can refer them as well.

![image](https://github.com/sergiobriito/system-design/assets/64617586/ac560205-d323-4b56-8c12-0fa6f29255f1)

## Message Queue:

A message queue is a fundamental component in distributed computing and software architecture, providing a reliable and efficient communication mechanism between different components or systems. It operates on the principle of asynchronous communication, allowing decoupling between producers and consumers of messages. In a message queue system, messages are placed in a queue by a sender and retrieved by a receiver, ensuring a smooth and orderly flow of information. This decoupling enhances system scalability and resilience, as components can operate independently, and any temporary imbalances in workload or processing speed can be mitigated. Additionally, message queues facilitate the integration of disparate systems, enabling seamless communication between applications regardless of their underlying technologies. This robust and flexible communication paradigm is integral to the development of scalable, distributed, and fault-tolerant systems in the realm of modern software engineering.

![image](https://github.com/sergiobriito/system-design/assets/64617586/9eb76209-8960-45cf-9150-100b5689a942)

## Back-of-the-Envelope Metrics:
Quick calculations estimating system requirements and performance metrics, including throughput and response time.

### Latency Numbers Every Programmer Should Know
![image](https://github.com/sergiobriito/system-design/assets/64617586/6d1f8289-dbe6-40dd-841d-6756ffbe4373)

## Multiple Servers and Consistent Hashing:
### Multiple Servers:
Utilizing multiple servers is crucial for scalability, fault tolerance, and load distribution in distributed systems.
- **Advantages:** Scalability, Fault Tolerance, Load Distribution.
- **Challenges:** Consistency, Coordination.

### Consistent Hashing

Consistent Hashing is a distribution technique that facilitates the effective distribution of data, minimizing reorganization efforts when nodes are added or removed. This property makes the system more scalable. The key advantage lies in its independence from the direct count of servers.

#### Overview

In Consistent Hashing, resizing the hash table typically requires remapping only a fraction (k / n) of keys, where k is the total number of keys, and n is the total number of servers. When a new node is added, it acquires shares from a subset of hosts without affecting the shares of others. Conversely, when a node is removed, its shares are redistributed among other hosts.

Consistent hashing is like a smart way of spreading data across multiple computers (nodes) so that if you add or remove a computer, you don't have to move a lot of data around. It's good at keeping the work balanced among the computers and works well for looking up a range of data. This makes it useful in situations where you want your system to be stable, handle changes smoothly, and not get overloaded on some computers while others are idle. It's a bit trickier to set up than modular hashing, but the benefits in stability and efficiency can be worth it in certain situations.

#### Basic Setup

1. **Hash Ring**: The hash function outputs within the range [0, INT_MAX], forming a "ring" known as the "Hash Ring."

![image](https://github.com/sergiobriito/system-design/assets/64617586/118c6dfc-4cea-4f26-8fb2-4934828ca922)


2. **Server Mapping**: Servers (A, B, C) are hashed onto the ring. Each key is associated with the closest server in a clockwise direction.

   Example:
   - "Alice" and "Bob" map to server B
   - "Casey" maps to server A
   - Server C remains idle
   
![image](https://github.com/sergiobriito/system-design/assets/64617586/c8fee3b2-f768-4188-9339-ad92113d5d9d)


#### Adding and Removing Nodes

- **Adding a Node (Server D)**: Some keys, originally mapped to other servers, now map to server D.

![image](https://github.com/sergiobriito/system-design/assets/64617586/af3d209b-dd13-4d81-8f39-d710dcadb38e)


- **Removing a Node (Server B)**: Keys initially mapped to server B are remapped to another server.

![image](https://github.com/sergiobriito/system-design/assets/64617586/46a53393-4eea-4e1f-b1de-6eba50b988a7)


#### Virtual Nodes

The basic setup may lead to uneven server loads. To address this, multiple hash functions are used to hash each server, creating virtual nodes. For instance, server A may have virtual nodes A0, A1, and A2.

- "Alice" maps to server A via A1
- "Bob" maps to server B via B0
- "Casey" maps to server C via C1

![image](https://github.com/sergiobriito/system-design/assets/64617586/9b5638c8-d390-4c6e-93b5-1a5e7c5cb39d)


#### Handling Node Changes

- **Adding Server D**: Only a small portion of keys is remapped to server D (e.g., "George" from server A to server D).

![image](https://github.com/sergiobriito/system-design/assets/64617586/27904988-c590-406e-9baf-af3aeca5f085)


- **Removing Server C**: Keys initially mapped to server C are remapped to other servers (e.g., "Eric" and "David" to server A, "Casey" to server B).

![image](https://github.com/sergiobriito/system-design/assets/64617586/91113f5d-2897-46e2-98ec-2dd6b25590e9)


#### Weight

The number of virtual nodes for a specific node is termed "Weight." In cases where some servers are more powerful, these servers can be assigned a higher weight, resulting in more virtual nodes. This weight variation ensures a more proportional distribution of keys to powerful servers.


## Bucket:

The bucket organizes and stores data in distributed storage systems, serving as a logical or physical unit.
- **Characteristics:** Scalability, Isolation, Access Control.
- **Examples:** Amazon S3 Buckets.

## Vector Clocks Technique:

Vector clocks are a technique used in distributed systems, including databases, to track the partial ordering of events across multiple nodes or processes. The primary goal is to provide a mechanism for determining the causality relationships between different events in a distributed environment. Vector clocks help maintain a consistent and accurate view of the order of events, especially in scenarios where nodes operate independently and may experience delays or communication issues.

![image](https://github.com/sergiobriito/system-design/assets/64617586/29ea5057-1a61-4f08-b5f2-540d15321d69)


## Hash Trees for Ensuring Database Consistency

A hash tree, also known as a Merkle tree, is a hierarchical data structure used to efficiently verify the integrity and consistency of data in a database or any other distributed system. It's particularly useful in ensuring that large amounts of data remain unchanged or consistent over time, especially in decentralized or distributed environments.

### Structure of a Hash Tree

- A hash tree consists of nodes organized in a tree-like structure.
- Each leaf node represents a small chunk of data (such as a block or a file).
- Non-leaf nodes are hashes of their child nodes.
- The lowest level contains the actual data chunks, and nodes higher up contain hashes of their children.

### How Hashing Works

- A cryptographic hash function (like SHA-256) generates fixed-size hashes from the data.
- These hashes are unique representations of the data.

### Construction of the Tree

- Data is recursively hashed in a binary tree structure.
- This process continues until a single root hash, known as the Merkle root, is obtained.
- The root hash serves as a summary of the entire dataset.

### Ensuring Consistency

- To verify integrity, nodes compare their root hash with the trusted source's root hash.
- Any change in data causes a different hash value.
- Changes propagate up the tree, affecting the root hash.
- Even a small alteration in the data results in a mismatch in the root hash, indicating inconsistency or tampering.

### Efficiency and Verification

- Hash trees allow for efficient verification by comparing just a few hashes.
- Verification is logarithmic to the number of data blocks, making it scalable for large datasets.
- In distributed systems, comparing root hashes ensures data consistency across different nodes or peers.

### Applications

- Blockchain technology uses Merkle trees to ensure block and transaction integrity.
- File systems, version control systems, and databases leverage hash trees for quick change detection and data consistency across distributed environments.

In essence, hash trees serve as a robust mechanism to maintain the consistency and integrity of large datasets by allowing efficient verification through hierarchical hashing structures.

![image](https://github.com/sergiobriito/system-design/assets/64617586/4d4fdef7-662b-4860-ac99-ce3f5fa2c595)


## Reference:

- "System Design Interview – An Insider's Guide" by Alex Xu 

