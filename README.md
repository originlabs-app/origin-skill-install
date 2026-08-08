# OriginSkill Connector

OriginSkill is a governed skill runtime for French business tasks: accounting
and tax, business law, labor law, professional training, and public
procurement. It answers through the Model Context Protocol (MCP) with
structured, source-cited responses instead of open-ended generation.

This repository is the OriginSkill connector. It installs and manages the
local bridge between an MCP-capable assistant, such as Codex, Claude Code, or
Cursor, and the OriginSkill runtime. It contains no protected business logic
and no secrets: only install tooling and client configuration.

## Why OriginSkill

Every executable answer follows the same five-block contract: `facts`,
`rules`, `values`, `sources`, `next_steps`. Two rules keep it honest:

- If a fact is missing, OriginSkill asks exactly one question about it and
  never asks again once you have answered.
- If a request falls outside its scope or jurisdiction, OriginSkill says so
  instead of improvising an answer.

OriginSkill never generates or serves files. Your assistant keeps its own
reasoning and tools; OriginSkill adds a controlled source of business
expertise on top of them.

## Quick start

Confirm the connector resolves and reports its version:

```sh
npx --yes --package="https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz" orizon --version
```

This should print `0.1.11`. Then install the MCP configuration for your
client:

```sh
npx --yes --package=https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz orizon install codex --yes --package-spec https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz
npx --yes --package=https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz orizon install claude-code --yes --package-spec https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz
npx --yes --package=https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz orizon install cursor --yes --package-spec https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz
```

The version above is current at the time of writing. [originskill.ai/installer](https://originskill.ai/installer)
always shows the current version and a ready-to-copy command, so treat that
page as the reference and this README as a companion.

On first run, the CLI asks for your OriginSkill access token in a masked
prompt if none is saved yet. It then writes the client configuration, backs
up any file it replaces, and reminds you to restart or reload your AI
client. Verify the result with:

```sh
orizon status
orizon mcp-check --json
```

## Requirements

- Node.js 20 or later.
- An active OriginSkill license.
- Network access to `https://api.originskill.ai/mcp`, the durable MCP
  endpoint used by every client configuration in this repository.

## How it works

- `npx` fetches the CLI from an immutable, versioned URL on originskill.ai.
  Each version is published once at its own path and never overwritten.
- Every download is served with an `x-orizon-cli-sha256` response header
  carrying the SHA-256 fingerprint of that exact file, so the artifact can be
  checked before use.
- The CLI writes client configuration that starts a small local proxy,
  `orizon-mcp-proxy`, pointed at the durable MCP endpoint
  `https://api.originskill.ai/mcp`. Your access token stays in
  `~/.orizon/token` with owner-only file permissions; it is never written
  into a client configuration file.
- Before changing an existing configuration file, the CLI keeps a full copy
  next to it (`.bak`, then `.bak.1`, `.bak.2`, and so on) and prints exactly
  how to restore it.

## Get your token

If you have not signed in yet, start an interactive, masked login:

```sh
npx --yes --package=https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz orizon login
```

After a purchase, you can also activate your license with your order
reference and the email used for the order:

```sh
npx --yes --package=https://originskill.ai/installer/cli/v0.1.11/orizon-cli-0.1.11.tgz orizon login --order <order-id> --email <email>
```

## Supported clients

This repository ships ready-to-use configuration for Codex (`clients/codex.toml`),
Claude Code (`clients/claude-code.json`), and Cursor (`clients/cursor.json`).
Other MCP-capable clients are supported through the same install command;
Claude Desktop users can instead download the `.mcpb` extension from their
OriginSkill account and skip the CLI entirely.

## Troubleshooting

- **`No OriginSkill access token found`**: run
  `orizon login --order <order-id> --email <email>`, or set
  `ORIZON_MCP_TOKEN` for a non-interactive install.
- **`Could not reach OriginSkill runtime`**: check your network connection
  and the `ORIZON_API_URL` / `ORIZON_MCP_URL` values if you overrode them,
  then run `orizon status`.
- **`The target MCP config file is not valid JSON`**: fix the file or move
  it aside, then rerun the install. The CLI will not overwrite a file it
  cannot parse.

Any other failure prints a short message. Set `ORIZON_DEBUG=1` and rerun the
same command to see the full technical detail behind it.

## License

Proprietary. See [LICENSE](./LICENSE). Full skill scope is listed in
[SKILL.md](./SKILL.md).

## Links

- [originskill.ai](https://originskill.ai)
- [originskill.ai/installer](https://originskill.ai/installer): current
  version and copy-paste install command.
