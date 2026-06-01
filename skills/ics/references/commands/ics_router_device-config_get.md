## ics router device-config get

Get the config the platform has STORED for a device

### Synopsis

Get the device configuration stored on the platform (the platform's copy,
with a version number) — not necessarily what the device is running right now.

To fetch the config currently LIVE on the device, use "router running-config".

```
ics router device-config get <device-id> [flags]
```

### Options

```
  -h, --help   help for get
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
