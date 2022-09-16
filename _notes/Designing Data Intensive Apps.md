---
title: Designing Data-Intensive Applications - Resume!! 📚
---

## Chapter 1 - Reliable, Scalable and Maintainable

What is a Data intensive application?

A data intensive application means the ammount of data, its complaxecity and speed of change increase quicly, so it needs a special aproach or it will be breaking every 5 hours!!!!!!

What can make part of an data-intensive app:

- Databases;
- Cache:
- Full-text index
- Message queues
- stream processing 
- bacth processing 
- application it self 

- Reliability:
  - The goal of this principle is to prevent the system to fail, or the system to provide the service required by the user. We can have different types of fails and diffenrent tool that we can addopt to prevent it: 
        Hardware errors: The system should be able to tolerate lost machines, or other kind of hardware. The hardware will fail and in the scalibity process the probalitity of it ti happen will incriease. We need to have our system ready to prevent it or to prevent the user to be affected by it. 
        Softwate error: When we have a system faylure is more probable to be related with sofware than hardware.
        Human error: As we all know, we fail, we do mistakes. so it is essencial to turn our system what I likes to call "fool prove". Not because we are fools, but sometimes it happens. So it is important to have our process rellieng the most we can on automation, our tools and our process configured to incentive the "right thing"  and discourage the "wrong thing". A roll back process and proper monotoring tools to identify the problems as soon as possible.
- Scalability:
  - It is how our system copes with increased load. We need to be able to anwser this questions:
  - How is the performance affected by the load increase, how can we set our system ready to takle the load increase. If we need to increase our ressouces, how mush? To be able to take actions we need to have data, and so we need to have metrics to help us deciding over the best technical approach. Some important metrics:
    - throughput - number of records we can process per second;
    - response time - time that the cliend needs to wait for the response (Latency plus processing time) - Usually it is useded the avarage response time, what is not a good metric because it is not clear how really it affect the clients and how many clients needs to wait. We should use percentiles:
      - Median (50th percentile or p50). Half of user requests are served in less than the median response time, and the other half take longer than the median
      - Percentiles 95th, 99th and 99.9th (p95, p99 and p999) are good to figure out how bad your outliners are.
  - Latency -  duration that a request is waiting to be handled, message trnaportantion 
  - We can define Service level objectives (SLOs) and service level agreements (SLAs). These metrics set expectations for clients of the service and allow customers to demand a refund if the SLA is not met. 
  - Tests from the client side to ensure that paralelas quests are not taking to much even when requests individual are really fast.

    How we can scale:
    - Scaling up or vertical scaling: Moving to a more powerful machine
    - Scaling out or horizontal scaling: Distributing the load across multiple smaller machines.
    - Elastic systems: Automatically add computing resources when detected load increase. Quite useful if load is unpredictable. - my favorite and really easy using the cloud services 

It is much easier to escalate stateless services than statefull

- Maintainability:
There are three diferent principles taht we sould approach regarding this topic:

- Operatibility - How easy is to keep the system running properly:
  -  Monotoring and restoring the system if something goes wrong;
  -  Tracking down the problems cause;
  -  Keeping sofware and plateforms up to date;
  -  Keeping a traker how the system affect each other. 
  -  Anticipating future problems (think before you do)
  -  Estabilishing, good practices, process and tool;
  -  Perform complex maisntenace tasks, as platform migrations and pen tests;
  -  Ensure the security of the system;
  -  Documentation;
   
   We cannot forget that the majority of the cost of software is in maintenance.

- Simplicity - The time to deliver and the number of bugs is directed relationed with the complecity of the system. So Complexe systems are harder to manage, to expande and escalete, to deliver and it will have much more bugs. 

- Evolvability - How easy is to do changes in the system? It can be related with the complexity of teh system but also with the processes followed by the company. One problem taht I've been facing all my live is score changes and requirement changes constantly. 

Functional requirements: what the application should do
Nonfunctional requirements: general properties like security, reliability, compliance, scalability, compatibility and maintainability.


## Chapter 2 - Data models and query language

Abstraction, such a beurifull word!! Most of our applciations are built supported on layers architecture, where each layers has a spicific function and hides its complexity from the previweis layers, it ensures a clean and escalable data model, allowing the resusing of the layers by defferent people working in paralell. 

We have two major data models:

- The network model - a record can have multiple parents,
- Hierarchical  modal - every node has exactly one node
- Relational model
  -  Relational databases lies on business data processing, transaton processing an batch processing. 
  -  We need to take into considerantion the impedance mismatch fenomeno. It is a bunch of problems that we can face due the difference betwwenn the database model and the program language model, to deal with issuas as programming language attribute data type being different from the attribute data type in the data model we need to have an layer to translate this two things. 
  
  -  Bettor suporting nd many-to-one and many-to-many relationships, so easy to perform joins;
  -  schema-on-write or compile-time checking;



