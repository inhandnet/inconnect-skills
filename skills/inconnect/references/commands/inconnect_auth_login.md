## inconnect auth login

Login via browser

```
inconnect auth login [flags]
```

### Examples

```
  # Login to China region (default)
  inconnect auth login

  # Login to dev environment
  inconnect auth login --host dev

  # Login to a custom domain
  inconnect auth login --host ics.example.com
```

### Options

```
      --context string     Context name to create/update (default "default")
  -h, --help               help for login
      --host string        Platform region: "cn", "us", "eu", "dev", "beta", or a custom domain (default "cn")
      --port int           Local callback server port (default 18920)
      --timeout duration   Timeout waiting for browser login (default 3m0s)
```

### Options inherited from parent commands

```
  -c, --columns strings   Table columns to show (comma-separated dot-paths; prefix ! to exclude)
      --debug             Enable debug output
      --jq string         Filter JSON output using a jq expression
      --oid string        Organization ID
  -o, --output string     Output format: json, table, yaml (default: table for TTY, json otherwise)
      --verbose int       API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
