## inconnect user update

Update a VPN user account

### Synopsis

Update a VPN user account.

<id> is the VPN user ID (the 'id' field from 'user list', not 'uid').

```
inconnect user update <id> [flags]
```

### Options

```
      --expire-at int    Expiration timestamp (epoch millis)
  -h, --help             help for update
      --lock             Lock or unlock the user
      --name string      User name
      --role-id string   Role ID
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