- Document model
  - Also colled Not Only SQL or NoSql
  - Advatages:
    - Geater scalbililty;
    - Easier to find an open source sofware that can answer our needs;
    - Easiar to optimize;
    - JSON model reduces the impendence mistach (does not eliminate it) and allows a more dynamic and expresisve data model.
    - better performance, due to locality, closer data structure to the ones used by the applcaition. 
  - This kind of databases usually follow the hieriracky model, that means that we have one-to-many relatinships, instead of many-to-many. So, we should not need joins, because they are expensive or impossible to do depending on the technology. Sometimes it needs to be emulated in th applcation layer making multiple queries. 
  - No schema keys forced in ddocuments, so when readding the users have no guaramtees of what expected from the document. (schema-on-read or runtime checking)

- Graph-like data models - I'm in love with this fooking shit 
  - For when we have a lot of many-to -many relations.
  - Property graphs
  - 
        Each vertex consists of:

        Unique identifier
        Outgoing edges
        Incoming edges
        Collection of properties (key-value pairs)
        
        Each edge consists of - relatioship:

        Unique identifier
        Vertex at which the edge starts (tail vertex)
        Vertex at which the edge ends (head vertex)
        Label to describe the kind of relationship between the two vertices
        A collection of properties (key-value pairs)
        Direction,
        Type


It is just dots and lines
Graphs provide a great deal of flexibility for data modelling. Graphs are good for evolvability.
Evolvability is the ability of a biological system to produce phenotypic variation that is both heritable and adaptive.
This kind of databases are great to represente real life organizations, like networks, biological stuff. 

Some examples:
 - Wikidata is a graph database that uses SparQL to retrive information. SPARQL is a declarative programming language and protocol for graph database analytics. 

https://query.wikidata.org/
https://www.youtube.com/watch?v=1jHoUkj_mKw&t=393s

 - Neo4j - graph data plataform 
https://neo4j.com/
https://www.youtube.com/watch?v=GekQqFZm7mA


## Chapter 3 - Storage and retrieval

Log files- 
The most simplest way how a database could work can be using a log, but a log is just an oppened-only sequece of records. So not good enough to managa all the process with a database needs to deal with (update, delete....)

Tp help in this process, databases use indexes. An index is just a structure that derives from the primary staructure. Index can improve the velocity of retriving data but also slow down the velocity to write. So they need to be well chosen.

  - Hash indexes - key value pair stored in memory. So, we need to be able to story the indexes in momory, but the value can be in disk. It can be a limitation because we need to be able to keep the entire hash table in memory. 
The keys, also called hash mapped, are updated everytime we add something to the disk. To add to the disk is an append, to prevent to run out off memory the database will the log into segments of a certain size max, and once you reached it creates a new segment file. Times a times we can perform compaction on these segments, this means trwoing way duplicated keys in the files and keeping only the most recent ones. We never modify segments, but we can delete, this gives us the oportunity to merge segments, creating new ones and removing the outdated ones. 
This append only technique can be really good working with concurrency and recovering from crash since it is a sequencial process and the merging process avoids all segments getting fragmented over time.

- SSTables and LSM-Trees
 key-value pairs is sorted by key.
 SSTables advatages over log segments with hash indexes
     - Merging segments is simple and efficient - When multiple segments contain the same key, we can keep the value from the most recent segment and discard the values in older segments.
     ** not mine
     -  You no longer need to keep an index of all the keys in memory. For a key like handiwork, when you know the offsets for the keys handback and handsome, you know handiwork must appear between those two. You can jump to the offset for handback and scan from there until you find handiwork, if not, the key is not present. You still need an in-memory index to tell you the offsets for some of the keys. One key for every few kilobytes of segment file is sufficient.
    - Since read requests need to scan over several key-value pairs in the requested range anyway, it is possible to group those records into a block and compress it before writing it to disk.
  ** not mine 

-HaahahahahahahAHAHAHAHA eu don't like it 

Data warehousing
Data warehouse should contain all the data from the different databases in the system. It is used to query data without the need to affect the several OLTP. 
Usually it is a read only relational database, and it can use a style known as a star schema or snowflake.

A fact table is a primary table in dimension modelling. it contains Measurements and facts align with the buseness and can becoma quite huge, often have over 100 columns. Dimensions represent the who, what, where, when, how and why of the event.

column-oriented storage
  Store all the values from a column together, not all the values from a row tugether.
  If each column is stored in a separate file, a query only needs to read and parse those columns that are used in a query, which can save a lot of work. This system is good for CPU cycles and compressin 


  But if you insert a row, you will have to update all the column files. 

   materialised aggregates - 
   materialised aggregates as some cache of the counts ant the sums that queries use most often

## Encoding and evolution

- Schema changes..😱😱😱😱😱😱 
It can be a mess if not well managed, but the truth is that it will happen because the features changed and the schema will need to change. 

In relational databases or Schema on right we will have just one schema at time, but it can be changed. 
In Schema on read databases or schemaless we can have several versions of the shecma at the same time.

   - Backward compatibility, newer code can read data that was written by older code.
   - Forward compatibility, older code can read data that was written by newer code.

