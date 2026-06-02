## inconnect router create

Create a VPN router

```
inconnect router create [flags]
```

### Options

```
      --custom-field strings   Custom field (key=value, can specify multiple)
  -h, --help                   help for create
      --lan-interface string   LAN interface
      --model string           Router model (e.g. IR900)
      --model-id string        Model ID
      --name string            Router name
      --network-id string      Network ID to assign
      --serial string          Device serial number (required, 15 chars)
      --subnet string          Router subnet
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
