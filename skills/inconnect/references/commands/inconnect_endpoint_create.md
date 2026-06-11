## inconnect endpoint create

Create an endpoint on a router

```
inconnect endpoint create [flags]
```

### Options

```
  -h, --help               help for create
      --ip string          Real IP address (required)
      --mac string         MAC address
      --name string        Endpoint name (required)
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
