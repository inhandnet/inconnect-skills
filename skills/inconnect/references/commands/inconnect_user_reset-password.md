## inconnect user reset-password

Reset a user's password (NOT usable by admins — see below)

### Synopsis

Reset a user's password.

<uid> is the account ID (the 'uid' field from 'user list', not 'id').

Note: the backend endpoint expects a verification 'code' from the self-service
"forgot password" email flow, which this command does not supply. As a result it
currently cannot perform a standalone admin-initiated reset.

```
inconnect user reset-password <uid> [flags]
```

### Options

```
  -h, --help           help for reset-password
      --language int   Notification language (1=English, 2=Chinese) (default 1)
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
