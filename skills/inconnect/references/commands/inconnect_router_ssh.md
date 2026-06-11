## inconnect router ssh

Print an SSH command to log into a device via ngrok

### Synopsis

Open a TCP ngrok tunnel to the device's SSH port and print a ready-to-use
ssh command. The ngrok server must have the embedded SSH reverse proxy
enabled; if it isn't, the tunnel URL won't carry a tunnel-id and this command
will fail.

```
inconnect router ssh <id> [flags]
```

### Options

```
  -h, --help            help for ssh
      --port int        Device-side SSH port (default 22)
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
