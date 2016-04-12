AWG meeting
===========
13 April 2016

## Discussion
Flume HDFS output data formats and aggregation policies

!

## Architecture
* Flume `agents` emitting log lines (JSON)
* Flume `sinks` collecting data and writing in *tmp* folders
* Daily (monthly) aggregations to delete duplicates and to consolidate 1GB files

!
