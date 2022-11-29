# Snowflake - architecture:

![Snowflake architecture](/images/architecture-overview.png)

[**Snowflake architecture refer.**](https://docs.snowflake.com/en/user-guide/intro-key-concepts.html)<br>

## Database Storage Layer:
* Stores table data and query results
* Data will be stored in columnar format
* Data will be stored in micro partitions
* Snowflake manages all aspects of how this
data is stored i.e. the data organization, file 
size, structure, compression, metadata,
statistics
* The data objects stored by Snowflake are not
directly visible nor accessible by customers;
they are only accessible through SOL query
operations run using Snowflake.
* We can define cluster keys on large tables for
better performance.

![Snowflake Data storage format (columnar format)](/images/columnar_format.jpg)

## Query Processing Layer:

* This is the actual processing unit of snowflake
* Snowflake processes queries using "virtual
warehouses"
* Each virtual warehouse is composed of
multiple compute nodes allocated by
Snowflake from a cloud provider.
* On AWS they are a group of EC2 instances
and on AZURE a group of Virtual Machines
Compute cost will be calculated on the basis
of query execution time on virtual warehouses
* Virtual Warehouses are considered as the
muscle of the system
* Can scale up and scale down easily
* Auto-Suspend and Auto-Resume is available

## Cloud Services Layer:

* Collection of services that coordinate
activities across Snowflake
* This is the Brain of the snowflake
* Authentication and access control
* Infrastructure management
* Metadata Management
* Security
* Manages all Serverless tasks like
* Snowpipe, Tasks, Materialized view
maintenance etc.