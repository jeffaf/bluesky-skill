# Changelog

All notable changes to the bsky CLI skill.

## [1.3.0] - 2026-02-01

### Added
- `bsky reply <uri> "text"` — Reply to posts
- `bsky quote <uri> "text"` — Quote-post
- `bsky thread <uri>` — View full conversation with parent chain and replies
- `--json` flag on timeline, search, notifications, profile, thread
- `--depth` flag on thread command (default: 6)
- Empty state messages ("No notifications yet — go make some noise!")
- Aliases: `r` for reply, `qt` for quote, `th` for thread

### Improved
- Refactored post building into reusable `build_post_with_facets()`
- Better URL/URI parsing (handles both `at://` and `https://bsky.app/` formats)
- Thread view shows parent chain above current post

### Changed
- Rebranded to OpenClaw

## [1.2.0] - 2026-01-29

### Added
- `logout` command — clear session and revoke access
- Mention facets — `@handle` becomes clickable link on Bluesky
- `--dry-run` flag for post command (preview without posting)
- `--version` flag

### Security
- Config file permissions set to 600 (owner-only read/write)
- Pinned atproto version (`>=0.0.65,<0.1.0`) to prevent surprise breaks

### Changed
- Rebranded to OpenClaw

## [1.1.1] - 2026-01-28

### Added
- `--version` flag
- `--dry-run` flag for post preview
- Input validation (reject empty posts, posts over 300 chars)

### Fixed
- Wrapper script symlink resolution

## [1.1.0] - 2026-01-28

### Security
- Removed plaintext password storage
- Now uses session tokens (JWT) — password only used during login
- Auto-migrates old configs to session-based auth

## [1.0.0] - 2026-01-24

### Added
- Initial release
- Commands: login, whoami, timeline, post, delete, search, notifications, profile
- URL auto-detection with proper facets
- Session-based authentication
