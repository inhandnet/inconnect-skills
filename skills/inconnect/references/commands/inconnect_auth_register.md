## inconnect auth register

Register a new organization account

```
inconnect auth register [flags]
```

### Examples

```
  # Register on China region (default)
  inconnect auth register --email user@example.com --name "My Org" --password "P@ssw0rd"

  # Register on dev environment
  inconnect auth register --host dev --email user@example.com --name "My Org" --password "P@ssw0rd"
```

### Options

```
      --country string    Country or region
      --deploy            Auto-deploy VPN server after registration (default true)
      --email string      Email address (required)
  -h, --help              help for register
      --host string       Platform region: "cn", "us", "eu", "dev", "beta", or a custom domain (default "cn")
      --industry string   Industry
      --name string       Organization name (required)
      --password string   Login password (required)
      --subnet string     VPN subnet CIDR (default "10.16.0.0/12")
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
