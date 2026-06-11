## inconnect router signal

Get a device's cellular signal time series (strength + quality)

### Synopsis

Get this device's cellular (modem) signal time series from site, mirroring
the web UI which queries two endpoints together:

  strength  GET /api/devices/{id}/signal          -> [time, rssi] / asu
  quality   GET /api/devices/{id}/signal-quality   -> asu, rssi, rscp, rsrp,
            rsrq, sinr, ssRsrp, ssRsrq, ssSinr, ecio, pci, cid

Output is a JSON object {"strength":..., "quality":...}.
The backend defaults to the last 7 days when --after/--before are omitted.
Use --fields to restrict the quality metrics (comma-separated).

```
inconnect router signal <id> [flags]
```

### Options

```
      --after string    Start time, e.g. 2026-06-01 (default 7 days ago)
      --before string   End time, e.g. 2026-06-02 (default now)
      --fields string   Comma-separated quality metrics to return (default all)
  -h, --help            help for signal
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
