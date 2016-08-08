## Nagios check script for Elasticsearch Watcher History

This is a simple script to check the status of an elasticsearch watcher history index.

####Usage
Count events in last 5 minutes using timefield __result.execution_time__ and ___query_string__
```
./nagios_es_watcher -H 127.0.0.1 -P 9200 --auth "username:password" \
-Q "result.condition.met:true" -L "5m" -T "result.execution_time"
```
