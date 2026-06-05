## Description: <br>
Bluesky CLI for timeline, search, notifications, posts, replies, threads, images, likes, reposts, follows, blocks, and mutes. <br>

This skill is ready for commercial/non-commercial use. <br>

## Publisher: <br>
[jeffaf](https://clawhub.ai/user/jeffaf) <br>

### License/Terms of Use: <br>
MIT-0 <br>


## Use Case: <br>
Developers, external users, and agents use this skill to operate a Bluesky account from the terminal, including reading feeds, posting content, engaging with posts, managing follows, and using moderation actions. <br>

### Deployment Geography for Use: <br>
Global <br>

## Known Risks and Mitigations: <br>
Risk: Bluesky app passwords can be exposed if pasted into chat, shell history, logs, or command-line arguments. <br>
Mitigation: Use the hidden password prompt, avoid sharing app passwords in chat or command arguments, and revoke the app password if exposure is suspected. <br>
Risk: Posting, replying, liking, reposting, following, blocking, muting, and deleting commands can publicly change the authenticated account. <br>
Mitigation: Review post text, URLs, handles, and target accounts before running mutating commands; use dry-run where supported for posts, replies, quotes, and threads. <br>
Risk: An active session lets the skill continue acting as the authenticated Bluesky user. <br>
Mitigation: Run logout or revoke the Bluesky app password/session when access should be removed. <br>


## Reference(s): <br>
- [ClawHub Bluesky Skill Page](https://clawhub.ai/jeffaf/bluesky) <br>
- [Bluesky](https://bsky.app) <br>
- [Artifact README](artifact/README.md) <br>
- [Skill Definition](artifact/SKILL.md) <br>


## Skill Output: <br>
**Output Type(s):** [Shell commands, Configuration instructions, API calls, JSON, Guidance] <br>
**Output Format:** [Markdown with inline bash commands and optional JSON output from read commands] <br>
**Output Parameters:** [1D] <br>
**Other Properties Related to Output:** [Read commands can emit JSON with --json; mutating commands operate on the authenticated Bluesky account.] <br>

## Skill Version(s): <br>
1.6.2 (source: frontmatter and server release metadata) <br>

## Ethical Considerations: <br>
Users should evaluate whether this skill is appropriate for their environment, review any generated or modified files before relying on them, and apply their organization's safety, security, and compliance requirements before deployment. <br>
