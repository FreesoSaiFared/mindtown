# MindTown

MindTown is a PlayCanvas village whose inhabitants can use separate browser conversations as minds.

Verified checkpoint **C0005** currently includes:

- an isometric voxel town and local workbench;
- deterministic perception, speech and movement events;
- world reactions to speech and arrivals;
- bounded per-character social memory;
- record/replay with matching final state;
- native tests and Chromium/WebGL2 verification;
- one-command VM continuation and full-plus-delta recovery.

## Resume

Inside an existing restored project:

```bash
cd /opt/dev/work/mindtown && ./resume-mindtown.sh
```

After a replacement VM, retrieve the immutable full checkpoint and newest cumulative delta from the Google Drive folder **MindTown VM Handoffs**, restore them, then run the command above. The Drive recovery set is the authoritative resumable project because it includes Git history and the pinned PlayCanvas runtime.

## Source snapshot

The verified text-source snapshot is stored at:

```text
releases/mindtown-source-c0005.tar.gz
```

Extract it for source inspection or to run the native tests:

```bash
mkdir mindtown-source
cd mindtown-source
tar -xzf ../releases/mindtown-source-c0005.tar.gz
./tools/test.sh
```

The GitHub snapshot intentionally excludes `.git`, inverse-agent history, and the pinned built PlayCanvas runtime. It is not a substitute for the Drive full-plus-delta recovery set, and `resume-mindtown.sh` will correctly refuse to run in a source-only extraction.

## Current next step

Render Oren as a second inhabitant and run independent, interleaved deterministic turns for Mira and Oren, each with its own perception and memory, while preserving deterministic replay.
