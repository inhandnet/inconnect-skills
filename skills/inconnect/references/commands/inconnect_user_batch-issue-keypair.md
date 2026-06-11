## inconnect user batch-issue-keypair

Issue new key pairs for multiple users

### Synopsis

Issue new key pairs for multiple users.

Arguments are VPN user IDs (the 'id' field from 'user list', not 'uid').

```
inconnect user batch-issue-keypair <id> [id...] [flags]
```

### Options

```
  -h, --help   help for batch-issue-keypair
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
