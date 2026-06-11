## inconnect router get

Get a VPN router by ID

### Synopsis

Get a VPN router by ID.

The router reports two INDEPENDENT status fields — don't confuse them:

  online    (1/0)         Device-management channel (MQTT): whether the
                          platform can reach the device (config push, remote
                          control, ngrok and reboot all rely on it).
  connected (true/false)  VPN tunnel (OpenVPN): whether the device has an
                          active VPN tunnel to its server and can carry VPN
                          traffic.

online=1 with connected=false is common: the device is manageable but has no
VPN tunnel (e.g. its server isn't running).

```
inconnect router get <id> [flags]
```

### Options

```
  -h, --help   help for get
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
