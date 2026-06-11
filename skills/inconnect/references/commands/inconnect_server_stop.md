## inconnect server stop

Stop VPN server(s) for an organization

```
inconnect server stop <org-id> [flags]
```

### Options

```
      --group string   Server group (if omitted, stops all servers)
  -h, --help           help for stop
```

### Options inherited from parent commands

```
  -c, --columns strings   Table columns to show (comma-separated dot-paths; prefix ! to exclude)
      --context string    Config context to use
      --debug             Enable debug output
      --jq string         Filter JSON output using a jq expression
      --oid string        Organization ID
  -o, --output string     Output format: json, table, yaml (default: table for TTY, json otherwise)
      --show-secrets      Reveal private keys in output (redacted by default)
      --verbose int       API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
