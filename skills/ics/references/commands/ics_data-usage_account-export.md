## ics data-usage account-export

Export account data usage to Excel

```
ics data-usage account-export [flags]
```

### Options

```
      --date string    Date filter (YYYY-MM-DD)
      --file string    Output file path (default: stdout)
  -h, --help           help for account-export
      --id string      Account ID filter
      --language int   Export language (1=English, 2=Chinese) (default 2)
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
