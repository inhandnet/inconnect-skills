## inconnect router list

List VPN routers

### Synopsis

List VPN routers.

Each router reports two INDEPENDENT status fields — don't confuse them:

  online    (1/0)         Device-management channel (MQTT): whether the
                          platform can reach the device. Config push, remote
                          control, ngrok and reboot all depend on this.
  connected (true/false)  VPN tunnel (OpenVPN): whether the device has an
                          active VPN tunnel to its server and can carry VPN
                          traffic.

A device is commonly online=1 while connected=false (manageable, but no VPN
tunnel — e.g. its server isn't running). Filter with --online / --connected.

```
inconnect router list [flags]
```

### Options

```
      --connected string   Filter by connection status (true/false)
      --cursor int         Pagination cursor / offset
  -h, --help               help for list
      --limit int          Maximum number of records to return (default 20)
      --name string        Filter by name
      --online string      Filter by online status
      --query string       Search across name and serial number
      --rip string         Filter by real IP address
      --serial string      Filter by serial number
      --sort string        Sort order (e.g. createdAt,desc)
      --vip string         Filter by virtual IP
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