Don't change the schema adding mandatory fields, use optional instead, this way the code that doesn't know the new schema will still run. 
Formats like Thrift ou ProtoBuf, encode the info in a specific order, we should keep the order. 
Don't remove fields.
Changes in the schema can be complicated, sometimes it is automatcly converted in the readng process like for instance int32 to int64 but sometimes a change requires a migration of data that needs extra atention because we need to re-write all the data in the database.

article about migraions: https://blog.pragmaticengineer.com/migrations-done-well-executing-them/

- Formats for encoding data

It is good that we have all the data in memory, but to use it we need to trnalate it in a way we can write it to a file or send it over the network. The name of this process is encoding or serialisation and the reverse process is decoding or deserialisation.

Programing languages ofen offer a support to encodinding-decoding in-memory objects into byte sequences, but it sould be avoided because it get you tied to a programming language (no one wants it), versioning can be a mess, efficiency and the decoding process needs to be able to instantiate arbitrary classes and this is frequently a security hole.

Standardised encodings like JSON, XML and CSV are much better option because it can be used by several laguanges and at the same time humam-readable. So when our sistem we can use different technolies comunication without loss of information.

But it still have some issues:
  - Ambiguity around the encoding of numbers and dealing with large numbers;
  - Support of Unicode character strings, but no support for binary strings. People get around this by encoding binary data as Base64, which increases the data size by 33%.
  - There is optional schema support for both XML and JSON, it means that sometimes we have to rely in the documentation and it can get outdated really fast. We should use a tool to help manage the schemas and expose it to the consumers. 
  - CSV does not have any schema, so the one consuming this info should get it just by analising the files. 

Json as XML use a lot of space when compared with binary formats (Apache Thrift and Protocol Buffers). But we can also find ninary encoding for JSON and XML (MesagePack, BSON, BJSON, UBJSON, BISON and Smile, WBXML and Fast Infoset). How it works, advantages and disavantages???

Differences between json and protobuffer:

- Protobuf supports binary serialization format, whereas JSON is for simple text serialization format
- JSON is useful for common tasks and is limited to certain types of data. It means JSON cannot serialize and de-serialize every python object. Whereas Protobuf covers a wide variety of data types when compared to JSON. Even enumerations and methods can be serialized with Protobuf.
- Protobuf is a binary data-interchange format developed by Google, whereas JSON is the human-readable data-interchange format. JSON is derived from JavaScript but as the name suggests, it is not limited to JavaScript only. It was designed in such a way that it can be used in multiple languages
- Both Protocol buffers and JSON are languages interoperable, but Protobuf are limited to subsets of programming language, whereas JSON is widely accepted.
- JSON contains the only message and not schema, whereas Protobuf not only has messages but also includes a set of rules and schemas to define these messages.
- Protobuf is mostly useful for internal services whereas JSON is mostly useful for web applications.
- Prior knowledge of schema is essential in decoding Protobuf messages, whereas data can be easily decoded or parsed in JSON with knowing schemas in advance.
- Protobuffer is much more compact than JSON
- Protobuffer is faster to process
 

Apache Thrift offers two different kinds of protocols:

- Binary procolol that uses field tahs instead of data. Are we usinf schemas on it?
- CompactProtocol which is equivalent to BinaryProtocol but it packs the same information in less space. It packs the field type and the tag number into the same byte.

How to keep compatibity when schemas change??

- Forward compatible support - We just need to add a new field, old code will just ignore new code.  
- Backwards compatible support - all the fiels should be option so will not impact services already cosnsuming it taht will not be updated. 

Avro - another binary format that has two schema languages, one intended for human editing (Avro IDL), and one (based on JSON) that is more easily machine-readable.


Advantages of bianry encoding protocols:
- Can be much more compact, since they can omit field names from the encoded data. Even protobuffer?
- Schema is a valuable form of documentation, required for decoding, you can be sure it is up to date.
- Database of schemas allows you to check forward and backward compatibility changes.
- Generate code from the schema is useful, since it enables type checking at compile time.

### Models and dataflows

- Via database - Two services or two different versionof the code consuming info from the same database.
Databases are really dificult to migrate, most realtional databases allow simple shema changes, unless explicitly we rewritten the shema and the data. And in this case we have to deal with the code that is using this database schema (more migrations...)

- Via service calls (sync - rest, rpc and GraphQL)

#### Rest 

Rest is an architectural style GraphQL to a set of constraints when developing web services.

REST seems to be the predominant style for public APIs. The main focus of RPC frameworks is on requests between services owned by the same organisation, typically within the same datacenter.

#### RPC 
Remote procedure calls (RPC) allows you to invoke a function on a remote server in a particular format and receive a response in the same format, that means that it tries to make a call to a remote service look like a call in the service. It has some issues:

  - A network request is unpredictable
  - A network request it may return without a result, due a timeout
  - Retrying will cause the action to be performed multiple times, unless you build a mechanism for deduplication (idempotence).
  - A network request is much slower than a function call, and its latency is wildly variable.
  - Parameters need to be encoded into a sequence of bytes that can be sent over the network and becomes problematic with larger objects.
  - The RPC framework must translate datatypes from one language to another, not all languages have the same types.

