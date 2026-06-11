## inconnect api

Make an authenticated API request

### Synopsis

Make a raw API request to the InConnect server. Example: inconnect api /api/invpn/networks/list

```
inconnect api <path> [flags]
```

### Options

```
  -h, --help            help for api
  -X, --method string   HTTP method (default "GET")
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
