Prepare this machine so GitHub pull requests can be fetched and read.

- `git` is installed and on PATH — confirm with `git --version`.
- The GitHub CLI `gh` is installed — confirm with `gh --version`.
- `gh` is authenticated as the account whose repositories will be reviewed — confirm with `gh auth status`. If it is not authenticated, ask the user to run `gh auth login`, wait for them to say it is done, then check again.
- Confirm the credential can actually reach the API with `gh api user`.

Do not review anything during setup. Preparing the machine is the whole job.
