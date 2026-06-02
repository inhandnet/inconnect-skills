## inconnect router device-config set

Push a full device config YOU supply to a device

### Synopsis

Push a full device configuration that you provide (via --content or
--content-file) to the device and apply it. Requires the device to be online.

You supply the entire config content here. To push only the platform-rendered
VPN config (certs/CA/firewall) without supplying content, use
"router config-send" instead.

```
inconnect router device-config set <device-id> [flags]
```

### Options

```
      --content string        Config content string
      --content-file string   Read config content from file
      --desc string           Config description
  -h, --help                  help for set
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
