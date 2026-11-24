# TOFIX

Findings from a code scan on 2026-10-04.

## Medium

- `rsconstruct.toml:1` - lacks the `[build] reject_dot_src_dirs = true` block that every other fleet `rsconstruct.toml` carries so CI enforces the rule; here only the local user config (`~/.config/rsconstruct/config.toml`) applies it, and CI never reads that. Add the block.

## Low

- `rsconstruct.toml:3` - no `[processor.taplo]` stanza, so `rsconstruct.toml` and `.rumdl.toml` are not linted here, unlike every sibling repo; add `[processor.taplo] src_files = [".rumdl.toml", "rsconstruct.toml"]`.
- `README.md:34` - "Keep each file sorted and free of duplicates" is a rule nothing checks (all files are currently sorted in C locale, by hand). Add an explicit processor that runs `LC_ALL=C sort -c -u` over the `*.txt` files so a misplaced or duplicate value fails the build.
