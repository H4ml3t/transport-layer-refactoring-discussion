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

![hadoop fs ls](hls_01.png "flume output example months")

!

![hadoop fs ls](hls_02.png "current month")

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
