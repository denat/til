# Use structured logging (JSON) in production

Always output logs as JSON in production. 

Production logs are meant to be parsed and indexed by search engines (like ElasticSearch) and viewed using various dashboards (like Grafana and Kibana). They're typically [not human scale](https://www.youtube.com/watch?v=HMELIR2msdg).

This comes with a major benefit: you can include A LOT of metadata in your json that you couldn't have logged otherwise! (because it would create too much noise for it to be human-readable)

Loggers like Pino can automatically add various metadata to a log entry:

```json
{
   "level":"info",
   "time":1631620242409,
   "pid":32636,
   "hostname":"MSI",
   "req":{
      "id":2,
      "method":"POST",
      "url":"/graphql",
      "headers":{
         "content-type":"application/json",
         "user-agent":"graphiql-app",
         "connection":"close",
         "content-length":"379"
      },
      "remoteAddress":"::ffff:127.0.0.1",
      "remotePort":62768
   },
   "res":{
      "statusCode":200,
      "headers":{
         "x-powered-by":"Express",
         "access-control-allow-origin":"*",
         "content-type":"application/json; charset=utf-8",
         "content-length":"35",
         "etag":"W/\"23-1ZLHNcgA0dB4jeOVD3/LVZJkhbE\""
      }
   },
   "responseTime":21040,
   "msg":"request completed"
}
```

Search engines like ElasticSearch will parse the JSON-structured log and destructure its properties into their own `log_processed` fields, allowing you to then query your logs easily.

Example Kibana query (KQL) to use the processed attributes:
```
log_processed.level: "info" and log_processed.res.statusCode: 200
```

Unstructured logging is OK for your local dev environment, or a staging environment where you're SSHing into the log output.