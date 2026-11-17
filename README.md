# Key Man Out for Claude Code

Use the `kmo` CLI with Claude Code to save production runbooks and secrets, or recover them as a Successor. The plugin teaches Claude to ask you to unlock in your terminal and pass secret values through files, stdin, or a consuming process's environment without printing them.

## Install

Install `kmo` from your vault's `/download` page first. Then run:

```bash
claude plugin marketplace add drgnstn/keymanout-claude
claude plugin install keymanout@keymanout
```

Start a new Claude Code session and run `/keymanout:vault`, or ask Claude to use Key Man Out. The plugin installs no MCP server, hooks, permissions, or CLI binary. Its native credential-handling examples require kmo 0.5.0 or newer; file/stdin fallback examples support 0.4.0.

If you previously added the downloadable local marketplace, replace that registration first:

```bash
claude plugin marketplace remove keymanout
claude plugin marketplace add drgnstn/keymanout-claude
claude plugin install keymanout@keymanout
```

## Use

Example requests:

- “Document this production database setup in Key Man Out. The existing password is at `/secure/db-password`; upload it without reading or printing it.”
- “Use the recovery runbook in Key Man Out to plan this restore. Ask me to unlock when needed and pass credentials directly to the restore tools.”

Sign in and unlock yourself on the same machine, OS account, and CLI profile as Claude. Never send Claude your passphrase, private identity, CLI token, or `KMO_SESSION`. Your successor must use their own account and follow the vault's access approvals.

The [vault skill](plugins/keymanout/skills/vault/SKILL.md) contains the full workflow. It provides handling guidance, not access isolation: a shell-capable agent can still read local files or an unlocked vault, and a consuming program can print or copy credentials. Instructions and asset names are unencrypted metadata; keep credentials out of them.

## Update or uninstall

```bash
claude plugin marketplace update keymanout
claude plugin update keymanout@keymanout
```

Uninstall with `claude plugin uninstall keymanout@keymanout`. Remove the marketplace with `claude plugin marketplace remove keymanout`.

## Develop

Clone this repository and validate both manifests:

```bash
git clone https://github.com/drgnstn/keymanout-claude.git
cd keymanout-claude
claude plugin validate . --strict
claude plugin validate ./plugins/keymanout --strict
```

Load a checkout for one session with `claude --plugin-dir ./plugins/keymanout`. Keep the marketplace name and plugin name `keymanout` so the install ID remains `keymanout@keymanout`. Increase the plugin manifest's version when publishing changes so installed copies can update.
