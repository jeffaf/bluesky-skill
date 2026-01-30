---
name: bluesky
version: 1.2.0
description: Read, post, and interact with Bluesky (AT Protocol) via CLI. Use when user asks to check Bluesky, post to Bluesky, view their Bluesky timeline, search Bluesky, or check Bluesky notifications. Supports timeline, posting, profile lookup, search, and notifications.
homepage: https://bsky.app
metadata:
  clawdbot:
    emoji: "🦋"
    requires:
      bins: ["python3"]
---

# Bluesky CLI

Interact with Bluesky/AT Protocol from the command line.

## Setup

First-time setup requires an app password from Bluesky:
1. Go to bsky.app → Settings → Privacy and Security → App Passwords
2. Create a new app password
3. Run: `bsky login --handle yourhandle.bsky.social --password xxxx-xxxx-xxxx-xxxx`

**Security:** Password is NOT stored. The CLI exports a session token on login, which auto-refreshes. Your app password only exists in memory during login. Config stored at `~/.config/bsky/config.json` with 0600 permissions.

## Commands

### Authentication
```bash
bsky login --handle user.bsky.social --password xxxx-xxxx-xxxx-xxxx
bsky logout                # Clear session and log out
bsky whoami                # Show current user info
```

### Timeline
```bash
bsky timeline              # Show home feed (default: 10 posts)
bsky timeline -n 20        # Show 20 posts
bsky tl                    # Alias
bsky home                  # Alias
```

### Posting
```bash
bsky post "Hello world!"   # Create a post (max 300 chars)
bsky p "Short post"        # Alias
bsky post "Test" --dry-run # Preview without posting

# Smart features (automatic):
# - URLs become clickable links
# - @mentions resolve to profiles (e.g., @someone becomes clickable)
```

### Delete
```bash
bsky delete <post_id>      # Delete by post ID
bsky delete <url>          # Delete by full bsky.app URL
bsky del <id>              # Alias
bsky rm <id>               # Alias
```

### Profile
```bash
bsky profile               # Your own profile
bsky profile @someone.bsky.social
bsky profile someone       # Auto-appends .bsky.social
```

### Search
```bash
bsky search "query"        # Search posts (default: 10 results)
bsky search "topic" -n 20  # More results
bsky s "query"             # Alias
```

### Notifications
```bash
bsky notifications         # Show recent notifications (default: 20)
bsky notif -n 30           # Alias with custom count
bsky n                     # Short alias

# Types: ❤️ like, 🔁 repost, 👤 follow, 💬 reply, 📢 mention, 💭 quote
```

### Version
```bash
bsky --version
bsky -v
```

## Output Format

**Timeline posts:**
```
@handle · Jan 25 14:30
  Post text (truncated to 200 chars)
  ❤️ likes  🔁 reposts  💬 replies
  🔗 https://bsky.app/profile/handle/post/id
```

**Search results:**
```
@handle: Post text (truncated to 150 chars)
  ❤️ likes  🔗 https://bsky.app/profile/handle/post/id
```

## Error Handling

| Error | Meaning | Fix |
|-------|---------|-----|
| "Session expired" | Token invalid | Run `bsky login` again |
| "Not logged in" | No saved session | Run `bsky login` |
| "Post is X chars (max 300)" | Too long | Shorten the text |

## Installation

Use the wrapper script (auto-creates venv on first run):
```bash
{baseDir}/scripts/bsky [command]
```

Manual setup if needed:
```bash
cd {baseDir}/scripts
python3 -m venv venv
./venv/bin/pip install -r ../requirements.txt
./venv/bin/python bsky.py [command]
```
