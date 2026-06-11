## inconnect billing list-orders

List billing orders/transactions

```
inconnect billing list-orders [flags]
```

### Options

```
      --after string      Start time (e.g. 2024-01-01, 2024-01-01T00:00:00Z)
      --before string     End time (e.g. 2024-12-31, 2024-12-31T23:59:59Z)
      --cursor int        Pagination cursor / offset
      --email string      Filter by email
  -h, --help              help for list-orders
      --invoiced string   Filter by invoice status (true/false)
      --limit int         Maximum number of records to return (default 20)
      --number string     Filter by order number
      --sort string       Sort order (e.g. createdAt,desc)
      --status string     Transaction status (default: succeeded)
      --type string       Transaction type (default: payment)
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
