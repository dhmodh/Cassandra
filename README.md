# Apache Cassandra 🌐

Apache Cassandra is a highly-scalable, partitioned row store. Rows are organized into tables with a required primary key.

[Partitioning](https://cwiki.apache.org/confluence/display/CASSANDRA2/Partitioners) ✨ allows Cassandra to distribute your data across multiple machines in an application-transparent manner. Cassandra will automatically repartition as machines are added and removed from the cluster.

[Row store](https://cwiki.apache.org/confluence/display/CASSANDRA2/DataModel) 🔗 means that, like relational databases, Cassandra organizes data by rows and columns. The Cassandra Query Language (CQL) is a close relative of SQL.

For more information, visit the [Apache Cassandra website](http://cassandra.apache.org/). 🔍

Issues should be reported on [The Cassandra Jira](https://issues.apache.org/jira/projects/CASSANDRA/issues/). 🔧

---

## Requirements ✅

- **Java**: Refer to `build.xml` (search for the property `java.supported`) for supported versions.
- **Python**: Required for `cqlsh`. Check the function `is_supported_version` in `bin/cqlsh` for compatible versions.

---

## Getting Started 🚀

This short guide will help you set up a basic one-node cluster and demonstrate simple reads and writes. For a more comprehensive guide, visit the [Getting Started Guide](https://cassandra.apache.org/doc/latest/cassandra/getting_started/index.html) on the Apache Cassandra website.

### Step 1: Unpack the Archive 🔑
```bash
$ tar -zxvf apache-cassandra-$VERSION.tar.gz
$ cd apache-cassandra-$VERSION

### Step 2: tart the Server 🚀

Run the startup script with the -f argument to keep Cassandra in the foreground and log to the console. Stop the server with Ctrl+C.
```bash
$ bin/cassandra -f

### Step 3: Use CQL to Read and Write Data 🔗

Start the interactive Cassandra Query Language shell (CQLSH):
```bash
$ bin/cqlsh

If everything is working, you’ll see:

```bash
Connected to Test Cluster at localhost:9160.
[cqlsh 6.3.0 | Cassandra 5.0-SNAPSHOT | CQL spec 3.4.8 | Native protocol v5]
Use HELP for help.
cqlsh>

Example Commands 🔄
Create a keyspace:

```bash
CREATE KEYSPACE dmx WITH replication = { 'class' : 'SimpleStrategy', 'replication_factor' : 1 }; -- dmx is Keyspace name

Switch to the new keyspace:

```bash
USE dmx;

Create a table:

```bash
CREATE TABLE users (
  user_id varchar PRIMARY KEY,
  first varchar,
  last varchar,
  age int
);

Insert data into the table:

```bash
INSERT INTO users (user_id, first, last, age)
VALUES ('dmx', 'Dishant', 'Modh', 24);

Retrieve data:

```bash
SELECT * FROM users;

Expected output:

```bash
 user_id | age | first | last
---------+-----+-------+-------
  dmx |  24 |  Dishant | Modh

If your session looks similar, congratulations! 🎉 Your single-node cluster is operational.

For more details, refer to the [CQL Reference] (https://cassandra.apache.org/doc/stable/cassandra/cql/).


