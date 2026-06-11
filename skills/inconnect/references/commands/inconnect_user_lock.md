## inconnect user lock

Lock a user account

### Synopsis

Lock a user account.

<uid> is the account ID (the 'uid' field from 'user list', not 'id').
By default an email notification is sent; pass --notice=false to suppress it.

```
inconnect user lock <uid> [flags]
```

### Options

```
  -h, --help           help for lock
      --language int   Notification language (1=English, 2=Chinese) (default 1)
      --notice         Send notification email (default true)
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
