## inconnect drc create

Create a config template

```
inconnect drc create [flags]
```

### Options

```
      --content string        Config content
      --content-file string   Read config content from file
      --content-type int      Content type (0=default)
      --desc string           Description
      --group-ids strings     Device group IDs
  -h, --help                  help for create
      --model string          Device model (required)
      --name string           Template name (required)
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
