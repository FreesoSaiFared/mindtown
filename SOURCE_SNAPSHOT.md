# Verified source snapshot C0005

This archive was produced from VM checkpoint:

```text
checkpoint: C0005
commit: 708a35889b8dd390000e1327f3eb058362d4bc5e
archive: releases/mindtown-source-c0005.tar.gz
SHA-256: a18838c966fa6fa60eb73ad0cf7c9db0395ba24b892ebbf23658c06521e37027
files: 43
```

It contains the application source, tests, recovery tools, action-named continuation files and project documentation. It excludes:

- `.git` and inverse-agent request/response history;
- `public/vendor/playcanvas.mjs`, because the complete pinned runtime is retained in the Google Drive recovery set;
- generated caches.

Extract it for inspection and native testing:

```bash
mkdir mindtown-source
cd mindtown-source
tar -xzf ../releases/mindtown-source-c0005.tar.gz
cat 00_AI_START_HERE__REPORT_STATE_AND_RUN_RESUME.md
./tools/test.sh
```

This is a source snapshot, not a resumable Git checkout. `resume-mindtown.sh` intentionally requires `.git` and therefore refuses to run here. The authoritative continuation path uses the original immutable full checkpoint plus `MINDTOWN_DELTA_FROM_FULL_C0005_708a35889b.zip` from the Drive folder **MindTown VM Handoffs**.
