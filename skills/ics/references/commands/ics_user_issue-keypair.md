## ics user issue-keypair

Issue a new key pair for a user

### Synopsis

Issue a new key pair for a user.

<id> is the VPN user ID (the 'id' field from 'user list', not 'uid').

```
ics user issue-keypair <id> [flags]
```

### Options

```
  -h, --help   help for issue-keypair
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
