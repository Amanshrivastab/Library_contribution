# Contributing a bot

Bots in this library are folders. One folder is one bot, and everything needed to list it, explain
it and install it lives inside.

You do not have to assemble that folder by hand.

## The short version

Open your coding agent in any folder, paste in
**[`docs/publish-prompt.md`](docs/publish-prompt.md)**, and answer its questions. If you have already
built bots with gitbot, it finds them, lists them and offers to publish one — as written, without
rewriting it. If not, it interviews you about a new one. Then it writes the folder, checks it, shows
you the diff and opens the pull request. It will stop and ask before it writes anything and again
before it opens the PR.

If you would rather do it by hand, [`docs/bot-schema.md`](docs/bot-schema.md) is the full
specification.

## What you are adding

```
bots/<slug>/
  bot.json           the listing and the settings
  instructions.md    the bot's standing job, in plain English
  setup.md           optional — only if the bot needs something installed on a machine
```

`bot.json` carries the name, one-line description, category, the "about" paragraph, three feature
bullets, an example prompt, your GitHub handle, the mascot, and the settings that make the bot real:
`agent`, `permissionMode`, and optionally `model` and tool lists. Every one of those listing fields
is required — a bot missing one renders a broken detail page, so it will not be merged.

`instructions.md` is the substance. It is used verbatim as the bot's instructions, so write it as a
standing job addressed to the agent — "Review the diff against main. Flag bugs and missing tests.
Never modify files." — complete enough to start from a first message that says nothing but "hi".
Keep it under 600 words; it is prepended to every conversation the bot ever has.

## Rules

- **One bot per pull request.** Do not edit another bot's folder in the same PR.
- **Nothing machine-specific.** No absolute paths, usernames, private repo names, tokens or keys.
  This text runs on strangers' computers.
- **No images or binaries.** The mascot is generated from two fields; your avatar comes from your
  GitHub handle.
- **Do not edit `index.json` or `verified.json`.** They are generated and maintained here.
- **Publishable, not personal.** A bot that only works in your own checkout belongs on your machine,
  not in the library. Say what shape of repo it assumes.
- **MIT, all of it.** Opening a pull request licenses your bot to everyone under the
  [MIT licence](LICENSE) that covers this repository. You keep the copyright in what you wrote.
- **Nothing you cannot license that way.** Text lifted from a repository under a copyleft or
  source-available licence, from paid material, or from an employer's private codebase cannot go in.
  Write it yourself, or do not submit it.

## Licensing

There is one licence for the whole library and it is not negotiable per bot.

Do not add a `LICENSE` file, a licence field or a licence header inside `bots/<slug>/` — the root
[`LICENSE`](LICENSE) already covers it, and a second licence in a bot folder will fail review. If
your bot genuinely cannot be MIT, keep it on your own machine; gitbot runs private bots perfectly
well without the library.

## Before you open the pull request

- The JSON parses, and `slug` matches the folder name.
- `features` has exactly three entries.
- `category`, `agent`, `permissionMode` and the mascot fields are spelled exactly as the spec lists
  them.
- No other bot already uses this name or slug.
- You have read `instructions.md` start to finish and it does what the description claims.
- Every word in the folder is yours to license under MIT, and the folder adds no licence file of its
  own.

## What review looks at

Validation catches the mechanical things. Review is for the two questions a schema cannot answer:

1. **Do the instructions do what the listing promises?** A description that oversells is worse than
   a plain one, because people install on the strength of it.
2. **Is the permission mode justified?** `plan` for anything that only reads. `ask-permissions` for
   anything that writes. `auto-approve` means every person who installs your bot has handed it their
   machine — expect to be asked why, and to pair it with a tool allowlist.

Expect a round of comments. Most first submissions need the instructions tightened rather than
rewritten.

## Suggesting one instead

Have an idea but not the time? [Open an issue](https://github.com/gitbot-hq/Library/issues) and
describe what the bot should do.
