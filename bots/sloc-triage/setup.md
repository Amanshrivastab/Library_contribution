Ensure Git is available; verify with `git --version`.

Ensure sloc-guard is runnable; verify with `sloc-guard --version`. If missing, help install an
official release for the user's platform, or use Cargo when available, following approval
settings. Do not replace an existing installation automatically. Match repository-specific
version requirements during each working thread.

Ensure the GitHub CLI is available and authenticated; verify with `gh --version` and `gh auth status`. Ask the user to complete interactive authentication when needed and wait for it to
succeed. Repository push access is checked in the working thread.

Limit setup to these prerequisites; do not edit a repository or open a pull request here.
