## inconnect endpoint list

List endpoints

### Synopsis

List endpoints for a specific router (--router-id) or all endpoints.

```
inconnect endpoint list [flags]
```

### Options

```
      --cursor int         Pagination cursor / offset
  -h, --help               help for list
      --limit int          Maximum number of records to return (default 20)
      --name string        Filter by name
      --rip string         Filter by real IP
      --router-id string   Filter by router ID
      --sort string        Sort order (e.g. createdAt,desc)
      --vip string         Filter by virtual IP
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
