# Optional React and TypeScript conventions

Use this profile only when React and TypeScript are confirmed for the project and code conventions are in scope. Inspect only the instructions, representative code, or configuration needed to verify the convention under consideration; do not scan unrelated areas. Existing project rules and configured tooling take precedence. Select only useful candidates; this profile is not a mandate to rewrite code or introduce a new architecture.

## Reusable candidates

- Name React components in `PascalCase`; put JSX in `.tsx` files. Follow the project's existing file and module casing for non-component code.
- Name custom hooks with the `use` prefix. Keep JSX in components; extract state transitions, effects, or long event flows into a hook when it makes responsibility clearer or enables real reuse. Do not create hooks for trivial one-use logic just to satisfy a pattern.
- Keep a simple component in one file. Add a feature folder or barrel only when multiple related modules or an intentional public API make it useful. Prefer module-level declarations for reusable components; preserve an explicit local convention for nested render helpers and do not refactor working code for style alone.
- Type public component props and shared context/API shapes. Follow the repository's `interface`/`type`, export, and type-file conventions; keep internal types private unless callers need them.
- Use a dedicated context hook with a clear missing-provider error when there is no meaningful fallback and the project uses that pattern. Stabilize a provider value only when identity matters to consumers, and include every reactive dependency.
- Consider compound components when the parent and children form one coherent public API. Do not force the pattern when children are independently useful or it creates hidden coupling.
- Separate genuinely platform-dependent behavior behind an intentional adapter or entry point when the build supports it. Keep platform filenames and dispatch mechanics specific to the project's bundler and runtime.
- Follow the configured test runner and existing test layout. Keep unit, integration, and end-to-end scopes distinct where the project does so; do not impose a directory or suffix convention from an unrelated repository.

## Keep these project-specific

The following details from individual React/TypeScript repositories are not universal defaults: a `.hook.ts` filename suffix; a fixed `Feature/Feature.tsx/useFeature.hook.ts/index.ts` layout; a blanket ban on nested component declarations; a mandatory Context/Provider/hook trio; `export *` barrels; a particular compound-component API; `test/` placement or `*.e2e.ts` naming; platform suffixes such as `.window.ts`, `.linux.ts`, or `.darwin.ts`; and package ownership, SDK boundaries, build commands, IDs, or product architecture. Carry any of them over only when the target project already uses it or explicitly adopts it.

When documenting a project, link its canonical code-convention source and summarize only confirmed, relevant choices. Do not present this profile's suggestions as current implementation facts or user decisions.
