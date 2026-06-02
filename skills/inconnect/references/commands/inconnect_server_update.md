## inconnect server update

Update a VPN server

```
inconnect server update <id> [flags]
```

### Options

```
  -h, --help                   help for update
      --second-increment int   Second octet increment for IP allocation
      --subnet string          Server subnet (e.g. 10.8.0.0/16)
      --third-increment int    Third octet increment for IP allocation
```

### Options inherited from parent commands

```
      --context string   Config context to use
      --debug            Enable debug output
      --jq string        Filter JSON output using a jq expression
      --oid string       Organization ID
  -o, --output string    Output format: json, table, yaml (default: table for TTY, json otherwise)
      --show-secrets     Reveal private keys in output (redacted by default)
      --verbose int      API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
