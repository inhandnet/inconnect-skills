## inconnect server create

Create a VPN server

```
inconnect server create [flags]
```

### Options

```
      --address string         Server address
      --deploy                 Deploy server (provision K8s pod) after creation; default creates the DB record only
      --group string           Server group name (default: "default")
  -h, --help                   help for create
      --host string            Server host
      --ifconfig-pool string   Ifconfig pool
      --netmask string         Server netmask
      --node-port int          Kubernetes node port
      --org-id string          Organization ID (required)
      --port int               Server port
      --proto string           Protocol (tcp or udp)
      --service-type string    Kubernetes service type
      --subnet string          Server subnet (e.g. 10.8.0.0/16)
      --version string         Server version
```

### Options inherited from parent commands

```
  -c, --columns strings   Table columns to show (comma-separated dot-paths; prefix ! to exclude)
      --context string    Config context to use
      --debug             Enable debug output
      --jq string         Filter JSON output using a jq expression
      --oid string        Organization ID
  -o, --output string     Output format: json, table, yaml (default: table for TTY, json otherwise)
      --show-secrets      Reveal private keys in output (redacted by default)
      --verbose int       API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
