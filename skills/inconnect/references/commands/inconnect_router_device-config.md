## inconnect router device-config

Manage the full device config stored on the platform

### Synopsis

Get or push the full device configuration tracked by the platform.

Related commands that are easy to confuse:
  - "router running-config" — the config currently LIVE on the device (read).
  - "router config-send"     — push the platform-rendered VPN-only config.

### Options

```
  -h, --help   help for device-config
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
