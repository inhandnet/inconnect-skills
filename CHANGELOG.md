# Changelog

## v0.2.0

### New Features

- **Diagnostics commands** integrated into the troubleshooting flow, matching
  inconnect-cli's new commands: `connection-log list` (VPN session logs),
  `vpn-event list` (VPN auth/connection events incl. `auth_failed` reasons),
  `router connection-events` (device MQTT online/offline with disconnect
  reasons), `server logs` (OpenVPN server Pod logs), and `router diagnose`
  (one-shot multi-source aggregation)
- **Reworked `references/diagnostics.md`**: explains the management-channel
  (MQTT) vs VPN-tunnel two-layer model, leads with `router diagnose`, adds a
  layered step-by-step flow and a symptom quick-reference table
- **SKILL.md**: cheat sheet covers the new commands; reference-loading trigger
  table extended with VPN auth-failure / session-log / server-log keywords
- **Command references**: regenerated to include the 7 new command docs

## v0.1.0

### New Features

- **Initial release**: Skills for managing the InConnect (InVPN) platform via the `inconnect` CLI
- **Persona "IC 管家"**: An InConnect secure remote-connectivity assistant covering VPN networks, servers, routers, users, endpoints, data usage, alerts, firmware, DRC templates, billing, and system administration
- **Command references**: Auto-generated per-subcommand docs under `references/commands/`, kept in sync with `inconnect-cli` releases
- **Topic guides**: Reference guides for router diagnostics, signal analysis, the router config-source distinction, VPN networks, server provisioning, data-usage analysis, and firmware upgrades
