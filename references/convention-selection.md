# Selecting project conventions

Use this guide when creating or adopting a wiki that needs to preserve working rules. The bundled wiki schema and maintenance procedure are the shared baseline; policies about Git, code style, and tools vary by project.

## Classify before transferring

| Category | Examples | How to use it |
| --- | --- | --- |
| Shared wiki practice | Evidence and scope, decision status, topic reuse, index and log maintenance, conflict handling | Start from the bundled template, then adapt its paths, language, and workflow to the existing project. |
| Repository policy | Branch strategy, commit timing and granularity, message format, merge target, branch cleanup, push/PR boundaries, ignored files | Preserve the project's explicit policy and link its canonical source. Do not turn one project's workflow into a default for another. |
| Technology convention | React component and hook structure, Python module style, database schema practices | Apply only when the stack is established by project instructions, configuration, or source. Use only relevant parts and honor existing conventions. |
| Toolchain and version rule | Package manager, formatter, test runner, build command, platform-specific resolution | Confirm from current project configuration and the relevant version. Do not infer commands or file layouts from another repository. |

For each candidate rule, record whether it is shared, repository-specific, technology-specific, or tool/version-specific. Keep its source and applicability clear. A sample may illustrate a useful pattern without establishing that the current project adopted it. Preserve disagreements and mark unknowns instead of promoting an inference to policy.

## Where the rule belongs

- Put short, repeated agent actions and boundaries in the project's existing instruction entry point.
- Keep detailed code, test, or Git procedures in their canonical project policy documents. Link those documents from `project.md`; do not copy the full rule set into the wiki.
- Keep durable project facts, decisions, evidence, and unresolved questions in topic pages under the established wiki.
- Do not create a second standards document when the project already has a canonical one. Add or split a document only when a real maintenance or navigation need justifies it.

## Version-control policy

When a project has a Git workflow, identify the parts that affect agent actions: branch choice and naming, commit unit and timing, message style, staging scope, merge target, branch cleanup, and whether push, pull request, or deployment is included. Distinguish the written policy from the current branch state and from what the user authorized for this task.

Do not infer automatic branch changes, commits, merges, branch deletion, pushes, or pull requests from a template or example. Follow the host instructions, the project's explicit policy, and the user's narrower request. If a policy is absent or unclear, leave it unspecified in `project.md`; wiki adoption does not create Git authorization. A user's request to record or review a Git policy does not itself request Git mutations.

## Technology profiles

Read only the profile relevant to a confirmed stack. Treat profile items as candidates, not requirements: retain existing project decisions, framework versions, lint/format rules, test layout, package boundaries, and local naming. Do not transfer sample product architecture, paths, package names, commands, or API design to another project. If the stack is absent or the task does not involve project standards, skip the profile.
