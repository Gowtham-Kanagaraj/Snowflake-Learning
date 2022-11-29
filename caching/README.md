# Snowflake - Caching

## Caching
* Cache is a temporary storage location that stores copies of files or
data, so that they can be accessed faster in near future.
* Cache plays vital role in saving costs and speeding up results.
* Improves query performance.
* 2 Types of caches in Snowflake 
     * * Query Results Cache 
      
     * * Local Disk Cache

![Snowflake architecture](/images/flow.jpg)

![Snowflake Caching](/images/caching.jpg)

## ResultS Cache
* Results Cache is located in cloud services layer. This Cached data will
be available for next 24 hours.
* Results Cache will be available and can be accessed across different
virtual warehouses.
* Query results returned to one user is available to any other user on
the system who executes the same query.
* Results cache works until underlying data has not changed.
* Here mandatory condition is query should be same, won't work for
subset of data, and even won't work if we re-order columns.

## Local Disk Cache
* Local Disk Cache is located in the Virtual Warehouse (i.e. EC2/VM's
RAM /SSD).
* Cache the Data(not the results) fetched by SQL queries.
* Whenever data is needed for a given query it's retrieved
the Remote Disk storage, and cached in SSD and memory.
* Cached data is only available until the VW is up, once VW is
suspended, cache gets deleted.
* Even works when we query subset of data that is available in Local
disk cache.

  * Eg. Suppose when we query 10k records for the first time, Local
  disk cache will hold this 10 k records data and next time if we try to
  query only 2k or 3k records which is subset of above 10k, it will fetch
  from Local disk cache itself.
* This Cache depends on the Virtual Warehouse Size we are using. 
  *  Eg. X-Small VW can't hold Millions of records, but can fetch part of
  the data from Local disk cache and remaining from Remote disk.