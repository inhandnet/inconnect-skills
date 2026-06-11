## inconnect router connection-events

List a device's MQTT online/offline events

```
inconnect router connection-events <device-id> [flags]
```

### Options

```
      --after string        Only events at/after this time (e.g. 2024-01-01T00:00:00Z)
      --before string       Only events before this time
      --cursor int          Pagination cursor / offset
      --event-type string   Filter by event type (e.g. online, offline)
  -h, --help                help for connection-events
      --limit int           Maximum number of records to return (default 20)
      --sort string         Sort order (e.g. createdAt,desc)
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
