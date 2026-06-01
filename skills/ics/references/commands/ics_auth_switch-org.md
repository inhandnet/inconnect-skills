## ics auth switch-org

Switch to a different organization

```
ics auth switch-org <org-id> [flags]
```

### Examples

```
  # List your organizations first
  ics auth orgs

  # Switch to another org
  ics auth switch-org 5e0956c46aa6d10001e931e6
```

### Options

```
  -h, --help   help for switch-org
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
