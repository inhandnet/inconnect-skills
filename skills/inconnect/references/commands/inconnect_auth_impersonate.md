## inconnect auth impersonate

Impersonate another user (requires ROOT privilege)

```
inconnect auth impersonate [flags]
```

### Examples

```
  # Impersonate by org ID (auto-resolves org admin)
  inconnect auth impersonate --org 5e0956c46aa6d10001e931e6

  # Impersonate a specific user in an org
  inconnect auth impersonate --org <oid> --user <uid>

  # Stop impersonation and restore admin identity
  inconnect auth impersonate --stop
```

### Options

```
  -h, --help          help for impersonate
      --org string    Organization ID
      --stop          Stop impersonation and restore admin identity
      --user string   User ID to impersonate
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
