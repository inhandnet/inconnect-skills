## inconnect router web

Open device web management UI via ngrok tunnel

```
inconnect router web <id> [flags]
```

### Options

```
  -h, --help            help for web
      --no-browser      Print URL only, don't open browser
      --port int        Device-side web port to expose (default 80)
      --server string   Ngrok server address (default: auto-detected from the active context's host)
      --timeout int     Task timeout in seconds (default 60)
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
