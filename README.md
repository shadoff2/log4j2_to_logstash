# log4j2_to_logstash
Example of log4j2 and logstash configurations working together

# wtf

Dummy java project with log4j2 configuration file

Make sure to change host and port in log4j2.properties:

```
appender.socket.host=
appender.socket.port=
```

## logstash configuration

log4j.conf with output to elasticsearch

```
input {
  tcp {
    port => 5000
    codec => json
  }
}

output {
  elasticsearch {
	hosts => ["localhost:9200"]
	index => "java"
  }
}
```

For example using deb ubuntu installation place it to /etc/logstash/conf.d
