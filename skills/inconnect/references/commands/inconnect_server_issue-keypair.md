## inconnect server issue-keypair

Issue new key pair for server(s)

```
inconnect server issue-keypair <org-id> [flags]
```

### Options

```
      --deploy-at string   Scheduled deployment date (ISO 8601)
  -h, --help               help for issue-keypair
      --server-id string   Specific server ID (if omitted, issues for all servers)
```

### Options inherited from parent commands

```
      --context string   Config context to use
      --debug            Enable debug output
      --jq string        Filter JSON output using a jq expression
      --oid string       Organization ID
  -o, --output string    Output format: json, table, yaml (default: table for TTY, json otherwise)
      --show-secrets     Reveal private keys in output (redacted by default)
      --verbose int      API field verbosity for GET requests (1-100, higher = more fields; 0 to omit) (default 100)
```
