## ics router exec

Run a shell command on a router remotely

### Synopsis

Run a shell command on a router remotely and print its output.

Examples:
  ics router exec <id> show log
  ics router exec <id> "ifconfig eth0"

```
ics router exec <id> <command>... [flags]
```

### Options

```
  -h, --help          help for exec
      --timeout int   Command timeout in seconds (default 30)
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
