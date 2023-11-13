# System Design Concepts:

## Distributed System:
A distributed system is a network of independent computers that work together to achieve a common goal. Key characteristics include concurrency, scalability, and fault tolerance.

## Vertical Scaling vs Horizontal Scaling:
- **Vertical Scaling:** Increasing the capacity of a single machine, suitable for smaller workloads.
- **Horizontal Scaling:** Adding more machines or nodes, enhancing scalability and fault tolerance for larger workloads.

![Remote Image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/20210209202449/Scaling-Concept.png)

## Caching:
Caching involves storing frequently accessed data temporarily to reduce retrieval latency and improve system performance.

![Remote Image](https://cdn-images-1.medium.com/max/1080/1*KNlUFMg72Ziy4QbbPpOwcw.png)

## CDN (Content Delivery Network)

A **CDN (Content Delivery Network)** is a network of distributed servers delivering web content to users based on their geographical location, reducing latency and improving content delivery speed.

![Remote Image](https://exponent-blog.ghost.io/content/images/pmlesson/2021/04/image-1.png)

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

![Remote Image](https://d1.awsstatic.com/Route53/how-route-53-routes-traffic.8d313c7da075c3c7303aaef32e89b5d0b7885e7c.png)

## Load Balancer:
A load balancer distributes incoming network traffic across multiple servers to optimize resource utilization and improve system reliability.

![Remote Image](https://www.cloud4u.com/upload/medialibrary/5a6/0_CCK15OF3DizmOITk.png)

## Servers (SQL and NoSQL):
- **SQL Servers:** Relational databases using SQL for defining and manipulating data.
  - **MySQL:** A popular open-source relational database management system that uses SQL for defining and manipulating data. It is commonly used in web applications.
  - **PostgreSQL:** Another open-source relational database system that supports advanced data types and has a strong focus on extensibility and standards compliance.
  - **Microsoft SQL Server:** A relational database management system developed by Microsoft, widely used in enterprise applications and business solutions.

- **NoSQL Servers:** Non-relational databases handling large volumes of unstructured or semi-structured data.
  - **MongoDB:** A leading NoSQL database that stores data in flexible, JSON-like documents. It is particularly well-suited for handling large amounts of unstructured data and is often used in modern web applications.
  - **Cassandra:** A distributed NoSQL database designed to handle large amounts of data across many commodity servers without any single point of failure. It is commonly used in scenarios where high availability and scalability are critical.
  - **Redis:** A versatile, in-memory data structure store often used as a cache or message broker. While it is not a traditional relational or document-based database, it falls under the NoSQL category due to its non-relational nature.


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

## Message Queue:

A message queue is a fundamental component in distributed computing and software architecture, providing a reliable and efficient communication mechanism between different components or systems. It operates on the principle of asynchronous communication, allowing decoupling between producers and consumers of messages. In a message queue system, messages are placed in a queue by a sender and retrieved by a receiver, ensuring a smooth and orderly flow of information. This decoupling enhances system scalability and resilience, as components can operate independently, and any temporary imbalances in workload or processing speed can be mitigated. Additionally, message queues facilitate the integration of disparate systems, enabling seamless communication between applications regardless of their underlying technologies. This robust and flexible communication paradigm is integral to the development of scalable, distributed, and fault-tolerant systems in the realm of modern software engineering.

![Remote Image](https://miro.medium.com/v2/resize:fit:828/format:webp/1*AxiArIjSXAo398GIKAKXjg.png)

## Back-of-the-Envelope Metrics:
Quick calculations estimating system requirements and performance metrics, including throughput and response time.

### Latency Numbers Every Programmer Should Know
![Remote Image](https://miro.medium.com/v2/resize:fit:786/format:webp/1*-LXqUWmvJ_nT5OQBbzEBLg.png)

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

![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FBnlgZvYhoF2aHfGp%2F-M5FDUTlsmjNHdO0Tkjm%2Fimage.png?alt=media&token=1847441c-aedc-4c5f-b024-112d6296f544)

2. **Server Mapping**: Servers (A, B, C) are hashed onto the ring. Each key is associated with the closest server in a clockwise direction.

   Example:
   - "Alice" and "Bob" map to server B
   - "Casey" maps to server A
   - Server C remains idle
   
![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FErdzRLhnaO3oZqhK%2F-M5FFr2cj8HdpUos6aj8%2Fimage.png?alt=media&token=f861b386-73b9-4369-811b-4451c60df4e5)

#### Adding and Removing Nodes

- **Adding a Node (Server D)**: Some keys, originally mapped to other servers, now map to server D.

![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FG0ElHCsKOpGeRibk%2F-M5FqVdck8I5JLkHo54a%2Fimage.png?alt=media&token=6036b3fe-3018-443d-9fa0-5f5de7834d96)

- **Removing a Node (Server B)**: Keys initially mapped to server B are remapped to another server.

![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FG0ElHCsKOpGeRibk%2F-M5Frah9CE4uNmXqiYMD%2Fimage.png?alt=media&token=f6b46c29-6737-4893-bb8b-62b99aa30abc)

#### Virtual Nodes

The basic setup may lead to uneven server loads. To address this, multiple hash functions are used to hash each server, creating virtual nodes. For instance, server A may have virtual nodes A0, A1, and A2.

- "Alice" maps to server A via A1
- "Bob" maps to server B via B0
- "Casey" maps to server C via C1

![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FwA4YIBAqAjZvdVpU%2F-M5Fxrb57Z3xWBLOQ2FZ%2Fimage.png?alt=media&token=0c3a1887-ed4d-41ae-85ad-2073b00f0fba)

#### Handling Node Changes

- **Adding Server D**: Only a small portion of keys is remapped to server D (e.g., "George" from server A to server D).

![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FwA4YIBAqAjZvdVpU%2F-M5Fz1p9jfeM9g3WNVKZ%2Fimage.png?alt=media&token=88382f99-6b12-4334-9336-cf69eaf0803f)

- **Removing Server C**: Keys initially mapped to server C are remapped to other servers (e.g., "Eric" and "David" to server A, "Casey" to server B).

![Hash Ring](https://1865312850-files.gitbook.io/~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4Bkp-b8HYQgJF1rkOc%2F-M5FwA4YIBAqAjZvdVpU%2F-M5FzsRNCDxPBSgEdtJa%2Fimage.png?alt=media&token=70a0ecf7-09ce-4dc1-8183-a55d594fc045)

#### Weight

The number of virtual nodes for a specific node is termed "Weight." In cases where some servers are more powerful, these servers can be assigned a higher weight, resulting in more virtual nodes. This weight variation ensures a more proportional distribution of keys to powerful servers.


## Bucket:

The bucket organizes and stores data in distributed storage systems, serving as a logical or physical unit.
- **Characteristics:** Scalability, Isolation, Access Control.
- **Examples:** Amazon S3 Buckets.

## Vector Clocks Technique:

Vector clocks are a technique used in distributed systems, including databases, to track the partial ordering of events across multiple nodes or processes. The primary goal is to provide a mechanism for determining the causality relationships between different events in a distributed environment. Vector clocks help maintain a consistent and accurate view of the order of events, especially in scenarios where nodes operate independently and may experience delays or communication issues.

![Vector Clocks](https://substackcdn.com/image/fetch/w_1456,c_limit,f_webp,q_auto:good,fl_progressive:steep/https%3A%2F%2Fbucketeer-e05bbc84-baa3-437e-9518-adb32be77984.s3.amazonaws.com%2Fpublic%2Fimages%2Fd789f2d3-32b1-4e32-a70c-a7ad2627f208_1600x1500.png)

## Analytics and Monitoring:

This is something that is needed in every system you create. This is a hidden requirement, no one calls it out in the requirement gathering but every interviewer wants this.

User logs in or logs out? Wishlisted an item? Payment failed? It is all the information for us! Anything of importance happens, fire an event and save it in your messaging queue.

You can perform real-time analytics on data or just dump it in a Hadoop cluster to use later. Similarly, if an API call is regularly failing, or if your servers are about to run out of resources, wouldn’t you like to know of it beforehand?

A good knowledge of tools like Grafana, Prometheus can help with you with Analytics and monitoring and also to impress your interviewer during system design interview. Alex Xu has also shared a lot of good information on Monitoring on his book and ByteByteGo course, you can refer them as well.

![Monitoring](https://res.cloudinary.com/practicaldev/image/fetch/s--xsg_RyoT--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://dev-to-uploads.s3.amazonaws.com/uploads/articles/duwydzsa9iu824aqy303.png)

## Reference:

- "System Design Interview – An Insider's Guide" by Alex Xu 

