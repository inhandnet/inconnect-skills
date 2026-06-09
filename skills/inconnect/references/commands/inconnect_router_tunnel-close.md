## inconnect router tunnel-close

Close an ngrok tunnel opened by `router web` or `router ssh`

### Synopsis

Explicitly close an ngrok tunnel by its tunnel id (uuid), instead of
waiting for the device-side idle timeout to reclaim it. The uuid is printed
by the "router web" and "router ssh" commands when the tunnel is opened.

```
inconnect router tunnel-close <uuid> [flags]
```

### Options

```
  -h, --help   help for tunnel-close
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
