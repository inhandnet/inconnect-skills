## inconnect org list

List organizations

```
inconnect org list [flags]
```

### Options

```
      --creator string   Filter by creator
      --cursor int       Pagination cursor / offset
      --email string     Filter by email
  -h, --help             help for list
      --limit int        Maximum number of records to return (default 20)
      --name string      Filter by name
      --sort string      Sort order (e.g. createdAt,desc)
      --status string    Filter by status
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
