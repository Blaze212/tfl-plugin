# tfl

The Fractional Life — workspace bootstrap + methodology skills for TFL Beta.

## What this plugin does

Installing this plugin gives a member the workspace root, `about/`, `templates/`, and
`outputs/` scaffold (all created under a named `the-fractional-life/` root — see the
workspace-root ADR below), plus:

- `tfl-setup` — first-run setup. Creates the scaffold, installs the 5 bundled templates
  (`templates/`) word-for-word, interviews the member one question at a time, and fills
  their `about/` profile files. Personalizes `START-HERE.md`. Safe to rerun: it fills gaps
  without clobbering populated files.
- `tfl-record-decisions` — keeps a local log at `about/decisions.md` of what the member has
  already decided (corrected facts, recipient choice, voice preferences, things they
  rejected) current with targeted edits — updating an existing entry in place and re-dating
  it when a decision changes, rather than blindly appending — so hosted skills and the
  workflow never make them repeat themselves.
- `tfl-build-value-add` — a **pointer skill** for the hosted workflow (see below).

## Layout

```text
plugins/tfl/
  .claude-plugin/plugin.json                    # plugin manifest
  skills/tfl-setup/SKILL.md                     # first-run setup skill (verbatim)
  skills/tfl-record-decisions/SKILL.md           # local decisions log (verbatim from source)
  skills/tfl-build-value-add/SKILL.md            # pointer skill -> hosted tfl_build_value_add
  templates/                                     # the bundled templates (verbatim), incl. about-templates/
  .mcp.json                                      # TFL MCP connector, wired to the production endpoint
  .mcp.json.example                              # template showing the connector shape
```

## Connecting to the hosted TFL methodology tools

The hosted methodology tools and the hosted workflow (`tfl_research_company`,
`tfl_identify_prospect_challenges`, `tfl_write_value_add`, `tfl_identify_decision_makers`,
`tfl_format_value_add`, `tfl_write_message`, `tfl_build_value_add`) are served over MCP. The
plugin ships a ready-to-use `.mcp.json` pointing at the production connector
(`https://ktazhzplyhpqayjaghur.supabase.co/functions/v1/tfl-mcp/mcp`), so installing the
plugin connects the tools automatically. The server uses OAuth — clients authorize on first
use. `.mcp.json.example` documents the config shape if you need to point at a different
endpoint.

## Pointer-skill-per-workflow convention

Every hosted **workflow** (as opposed to a single methodology skill) gets a matching
plugin **pointer skill** under `skills/<workflow-name>/SKILL.md`. The pointer skill carries
no methodology of its own — its only job is to give the member slash completion (e.g.
`/tfl:tfl-build-value-add`) and tell Claude to call the hosted tool by name. The hosted
tool's server-side prompt remains the single source of truth for the workflow's process; the pointer skill must never
duplicate or paraphrase it. `tfl-build-value-add` is the first instance of this convention;
apply it to every future hosted workflow.

## Versioning

`.claude-plugin/plugin.json` `version` is the single source of truth for the packaged release
artifact name (`tfl-plugin-v<version>.zip`, built by CI). Bump it to publish a new release.
