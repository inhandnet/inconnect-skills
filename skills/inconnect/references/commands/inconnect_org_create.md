## inconnect org create

Create an organization (admin)

```
inconnect org create [flags]
```

### Options

```
      --country string    Country or region
      --deploy            Auto-deploy VPN server after creation (default true)
      --email string      Admin email address (required)
  -h, --help              help for create
      --industry string   Industry
      --name string       Organization name (required)
      --password string   Initial login password (required)
      --subnet string     VPN subnet CIDR (default "10.16.0.0/12")
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
