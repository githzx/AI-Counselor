# AI Counselor

[简体中文](./README.md) | [English](./README_EN.md)

An AI counseling companion with memory across conversations, built on [OpenCode](https://opencode.ai)'s multi-agent architecture.

This repository provides complete **AI build instructions**. Give them to your OpenCode to generate the project, install dependencies, and run the checks. Then use the system in OpenCode.

## How to setup

Create a new folder and start OpenCode in it. Open [AI_Counselor_SPEC_EN.md](./AI_Counselor_SPEC_EN.md), copy the entire document, and send to OpenCode. It can follow the instruction and setup automatically.

## How it works

Three agents handle different parts of the process:

| Agent | Responsibility |
|---|---|
| counselor | Talks with you using a person-centered approach supported by CBT. Replies are brief and natural; this agent does not write records. |
| recorder | Updates your profile and session notes from the original transcripts after a conversation. Records faithfully without deep interpretation. |
| analyst | Identifies patterns and changes across sessions, writes analysis reports, and prepares summaries for future conversations. Speculation must be labeled. |

A plugin automatically saves the conversations. Long-term memory lives in Markdown records, which are loaded at the start of a conversation and periodically summarized for future use.

## How to use

After building, launch OpenCode in the project directory. Press Tab to switch to Counselor mode, and run:

```text
/start
```

Talk normally. When you are done, run:

```text
/end
```

For reflection and review, use:

| Command | What it does |
|---|---|
| `/start` | Loads memory records and opens the conversation as the counselor. |
| `/end` | Processes the current consultation's unrecorded messages and updates records and session notes. |
| `/analyze` | Generates an in-depth analysis from transcripts and records. |
| `/weekly` | Generates an analysis, archives the previous summary, and prepares a summary for the next conversation. |

You can have multiple consultations on the same day. Repeating `/end` without new messages does not duplicate records. If you continue talking in the same primary session, another `/end` processes only the new material. Run `/weekly` manually when needed.

## What gets generated

```text
.opencode/
  agents/             Counselor, recorder, and analyst definitions
  commands/           The four everyday commands
  plugins/            Automatic transcripts and source-session identification
records/
  profile.md          Stable background and important relationships
  timeline.md         Key events
  themes.md           Recurring themes
  insights.md         In-depth analysis reports
  transcripts/        Original conversation transcripts
  sessions/           Session notes and processed-message markers
  summaries/          Current summary and archived summaries
```

The build specification contains the complete directory layout, file templates, and plugin behavior requirements. It contains none of the author's actual counseling records.

## Privacy and scope

`records/` contains your private counseling material. The build excludes it through `.gitignore`.

This is a self-help companion for reflection and personal understanding. It cannot replace licensed psychotherapy or psychiatric care. Its crisis protocol directs users toward professional support when needed, adapt them to your location during the build.
