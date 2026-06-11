## inconnect network members update

Add or remove routers and accounts from a network

```
inconnect network members update <network-id> [flags]
```

### Options

```
      --add-accounts strings   Account IDs to add
      --add-routers strings    Router IDs to add
      --del-accounts strings   Account IDs to remove
      --del-routers strings    Router IDs to remove
  -h, --help                   help for update
      --transfer-to string     Network ID to transfer removed members to
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
