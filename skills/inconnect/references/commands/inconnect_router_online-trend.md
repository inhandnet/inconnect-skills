## inconnect router online-trend

Get a device's online/offline trend over a time range

### Synopsis

Get this device's online/offline state over time (a time series of
[timestamp, 0|1] where 1 = online).

For an instantaneous online/offline count across the organization, use
"router stats" instead.

```
inconnect router online-trend <id> [flags]
```

### Options

```
      --after string    Start time, e.g. 2026-06-01 (default 24h ago)
      --before string   End time, e.g. 2026-06-02 (default now)
  -h, --help            help for online-trend
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
