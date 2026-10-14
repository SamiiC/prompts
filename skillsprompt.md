I want to install a modified version of pstack for both Claude Code and Codex, entirely offline.

I will provide a single text bundle containing 127 files, delimited by:

`========== BEGIN FILE: relative/path ==========`

`========== END FILE: relative/path ==========`

**Your task:**

1. Parse the bundle and reconstruct all files, preserving their original relative paths, contents, and directory structure.
2. Verify that all 127 files were reconstructed successfully. Report any missing, truncated, or malformed files.
3. Inspect the skills, agents, playbooks, references, and supporting scripts to understand their dependencies.
4. Install the skills into my user-level Claude Code and Codex directories so they are accessible across all projects:
   - Claude Code: `~/.claude/skills/` and `~/.claude/agents/`
   - Codex: `~/.agents/skills/`
   - Account for any platform-specific conventions.
5. Ensure the `poteto-mode` skill is discoverable in both tools and can be activated by saying **"use poteto mode"**.

**Important requirements:**

- Do not use Git, npm, npx, internet access, or plugin marketplaces.
- Do not install plugin manifests, startup hooks, or automatic session triggers.
- All agents and subagents must inherit the model selected in the current session. Do not configure or hard-code model names.
- Preserve multi-agent workflows, architecture reviews, debugging, implementation planning, and plan validation.
- Remove any remaining references to GitHub PR automation, automated merging, worktree auditing, or unavailable scripts. Adapt affected playbooks so their workflows remain coherent.
- GitLab merge requests, commits, pushes, and merges are exclusively my responsibility. Never perform these automatically.
- Do not execute bundled scripts without first inspecting them.
- Preserve the intended pstack methodology rather than rewriting or simplifying the skills unnecessarily.
- Back up existing files before making changes. Do not silently overwrite unrelated skills.

**Validation:**

After installation, verify that:

1. Both Claude Code and Codex can discover the installed skills.
2. "Use poteto mode" invokes the correct workflow.
3. Referenced skills, playbooks, and agents resolve correctly.
4. Plan validation works without requiring GitHub tooling.
5. No removed scripts, manifests, model configurations, or hooks are referenced by active workflows.

Fix any installation or reference issues you discover.

Finally, report which files were installed, any changes made, unresolved limitations, and how to invoke poteto mode in both tools.

I will paste the complete bundle next. Wait until you receive it before beginning installation.