gRPC 
As a variant of the RPC architecture, gRPC was created by Google to speed up data transmission between microservices and other systems that need to interact with each other. Compared to REST APIs, gRPC APIs are unique in the following ways: 
  - Protobuf Instead of JSON
  - Built on HTTP 2 Instead of HTTP 1.1
  - In-Born Code Generation Instead of Using Third-Party Tools Like Swagger
  - 7 to 10 times Faster Message Transmission
 - Slower Implementation than REST 

#### GraphQL 

GraphQL is an open-source data query and manipulation language for APIs



- Via asynchronous message passing ( message brokers)
The communication happens only in one direction using a message broker that will store the message temporatly and then sent it to the proper service. The sender doesn't wait for the message to be delivered, but simply sends it and then forgets about it (asynchronous) (fire and forget).

One process sends a message to a named queue or topic and the broker ensures that the message is delivered to one or more consumers or subscribers to that queue or topic.

Some caracteristis:
  - Message deliver is not guaranteed. 
  - It can act as a buffer if the recipient is unavailable or overloaded
  - It can automatically redeliver messages to a process that has crashed and prevent messages from being lost
  - It avoids the sender needing to know the IP address and port number of the recipient (useful in a cloud environment)
  - It allows one message to be sent to several recipients
  - Decouples the sender from the recipient

## Replication

We have two kinds of distibuited systems: Shared Nothing Architecture like stateless web services where we can just kill or add more services, since they share any ressource it can happen. And we have databases taht can have indivisual hardware ressources but it will need to share the data. 
Why do we need to replicate data:
- To keep data geographicallu close to the users;
- Incrise availability;
- Increase read throudgpout

In a database system each noad has its how role as leader or follower.
The leader replic will the the one with the writers rights, and tthe it will send the info to the followers replics. 
The followers can be used just to read info. 

Synchronous vs asynchronous:
- Synchronous - the cliets ask for an operation that will be executed in the leaders, then propagated to the followers and than returned a response to the client.
  One huge advantage of it is that we can ensure that the client has the most updated data, one big disavange is that if the follower is down that write process cannot be done and if we have a lot of write operations we will be creating a bottle net in thw writes witing for followers anwsers;

- Asynchronous - The client askes from an action in the database, it is executed in the leader and sent a message to the client. Then that data will be replciated in the followers. It can be much faster that in sync systems because the leader can continue processing info but we are not complitly sure of the data consistency.

How can we deal when some of the nodes fails?

- If it is the follower we just need to do a catchup recovery. In this case, the follower will just connect with the leader and ask for the data changes thap happened meanwhile.
- If it was the leader failing than we have the failover process. a new follower will be promoted to be the new leader, clientes may need to be reconfigured to start using the new lead or the database configs need to be changed.

In the automatic process we need to define when we sould assume that the leader is dead, promote a new leader using Paxos or Raft consensus algorithm, usually is the follower most updated that will assume leadership. Make sure taht the old leader will return as a follower.

Things that could go wrong:

- If asynchronous replication is used, the new leader may have received conflicting writes in the meantime.
- Discarding writes is especially dangerous if other storage systems outside of the database need to be coordinated with the database contents.
- It could happen that two nodes both believe that they are the leader (split brain). Data is likely to be lost or corrupted.
- What is the right time before the leader is declared dead?

Implementation of the replication logs:

- Statement-based replication
  The leader logs every statement and sends it to its followers (every INSERT, UPDATE or DELETE).

This type of replication has some problems:

- Non-deterministic functions such as NOW() or RAND() will generate different values on replicas.
- Statements that depend on existing data, like auto-increments, must be executed in the same order in each replica.
- Statements with side effects may result on different results on each replica.

A solution to this is to replace any nondeterministic function with a fixed return value in the leader.

- Write-ahead log (WAL) shipping
  The log is an append-only sequence of bytes containing all writes to the database. The leader can send it to its followers. This way of replication is used in PostgresSQL and Oracle.

The main disadvantage is that the log describes the data at a very low level (like which bytes were changed in which disk blocks), coupling it to the storage engine.

Usually is not possible to run different versions of the database in leaders and followers. This can have a big operational impact, like making it impossible to have a zero-downtime upgrade of the database.

- Logical (row-based) log replication

The log is an append-only sequence of bytes containing all writes to the database. The leader can send it to its followers. This way of replication is used in PostgresSQL and Oracle.

The main disadvantage is that the log describes the data at a very low level (like which bytes were changed in which disk blocks), coupling it to the storage engine.

Usually is not possible to run different versions of the database in leaders and followers. This can have a big operational impact, like making it impossible to have a zero-downtime upgrade of the database.

- Trigger-based replication
  Sometimes makes sense to move it to the application layer. In this case we have the applciation responsible for the duplication. It is a really flexible approach, we can even have a different kind of techlogy between leaders and followers but it is really error prone.

### replication lag
It can happen because of scability or latency and it can create confusion and issues in the clients. No one likes to see unupdated data. And teh application lag can go from a few seconds to a few minutes or even hours. 
Adding more followers would be a problem in a sync architecture because it will increase the processing time, it is even irrealistic in a sync process.

