## inconnect network update

Update a VPN network

```
inconnect network update <id> [flags]
```

### Options

```
      --center string        Center router ID (for star topology)
      --description string   Network description
  -h, --help                 help for update
      --name string          Network name
      --real-ip string       Real IP address
      --site-isolate         Enable site isolation
      --type string          Network type (mesh or star)
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
