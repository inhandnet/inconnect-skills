## inconnect mail verify

Send a test/verification email

```
inconnect mail verify [flags]
```

### Options

```
      --address string   Test email address (required)
      --content string   Email content (required)
  -h, --help             help for verify
      --only-admin       Send only to admins
      --title string     Email title (required)
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
