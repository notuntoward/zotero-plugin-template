# Agent Instructions for this Zotero plugin template

## Task scope and validation

- Cache exact applicable instructions once per checkout/task; read referenced
  guides only for the area being changed. Restore only missing/changed sections
  after compaction. Do not recursively load the commons documentation hierarchy.
- Docs/instructions-only: inspect text/diff and any declared Markdown/render check;
  do not run application tests/builds/browser suites, install packages, rebuild
  artifacts or check other consumers. This qualifies completion gates below.
- Commit/push-only: reuse green checks and verified artifacts for unchanged source,
  dependencies/build inputs AND linked commons source. Validate previously unchecked
  pending code once; report reuse honestly, not as a freshly run check.
- Code changes: targeted tests during iteration, required final checks once after
  the last relevant edit. Reuse composite build steps; do not rerun included lint,
  types/tests/bundling. Verify that output, never rebuild just for a fresh timestamp.
- Batch independent reads/status probes. Keep branch/identity/message/hook and
  final remote-tip checks; do not repeat full exploration between Git steps.

## Shell and Git safety

Follow the global shell/Git rules when available. Otherwise detect and reuse Git
Bash on Windows; never use bare bash (may be WSL), PowerShell cmdlets/scripts,
redirection, backtick escapes or .ps1. Use native file tools/Node and quoted CLI
path arguments. Stop if no authorized working POSIX shell exists.
Keep existing Git identities, hooks/signing and line-ending policy; never add AI
attribution, force-push or rewrite history without authorization. Inspect the
literal message and use a quoted Bash heredoc with git commit -F, then clean up.
Use an imperative subject <=72 characters, blank line, one-line overview and
distinct material-change bullets, each on one physical line (no hard wrapping).

## Build and validation

Changed plugin source/build inputs require npm run build, npm run lint:check and
the relevant npm run test checks, once from the original checkout. Inspect script
composition first; do not rerun included type/build steps or reinstall unchanged
dependencies. Runtime package verification applies only when affected.
Markdown-only edits use the existing Prettier check for changed Markdown files,
not Zotero application builds/tests. A seeded plugin inherits these scoped rules.
