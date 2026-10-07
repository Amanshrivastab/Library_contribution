Triage sloc-guard content (file size) and structure (counts, depth, naming, companions, placement)
findings in the current GitHub repository. Start on the first message, including greetings.
Use sloc-guard for policy and measurements, semantic analysis for remedies.

Read repository instructions and conventions. Resolve the root, preserve existing changes, and
create a branch before editing. Confirm the GitHub remote and push access. Ask if work cannot
be isolated or required repository/policy information is missing. Never commit to the default
branch, force-push, merge, or include unrelated changes.

Match the installed sloc-guard version to CI's pin. Reproduce CI's command, working directory,
configuration, scope, and baseline. If no CI command exists, run `sloc-guard check` from the root.
Read the effective configuration in full, including inherited presets and remote configuration;
do not silently contradict inherited policy. Use `sloc-guard explain <path>` with matching
options to find winning rules; consult installed-version documentation, not guessed
syntax. Tool/configuration errors block triage. Inspect diagnostics as well as exit status:
warnings, including directories exactly at their limit, are actionable but do not mandate
splitting. With no findings, report and finish.

Inspect code, dependencies, and surrounding layout before editing. Weigh architecture and
maintainability: counts are proxies, not goals. Each resulting module needs a descriptive name
and a responsibility explainable in one sentence. For folders, distinguish meaningful clusters from deliberately
flat registries; reject splits that mostly re-export moved code and merely deepen paths.

Choose per finding:
- Extract cohesive responsibilities behind narrow interfaces; never split by line count or into
  `part1`/`part2`. Directory moves create module boundaries: check exports, Go `internal/`
  visibility and cycles, TypeScript paths/barrels, callers, tests/helpers, build tags,
  generated-file headers, and ownership rules. Update affected references; preserve behavior
  and public contracts. Require a boundary worth documenting.
- Raise a scoped limit when the shape is justified, such as a cohesive parser or flat registry.
  Explain why restructuring worsens the design.
- Exclude only entries unsuited to measurement, such as generated output, fixtures, or vendored
  code. Use `count_exclude` for counting alone; naming, presence, allowlist, and deny checks remain.
- Fix supported naming, companion-file, or placement violations directly; update references
  after renames and confirm artefacts are disposable before deleting.
- Pause before changes that are not trivially safe, too entangled to verify, affect public
  APIs/serialized formats/CLI contracts, or depend on unresolved decisions or unavailable
  verification. Outline the work and ask for the specific decision before proceeding.

For policy changes, choose the narrowest `[[content.rules]]` or `[[structure.rules]]`, include `reason`,
and use future `expires` dates for temporary exceptions. Rules are last-match-wins; the winning
rule's `count_exclude` combines with global exclusions even when limits fall back to globals.
Structure `scope`: `dir` exact, `dir/*` direct children, `dir/**` descendants only, `dir/` includes
the directory and subtree. Justify exemptions before editing; never relax policy after a failed
refactor, raise global limits, disable checks, weaken baseline ratchets, or regenerate baselines
to hide findings. Do not reformat or reorganize unaffected code.

Repeat the same sloc-guard invocation and required build/test/lint/type checks. Compare remaining
findings against the initial results; distinguish pre-existing failures from regressions.
Unverified, regressing, or unresolved changes must not be pushed. Independent verified fixes
may proceed with deferred findings documented.

For verified changes, review the full diff, commit only your work without attribution trailers,
push the branch, and open a PR following repository templates and approval rules. Per finding,
report the winning rule, remedy, architectural/maintenance rationale, module responsibilities
and what crosses new boundaries, exemption reasons/expiry, checks/results, and limitations.
Return the PR link and outcome; never claim unrun checks passed.
