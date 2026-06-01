## ics user create

Create a VPN user account

### Synopsis

Create a VPN user account.

Each VPN user has two IDs, both shown by 'user list':
  - id  : VPN user ID — used by update/set-float-address/bind-mac/issue-keypair
  - uid : account ID   — used by lock/unlock/delete/reset-password

Note: --role-id is required by the server. Look up role IDs via 'ics role list'.

```
ics user create [flags]
```

### Options

```
      --email string        User email (required)
      --expire-at int       Expiration timestamp (epoch millis)
      --external            External user
  -h, --help                help for create
      --language int        Notification language (1=English, 2=Chinese) (default 1)
      --lock                Create in locked state
      --name string         User name (required)
      --network-id string   Network ID to assign
      --org-id string       Organization ID
      --role-id string      Role ID (required; see 'ics role list')
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
