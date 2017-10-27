# Hands on Druid

Agenda:

Loading data into Druid 
  - Loadind data into a kerberized Druid cluster
    - Loading data using Superset
    - Loading data using Hive (LLAP)
    - Loading data using CURL 
  - Loading data into a non-kerberized Druid cluster
    - Loading data using Superset
    - Loading data using Hive (LLAP)
    - Loading data using CURL 

Reading data from Druid
  - Reading data into a kerberized Druid cluster
    - Reading data using Superset
    - Reading data using Hive (LLAP)
    - Reading data using CURL 
  - Reading data into a non-kerberized Druid cluster
    - Reading data using Superset
    - Reading data using Hive (LLAP)
    - Reading data using CURL 



## Loading Data into Druid 

#### Requirements
- Should have a HDP cluster with HDP 2.6.2 version
- Have druid installed as a service

### Sample Data to use
We'll use this sample data for our testing

```
{"time": "2015-09-01T00:00:00Z", "url": "/foo/bar", "user": "alice", "latencyMs": 32}
{"time": "2015-09-01T01:00:00Z", "url": "/", "user": "bob", "latencyMs": 11}
{"time": "2015-09-01T01:30:00Z", "url": "/foo/bar", "user": "bob", "latencyMs": 45}
```
> Timestamps are mandatory, strings are dimensions and integer values are metrics.
> In our example, *time* represents timestamp, *url* and *user* represent dimensions and *latencyMs* is the only metric


### Loading static file from HDFS

- Create a file with those three lines named index.json
- Upload the file to HDFS under /apps/druid/warehouse/
```
hdfs dfs -put index.json /apps/druid/warehouse
```
- Data can be loaded through overlord hostname and port as endpoint 
```
curl -X 'POST' -H 'Content-Type:application/json' -d@load_from_hdfs.json xlhost1.openstacklocal:8090/druid/indexer/v1/task 
```
















