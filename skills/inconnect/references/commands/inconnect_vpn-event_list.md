## inconnect vpn-event list

List VPN events (connected/disconnected/auth_failed)

```
inconnect vpn-event list [flags]
```

### Options

```
      --after string      Only events at/after this time (e.g. 2024-01-01T00:00:00Z)
      --before string     Only events before this time
      --cursor int        Pagination cursor / offset
  -h, --help              help for list
      --limit int         Maximum number of records to return (default 20)
      --rid string        Filter by router ID
      --sort string       Sort order (e.g. createdAt,desc)
      --type string       Filter by event type, comma-separated (e.g. auth_failed,connected)
      --uid string        Filter by user ID
      --username string   Filter by username (prefix match)
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
