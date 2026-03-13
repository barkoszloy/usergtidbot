# How to Find a Telegram User ID (5 Working Methods in 2026)

Every Telegram account has a unique numeric ID that never changes — even if the user changes their name, username, or phone number. If you work with Telegram bots, manage groups, or build automations, you'll need these IDs regularly. Here's how to get them.

## What Is a Telegram User ID?

A Telegram user ID is a permanent numeric identifier assigned to every account at registration. Unlike usernames (which are optional and changeable), the ID stays the same for the lifetime of the account.

For example, a user might have the username `@johndoe` today and `@john_smith` tomorrow, but their numeric ID — something like `123456789` — will always point to the same account.

Groups and channels also have IDs. Group IDs are negative numbers (like `-1001234567890`), which helps distinguish them from user IDs in bot code.

## Why Would You Need a Telegram ID?

There are several practical reasons:

- **Bot development** — Most Telegram Bot API methods require numeric IDs, not usernames. To send a message, restrict a user, or check membership, you need the ID.
- **Group administration** — When banning users or setting up automations, usernames can change. IDs don't.
- **Webhook configuration** — Setting up notifications or integrations often requires your own chat ID or a group ID.
- **User verification** — Confirming someone's identity across different groups or channels.
- **Database records** — If you store Telegram users in your system, the numeric ID is the only reliable key.
- **Automation scripts** — Any script that interacts with the Telegram API needs IDs to target the right chats.

## Method 1: Use @usergtidbot (Fastest)

