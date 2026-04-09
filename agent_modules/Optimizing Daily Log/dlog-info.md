# DLOG — Daily Activity Log System

A minimal system for recording what you did each day via an LLM CLI. Designed to consume as few tokens as possible while giving you a clean, reviewable activity list at end of day.

---

## How It Works

The LLM silently appends a plain-English line to a flat file after every meaningful action during a session. You never have to ask it to — it just happens. At end of day you run `eod`, review the full list, make any edits you want in the conversation, then save.

---

## Your Two Commands

| Command | When | What happens |
|---------|------|--------------|
| `today dlog` | First prompt of the day | Creates today's log file if it doesn't exist |
| `eod` | When you're done for the day | Loads today's log into context as a table, awaits your instructions |

After `eod` you can do anything with the list — edit, delete, merge, rewrite — just by telling the LLM in plain language. When you're happy, say `save` or `done` and it writes the final version to the EOD folder.

---

## File Structure

```
~/.dlog/
  index                  ← registry of all day files
  days/YYYY-MM-DD        ← live log written during sessions
  eod/YYYY-MM-DD.md      ← final saved output after review
  AGENTS.md              ← LLM instructions (loaded every session)
  dlog-eod.md            ← EOD logic (loaded only on eod command)
  dlog-info.md           ← this file
```

---

## Log File Format

Each line written during the day looks like:

```
001|09:11|initialized project structure
002|14:02|fixed db connection error
003|14:31|wrote migration for meals table
```

Line number, 24h timestamp, plain description. One line per meaningful action.

---

## What Counts as a Meaningful Action

The LLM writes a line after things like creating or editing a file, fixing a bug, completing research, making a decision, or running a script. It does not log clarifying questions, re-reads, or minor back-and-forth.

---

## EOD Flow

```
you:  eod
llm:  DATE — 2026-04-08
      ──────────────────────────────
       001  09:11  initialized project structure
       002  14:02  fixed db connection error
       003  14:31  wrote migration for meals table
      ──────────────────────────────
      3 entries loaded. ready.

you:  [edit, delete, merge, or just say save]
llm:  EOD saved → ~/.dlog/eod/2026-04-08.md
```

If you forgot to run EOD the previous day, `eod` will detect the missing file and offer to load yesterday instead.

---

## Token Footprint

| File | When loaded | Approx tokens |
|------|-------------|---------------|
| `AGENTS.md` | Every session | ~55 |
| `dlog-eod.md` | Only on `eod` | ~80 |
| `dlog-info.md` | Never (wiki only) | — |
