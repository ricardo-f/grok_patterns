# Uncategorized or one grok pattern stuff will be here:

1. **MongoDB Logs**

```
%{TIMESTAMP_ISO8601:timestamp}\s*%{MONGO3_SEVERITY:severity}\s*%{MONGO3_COMPONENT:component}%{SPACE}(?:\[%{DATA:context}\])?\s*%{GREEDYDATA:message}
```
