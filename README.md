Agent skills for managing InHand Networks **InConnect (InVPN)** — the secure remote-connectivity manager for industrial IoT routers and gateways — via the `inconnect` CLI.

These skills follow the [Agent Skills specification](https://agentskills.io/specification) so they can be used by any skills-compatible agent, including Claude Code and Codex CLI.

## What can it do?

Once installed, talk to your AI agent in natural language to manage your InConnect platform — no need to memorize CLI commands.

- **VPN networks** — create and manage networks, members, routers, accounts, endpoints, centers
- **VPN servers** — provision/deploy OpenVPN servers, issue key pairs, stop/recover, send commands
- **Routers** — lifecycle, remote exec/reboot/kick, web management, live vs stored config, telemetry
- **VPN users & endpoints** — create/lock/unlock users, issue key pairs, bind MACs, manage endpoints
- **Data usage** — per-account and per-router VPN usage, daily/monthly, exports
- **Alerts** — view alerts, acknowledge, manage alert rules
- **Config templates** — DRC templates for batch device configuration
- **Firmware** — single/batch OTA upgrades, track job progress
- **Tasks** — list, cancel, restart platform tasks
- **Billing** — orders, receipts, invoices, seller settings
- **System & orgs** — organizations, settings, banners, audit logs, registration logs, service info
- **Identity** — multi-context/multi-account switching, organization switching, impersonation

## Prerequisites

- An InConnect (InVPN) account

> [!NOTE]
> The [`inconnect` CLI](https://github.com/inhandnet/inconnect-cli) is required but you don't need to install it beforehand — the skill will guide Claude through the CLI installation and login automatically on first use. You can also [install it manually](https://github.com/inhandnet/inconnect-cli) if you prefer.

## Installation

### Claude Code Plugin

Works on all Claude Code platforms — CLI, Desktop App, Web ([claude.ai/code](https://claude.ai/code)), and IDE extensions (VS Code, JetBrains).

1. **Add the marketplace** (only needed once):

   ```
   /plugin marketplace add inhandnet/inconnect-skills
   ```

2. **Install the plugin**:

   ```
   /plugin install inconnect@inconnect-skills
   ```

3. **Activate** — start a new session for the plugin to take effect:
   - **CLI**: exit and re-run `claude`
   - **Desktop App / Web**: open a new conversation
   - **IDE extensions**: restart the Claude Code panel

4. **Verify** — the plugin is loaded when you see `inconnect` listed in `/plugin > Installed`.

> [!TIP]
> **Desktop App**: click the **+** button next to the prompt box → **Plugins** → **Add plugin** to browse and install from the plugin manager UI.

> [!TIP]
> **Interactive browser (CLI / IDE)**: run `/plugin`, go to the **Discover** tab, find **inconnect**, and select your preferred installation scope (User / Project / Local).

> [!TIP]
> **Terminal commands** (outside the REPL):
> ```bash
> claude plugin marketplace add inhandnet/inconnect-skills
> claude plugin install inconnect@inconnect-skills
> ```
> The plugin will be active on the next Claude Code session.

#### Install for your team

To share the plugin with all project collaborators, install with **project scope**:

In the REPL, run `/plugin`, go to **Discover**, select **inconnect**, and choose **Project** scope. This adds the marketplace and plugin to `.claude/settings.json`, so teammates get it automatically when they trust the project folder.

#### Update

```
/plugin update inconnect@inconnect-skills
```

#### Uninstall

```
/plugin uninstall inconnect@inconnect-skills
```

### Codex CLI

Copy the `skills/inconnect` directory into one of the [Codex skills directories](https://developers.openai.com/codex/skills):

```bash
# User-level (available in all projects)
cp -r skills/inconnect ~/.agents/skills/

# Or project-level (shared with team via git)
cp -r skills/inconnect .agents/skills/
```

### Load without installing (session only)

If you have a local clone of this repo, you can load it into Claude Code for a single session:

```bash
claude --plugin-dir /path/to/inconnect-skills
```

## Usage

The skill supports both English and Chinese. In most cases, just describe what you need — Claude automatically activates the skill when it detects requests related to:

- VPN network and server management (create, deploy, recover)
- Router operations (status, remote exec, reboot, web management, config)
- VPN user and endpoint management
- Data usage, alerts, firmware upgrades, DRC templates
- Billing, organizations, audit logs, identity switching

```
You:    列出 laoli 组织所有离线的路由器
Claude: [自动加载 inconnect 技能，列出离线路由器]

You:    部署一台新的 VPN server 并下发到 K8s
Claude: [先确认影响范围，再 server create --deploy]

You:    查这台路由器的蜂窝信号质量
Claude: [查询信号历史并分析 RSSI/RSRP/SINR]
```

> [!TIP]
> **How to tell the skill is active:**
> - **CLI / IDE**: look for the loading indicator in the output:
>   ```
>   ⏺ Skill(inconnect:inconnect)
>     ⎿  Successfully loaded skill
>   ```
> - **Desktop App / Web**: the skill name appears highlighted in the prompt area when invoked, or Claude starts running `inconnect` commands in its response.

You can also invoke it explicitly — type `/` in the prompt box to browse available skills, or type `/inconnect` directly:

```
/inconnect List all offline routers
/inconnect Check cellular signal quality for this router
/inconnect Deploy a new VPN server to Kubernetes
/inconnect Show this month's VPN data usage by account
/inconnect Schedule a firmware upgrade for all IR900 routers
```

## Troubleshooting

### "inconnect: command not found"

The `inconnect` CLI is not installed. Follow the installation instructions at [inconnect-cli](https://github.com/inhandnet/inconnect-cli).

### "unauthorized" or "401" errors

Your CLI session has expired. Run `inconnect auth login` to re-authenticate.

### Plugin skills not appearing after installation

1. Run `/reload-plugins` to reload all plugins
2. Check `/plugin > Errors` for any loading errors
3. If the issue persists, try `claude plugin uninstall inconnect@inconnect-skills` and reinstall

## Skills

| Skill | Description |
|-------|-------------|
| [inconnect](skills/inconnect) | Manage the InConnect (InVPN) platform — VPN networks, servers, routers, users, endpoints, data usage, alerts, DRC templates, firmware, billing, and system administration |
