## ics billing update-invoice

Update invoice status for an order

```
ics billing update-invoice <order-id> [flags]
```

### Options

```
      --action string                 Action: invoice or revert (required)
      --channel-order-number string   Channel order number
  -h, --help                          help for update-invoice
      --invoice-number string         Invoice number
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
