# tmux-claude

Manage tmux sessions paired with [Claude Code](https://claude.ai/claude-code) sessions.

## Features

- Lists existing sessions from both tmux and `~/.claude/sessions/*.json`, de-duplicated
- Resumes Claude Code sessions by ID when re-opening a known session
- Creates new tmux + Claude Code sessions with a given name
- Falls back to the working directory basename for unnamed Claude sessions
- Flags each session with `T` (tmux active) and/or `C` (Claude session on disk)

## Install

Copy or symlink `tcs` (or `tmux-claude`) somewhere on your `$PATH`:

```sh
cp tcs /usr/local/bin/
# or
ln -s "$PWD/tcs" /usr/local/bin/tcs
```

## Usage

```
tcs                # interactive session picker
tcs <name>         # attach or create a session with that name
```

### Interactive mode

```
Sessions:

  1) [T ] work
  2) [TC] my-project
  3) [ C] old-session

  T = tmux session active, C = claude session exists

Pick a number, or type a new session name:
```

Picking an existing session attaches to it (tmux) or resumes it (Claude Code).
Typing a new name creates a fresh tmux session with `claude -n <name>` in the first window.

## Dependencies

- `sh` (POSIX shell)
- `tmux`
- `claude` (Claude Code CLI)
- `grep`, `sed` (standard utilities)

## License

MIT
