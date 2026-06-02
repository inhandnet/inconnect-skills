## inconnect firmware create

Create a firmware package

```
inconnect firmware create [flags]
```

### Options

```
      --desc string       Description
      --fid string        File ID from upload (required)
  -h, --help              help for create
      --job-timeout int   Job timeout in minutes (1-60)
      --model string      Device model (required)
      --name string       Firmware name (required)
      --version string    Firmware version (required)
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
