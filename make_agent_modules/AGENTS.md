# SESSION START
1. Parse VARS.md (KEY=VALUE) from this directory.
2. If any value == `<SET_ME>`: STOP — tell user "Edit VARS.md and set all paths, then restart."
3. Expand `~` in all paths. Store as: AGENTS_VERSIONING_DIR, AGENTS_DEPLOY_DIR, AGENTS_MODULES_DIR.
4. If AGENTS_VERSIONING_DIR or AGENTS_DEPLOY_DIR do not exist: execute INIT.md.

# MODULE CREATION
- Only execute PLAN mode until user confirms ready to execute.
- Offer token-saving suggestions or improvements to the AGENT file in PLAN mode.
- parameter_name: defined per prompt; used as module identity.
- Output file: `{parameter_name}_AGENTS.md` — optimized for LLM, not human reading.
- details-location: separate file/dir with human-readable detail; reference it with minimal tokens in the AGENT file.
- Store all output files in: `{AGENTS_VERSIONING_DIR}/{parameter_name}/v{N}/` (v0 if first version).
- Maintain `{AGENTS_VERSIONING_DIR}/{parameter_name}/CHANGELOG.md` — append on every create/update: datetime, version, brief description.

# DEPLOYMENT
- Use `deploy.sh` (in AGENTS_MODULES_DIR) to deploy, activate, or deactivate modules.
- Deployed files use naming: `activated_{param}_AGENTS.md` or `deactivated_{param}_AGENTS.md`.

# PROMPTS
- User may drop a prompt file in `{AGENTS_MODULES_DIR}/prompts/` and say "execute it", or type a prompt directly.
- Execute the prompt following the rules above.
