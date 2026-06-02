## inconnect router list

List VPN routers

```
inconnect router list [flags]
```

### Options

```
      --connected string   Filter by connection status (true/false)
      --cursor int         Pagination cursor / offset
  -h, --help               help for list
      --limit int          Maximum number of records to return (default 20)
      --name string        Filter by name
      --online string      Filter by online status
      --query string       Search across name and serial number
      --rip string         Filter by real IP address
      --serial string      Filter by serial number
      --sort string        Sort order (e.g. createdAt,desc)
      --vip string         Filter by virtual IP
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
