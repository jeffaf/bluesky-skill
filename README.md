# 🦋 Bluesky CLI

An OpenClaw skill for interacting with Bluesky (AT Protocol) from the command line.

**Version:** 1.3.0

## Features

- **Timeline** - View your home feed
- **Post** - Create posts with auto-linked URLs and @mentions
- **Reply** - Reply to posts (NEW in 1.3)
- **Quote** - Quote-post with your commentary (NEW in 1.3)
- **Thread** - View full conversation context (NEW in 1.3)
- **Search** - Search posts across Bluesky
- **Notifications** - Check likes, reposts, follows, mentions, quotes
- **Profile** - Look up user profiles
- **Delete** - Remove your posts
- **JSON Output** - `--json` flag on all read commands (NEW in 1.3)
- **Secure** - Session-based auth (password never stored)

## Setup

### 1. Get an App Password

1. Go to [bsky.app](https://bsky.app) → Settings → Privacy and Security → App Passwords
2. Create a new app password (looks like `xxxx-xxxx-xxxx-xxxx`)

### 2. Login

```bash
bsky login --handle yourhandle.bsky.social --password xxxx-xxxx-xxxx-xxxx
```

Your password is used once to create a session token, then discarded. It's never stored on disk.

### 3. Verify

```bash
bsky whoami
```

## Usage

### Authentication
```bash
bsky login --handle user.bsky.social --password xxxx-xxxx-xxxx-xxxx
bsky logout                # Clear session
bsky whoami                # Show current user
```

### Timeline
```bash
bsky timeline              # Show 10 posts
bsky timeline -n 20        # Show 20 posts
bsky tl                    # Alias
bsky home                  # Alias
```

### Posting
```bash
bsky post "Hello Bluesky!"
bsky p "Short post"              # Alias
bsky post "Test" --dry-run       # Preview without posting
```

**Smart features (automatic):**
- URLs become clickable links
- `@mentions` resolve to profiles and become clickable

### Reply
```bash
bsky reply <post-url> "Your reply here"
bsky reply <at://uri> "Reply text"
bsky r <url> "Short alias"                         # Alias
bsky reply <url> "Test" --dry-run                  # Preview without posting
```

### Quote
```bash
bsky quote <post-url> "Your commentary"
bsky qt <url> "Short alias"                        # Alias
bsky quote <url> "Test" --dry-run                  # Preview without posting
```

### Thread
```bash
bsky thread <post-url>                             # View full conversation
bsky thread <url> --depth 10                       # Fetch more replies
bsky thread <url> --json                           # Output as JSON
bsky th <url>                                      # Alias
```

### Delete
```bash
bsky delete <post_id>                              # Delete by ID
bsky delete https://bsky.app/profile/.../post/... # Delete by URL
bsky del <id>                                      # Alias
bsky rm <id>                                       # Alias
```

### Search
```bash
bsky search "query"
bsky search "topic" -n 20   # More results
bsky s "query"              # Alias
```

### Notifications
```bash
bsky notifications          # Show 20 notifications
bsky notif -n 30            # Custom count
bsky n                      # Alias
```

Notification types: ❤️ like, 🔁 repost, 👤 follow, 💬 reply, 📢 mention, 💭 quote

### Profile
```bash
bsky profile                        # Your profile
bsky profile @someone.bsky.social   # Someone else's
bsky profile someone                # Auto-appends .bsky.social
```

### Version
```bash
bsky --version
bsky -v
```

## Output Format

**Timeline:**
```
@handle · Jan 25 14:30
  Post text here...
  ❤️ 42  🔁 5  💬 3
  🔗 https://bsky.app/profile/handle/post/id
```

**Search results:**
```
@handle: Post text (truncated)...
  ❤️ 42  🔗 https://bsky.app/profile/handle/post/id
```

## Requirements

- Python 3.8+
- `atproto` package (auto-installed via venv)

## Installation

Clone into your skills directory:
```bash
git clone <repo-url> ~/clawd/skills/bluesky
```

The wrapper script auto-creates a virtual environment on first run.

## Configuration

- **Location:** `~/.config/bsky/config.json`
- **Permissions:** 600 (owner-only)
- **Contents:** Session token and handle (no passwords)

## Security

- App password used only during `login`, never stored
- Session tokens (JWT) auto-refresh as needed
- Config file restricted to owner-only permissions

## License

MIT

---

*Built for [OpenClaw](https://github.com/openclaw/openclaw)*
