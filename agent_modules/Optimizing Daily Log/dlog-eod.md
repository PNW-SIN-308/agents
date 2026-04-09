# DLOG EOD

## trigger: "eod" or "eod YYYY-MM-DD"
1. determine target date:
   - "eod" → today
   - "eod YYYY-MM-DD" → that date
   - if today's file missing or empty → offer yesterday as fallback
2. read ~/.dlog/index → resolve path for target date
3. read that day file
4. print table:

DATE — YYYY-MM-DD
─────────────────────────────────────
 001  09:11  action description
 002  14:02  action description
─────────────────────────────────────
N entries loaded. ready.

5. stop — await user instructions
6. on "save" or "done" → write whatever the current state of the list is to ~/.dlog/eod/YYYY-MM-DD.md → confirm path