With a async process we have to deal with eventual consistency. 

How can we solve replication lag?

- Reading your own writes
  Read-after-write ensures that the client will read always his lasy updates submited by himself. If we need to read something that was submited by the client, we sould read from the leader. like the users profile. 
- Monotonic reads
- Consistent prefix reads

### Multi-leader replication 

This makes sense we we have multi data centers for different regions, it can improve the system performance removing the network delay for some users. It also can be useful if a datacenter fails, it can be replaced by another one. 

It works with leader nodes assuming the folowing role of other leaders, so each leader will replicate all the data to other leader. Of course it can raise consistency probles when:

- Autoincrementing keys, triggers and integrity constraints can be problematic;
- Clients with offline operation - each client lcoal database will work as a lead, CouchDB is designed for this mode of operation;
- Collaborative editing;
- Handling write conflicts - the best way to solve conflits is avoiding it, so make sure that each users will be righting just in on datacenter, all the time.
  Solve conflits in a multi leader replaication can be though and we can have data loss. How do we decide what is the most updated data? We can use an Id and change the most recent one or we can ask the user to choose the most recent. 

We can decide to solve the conflits in two stages:

- write: As soon as the database system detects a conflict in the log of replicated changes, it calls the conflict handler. 
- Read: All the conflicting writes are stored. On read, multiple versions of the data are returned to the application. The application may prompt the user or automatically resolve the conflict. CouchDB works this way.

All-to-all topology is the most adapted to multi leader replication, where every leader sends its writes to every other leader. We can have circular and start topologies. In the circular topology one leader receives info from one node and propagates it to the next one. In the start one design node fowards data to teh rest of the leaders. It can be a problemif a node fails and interrropts the replication chain. To prevent it we should ensure that messages can travel along from differents paths avoiding a single point of failure. But in this case we can have some messages overtaken others in the wrong order because they can reach the node faster.  
  
If possible avoid multi-leader replication. 

## Leaderless replication

Any replica can directly accept writes from clients. Dynamo style replication (not dynamo db) and cassandra works this way.

Eventually, all the data is copied to every replica. After a unavailable node come back online, it has two different mechanisms to catch up:

- Read repair. When a client detect any stale responses, write the newer value back to that replica.
- Anti-entropy process. There is a background process that constantly looks for differences in data between replicas and copies any missing data from one replica to he other. It does not copy writes in any particular order.
 This kind of replciation is good to system that can tolerate eventual consistency. 

Quorums is the algorithm used to manage the writers in a leaderless replciation database.

Quorums algorithm:
If there are n replicas, every write must be confirmed by w nodes to be considered successful, and we must query at least r nodes for each read. As long as w + r > n, we expect to get an up-to-date value when reading. r and w values are called quorum reads and writes. Are the minimum number of votes required for the read or write to be valid.

Limitations:

- Sloppy quorum, the w writes may end up on different nodes than the r reads, so there is no longer a guaranteed overlap.
- If two writes occur concurrently, and is not clear which one happened first, the only safe solution is to merge them. Writes can be lost due to clock skew.
- If a write happens concurrently with a read, the write may be reflected on only some of the replicas.
- If a write succeeded on some replicas but failed on others, it is not rolled back on the replicas where it succeeded. Reads may or may not return the value from that write.
- If a node carrying a new value fails, and its data is restored from a replica carrying an old value, the number of replicas storing the new value may break the quorum condition.


# Partitioning

Partitioning or sharding is usefull when we have a really huge ammount of info and replication is not enough. Scability is the main reason to implement partitioning, we can distribuite the query load across many processors. 

Each partition is a small database, that can have its own replication process. And a node can noda can have more than one partition. 

If the goal of partition is to spread data across several nodes to spred the effort to query the data we need to be cadeful with the partition strategy used to prevent to end up with partitions with more info than other (hotspots). We call skewed when a partition is unfair (less data) and it creates a system less efeective. 

## Partition by key range

To distrute the data randomly is not a good idea because then we have to request all the partitions to find the data.

If we take as exaple instagram we can see taht if we used the user names to distribute data, using alpahbetic order it would be unffair because Adriana Grand and Criatiano Ronaldo has a lot of followers.

## Partitioning by hash of key

Instead of it we can use hash heys. But even than can be a problem because we will still have a lot of information for some users like Cristiano Ronaldo. In this case we can add a number to the begin ot end of the key and distribute Cristaiano data across several partitions. In this especific solution we will have more work to combine all the data for this user in the readers. 

## secondary indexes

A secondary index is a data structure that contains a subset of attributes from a table, along with an alternate key to support Query operations

It can get even more complicated when we need to use secondary indexs, this usually don't identify just one record, so they don't map just one partition. It is a mix of partitions!!! Ohhh noooooooo


Solutions:
### Partitioning secondary indexes by document

Which partition will have their ones secondary indexs, so we need to query all partions and combine the results to have the final secodnary index. 

### global index (term-partitioned)

In this case we create a global index that will cover all the data in all the partitions, this index can be partitioned too to avoid bottleneck. The advantage is taht the reads will be much more faster because we check the indesxs before but the writes can be much more slower. 

