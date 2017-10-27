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

### Using CURL

We'll use this sample data for our testing

-- {"time": "2015-09-01T00:00:00Z", "url": "/foo/bar", "user": "alice", "latencyMs": 32}
-- {"time": "2015-09-01T01:00:00Z", "url": "/", "user": "bob", "latencyMs": 11}
-- {"time": "2015-09-01T01:30:00Z", "url": "/foo/bar", "user": "bob", "latencyMs": 45}
