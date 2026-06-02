## inconnect billing download-receipt

Download a payment receipt PDF

```
inconnect billing download-receipt <payment-id> [flags]
```

### Options

```
      --file string    Output file path (default: stdout)
  -h, --help           help for download-receipt
      --title string   Receipt title for filename (default "receipt")
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
