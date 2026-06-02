## inconnect audit-log list

List audit/behavior logs

```
inconnect audit-log list [flags]
```

### Options

```
      --after string      Start time (required, e.g. 2024-01-01, 2024-01-01T00:00:00Z)
      --before string     End time (required, e.g. 2024-12-31, 2024-12-31T23:59:59Z)
      --cursor int        Pagination cursor / offset
  -h, --help              help for list
      --level ints        Log level filter (can specify multiple)
      --limit int         Maximum number of records to return (default 20)
      --sort string       Sort order (e.g. createdAt,desc)
      --username string   Filter by username
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
