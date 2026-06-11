## inconnect audit-log export

Export audit logs to XLS file

```
inconnect audit-log export [flags]
```

### Options

```
      --after string    Start time (e.g. 2024-01-01, 2024-01-01T00:00:00Z)
      --before string   End time (e.g. 2024-12-31, 2024-12-31T23:59:59Z)
      --file string     Output file path (default: stdout)
  -h, --help            help for export
      --language int    Export language (1=English, 2=Chinese) (default 2)
      --level int       Log level filter
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
