Prepare this machine to run the skill-audit-mcp scanner. It is a standard-library Python script and needs nothing else installed.

- `git` is installed and on PATH — confirm with `git --version`.
- Python 3.8 or newer is installed as `python3` — confirm with `python3 --version`.
- The scanner is checked out at the pinned release, in a folder outside any project, such as `~/.gitbot-tools/skill-audit-mcp`: `git clone --depth 1 --branch v1.2.0 https://github.com/eltociear/skill-audit-mcp <folder>`. If the folder already exists, confirm it is on that tag with `git -C <folder> describe --tags`.
- The scanner runs — confirm with `python3 <folder>/cli.py --help`.
- Tell the user the folder you used, and remember it: the audit runs `cli.py` from there.

Do not audit anything during setup. Preparing the machine is the whole job.
