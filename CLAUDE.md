# 开发约定

## 命令参考文档

`skills/ics/references/commands/` 目录由 `ics-cli` 仓库的 `make docs` (cmd/docgen) 自动生成，**请勿手动编辑**。

`ics-cli` 每次打 tag 发版时，其 release workflow 会自动重新生成这些文档并推送到本仓库（见 ics-cli 的 `.github/workflows/release.yml`）。因此命令明细与 CLI 版本始终保持联动。

如需手动更新（例如本地验证）：

1. 在 `ics-cli` 仓库执行 `make docs DOCS_DIR=<本仓库>/skills/ics/references/commands`
2. 提交生成的 markdown 文件

## 发版流程

1. 更新 `.claude-plugin/plugin.json` 中的 `version`
2. 更新 `CHANGELOG.md`
3. 提交并打 tag（格式 `v0.x.0`）
