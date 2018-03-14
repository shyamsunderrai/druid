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
[druid@xlhost1 ~]$ curl -X 'POST' -H 'Content-Type:application/json' -d@load_from_hdfs.json xlhost1.openstacklocal:8090/druid/indexer/v1/task
{"task":"index_hadoop_sample_2017-10-27T06:30:01.462Z"}
[druid@xlhost1 ~]$  
```
Searching/querying the loaded data requires a POST request in JSON format or depending on the type of data being loaded/read.

```
{
  "queryType": "search",
  "dataSource": "wikipedia_20180313",
  "granularity": "day",
  "searchDimensions": [
    "page",
    "language"
  ],
  "query": {
    "type": "insensitive_contains",
    "value": "Atractus"
  },
  "sort" : {
    "type": "lexicographic"
  },
  "intervals": [
    "2015-09-12T00:00:00.000Z/2015-09-13T00:00:00.000Z"
  ]
}
```

- Query is executed using the POST method like this 
```
[druid@xlautomation-1 ~]$  curl -X POST 'xlautomation-1.h.c:8082/druid/v2/?pretty' -H 'Content-Type:application/json' -d @search.json
```
:Result

```
[ {
  "timestamp" : "2015-09-12T00:00:00.000Z",
  "result" : [ {
    "dimension" : "page",
    "value" : "Atractus apophis",
    "count" : 1
  }, {
    "dimension" : "page",
    "value" : "Atractus bocki",
    "count" : 1
  }, {
    "dimension" : "page",
    "value" : "Atractus duboisi",
    "count" : 1
  }, {
    "dimension" : "page",
    "value" : "Atractus edioi",
    "count" : 1
  }, {
    "dimension" : "page",
    "value" : "Atractus flammigerus",
    "count" : 1
  } ]
} ]
```












