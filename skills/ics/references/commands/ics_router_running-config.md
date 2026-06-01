## ics router running-config

Fetch the config currently LIVE on the device (decoded)

### Synopsis

Fetch the configuration currently running on the device right now (live,
server-side decoded). Requires the device to be online.

Related commands that are easy to confuse:
  - "router device-config get" — the platform's STORED copy (may differ from live).
  - "router config-send"        — push the platform-rendered VPN-only config.

```
ics router running-config <id> [flags]
```

### Options

```
  -h, --help          help for running-config
      --timeout int   Task timeout in seconds (default 60)
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
