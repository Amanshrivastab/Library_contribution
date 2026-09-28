Write release notes for the work merged since the last release. Draft them for the people who use the software, not the people who wrote it, and ask before writing anything to a file.

**Find the range**

- Start right away, even if the first message is just "hi". The range is from the most recent tag reachable from the current branch to `HEAD`. If the user names a tag, a version, a date or a commit range, use that. If the repository has no tags, use the last 30 days of history and say so.
- Read the merge commits and pull request titles first, then the individual commits under them, then the diff only where a message is too vague to explain. Ignore merges of the base branch into feature branches, version bumps, lockfile churn and formatting-only commits.

**Decide what matters**

- Group entries as: breaking changes, new features, improvements, fixes, and, if the project has them, deprecations and security fixes. Leave a group out if it is empty.
- Write each entry as what changed for the user and why they might care, in one sentence, in plain language. "Uploads over 100 MB no longer fail silently" rather than "Fix stream backpressure in upload handler". Merge several commits into one entry when they are one change.
- Put breaking changes first and say what the user has to do about each one.
- Include the pull request or issue number when it is in the commit message. Do not invent one.
- Leave out internal refactors and test-only changes unless they change behaviour.

**Match the repository**

- If there is a `CHANGELOG.md`, `HISTORY.md`, `RELEASES.md` or a `docs/` changelog, follow its heading style, version format, ordering and link style exactly. Insert the new entry where the newest entry belongs, above older ones.
- If there is no changelog file, print the notes in the chat as Markdown and offer to create one.
- Do not decide the version number. If the notes need one and the user has not given it, use a placeholder such as `Unreleased` and say so.

**Report**

- Show the full draft in the chat first. Then, only after the user approves, write it to the file. Finish with the file changed, the range covered, and any commits you left out because you could not tell what they did.

**Rules**

- Never commit, tag, push or create a release. Never change any file other than the changelog.
- Never fetch or pull; work from the history that is already here.
- Quote commit messages faithfully; do not attribute work to people by name unless the changelog already does.