# Transactions

Defenition of transaction: all the reads and writes in a transaction are executed as one operation: either the entire transaction succeeds (commit) or it fails (abort, rollback).
The goal is to avoid inconsistent states in the storage system. 
A transaction is a mechanism for grouping multiple operations on multiple objects into one unit of execution.


ACID is an acronym that refers to the set of 4 key properties that define a transaction: Atomicity, Consistency, Isolation, and Durability. ACID transactions ensure the highest possible data reliability and integrity.

- Atomicity. Is not about concurrency. It is what happens if a client wants to make several writes, but a fault occurs after some of the writes have been processed. Abortability would have been a better term than atomicity. Either the entire statement is executed, or none of it is executed.  This property prevents data loss and corruption from occurring if, for example, if your streaming data source fails mid-stream. It can be implemented using a log for crash recovery.

- Consistency. Invariants on your data must always be true. The idea of consistency depends on the application's notion of invariants. Atomicity, isolation, and durability are properties of the database, whereas consistency (in an ACID sense) is a property of the application. ensures that transactions only make changes to tables in predefined, predictable ways. Transactional consistency ensures that corruption or errors in your data do not create unintended consequences for the integrity of your table.
  
- Isolation. Concurrently executing transactions are isolated from each other. It's also called serializability, each transaction can pretend that it is the only transaction running on the entire database, and the result is the same as if they had run serially (one after the other). When multiple users are reading and writing from the same table all at once, isolation of their transactions ensures that the concurrent transactions don’t interfere with or affect one another. Each request can occur as though they were occurring one by one, even though they're actually occurring simultaneously. It can be implemented using a lock on each object, allowing only one thread to access an object at any one time.
  
- Durability. Once a transaction has committed successfully, any data it has written will not be forgotten, even if there is a hardware fault or the database crashes. In a single-node database this means the data has been written to nonvolatile storage. In a replicated database it means the data has been successfully copied to some number of nodes.

The advantage of aborts is to keep data consistent and enable safe retries. 

To implement isolation and prevent concurrent isser or race conditions we can implement several levels of isolation: 

### Read committed
It makes two guarantees:
- when readinf we will just read data commit. That means that we will just read infomartion from transations finished. Read locker is not a good idea because we can force writes to ways for a long time when we have long readers executing. But is this case we can read outdated data because the transation is not finished yet. 

- When writing from database we are just overwriting over data taht has been commited. To avoud dirty writes the row is locked until the transation is finished. 

### Snapshot isolation and repeatable read

Nonrepeatable read or read skew, when you read at the same time you committed a change you may see temporal and inconsistent results.

Backups and Analytic queries and integrity checks sould avoid skew to prevent restores from incosistent data and to prevent to get data that doesn't makes sense. 

Snapshop isolation is a possibel solution where each transation reads from a consistent snapshot from the database. 

### Lost updates

It may happen if in two idenpendt transations, the app needs to read something the databasem modify and commit it again (read-modify-write cycles). It can be prevented using an atomic operation. 
Atomic operations can be prformed in individual small units, everything at once like in the following query:

UPDATE counters SET value = value + 1 WHERE key = 'foo';

It cannnot be applyed in o complex data structures in the way that locks can.

Explicit locking - lock objects that will be updated. 

Compare-and-set - In the transation read the value, before finishe the commit read again and compare with the previews one. If it doens't match the transaction will fail. It doesn't work with multi-leader or leaderless replication. Example:

UPDATE wiki_pages SET content = 'new content'
  WHERE id = 1234 AND content = 'old content';


## Write skew

 can occur if two transactions read the same objects, and then update some of those objects. You get a dirty write or lost update anomaly.

The shift doctores problem: (cahnge this)

ALICE                                   BOB

┌─ BEGIN TRANSACTION                    ┌─ BEGIN TRANSACTION
│                                       │
├─ currently_on_call = (                ├─ currently_on_call = (
│   select count(*) from doctors        │    select count(*) from doctors
│   where on_call = true                │    where on_call = true
│   and shift_id = 1234                 │    and shift_id = 1234
│  )                                    │  )
│  // now currently_on_call = 2         │  // now currently_on_call = 2
│                                       │
├─ if (currently_on_call  2) {          │
│    update doctors                     │
│    set on_call = false                │
│    where name = 'Alice'               │
│    and shift_id = 1234                ├─ if (currently_on_call >= 2) {
│  }                                    │    update doctors
│                                       │    set on_call = false
└─ COMMIT TRANSACTION                   │    where name = 'Bob'  
                                        │    and shift_id = 1234
                                        │  }
                                        │
                                        └─ COMMIT TRANSACTION



How to solve this?
Craete a transaction that will lock all the rows that can afect it, in this case, all the rows off doctores on call:

BEGIN TRANSACTION;

SELECT * FROM doctors
WHERE on_call = true
AND shift_id = 1234 FOR UPDATE;

UPDATE doctors
SET on_call = false
WHERE name = 'Alice'
AND shift_id = 1234;

COMMIT;

### Serializability

