# CLAUDE.md - Bluesky CLI Skill

## What This Is

A full-featured CLI for Bluesky (AT Protocol). Designed as an OpenClaw skill but works standalone.

## Structure

```
scripts/bsky.py    # Main CLI (Python, uses atproto library)
SKILL.md           # OpenClaw skill manifest
README.md          # User docs
CHANGELOG.md       # Version history
TESTING.md         # Test procedures
ROADMAP.md         # Future plans
tests/             # pytest tests
```

## Quick Commands

```bash
bsky whoami              # Check auth status
bsky login --handle X --password Y  # Auth with app password
bsky timeline            # View feed
bsky post "text"         # Post
bsky post "text" --dry-run  # Preview without posting
```

## Development

- **Language:** Python 3.8+
- **Key dependency:** `atproto` library
- **Config location:** `~/.config/bsky/config.json` (session tokens, never passwords)
- **Tests:** `pytest tests/`

## Making Changes

1. The CLI is `scripts/bsky.py` — single file, straightforward
2. Update version in both `SKILL.md` frontmatter AND `bsky.py --version`
3. Add entry to `CHANGELOG.md`
4. Test with `--dry-run` before live testing

## Publishing Updates

```bash
clawdhub publish ~/clawd/skills/bluesky --slug bluesky --version X.Y.Z
```

## Security Notes

- App passwords are used once for login, then discarded
- Session tokens (JWT) stored in config, not passwords
- Config file permissions set to 600 (owner-only)
