<!-- foundation:identity -->
# Aurora Chat

A ChatGPT-style chat application: users sign in with OAuth, start conversations, send messages, and watch assistant replies stream back token by token through a pluggable AI provider adapter. Ships wi

- Site: https://aurora-chat.api.holode.xyz
- Support: support@aurora-chat.api.holode.xyz
<!-- /foundation:identity -->

## What this is

A ChatGPT-style chat application: users sign in with OAuth, start conversations, send messages, and watch assistant replies stream back token by token through a pluggable AI provider adapter. Ships with a working demo adapter that returns canned streaming replies, plus complete real-provider configuration (OpenAI-compatible streaming API) so swapping in a real key is the only change needed.

## Who it is for

- User: signs in via Google or GitHub OAuth, owns conversations and messages
- Admin: optional foundation admin access

## Main features

- **Sign in** — Google/GitHub OAuth account linking; lands on the chat product itself, not a dashboard
- **Start a conversation** — New chat from the sidebar; conversation appears in history
- **Send a message and stream a reply** — User message persists, assistant placeholder starts streaming via SSE, chunks append live, final content saved
- **Switch conversations** — Sidebar lists conversations with previews; clicking loads the full history
- **Delete a conversation** — Remove a thread and its messages

## Core entities

- User
- Conversation
- Message

## Run locally

```bash
bundle install
bin/rails db:prepare
bin/dev
```

Requires Ruby, PostgreSQL, and the usual Rails toolchain. See `bin/setup` if present.

## Demo

One demo user (demo@aurora.local) with two conversations (a short greeting exchange and a longer exchange) so sidebar history and message bubbles render immediately; the demo provider adapter streams canned replies live.

## Deploy notes

Production `config.hosts` is derived from `domain` in `config/foundation.yml`. Keep that value aligned with the real host or every request will 403.