Serializability will prevent more than one transation happening at the same time. Best isolation strategy. How?

- serial execution - emove concurrency entirely and execute only one transaction at a time, in serial order, on a single thread. No consurrency is possible. 
  We can use stored procedures to encrise the velocity in precess the information, this way all the data is already in memory and we just need to execute it. Disavantages:
    - Each database vendor has its own language for stored procedures. They usually look quite ugly and archaic from today's point of view, and they lack the ecosystem of libraries.
    - It's harder to debug, more awkward to keep in version control and deploy, trickier to test, and difficult to integrate with monitoring. No one likes SP. 

- Two-phase locking (2PL)
  First phase is when the locks are acquired, second phase is when all the locks are released. The readers don't block anything but the writers block readers + writers.

The lock is used as follows:

if a transaction want sot read an object, it must first acquire a lock in shared mode.
If a transaction wants to write to an object, it must first acquire the lock in exclusive mode.
If a transaction first reads and then writes an object, it may upgrade its shared lock to an exclusive lock.
After a transaction has acquired the lock, it must continue to hold the lock until the end of the transaction (commit or abort). First phase is when the locks are acquired, second phase is when all the locks are released.

  A deadlock will happen when a transation A is waiting for the transation B to release the lock. This startegy can be painfull at high percentiles and when a specific transation needs to access a lot of data blocking the data to the rest of the application.  


- Serializable snapshot isolation (SSI) - is a multi-version concurrency control approach that shares many features of Snapshot Isolation and, in addition, ensures that all executions of the system have the property of serializability.

https://www.integrate.io/blog/snowflake-schemas-vs-star-schemas-what-are-they-and-how-are-they-different/#:~:text=Star%20schemas%20will%20only%20join,for%20datamarts%20with%20simple%20relationships.



## The trouble with distributed systems

Ok, things will fail, components will unpredicable fail, services, databases...everything can fail. And partial fails need to be nondeterministic. That means tha we need to build a fault-tolerant mechanism. **We need to build a reliable system from unreliable components.**

What can goes wrong??

### Unreliable networks

In a share nothing architecture, we have multiple nodes that doesn't share any ressource (memory, disk-space, cpu...). It has several advantages and disavantages. In this systems it is easier to scale, eliminate single points of failure, simplicafies upgrades and prevents downtimes from the entire system. One of the disavanges of this systems are network problms, it can decrease the performance of the system due to time spent in transations and it will increase the probablity of some system fail. Because if we have more nodes to take care something will happen for sure:

- Request lost
- Request waiting in a queue to be delivered later
- Remote node may have failed
- Remote node may have temporarily stoped responding
- Response has been lost on the network
- The response has been delayed and will be delivered later
- Someones dog just ate the internet cabe

And when it fails it is impossible to the one requesting info to know why. The tarditional way how to deal with it is ** timeout** 

### Servers failing

-  Crash-Stop - if fails and don't recover alone. 

- Crash-Recovery - it fails for some time, it can be caused for a SO crash or Stop-the-world GC problem 
  
### Timeouts and unbounded delays

The right value to set the timeout is the question that everyone wants to have anwsered. If you declare a log timeout maybe we will taking to long to declare the node dead and we will lose some information. If it is to short we can be incorrecly declaring the node dead and it can be even worse. 

We can use a timeout dynamic, by measuring the distribution of network round-trip times over an extended period.

Retry is a good startegy to add some tolerance to fails, the problem with retry is that it can increase even more the possible problem adding more requests to a system that cannot process what he already have, so we can configure a Exponential Backoff that means that we will add time betewwen any request:

try 1: after the failed request
try 2: after 50ms
try 3: after 500ms
try 4: after 5000ms

This way we are giving time to the server deal with all its mess!!!

Circuit Breaker pattern can prevent an application from repeatedly trying to execute an operation that's likely to fail. Allowing it to continue without waiting for the fault to be fixed or wasting CPU cycles while it determines that the fault is long lasting and it can be used together with the retry pattern. If it will fail, just don't do it until it is solved. 

The proxy can be implemented as a state machine with the following states that mimic the functionality of an electrical circuit breaker:

- Closed: The request from the application is routed to the operation. The proxy maintains a count of the number of recent failures, and if the call to the operation is unsuccessful the proxy increments this count. If the number of recent failures exceeds a specified threshold within a given time period, the proxy is placed into the Open state. At this point the proxy starts a timeout timer, and when this timer expires the proxy is placed into the Half-Open state.

The purpose of the timeout timer is to give the system time to fix the problem that caused the failure before allowing the application to try to perform the operation again.

- Open: The request from the application fails immediately and an exception is returned to the application.

- Half-Open: A limited number of requests from the application are allowed to pass through and invoke the operation. If these requests are successful, it's assumed that the fault that was previously causing the failure has been fixed and the circuit breaker switches to the Closed state (the failure counter is reset). If any request fails, the circuit breaker assumes that the fault is still present so it reverts back to the Open state and restarts the timeout timer to give the system a further period of time to recover from the failure.

### Chaos Monkey

