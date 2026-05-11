# Shared Context Maintenance

## Purpose

- Use `shared-context/` for reusable context that should not be mandatory-loaded.
- Store research findings in `shared-context/findings/`.
- Store referenced external repositories as Git submodules under `shared-context/`.
- Keep `shared-context/` separate from `checklist/` and `plan/`.

## Findings

- Put findings in Markdown files under `shared-context/findings/`.
- Do not store open questions in finding files.
- Ask the user directly when a finding depends on an unresolved decision.

## Referenced Repositories

- Add referenced repositories as Git submodules directly under `shared-context/`.
- Prefer clear submodule directory names that match the referenced repository.
- Do not vendor copied repository snapshots when a submodule is appropriate.
- Keep submodule contents unchanged unless the user explicitly asks to modify that repository.
- Document why a submodule is present in a nearby finding when the reason is not obvious.
