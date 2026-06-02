## inconnect mail create

Create and send an email notification

```
inconnect mail create [flags]
```

### Options

```
      --content string   Email content (HTML supported, required)
  -h, --help             help for create
      --only-admin       Send only to organization admins
      --title string     Email title (required)
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