I love this idea. Create problems and failes in the system so we can solve problems before the users have to deal with it. https://en.wikipedia.org/wiki/Chaos_engineering#Chaos_Monkey

### Unreliable clocks

Clock are a pain to developers, well, it can get worse. Clocks to manage syncronzations. 

It is possible to synchronise clocks with **Network Time Protocol (NTP)**.

Each machine in the network has two types of clocks:

- Time-of-day clocks:Return the current date and time according to some calendar (wall-clock time). If the local clock is toof ar ahead of the NTP server, it may be forcibly reset and appear to jump back to a previous point in time. This makes it is unsuitable for measuring elapsed time.

- Monotonic clocks: They are guaranteed to always move forward. It calculates the time spent so it cannot be affected by the NTP sync. It is ok to use this clock to manage messages order when we are using just one machine to produce the messages. When we have multiple estrategies we can use the Last-Write-Wins, but sometimes it will have information losted. 

## Consistency and consensus

**eventual consistency** - The inconsistency is temporary, and eventually resolves itself, it is just a time question. 

**Linearizability** - makes sure that for the developer seems that we have just one data source. So, all the operaitons on it are atomic

**Serializability** - Transactions behave the same as if they had executed some serial order.

### What do we need to have Linearizability?

## Batch processing

What it is??? 
Batch processing is something that reads a large file of info and generates a report or something with that info.

### Batch processing with Unix tools
If the size of the data to analise is not to big we can build a simple log analysis job using Unix tools use stdin and stdout as input and output.

## Hadoop File System (HDFS)

Uses MapReduce jobs that read and write files on a distributed filesystem, so it is developed to work with large ammounts of info. 

HDFS is a centralised storage applicance, based on the shared-nothing principle exposing a network of nodes with files, a central node called the NameNode 

Systema de dados distribuidos 
- 
RFC
ADR

## Stream processing

The main goal is to abandone the sync processing and data updating and do it incrementally available all over teh time. - Eventual concistency.

A record is an event with a timespan. An event is created and published by a publisher (publisher or sender) and consumed my one or more consumers or subcribers (subcribers or recipients). 

We can have a publisher sending mensagens directly to the consumer, but it is not a good ideia becuase we need to deal with nodes getting offline and messages flow, erros, metrics 

Let's use message blokers.


Message brokers or message queue is a kind of database optimised to manage comunication between publishers and consumers. This way we are delegating to the message broker all the logistic to receive and send the messages to the right subriver. Some of the message brokers just keep the messages temporarly with others keep it in disk to avoid to lose info if something goes wrong. This is an async process. So the publisher just waits for the anwser from the message broker that it received the message, but then it is responsabolity of the broker to propagate it (fire and forget)

The tarditional message brokers use XA and JTA protocols, is a kind of system insurance against data corruption (and the resulting business losses). This wait the top caracteristics from a message broker as a database base are:

- Most message brokers automatically delete a message when it has been successfully delivered to its consumers. This makes them not suitable for long-term storage.
- Most message brokers assume that their working set is fairly small. If the broker needs to buffer a lot of messages, each individual message takes longer to process, and the overall throughput may degrade.
- Message brokers often support some way of subscribing to a subset of topics matching some pattern.
- Message brokers do not support arbitrary queries, but they do notify clients when data changes.

When multiple consumers read messages in the same topic, to main patterns are used:

- Load balancing: Each message is delivered to one of the consumers. The broker may assign messages to consumers arbitrarily.
- Fan-out: Each message is delivered to all of the consumers.
  
To make sure that the message broker doesn't delete messages that have not being consumed yet we have the acknowledgements from the consumers that it processed properly the message. 

Since applications using event sourcing usally saves a log of events and transform it into an applciation status it turns much more easier to detect and solve problems and recover data when something wrong or an exception happens. (storing snapshots)

When using event sourcing the first interaction from the client would be a command (sync) with validations and a response to the user. Then an event will be created and published (async). We can have a second event as a result of a validation. It allow us to have async validations.

Immutable events - events cannot be changes, once they happend they will persist in the database like that. Since message brokers worked as  append-only ledger, that means that we are just adding information to the log, never changing, if something goes wrong we will raise new events to compensate for the mistakes, never remove or change it.

Message brokers as Kafka can be used to store data that will be digested by technologies like Druid and pistachio.  Kafka Connect sinks can export data from Kafka to various different databases and indexes.



### command query responsibility segregation (CQRS)

Separece the resposability to write data from to read data. 
The biggest problem of event sourcing is that with async actions and SQRS a user can make a write in a database and read from one that is not updated yet. 

And remove sensitive information. How can we do it???



## References
https://brenocferreira.medium.com/designing-data-intensive-apps-um-resumo-1a62de5358f4
https://github.com/keyvanakbary/learning-notes/blob/master/books/designing-data-intensive-applications.md#reliable-scalable-and-maintainable-applications
https://www.youtube.com/watch?v=PdtlXdse7pw&list=PL4KdJM8LzAMecwInbBK5GJ3Anz-ts75RQ

https://thrift-tutorial.readthedocs.io/en/latest/thrift-stack.html