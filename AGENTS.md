# Agent Instructions for this Zotero plugin template

These rules apply to work in this repository and to every plugin seeded from it.
The global `AGENTS.md` rule "Windows command-line safety" also applies and must
not be weakened here.

## Windows command-line safety

- **Always run terminal commands in Git Bash, never PowerShell.** The terminal
  tool may default to PowerShell; never accept it. Wrap commands as
  `& "C:\Program Files\Git\bin\bash.exe" -lc "<command>"` or set the tool shell
  to Git Bash. Never use bare `bash` on Windows (it may resolve to WSL).
- **Resolve a POSIX shell in order:** Git Bash
  (`C:\Program Files\Git\bin\bash.exe`, then
  `C:\Program Files\Git\usr\bin\bash.exe`), MSYS2
  (`C:\tools\msys64\usr\bin\bash.exe`), Cygwin, then WSL only when
  `wsl.exe -l -q` lists a distribution. Probe each with `-lc 'echo ok'`.
  If you use a fallback, say so once. If none works, stop and ask the user to
  install Git for Windows; do not run the command in PowerShell.
- **Never use PowerShell-only tokens:** `Get-ChildItem`, `Get-Content`,
  `Set-Content`, `Add-Content`, `Out-File`, `Remove-Item`, `Test-Path`,
  `New-Item`, `Copy-Item`, `Move-Item`, `Select-String`, `Select-Object`,
  `Where-Object`, `ForEach-Object`, `Write-Output`, `Write-Host`,
  `Start-Process`, `Invoke-*`, `$env:`, `$LASTEXITCODE`, `if ($?)`, backticks
  as escapes, and `.ps1` scripts. Use `ls`, `cat`, `printf`, `grep`, `sed`,
  `awk`, `find`, `test`, `rm`, `$?`, and `&&`/`||` instead.
- **Use Node.js scripts or the agent's file tools for edits.** Do not add
  PowerShell scripts, tasks, or documentation for agent workflows; prefer npm
  scripts and Bash.

## Build and validation

- Use the repository's npm scripts: `npm run build`, `npm run lint:check`, and
  `npm run test`. They are shell-agnostic and must be run from Git Bash on
  Windows.
- Write commit messages with a file or a Bash heredoc and pass them with
  `git commit -F <file>`; never use PowerShell redirection.