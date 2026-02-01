---
name: bluesky
version: 1.5.0
description: "Complete Bluesky CLI: post, reply, like, repost, follow, block, mute, search, threads, images. Everything you need to engage on Bluesky from the terminal."
homepage: https://bsky.app
metadata:
  openclaw:
    emoji: "🦋"
    requires:
      bins: ["python3"]
    tags: ["social", "bluesky", "at-protocol", "cli"]
---

# Bluesky CLI

Full-featured CLI for Bluesky/AT Protocol.

## Setup

First-time setup requires an app password:
1. Go to bsky.app → Settings → Privacy and Security → App Passwords
2. Create a new app password
3. Run: `bsky login --handle yourhandle.bsky.social --password xxxx-xxxx-xxxx-xxxx`

**Security:** Password is NOT stored — only a session token that auto-refreshes.

## Quick Reference

| Action | Command |
|--------|---------|
| View timeline | `bsky timeline` or `bsky tl` |
| Post | `bsky post "text"` |
| Post with image | `bsky post "text" --image photo.jpg --alt "description"` |
| Reply | `bsky reply <url> "text"` |
| Quote-post | `bsky quote <url> "text"` |
| View thread | `bsky thread <url>` |
| Like | `bsky like <url>` |
| Repost | `bsky repost <url>` |
| Follow | `bsky follow @handle` |
| Block | `bsky block @handle` |
| Mute | `bsky mute @handle` |
| Search | `bsky search "query"` |
| Notifications | `bsky notifications` or `bsky n` |
| Delete post | `bsky delete <url>` |

## Commands

### Timeline
```bash
bsky timeline              # 10 posts
bsky timeline -n 20        # 20 posts
bsky timeline --json       # JSON output
```

### Posting
```bash
bsky post "Hello world!"                           # Basic post
bsky post "Check this!" --image pic.jpg --alt "A photo"  # With image
bsky post "Test" --dry-run                         # Preview only
```

### Reply & Quote
```bash
bsky reply <post-url> "Your reply"
bsky quote <post-url> "Your take on this"
```

### Thread View
```bash
bsky thread <post-url>           # View conversation
bsky thread <url> --depth 10     # More replies
bsky thread <url> --json         # JSON output
```

### Engagement
```bash
bsky like <post-url>             # ❤️ Like
bsky unlike <post-url>           # Remove like
bsky repost <post-url>           # 🔁 Repost (aliases: boost, rt)
bsky unrepost <post-url>         # Remove repost
```

### Social Graph
```bash
bsky follow @someone             # Follow user
bsky unfollow @someone           # Unfollow user
bsky profile @someone            # View profile
bsky profile --json              # JSON output
```

### Moderation
```bash
bsky block @someone              # 🚫 Block user
bsky unblock @someone            # Unblock
bsky mute @someone               # 🔇 Mute user
bsky unmute @someone             # Unmute
```

### Search & Notifications
```bash
bsky search "query"              # Search posts
bsky search "topic" -n 20        # More results
bsky notifications               # Recent notifications
bsky n -n 30                     # More notifications
```

### Delete
```bash
bsky delete <post-url>           # Delete your post
bsky delete <post-id>            # By ID
```

## JSON Output

Add `--json` to read commands for structured output:
```bash
bsky timeline --json
bsky search "topic" --json
bsky notifications --json
bsky profile @someone --json
bsky thread <url> --json
```

## Error Handling

| Error | Fix |
|-------|-----|
| "Session expired" | Run `bsky login` again |
| "Not logged in" | Run `bsky login --handle ... --password ...` |
| "Post is X chars (max 300)" | Shorten text |
| "Image too large" | Use image under 1MB |

## Notes

- All `<url>` parameters accept either `https://bsky.app/...` URLs or `at://` URIs
- Handles auto-append `.bsky.social` if no domain specified
- Image posts require `--alt` for accessibility (Bluesky requirement)
- Session tokens auto-refresh; password never stored
