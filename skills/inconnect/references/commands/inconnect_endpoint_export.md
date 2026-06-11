## inconnect endpoint export

Export endpoints to Excel

```
inconnect endpoint export [flags]
```

### Options

```
      --file string        Output file path (default: stdout)
  -h, --help               help for export
      --language int       Export language (1=English, 2=Chinese) (default 2)
      --name string        Filter by name
      --router-id string   Filter by router ID
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
