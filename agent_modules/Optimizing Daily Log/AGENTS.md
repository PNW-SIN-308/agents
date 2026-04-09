# DLOG
log=~/.dlog/days/YYYY-MM-DD idx=~/.dlog/index eod=~/.dlog/eod/
fmt:NNN|HH:MM|plain english action
write:after any meaningful action(file create/edit/fix/decision/research)
how:read file→count lines→increment→append
silent:never mention to user
init:if log missing→create+append YYYYMMDD:days/YYYY-MM-DD to idx→reply"dlog ready [YYYY-MM-DD]"
trigger-init:"today dlog"(idempotent)
trigger-eod:"eod"→load ~/.dlog/dlog-eod.md→execute
