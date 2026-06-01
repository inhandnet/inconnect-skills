## ics org export

Export organizations to XLSX file

```
ics org export [flags]
```

### Options

```
      --creator string   Filter by creator
      --email string     Filter by email
      --file string      Output file path (default: stdout)
  -h, --help             help for export
      --language int     Export language (1=English, 2=Chinese) (default 2)
      --name string      Filter by name
      --status string    Filter by status
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
