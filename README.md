<div align="center">

# gitbot Library

**Ready-made bots for [gitbot](https://github.com/gitbot-hq/GitBot). Install one, point it at a folder, put it to work.**

[![npm version](https://img.shields.io/npm/v/@gitbot-hq/gitbot?label=%40gitbot-hq%2Fgitbot)](https://www.npmjs.com/package/@gitbot-hq/gitbot)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

[Get gitbot](#get-gitbot) · [What is a bot?](#what-is-a-bot) · [Using a bot](#using-a-bot-from-the-library) · [Publish a bot](#publish-your-own) · [License](#license)

</div>

> [!NOTE]
> **The first bots are coming soon.** This repository is where they will live. Watch or star the repo to hear when they land.

## What is this?

[gitbot](https://github.com/gitbot-hq/GitBot) lets you turn an AI coding agent — Claude Code, Codex or OpenCode — into reusable **bots** that run on your own machine. This library is the home for bots built with it: bots you can install instead of writing from scratch, and read to learn how a good bot is put together.

## Get gitbot

You need gitbot to use anything here.

```bash
npm install -g @gitbot-hq/gitbot
gitbot start
```

- **npm package:** [`@gitbot-hq/gitbot`](https://www.npmjs.com/package/@gitbot-hq/gitbot)
- **Source, docs and issues:** [github.com/gitbot-hq/GitBot](https://github.com/gitbot-hq/GitBot)

gitbot needs Node.js 18+ and at least one agent installed and logged in. The [gitbot README](https://github.com/gitbot-hq/GitBot#install) covers setup.

## What is a bot?

A bot is an agent you define once and reuse:

- **Instructions** — its standing job, e.g. *"Review the diff against main. Flag bugs and missing tests. Never modify files."*
- **An agent** — Claude Code, Codex or OpenCode — and optionally a model.
- **A permission mode** — ask before each tool, auto-approve, or plan only.
- **Tool lists** — optionally, the only tools it may use.
- **Setup steps** — optionally, what it needs on a machine (*"ffmpeg must be on PATH"*), which it checks or prepares once.

Every bot in this library is one folder under `bots/` holding exactly that, plus the words that describe it. You can read any of them in full before you install — the instructions are plain Markdown, not an encoded blob.

## Using a bot from the library

1. Open the gitbot hub and go to **Discover**.
2. Find a bot and open it. Read what it does, what it can help with, and the permission mode it runs in.
3. Click **Install**. The bot is added to your machine, with approvals on by default.
4. Open a thread in the folder you want it to work in, and say hi. The bot starts its job on your first message, whatever that message says.

> [!WARNING]
> **Read a bot before you install it.** A bot is a set of instructions for an AI agent that runs on your machine with your file access. Its detail page shows the instructions it will run under and the permission mode it carries, and a bot with setup steps begins its one-time setup run as soon as you install it. Install bots you have read or whose author you trust — the same care you would give a script from the internet. See [gitbot's security notes](https://github.com/gitbot-hq/GitBot#security).

## Publish your own

Built a bot that earns its keep? Add it here with a pull request.

The quickest way is to let an agent do it: paste [`docs/publish-prompt.md`](docs/publish-prompt.md) into Claude Code, Codex or OpenCode. It starts by listing the bots you have already built on this machine and offering to publish one of them as it stands; otherwise it interviews you about a new one. Either way it writes the folder, checks it and opens the pull request, pausing for your approval before it writes anything and before it submits.

- **[Contributing guide](CONTRIBUTING.md)** — the rules, the checklist, and what review looks for.
- **[Bot folder specification](docs/bot-schema.md)** — every field, its limits, and why it is shaped that way.

Everything published here is MIT licensed, so anyone can read a bot, install it, fork it and adapt
it. Submitting a pull request means you are offering your bot on those terms.

Have an idea but not the time to build it? [Open an issue](https://github.com/gitbot-hq/Library/issues) and describe what the bot should do.

## License

[MIT](LICENSE) — the same licence as [gitbot](https://github.com/gitbot-hq/GitBot) itself.

This covers the whole repository, every bot in it, and the docs. There are no per-bot licences: a
bot that cannot be published under MIT cannot be published here. Contributors keep the copyright in
what they write and licence it to everyone else under MIT by submitting it.

## Links

- gitbot on npm — [npmjs.com/package/@gitbot-hq/gitbot](https://www.npmjs.com/package/@gitbot-hq/gitbot)
- gitbot on GitHub — [github.com/gitbot-hq/GitBot](https://github.com/gitbot-hq/GitBot)
- Report a problem with gitbot itself — [GitBot issues](https://github.com/gitbot-hq/GitBot/issues)
