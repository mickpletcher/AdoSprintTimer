# Reference Prompts

This directory contains reference-only prompt files.

Files in this folder are kept for documentation, comparison, or historical context.
They are not part of the active prompt sequence in the parent Prompts directory.

The prompt files that drive the actual workflow live one level up in the main Prompts folder.
If a prompt appears in both locations, use the version in the parent directory as the source of truth.

Rules for this folder:

1. Do not treat these files as runnable workflow prompts.
2. Do not include these files in any ordered prompt list.
3. Do not update implementation behavior based on files here unless the parent prompt explicitly references them.
4. Use these files only as supporting reference material.
5. Do not treat compatibility filename aliases in the parent folder as workflow prompts either.

Current intent:

- `05-Implement-Tasks.md` in this folder is only a compact reference version.
- `../05-Implement-Tasks.md` is the active implementation prompt.

If you are following the GitHub Spec workflow for this repository, start from the prompts in the parent Prompts directory and ignore this folder unless you specifically need reference context.

Related note:

- Parent folder compatibility files such as `../Generate-Formal-Spec.md` exist to satisfy legacy path references and are not part of the ordered workflow.
