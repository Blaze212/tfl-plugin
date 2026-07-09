# tfl-plugin

Public distribution point for the **TFL** Claude Code plugin — _The Fractional Lever_
workspace bootstrap + methodology skills for TFL Beta.

This repository is a **mirror**. Its contents are generated automatically from CM Career
Systems' private source repository on each tagged release. Do not open PRs here — changes
made directly to this repo will be overwritten on the next release.

## Install

In Claude Code:

```
/plugin marketplace add Blaze212/tfl-plugin
/plugin install tfl@tfl
```

To get new versions automatically, enable auto-update for the marketplace once
(`/plugin` → **Marketplaces** → select **tfl** → **Enable auto-update**). Otherwise pull
updates on demand with:

```
/plugin marketplace update tfl
```

## What's here

- `.claude-plugin/marketplace.json` — the marketplace manifest.
- `plugins/tfl/` — the plugin bundle (skills, templates, and the hosted-tools MCP
  connector). See [`plugins/tfl/README.md`](plugins/tfl/README.md) for what the plugin does.

## License

© CM Career Systems. All rights reserved. This content is published for distribution to
TFL Beta members and is not licensed for redistribution or reuse.
