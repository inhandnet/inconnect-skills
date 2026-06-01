## ics router traffic-day

Get a device's per-day data traffic for a month

### Synopsis

Get this device's daily data traffic (one entry per day) for a month.

This is the device-level traffic tracked by site. For organization/router/account
VPN data usage (a different service), use the top-level "data-usage" commands.

```
ics router traffic-day <id> [flags]
```

### Options

```
  -h, --help           help for traffic-day
      --month string   Month, YYYY-MM or YYYYMM (default current month)
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
