# Submission Checklist

Use this list before opening the pull request.

## Required Items

- [x] Team folder: `submissions/the-randoms/`
- [x] Project readme: `submissions/the-randoms/README.md`
- [x] AI process doc: `submissions/the-randoms/HOW_WE_BUILT.md`
- [x] Source folder: `submissions/the-randoms/src/`
- [ ] Demo video: `submissions/the-randoms/demo.mp4` (replace placeholder with real recording)

## Documentation Accuracy Checks

- [x] Run commands use current paths under `submissions/the-randoms/src/`
- [x] Folder tree in README matches the actual structure
- [x] HOW_WE_BUILT includes model choices, prompt examples, and iteration/testing details

## Recommended Final Validation

1. Start backend from `src/simple-backend`.
2. Start frontend from `src/react-video-client-avatar`.
3. Run one full demo flow and record it.
4. Replace `demo.mp4` with the recorded file.
5. Re-open README and verify no machine-specific absolute paths remain.

## Hard Blockers Before PR

- `demo.mp4` must be non-empty and playable.
- README quickstart commands must work from repository root.

## Optional Command Checks

```bash
# Demo file should be larger than 0 bytes
stat -f "%z bytes  %N" submissions/the-randoms/demo.mp4

# No machine-specific absolute paths in markdown docs
rg -n "/Users/|C:\\\\" submissions/the-randoms --glob "**/*.md" -S
```
