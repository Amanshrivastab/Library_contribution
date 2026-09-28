| [![GitBot](gitbot-logo.svg)](#gitbot-library) | [Overview](#gitbot-library) · [Use](#use-the-library) · [Publish](#publish-a-bot) · [Bot format](#what-a-published-bot-contains) · [Safety](#before-you-install) · [License](#license) |
| :--- | ---: |

<br><br><br>

# GitBot Library

[![GitBot on npm](https://img.shields.io/npm/v/%40gitbot-hq%2Fgitbot?style=flat-square&label=gitbot)](https://www.npmjs.com/package/@gitbot-hq/gitbot)
[![GitHub stars](https://img.shields.io/github/stars/gitbot-hq/Library?style=flat-square&logo=github)](https://github.com/gitbot-hq/Library/stargazers)
[![Pull requests welcome](https://img.shields.io/github/issues-pr/gitbot-hq/Library?style=flat-square&label=pull%20requests)](https://github.com/gitbot-hq/Library/pulls)
[![License MIT](https://img.shields.io/github/license/gitbot-hq/Library?style=flat-square&label=license)](LICENSE)

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="library-cover-dark.webp">
  <source media="(prefers-color-scheme: light)" srcset="library-cover-light.webp">
  <img alt="GitBot Library" src="library-cover-light.webp">
</picture>

**Ready-made bots for [GitBot](https://github.com/gitbot-hq/GitBot). Read one, install it, and put it to work in your own folders.**

GitBot turns Claude Code, Codex, or OpenCode into reusable bots that run on your machine. This repository is the public catalog behind GitBot's **Marketplace**. Every listing includes the bot's instructions, settings, and optional setup steps in plain files you can inspect before installing it.

<br><br><br>

## Use the Library

First, install and start GitBot:

```bash
npm install -g @gitbot-hq/gitbot
gitbot start
```

Then:

1. Open GitBot and go to **Marketplace**.
2. Choose a bot and review what it does, its instructions, setup steps, agent, and permissions.
3. Select **Install** to add it to your machine.
4. Start a thread in the folder where you want it to work.

GitBot needs Node.js 18 or newer and at least one supported coding agent installed and signed in. See the [GitBot README](https://github.com/gitbot-hq/GitBot) for the full requirements.

<br><br><br>

## Before you install

> [!WARNING]
> A bot is a set of instructions for an AI coding agent running with your file and shell access. Read its files and permission mode before installing it, just as you would inspect a script from the internet.

A bot may include one-time setup instructions that run after installation. Prefer bots whose behavior you understand, keep approvals enabled when trying one for the first time, and use GitBot only on a trusted network. Read the [GitBot README](https://github.com/gitbot-hq/GitBot) before giving a bot broader permissions.

<br><br><br>

## Publish a bot

You can publish with an agent or prepare the files yourself.

### Ask an agent to prepare it

Give Claude Code, Codex, or OpenCode the [`publish-prompt.md`](docs/publish-prompt.md) instructions. The agent can find an existing local bot or help shape a new one, validate the listing, show you the final diff, and wait for your approval before opening a pull request.

### Create it manually

Read the [contributing guide](CONTRIBUTING.md) and [bot schema](docs/bot-schema.md), then open a pull request containing one new folder under `bots/`.

```text
bots/<slug>/
  bot.json           listing, mascot, agent, and permissions
  instructions.md    the bot's standing job
  setup.md           optional one-time setup requirements
```

Keep submissions portable: no local paths, private repository names, credentials, personal machine details, images, or binaries.

Opening a pull request publishes your bot under this repository's [MIT license](LICENSE). You keep the copyright in what you wrote, and bot folders carry no license file of their own.

<br><br><br>

## What a published bot contains

- **A clear listing** with its name, description, category, features, example prompt, and author.
- **Readable instructions** that define the job the agent performs in every thread.
- **Runtime settings** for its agent, permission mode, optional model, and tool limits.
- **A GitBot mascot** selected by body, color, and activity tokens.
- **Optional setup instructions** only when the job genuinely needs machine preparation.

The repository's generated index is maintained separately. Contributors add a bot folder and never edit `index.json` or `verified.json` directly.

<br><br><br>

## Review and contribution

Each pull request should publish one bot. Review checks the schema, file layout, field limits, author, and common privacy mistakes. Maintainers also check whether the instructions deliver what the listing promises and whether the requested permission mode fits the job.

Have an idea without a finished bot? [Open an issue](https://github.com/gitbot-hq/Library/issues) and describe the job it should perform.

<br><br><br>

## License

[MIT](LICENSE), the same license as [GitBot](https://github.com/gitbot-hq/GitBot) itself.

One license covers the repository, the docs, and every bot in it, so nothing here needs its own terms and nobody has to check a bot's license before installing it. Contributors keep the copyright in what they write and license it to everyone else under MIT by submitting it. A bot that cannot be published under MIT belongs on its author's machine instead.

<br><br><br>

## Links

- [GitBot source and documentation](https://github.com/gitbot-hq/GitBot)
- [GitBot on npm](https://www.npmjs.com/package/@gitbot-hq/gitbot)
- [Contributing guide](CONTRIBUTING.md)
- [Bot folder specification](docs/bot-schema.md)
- [Agent publishing prompt](docs/publish-prompt.md)
