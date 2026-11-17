# Key Man Out vault skill

Use the `kmo` CLI to save production runbooks and handle encrypted secrets through files, stdin, or consuming programs. Claude asks you to sign in and unlock in your own terminal. The plugin installs no MCP server, hooks, permissions, or CLI binary.

Install from the public marketplace:

```bash
claude plugin marketplace add drgnstn/keymanout-claude
claude plugin install keymanout@keymanout
```

Start a new Claude Code session and run `/keymanout:vault`. Install kmo from your vault's `/download` page first. Native credential-handling commands require kmo 0.5.0; fallback examples support 0.4.0.

The [vault skill](skills/vault/SKILL.md) provides handling guidance, not isolation against a shell-capable agent. Never share unlock credentials in chat. Consumer output is not redacted. Use your own account and follow successor access approvals.

See the [marketplace README](https://github.com/drgnstn/keymanout-claude#readme) for usage, updates, migration from the local ZIP, and development.