The quickest way to find any Telegram ID is the [@usergtidbot](https://t.me/usergtidbot) bot. It was built specifically for this task and goes well beyond basic ID lookup.

### How to use it

1. Open [@usergtidbot](https://t.me/usergtidbot) in Telegram
2. Tap **Start**
3. Use the native picker buttons to select any user, group, or channel
4. Get the ID instantly

### What you get back

The bot returns more than just the ID:

- **Telegram ID** — the numeric identifier
- **Datacenter** — which Telegram server (DC1 through DC5) hosts the account. DC1 and DC3 are in Miami, DC2 and DC4 are in Amsterdam, DC5 is in Singapore
- **Estimated registration date** — based on known ID ranges, the bot estimates when the account was created (accuracy: ±2-3 months)
- **Account age badge** — Veteran (10+ years), Experienced (5-10), Seasoned (2-5), Regular (1-2), Newcomer (< 1 year)
- **Username history** — if the bot has tracked changes, it shows previous usernames
- **Birthday** — if the user has set their birthday in Telegram
- **Emoji status** — current custom emoji status (Premium feature)
- **All active usernames** — including collectible usernames purchased on Fragment
- **Personal channel** — linked personal channel, if set
- **Forward privacy** — whether the user has restricted message forwarding
- **Profile color** — custom accent color (Premium feature)
- **Business profile** — location and working hours for Telegram Business accounts
- **Profile photos count** — total number of profile photos
- **Bio** — the user's "About" text
- **Scam/Fake detection** — flags accounts marked by Telegram as scam or fake

### Extra features

- **Visual ID Card** — Generate a PNG card with avatar, ID, datacenter, registration date, and age badge
- **Inline mode** — Type `@usergtidbot` in any chat to look up IDs without opening the bot
- **QR code** — Generate a QR code containing the account ID
- **Compare accounts** — See which of two accounts was registered first
- **JSON export** — Get structured data for use in scripts or APIs
- **CSV export** — Export data for spreadsheets or bulk processing
- **Group admin tools** — List admins, check permissions, member count
- **Referral system** — Share the bot and track referrals

This is the most feature-rich option available. No forwarding messages, no copying links — just tap and get results.

## Method 2: Use @userinfobot

[@userinfobot](https://t.me/userinfobot) is one of the older ID bots on Telegram.

### How to use it

1. Open the bot and tap Start
2. Forward a message from the user whose ID you want
3. The bot returns the sender's ID

### Limitations

- You need to forward a message, which means you need a message from that person
- Only returns the ID and basic info — no datacenter, no registration estimate, no export options
- Does not support native picker buttons
- No inline mode

It works for simple lookups but lacks the depth of more modern tools.

## Method 3: Forward a Message to @rawdatabot

[@rawdatabot](https://t.me/rawdatabot) shows the raw JSON data that Telegram sends for any message.

### How to use it

1. Open @rawdatabot and start it
2. Forward any message to the bot
3. Look for the `forward_from` field in the JSON output — the `id` value is the user's Telegram ID

### Limitations

- The output is raw JSON, which is hard to read if you're not a developer
- If the user has privacy settings that hide forwarding, the `forward_from` field won't appear
- No extra features — it's a debugging tool, not an ID lookup tool

This method is mainly useful for developers who want to see the full message structure.

## Method 4: Use Telegram Web (for Your Own ID)

You can find your own ID through the Telegram Web interface, though it takes a few steps.

### How to do it

1. Open [web.telegram.org](https://web.telegram.org) in your browser
2. Log in to your account
3. Open any chat
4. Open your browser's developer tools (F12 or right-click → Inspect)
5. Go to the **Network** or **Console** tab
6. Look for API calls that contain your user ID, or check the application storage

### Limitations

- Only works for your own ID, not other users
- Requires developer tools knowledge
- The interface changes between Telegram Web versions (K and A), so the exact steps vary
- Not practical for regular use

This is a last resort if you can't use bots for some reason.

## Method 5: Telegram Bot API (for Developers)

If you run your own bot, you can get user IDs from incoming updates.

### How to do it

1. Create a bot via [@BotFather](https://t.me/BotFather)
2. Set up a webhook or poll for updates
3. When a user sends a message to your bot, the update JSON includes `message.from.id`

```python
# Example: getting user ID from an update
user_id = update.message.from_user.id
print(f"User ID: {user_id}")
```

### Limitations

- Requires programming knowledge
- The user must interact with your bot first
- Only gives you IDs of people who message your bot
- Significant setup overhead for a simple ID lookup

This is how bots internally resolve user IDs, but it's overkill if you just need to look up an ID.

## Comparison Table

| Feature | @usergtidbot | @userinfobot | @rawdatabot | Telegram Web | Bot API |
|---|---|---|---|---|---|
| Lookup speed | Instant | Requires forwarding | Requires forwarding | Manual process | Requires coding |
| Native picker buttons | Yes | No | No | No | No |
| Datacenter detection | Yes | No | No | No | No |
| Registration date estimate | Yes | No | No | No | No |
| Account age badges | Yes | No | No | No | No |
| Birthday / emoji status | Yes | No | No | No | No |
| Collectible usernames | Yes | No | No | No | No |
| Business profile info | Yes | No | No | No | No |
| Visual ID card (PNG) | Yes | No | No | No | No |
| Username history | Yes | No | No | No | No |
| Inline mode | Yes | No | No | N/A | N/A |
| QR code | Yes | No | No | No | No |
| JSON export | Yes | No | Raw only | No | Raw only |
| CSV export | Yes | No | No | No | No |
| Compare accounts | Yes | No | No | No | No |
| Group admin tools | Yes | No | No | No | Custom only |
| Works for groups/channels | Yes | Limited | Yes | Own only | Yes |
| No forwarding needed | Yes | No | No | N/A | N/A |

## Which Method Should You Use?

For most people, [@usergtidbot](https://t.me/usergtidbot) is the clear choice. It handles all the common cases — looking up users, groups, channels — and adds useful context like the datacenter and account age. The native picker buttons mean you don't need to forward messages or know someone's username.

If you're a developer debugging message structures, @rawdatabot can be handy for seeing the full JSON payload.

If you only need your own ID once, any method works.

For ongoing bot development or group administration, having @usergtidbot in your toolkit saves time every day. The inline mode alone is worth it — type `@usergtidbot` in any chat, pick a user, and you have the ID without leaving the conversation.

## Frequently Asked Questions

### Can someone change their Telegram ID?

No. The ID is assigned at registration and cannot be changed. Usernames, display names, and phone numbers can all change, but the ID is permanent.

### Are Telegram IDs sequential?

Roughly, yes. Earlier accounts have lower IDs. This is how bots like @usergtidbot estimate registration dates — by mapping known ID ranges to time periods.

### What's the difference between a user ID and a chat ID?

For private conversations, the chat ID equals the user ID. For groups and supergroups, the chat ID is a separate negative number. Channels also have their own negative IDs.

### Can I find someone's ID if they have no username?

Yes. With @usergtidbot, you can use the native picker button to select any contact — no username required.

### Is it safe to share my Telegram ID?

Your Telegram ID is not secret. Anyone who shares a group with you or receives a forwarded message from you can see it. It cannot be used to access your account, send you messages (unless through a bot), or find your phone number.
