## inconnect router diagnose

Aggregate multi-source diagnostics for a router into one report

### Synopsis

Pull a router's diagnostics from several sources in one shot:

  - connectionLogs   VPN session logs (vpn-controller)
  - vpnEvents        VPN auth/connection events (vpn-controller)
  - connectionEvents device MQTT online/offline events (site)
  - registerEvents   device registration events (site)

Output is a single JSON object keyed by source. Individual sources that fail
are reported to stderr and left as empty arrays (best-effort).

```
inconnect router diagnose <router-id> [flags]
```

### Options

```
      --after string    Only records at/after this time (e.g. 2024-01-01T00:00:00Z)
      --before string   Only records before this time
  -h, --help            help for diagnose
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
