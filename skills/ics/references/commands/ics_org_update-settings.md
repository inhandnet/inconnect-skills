## ics org update-settings

Update organization settings

```
ics org update-settings <org-id> [flags]
```

### Options

```
      --data-threshold int            Data usage threshold in bytes for notification
      --diff-ip-pool                  Separate account and device IP pools
  -h, --help                          help for update-settings
      --notification-emails strings   Notification emails (max 5)
      --real-ip-enabled               Enable real IP for routers
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
