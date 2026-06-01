## ics alert list

List alerts

```
ics alert list [flags]
```

### Options

```
      --ack string           Filter by ack status (true/false)
      --after string         Start time (e.g. 2024-01-01, 2024-01-01T00:00:00Z)
      --before string        End time (e.g. 2024-12-31, 2024-12-31T23:59:59Z)
      --cursor int           Pagination cursor / offset
  -h, --help                 help for list
      --limit int            Maximum number of records to return (default 20)
      --name string          Filter by name
      --rid string           Filter by router ID
      --router-name string   Filter by router name
      --sort string          Sort order (e.g. createdAt,desc)
```

### Options inherited from parent commands

```
      --context string   Config context to use
      --debug            Enable debug output
      --jq string        Filter JSON output using a jq expression
      --oid string       Organization ID
  -o, --output string    Output format: json, table, yaml (default: table for TTY, json otherwise)
      --verbose int      API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
