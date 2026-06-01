## ics network endpoints list

List endpoints in a network

```
ics network endpoints list <network-id> [flags]
```

### Options

```
      --cursor int    Pagination cursor / offset
  -h, --help          help for list
      --limit int     Maximum number of records to return (default 20)
      --name string   Filter by name
      --rip string    Filter by real IP
      --sort string   Sort order (e.g. createdAt,desc)
      --vip string    Filter by VIP
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
