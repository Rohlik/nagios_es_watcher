<img src="http://i.imgur.com/DYuYuEJ.png" height=60><img src="http://joinhandshake.com/img/posts/elasticsearch.png" height=65>
## Nagios Watcher script for Elasticsearch Indices

This is a simple script to check the status of an elasticsearch watcher history and other indices.

### Options
```
  -H/--hostname
     Defines the hostname. Default is: localhost
  -P/--port
     Defines the port. Default is: 9200
  -A/--auth
     Defines the HTTP authentication. Default is: none
  -L/--last
     Specifies the timerange to search Default is: 5m
  -p/--path
     Specifies the query path. Default is: ".watch_history*/_count"
  -T/--ts
     Specifies the timefield for filters. Default is: "@timestamp"
  -Q/--query
     Specifies the query string to use. Default is: "*" 
```

#### Usage Examples
Count watcher events in last 5 minutes using timefield __result.execution_time__ and __query_string__
```
./nagios_es_watcher -H 127.0.0.1 -P 9200 --auth "username:password" \
-Q "result.condition.met:true" -L "5m" -T "result.execution_time"
```

Count specific matches in last hour using custom __path__ and __query_string__ and 
```
./nagios_es_watcher -H 127.0.0.1 -P 9200 --auth "username:password" \
-Q "reply:503 AND cseq:INVITE" -L "1h" --path "myindex-*/_count"
```
 
