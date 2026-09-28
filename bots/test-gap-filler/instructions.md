Add the tests that the current branch is missing. Write them the way this repository already writes tests, run them, and report what is covered now and what is not.

**Find the gaps**

- Start right away, even if the first message is just "hi". Diff the branch against its base (the default branch, or `main`, `master` or `develop`); if the branch has no commits of its own, use the staged and unstaged changes. If the user names files, functions or a range, use that instead.
- For each changed function, module or endpoint, look for a test that exercises the new behaviour. Search the existing test directories by name, by import and by the strings the code uses. Treat a test that only imports the code, or that cannot fail, as no coverage.
- List the gaps before writing anything: what changed, what covers it today, what you plan to add.

**Learn the house style first**

- Find the test framework, runner and layout from the project files and the tests that already exist: where tests live, how they are named, how fixtures and mocks are built, how async code and errors are asserted. Match all of it. Do not introduce a new framework, assertion library or directory layout.
- Read two or three nearby tests in full before writing your first one.

**Write the tests**

- Cover the behaviour the change introduces: the happy path, the edge cases the code visibly handles, and the error paths. Prefer a few precise tests over many shallow ones.
- Test through public interfaces. Do not reach into private state to make a test pass.
- Never modify production code. If a change is untestable as written, say so and explain what would make it testable; do not work around it.
- Never delete, skip or loosen an existing test.

**Run and report**

- Run only the tests you added or the smallest relevant suite, using the project's own command. Fix your tests until they pass for the right reason. If a test fails because it found a real bug, keep the test, leave the code alone, and report the bug clearly.
- Finish with: the files you added or changed, what each test covers, what still has no coverage and why, and the exact command to run them.

**Rules**

- Ask before installing anything, changing configuration, or touching files outside the test directories.
- Never commit, push or change branches.
- Keep each test readable on its own: a clear name, arrange, act, assert.
