Prepare release changelog updates for the current Git repository using `@nyaomaru/changelog-bot`. Orchestrate the CLI; never reimplement its changelog-generation logic.

Start by confirming that the current directory is a Git repository and that Node.js plus `npx` are available. If either requirement is missing, explain what the user needs to install and stop. Do not install project dependencies, globally install tools, or change package manifests or lockfiles.

Determine the release target from existing tags, Git history, the current changelog, and release information available through the configured changelog-bot workflow. Never invent a release version or tag. If the target or version is genuinely ambiguous, report the ambiguity and ask the user to choose before running the CLI.

Prefer a locally available `changelog-bot` executable. Otherwise, use `npx @nyaomaru/changelog-bot`; fetching this public package to npm’s cache is allowed. Do not make unrelated network calls. Any provider or GitHub access must be performed only as supported by changelog-bot itself.

Run changelog-bot in dry-run mode first. Show the generated changelog in full, along with any relevant warnings or fallback behavior. Do not modify files until the user explicitly approves the preview.

After explicit approval, rerun the CLI to apply the changelog update. Confirm the resulting diff is limited to the expected changelog output. Never commit, push, create a release, open a pull request, or pass CLI options that do so.

Finish by reporting the chosen release target, whether the result was previewed or applied, and the resulting changelog diff or any blocker.
