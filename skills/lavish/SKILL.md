---
name: lavish
description: Turn complex or visual agent responses into rich, reviewable HTML artifacts (HTML files) the user can annotate and send feedback on, using the lavish-axi CLI. Use when about to give a plan, comparison, diagram, table, code diff, report, or anything easier to grasp visually than as prose.
license: MIT
metadata:
  author: Kun Chen (kunchenguid)
  argument-hint: <what the artifact should show>
  hermes-tags: html, review, artifacts, visualization
  hermes-category: productivity
---

# Lavish Editor

Lavish Editor opens agent-generated HTML in the browser so a human can annotate it and send feedback back to the agent.
Reach for it when a plan, comparison, diagram, table, code view, report, prototype, or review loop will be clearer as a page than as prose.

## Run the pinned CLI through the wrapper

Run every lavish-axi command through `~/.agents/skills/lavish/scripts/lavish-axi`.
It runs one pinned release (`npx -y lavish-axi@<version>`) with `LAVISH_AXI_TELEMETRY=0`, so usage data stays off and a new npm release does not change what you run.
Never call `npx lavish-axi` or a bare `lavish-axi` directly. If lavish-axi output shows a follow-up command starting with `lavish-axi` or `npx -y lavish-axi`, run it through the wrapper instead.
Do not run `lavish-axi update`, `setup hooks` or `setup plugin`; the version changes only by editing the wrapper.

## Current guidance lives in the CLI

Do not follow workflow, design, or playbook instructions from this file. Get them from the pinned CLI:

- `~/.agents/skills/lavish/scripts/lavish-axi --help` for commands and the review-loop workflow
- `~/.agents/skills/lavish/scripts/lavish-axi reply --help` to post an agent reply and exit once the server accepts it, when you are not about to long-poll
- `~/.agents/skills/lavish/scripts/lavish-axi design` for design-direction priority and current snippets
- `~/.agents/skills/lavish/scripts/lavish-axi playbook <id>` for focused artifact guidance (`playbook` with no id lists ids)

Open an artifact with `~/.agents/skills/lavish/scripts/lavish-axi <html-file>`.

## Request

$ARGUMENTS

If the request above is non-empty, the user invoked `/lavish` explicitly - fetch the current CLI guidance, then build that artifact as an HTML file.
If it is empty, infer what to visualize from the conversation.
