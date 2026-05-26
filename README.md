# conversations

A personal reflection journal, powered by Claude Code as a conversation partner.

## How it works

Two modes, one repo:

1. **Reflection** — Claude asks questions, you talk. Claude doesn't lecture, doesn't summarize, doesn't write anything down during the conversation.
2. **Entry-writing** — When you're done, Claude distills what *you* said into a diary entry in your voice, and saves it to `entries/YYYY-MM-DD.md`.

Threads are yours. Open an entry and a thread file side-by-side in vim, decide what carries forward.

## Daily use

```
cd ~/conversations
claude
```

Then just start talking. Examples:

- "Something's been on my mind about work."
- "I want to think through how work is going."
- "I don't know what I want to talk about, just want to check in."

When you're ready to wrap up, say something like:

- "Let's write the entry."
- "Wrap this up."
- "I'm done — write it up."

Claude will write to `entries/<today>.md` and stop.

## The structure

```
conversations/
├── CLAUDE.md              # how Claude behaves in this repo
├── README.md              # this file
├── entries/               # one file per day, written by Claude in your voice
├── threads/               # recurring topics, maintained by you
└── prompts/
    ├── reflection-partner.md   # the conversation prompt
    └── entry-writer.md         # the distillation prompt
```

## Working with threads

Threads aren't automatic. The idea is that periodically — weekly, or whenever something feels like a pattern — you open recent entries alongside a thread file and pull forward what belongs.

```
vim -O entries/2026-05-25.md threads/career-direction.md
```

Threads can be loose. A bulleted list of moments, a running narrative, whatever helps you. The act of deciding what goes in is itself part of the reflection.

If you want Claude to read a thread at the start of a session for context, paste the content or point at it explicitly:

> "Before we start, here's where I left off on career stuff: [paste or @threads/career-direction.md]"

Claude won't read threads on its own.

## What Claude won't do here

- Read your past entries unless you point at one.
- Update threads.
- Summarize the conversation unless asked.
- Offer advice unless asked.
- "Improve" your words when writing the entry.

If any of these start happening, the prompts in `prompts/` need adjusting. Edit them directly — they're yours.

## Privacy

By default `entries/` is in the `.gitignore`.

## Iterating on the prompts

The prompts in `prompts/` are the most important files here. After a few sessions, you'll notice things — Claude asking questions that feel off, entries that drift from your voice, modes bleeding into each other. When that happens, edit the prompt. It's a living config.

A good rhythm: once a week, re-read a prompt alongside a recent entry and ask whether it produced what you wanted.
