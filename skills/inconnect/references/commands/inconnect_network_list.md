## inconnect network list

List VPN networks

```
inconnect network list [flags]
```

### Options

```
      --cursor int    Pagination cursor / offset
  -h, --help          help for list
      --limit int     Maximum number of records to return (default 20)
      --name string   Filter by name
      --sort string   Sort order (e.g. createdAt,desc)
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
