# Bluesky CLI Roadmap

Current version: **v1.5.0**

## ✅ Shipped

### v1.5.0
- Block/unblock users
- Mute/unmute users
- Image posting with alt text

### v1.4.0
- Like/unlike posts
- Repost/unrepost
- Follow/unfollow users

### v1.3.0
- Reply to posts
- Quote-post
- Thread view with depth control
- `--json` flag on all read commands

### v1.2.0
- Logout command
- Mention facets (@handle → clickable)
- `--dry-run` flag
- `--version` flag

### v1.1.0
- Session-based auth (no password storage)
- Auto-migrate from old configs

### v1.0.0
- Core commands: login, whoami, timeline, post, delete, search, notifications, profile
- URL auto-detection with facets

---

## 🔮 Future Ideas (v2.0+)

### Feeds
- [ ] `bsky feed <name>` — View custom feeds (Discover, What's Hot, etc.)
- [ ] `bsky feed list` — List available feeds

### Threading
- [ ] `bsky thread "Post 1" "Post 2" "Post 3"` — Create threaded posts
- [ ] Partial failure recovery (see docs/THREADING.md)

### Lists
- [ ] `bsky list create "name"` — Create moderation list
- [ ] `bsky list add <list> @handle` — Add to list
- [ ] `bsky list subscribe <list>` — Subscribe to list

### Analytics
- [ ] `bsky stats` — Your engagement stats
- [ ] `bsky post <url> --stats` — Post analytics

### Scheduling (would need external service)
- [ ] `bsky schedule "text" --at "2024-01-15 09:00"`

### Polish
- [ ] Demo GIF in README
- [ ] GitHub Actions: lint on PR
- [ ] Shell completions (bash/zsh/fish)

---

*Last updated: 2026-02-04*
