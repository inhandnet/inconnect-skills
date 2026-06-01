## ics alert rule create

Create an alert rule

```
ics alert rule create [flags]
```

### Options

```
      --alert-type string         Alert type: vpn_connected, vpn_disconnected (required)
  -h, --help                      help for create
      --notify-channels strings   Notification channels (email, sms)
      --notify-users strings      User IDs to notify
      --retention int             Retention period in seconds
      --router-ids strings        Router IDs (for rule-type=router)
      --rule-type string          Rule type (all or router) (default "all")
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
