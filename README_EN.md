# AI Counselor

[简体中文](./README.md) | [English](./README_EN.md)

An AI counseling companion with memory across conversations, built on [OpenCode](https://opencode.ai)'s multi-agent architecture.

This repository provides complete **AI build instructions**. Give them to your AI coding assistant to generate the project, install dependencies, and run the checks. Then use the system in OpenCode.

## Build your own

Open [AI_Counselor_SPEC_EN.md](./AI_Counselor_SPEC_EN.md), copy the entire document, and give it to an AI coding assistant that can create files and run commands:

```text
Build AI Counselor in the current target directory using the complete instructions below.
Create the configuration, plugin, commands, empty records, and dependencies,
then check the result against the checklist in the specification.
Preserve existing README files, build specifications, and Git information.
Do not overwrite conflicting files or existing counseling records.

(Paste the entire contents of AI_Counselor_SPEC_EN.md here.)
```

You can also download or clone this repository and ask your AI to read and follow `AI_Counselor_SPEC_EN.md` in that directory. The specification is self-contained; you do not need any other files from the author's working project.

Use whichever AI coding assistant you prefer to build it. The generated system runs in OpenCode. The [Chinese specification](./AI_Counselor_SPEC.md) is also available. Each edition contains all templates needed to build independently; the English edition includes English agent prompts and record templates.

## How it works

Three agents handle different parts of the process:

| Agent | Responsibility |
|---|---|
| counselor | Talks with you using a person-centered approach supported by CBT. Replies are brief and natural; this agent does not write records. |
| recorder | Updates your profile and session notes from the original transcripts after a conversation. Records faithfully without deep interpretation. |
| analyst | Identifies patterns and changes across sessions, writes analysis reports, and prepares summaries for future conversations. Speculation must be labeled. |

A plugin automatically saves the conversations. Long-term memory lives in Markdown records, which are loaded at the start of a conversation and periodically summarized for future use.

## Everyday use

After building, launch OpenCode in the project directory. Create a new primary session for each new consultation and run:

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

`records/` contains your private counseling material. The build excludes it through `.gitignore`. Do not commit it to GitHub or expose real consultation content in issues, screenshots, or examples.

This is a self-help companion for reflection and personal understanding. It cannot replace licensed psychotherapy or psychiatric care. Its crisis protocol directs users toward professional support when needed. The default hotline numbers are for mainland China; adapt them to your location during the build.

## License

The documentation and build instructions are available under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). You may use, modify, and share them with attribution to the source.
