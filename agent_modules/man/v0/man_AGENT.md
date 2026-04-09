param: man
goal: display human-readable info about an agent by name
details-location: ./details.md
input: <name>
exec:
1. scan ~/defined-home-agents/ for {activated_,deactivated_}<name>_AGENTS.md
2. parse details-location from matched file(s)
3. output content at details-location
note: notify user if status=deactivated_
