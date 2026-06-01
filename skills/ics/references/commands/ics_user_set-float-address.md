## ics user set-float-address

Enable or disable floating IP for a user

### Synopsis

Enable or disable floating IP for a user.

<id> is the VPN user ID (the 'id' field from 'user list', not 'uid').

```
ics user set-float-address <id> [flags]
```

### Options

```
      --enable   Enable or disable float address (default true)
  -h, --help     help for set-float-address
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
