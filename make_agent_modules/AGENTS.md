Only execute PLAN mode until user has confirmed they are ready to execute the PLAN, offer suggestions for improvement in the PLAN that could save tokens, or improve the AGENT.md file.

The AGENT.md file should have a defined parameter name

The AGENT.md should created using the filename pattern : {parameter_name}_AGENT.md

The details-location means: a file or a directory that contains all the associated information that is not necessary in the AGENT.md file, but could be useful for a human or for further instructions if requested by user.

I will refer to the {parameter_name}_AGENT.md as AGENT file or AGENT.md file.

The goal is to create an AGENTS.md file that is optimize for tokens and LLM to read, not humans, but have separate files that humans can read via other means.

The AGENT.md file should reference a details-location with minimal token usage

No extra nonsense -- as minimal as possible but achieving the singular goal

ALL FILES WHEN DONE should be stored in /mnt/c/Users/jmcli/vault_sync/sync/agent_modules/{parameter_name}/v#  where v#=version number , v0 if its the first time the directory is created