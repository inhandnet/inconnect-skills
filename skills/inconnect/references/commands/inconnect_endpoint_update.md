## inconnect endpoint update

Update an endpoint

```
inconnect endpoint update <id> [flags]
```

### Options

```
  -h, --help               help for update
      --ip string          Real IP address
      --mac string         MAC address
      --name string        Endpoint name
      --router-id string   Router ID (required)
      --vip string         Virtual IP address
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
