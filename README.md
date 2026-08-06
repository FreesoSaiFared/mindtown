# MindTown

MindTown is a PlayCanvas village whose inhabitants can use separate ChatGPT or Gemini browser conversations as their minds.

## Current verified state

VM checkpoint **C0008**, deployment build **C0009**, implements:

- an isometric voxel town and workbench;
- Mira and Oren as separately selectable inhabitants;
- a plain-language personality descriptor for each character;
- **hand-of-God nudges** rather than direct avatar movement;
- character protest, resistance, reinterpretation and autonomous acceptance;
- calm-awareness packets that deepen during stillness;
- initiative, stillness and meditation tendencies;
- strict `[[MINDTOWN ...]]` command envelopes plus legacy move-command parsing;
- a Manifest V3 extension that maps characters to ChatGPT/Gemini tabs;
- awareness delivery, provider response monitoring and decision return routing;
- deterministic recording and replay;
- ChromeOS-oriented WebGL context and resize diagnostics;
- one-command Cloudflare deployment using an existing Wrangler login;
- full-plus-delta VM recovery through Google Drive.

## Agency rule

Clicking the town does not directly move a character. It creates external pressure:

> Something seems to be urging you north-east. This is not an order.

The character may refuse, protest, wait, meditate, reinterpret the suggestion, or later decide to go there for a reason that fits its own personality.

## Verified tests

- 24 native tests passed.
- Chromium reached WebGL2.
- A dock-style viewport resize completed without context loss.
- The first nudge left Mira in place and produced an agency protest.
- A later awareness turn let Mira adopt the destination as her own decision.
- Clean-room restoration reached commit `ed89f851f03e50349ea47a3f8b80ca0db747d1d8` with a clean worktree and all tests passing.

## Deploy

The durable deployment artifacts are stored in the Google Drive folder **MindTown VM Handoffs**. Download:

```text
DEPLOY_MINDTOWN_C0009_FROM_DOWNLOADS.sh
```

Then run in Crostini, Debian or WSL2:

```bash
bash ~/Downloads/DEPLOY_MINDTOWN_C0009_FROM_DOWNLOADS.sh
```

The script uses an existing Wrangler OAuth login; it does not require `CLOUDFLARE_API_TOKEN`.

## Resume development

Inside a restored project:

```bash
cd /opt/dev/work/mindtown && ./resume-mindtown.sh
```

After a replacement VM, restore the immutable full checkpoint plus the newest cumulative delta from **MindTown VM Handoffs**. Google Drive remains the authoritative resumable source because it contains Git history and the pinned PlayCanvas runtime.

## Precise remaining boundary

The extension and local provider fixtures are implemented, but an authenticated live ChatGPT/Gemini turn has not yet been proven. The next test is one real mind tab: insert awareness, submit it, extract one strict decision, then bind Mira and Oren to two separate tabs and interleave their turns.
