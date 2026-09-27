# Privacy Policy — WestBot

**Last updated:** 26 September 2026

This policy explains what data WestBot collects, why it collects it, and what it does with it. WestBot is a Discord bot. It is not operated by Discord, Inc., and its use is governed by Discord's Terms of Service and Privacy Policy as well as the Discord Developer Policy.

## Summary

WestBot is a community utility bot for Discord servers. It stores data only where a server explicitly configures a feature, and only for as long as that feature is in use. It does not sell, rent, trade, or share your data with anyone. It does not build advertising profiles, and it does not use your data for automated decision-making or AI training.

## Who runs WestBot

WestBot is operated by its individual maintainers. Contact: **zFons** or **YvngxSanty** (Discord users). For any privacy request, open a ticket with the bot's support server, or contact a maintainer directly on Discord.

## Data we store

WestBot runs on an application database (hosted on Heroku's PostgreSQL service). It does not scrape Discord, and it does not read message content except as described under "Message content" below.

### 1. Server configuration
Each Discord server using WestBot stores its own settings: server ID, configured log/moderation/ticket/suggestion channel IDs, configured moderator role IDs, feature toggles, and infraction thresholds. This identifies the server, not its members.

### 2. Moderation records
When a moderation action is taken through WestBot, we store a case record: server ID, action type, the user acted upon (Discord user ID), the moderator who performed it (Discord user ID), and the reason text supplied by the moderator. Appeals submitted against those cases store the appealing user's ID, the appeal text, and the reviewing moderator. These records are retained for server accountability and are visible to that server's moderation staff. Data for a given server can be deleted on request from the server owner or a moderator.

### 3. Staff activity logs
WestBot keeps an audit log of staff actions so that server owners can review moderator behaviour. This records: the staff member's Discord user ID and display name, the action performed, the target user, the reason text, the channel, and a timestamp. This log is the reason WestBot requests the **Server Members Intent** and **Message Content Intent** (see below), and it is accessible only to the server's configured staff.

### 4. User preference and social feature data
Optional community features store per-user state such as: AFK status and its timestamp (cleared as soon as you send a message), opt-in relationship/"marriage" records, interaction statistics (for example hug/kiss counters), blocked-user entries, and football-prediction picks. Each of these is opt-in and tied to your Discord user ID. Stored locally in the bot's database, and not transmitted anywhere else.

### 5. Spotify authorization tokens
If you use the Spotify integration, you authorize it through Spotify's own OAuth flow. To play a track on your behalf, WestBot must store your Spotify access token and refresh token, along with the granted scopes and expiry time, against your Discord user ID. These tokens are used **solely** to call the Spotify Web API on your behalf to control your own playback. They are never read by a human, never displayed publicly, never sold, and never shared with any third party. If you revoke access in Spotify's account settings, the tokens simply expire and are no longer usable. You may also ask the maintainers to delete your stored tokens.

### 6. Ephemeral and technical data
Short-lived operational data such as rate-limit state, cooldowns, and the contents of an unconfirmed setup wizard (Discord's own confirmation token) is held only in memory while the bot runs. It is not written to the database. Database backups are retained by our hosting provider for a limited window and then deleted.

## Message content

WestBot requests the **Message Content Intent** for two specific purposes only:

1. **Prefix commands.** All of WestBot's commands are Discord *hybrid* commands, meaning each command is registered both as a slash command and as a prefix (text) command such as `w.help`. The prefix form only works if the bot can read the message text. Without this intent, all of WestBot's commands would lose their prefix form.
2. **Staff activity auditing.** In a server's configured moderation channel, when a staff member issues a moderation command that is executed by a *different, third-party* moderation bot, WestBot reads that staff member's message to record who ran which moderation action, against whom, and with what reason, in the unified staff activity log described above. It parses only the moderation command itself and its reason. It does not retain the full text of the message.

WestBot does **not** read, store, or analyze the content of ordinary conversation, does not build profiles from message content, and does not use message content for any purpose other than these two features. Features that do not need the text of a message (for example the AFK system and the image-attachment reminder handler) are deliberately written to work without it.

## Member data

WestBot requests the **Server Members Intent** for a single purpose: receiving the ban event so that a server's log channel can record who was banned, when, and the reason given. Discord delivers this only to applications holding the intent.

WestBot does **not** use this intent to send join or leave notifications, to enumerate or store a member list, or for any form of profiling. Member data received in a ban event is used only to render that log entry and is not stored separately. Where WestBot needs to look up a user by name, it uses Discord's own non-restricted search endpoint, and reads the result only to display it in the resulting message. Where it needs a member total, it uses the count included in the guild payload.

WestBot does **not** request the **Presence Intent**. It never reads users' online status, custom status, or playing activity.

## Permissions the bot requests

In addition to the two privileged intents above, WestBot requests only the standard Discord permissions its features need: Manage Messages, Manage Roles (only to apply configured punishment roles), Ban Members, Kick Members, Moderate Members, Read Message History, Send Messages, Embed Links, Attach Files, and Add Reactions. Permission levels are configurable per server by the server owner.

## Third parties

WestBot's only third-party data flows are:

- **Discord** — the platform itself, governed by Discord's own privacy policy.
- **Spotify** — only for users who explicitly authorize the Spotify integration, governed by Spotify's privacy policy.
- **Tenor** — image/GIF search, used to resolve a user-requested search term into a media URL. Search terms are sent to Tenor only when a user invokes a GIF command.
- **Heroku** — application hosting and the PostgreSQL database, governed by Heroku's privacy policy.

WestBot does not send user data to any analytics, advertising, or tracking service.

## Data retention and deletion

- Per-server moderation and staff activity data is retained for as long as the server uses the relevant feature, and can be deleted on request from the server owner or a moderator.
- AFK status is deleted automatically when you next send a message.
- Social/preference data persists until you or a server moderator remove it via the corresponding command, or until you request deletion.
- On request from a user, we will delete the data associated with that user's Discord user ID. On request from a server owner, we will delete that server's configuration and logs.
- Data is removed from the live database within a reasonable period of a verified request. Residual copies may persist in backups for a short additional window before being rotated out.

### Retention periods

Not all data is short-lived. The following periods apply:

| Data | Retention |
| --- | --- |
| AFK status | Until you next send a message, then deleted immediately |
| Pre-ban warnings | 5 days, then expire automatically |
| Moderator activity log (command, target user, reason text taken from a message) | Kept for as long as the server uses the staff feature, as it exists to let server owners review moderator behaviour |
| Moderation cases and appeals | Kept for as long as the server uses the moderation feature, as they are the server's accountability record |
| Ticket metadata (counts, participants, timestamps) | Kept for as long as the server uses the ticket feature; no message text is stored |
| Opt-in social state (relationships, interaction counters) | Until you or a server moderator remove it |
| Spotify tokens | Until you revoke access in Spotify or request deletion |
| Server configuration | Until the server owner removes the feature or the bot |

Text derived from message content is retained only in the moderator activity log described above, which is accessible solely to the server's administrators and can be deleted by them or by the server owner at any time.

Moderation case and appeal records are intentionally retained longer than 30 days because their purpose is server accountability: a short retention window would defeat the ability to review staff conduct. These records are accessible only to that server's administrators, and a server owner or moderator can delete them at any time.

## Security

Discord tokens and database credentials are stored only as environment variables on the hosting platform and are never committed to the source repository. The application is served over HTTPS, and database connections require TLS (`sslmode=require`). The database is hosted on Heroku Postgres, which encrypts all data at rest with AES-256 block-level storage encryption on every plan tier, and stores physical backups encrypted as well. Access to production data is limited to the bot maintainers.

## Children

WestBot is not directed at children under 13 and is not intended for use by them. Servers that are not primarily intended for an adult audience should not invite the bot.

## Changes to this policy

If this policy changes materially, the updated version will be published at the same public URL, and the "Last updated" date at the top will be revised. Continued use of WestBot after a change constitutes acceptance of the updated policy.

## Source code

WestBot is a closed-source project. Its source code is not published and is not distributed to third parties. This document is the only publicly published page about the project.
