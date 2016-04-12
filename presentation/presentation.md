AWG meeting
===========
13 April 2016

## Discussion
Flume HDFS output data formats and aggregation policies

!

## Architecture
* Flume `agents` emitting log lines (JSON)
* Flume `sinks` collecting data and writing in *tmp* folders
* Daily (monthly) aggregations to delete duplicates and to consolidate logs in 1GB files
* Monthly output folders

!

## HDFS view

For each dataset:

![hls](hls_01.png)

!

```
hadoop fs -ls /project/itmon/archive/lemon/vocmsweb/2016-04
Found 4 items
-rw-r--r--   3 itmonops ts          0 2016-04-12 05:45 /project/itmon/archive/lemon/vocmsweb/2016-04/_SUCCESS
-rw-r--r--   3 itmonops ts  817035112 2016-04-12 05:44 /project/itmon/archive/lemon/vocmsweb/2016-04/part-r-00000
-rw-r--r--   3 itmonops ts  816982481 2016-04-12 05:45 /project/itmon/archive/lemon/vocmsweb/2016-04/part-r-00001
-rw-r--r--   3 itmonops ts  817530853 2016-04-12 05:44 /project/itmon/archive/lemon/vocmsweb/2016-04/part-r-00002
```

!

## Record description

Each line is a JSON containing:

```json
{
  body: "",
  host: "",
  timestamp: "",
  toplevel_hostgroup: "",
  producer: ""
  metric: "",
  value: ""
}
```

!

# My experience

- Consumer only
- Daily running jobs to convert JSON in Parquet/Avro/CSV

!

## Issues

1) Not incremental updates
2) 

!

## Possible improvements

- Avoid to write encoded JSONs
