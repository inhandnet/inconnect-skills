## inconnect connection-log list

List VPN connection session logs

```
inconnect connection-log list [flags]
```

### Options

```
      --after string      Only sessions started at/after this time (e.g. 2024-01-01, 2024-01-01T00:00:00Z)
      --before string     Only sessions started before this time
      --cursor int        Pagination cursor / offset
  -h, --help              help for list
      --limit int         Maximum number of records to return (default 20)
      --rid string        Filter by router ID
      --sort string       Sort order (e.g. createdAt,desc)
      --status string     Filter by session status: active or closed
      --type string       Filter by account type: user or router
      --uid string        Filter by user ID
      --username string   Filter by account username (prefix match)
```

### Options inherited from parent commands

```
  -c, --columns strings   Table columns to show (comma-separated dot-paths; prefix ! to exclude)
      --context string    Config context to use
      --debug             Enable debug output
      --jq string         Filter JSON output using a jq expression
      --oid string        Organization ID
  -o, --output string     Output format: json, table, yaml (default: table for TTY, json otherwise)
      --verbose int       API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
