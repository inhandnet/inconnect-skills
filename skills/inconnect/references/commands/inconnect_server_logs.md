## inconnect server logs

Stream the org's OpenVPN server Pod logs (current Pod lifecycle only)

### Synopsis

Read the OpenVPN server Pod logs in real time (not persisted).

Only logs from the current Pod lifecycle are available; a Pod restart loses
previous output. Logs may contain client real IP, so this requires admin.

```
inconnect server logs <server-id> [flags]
```

### Options

```
      --format string   Output format: text (raw) or json (line-wrapped) (default "text")
  -h, --help            help for logs
      --since string    Only logs within this window (e.g. 10m, 1h)
      --tail int        Return the last N lines (max 2000) (default 200)
```

### Options inherited from parent commands

```
      --context string   Config context to use
      --debug            Enable debug output
      --jq string        Filter JSON output using a jq expression
      --oid string       Organization ID
  -o, --output string    Output format: json, table, yaml (default: table for TTY, json otherwise)
      --show-secrets     Reveal private keys in output (redacted by default)
      --verbose int      API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
