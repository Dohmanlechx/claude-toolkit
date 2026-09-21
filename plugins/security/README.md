# security

Security review tooling for Claude Code.

Today this plugin ships one skill: **`security-grill`**, an interactive security
interrogation that reads your change, then questions you about it until every
concern is resolved.

## Install

```
/plugin marketplace add Dohmanlechx/claude-toolkit
/plugin install security@claude-toolkit
```

## Usage

```
/security:security-grill                                  # the current branch diff vs its base
/security:security-grill 1234                             # a GitHub PR number
/security:security-grill https://github.com/o/r/pull/1234 # a GitHub PR URL
/security:security-grill path/to/file.kt                  # a single file or document
```

With no argument it reviews the current repo's branch diff against its merge-base
with `develop` or `main`. Outside a git repo it demands a target and stops.

## How the grilling works

1. **Silent read.** The reviewer reads the target in full and builds a private
   question list. Nothing is printed during this pass - no findings, no counts, no
   preliminary report.
2. **Interrogation.** One question per turn, in character, hardest first. Vague or
   evasive answers get followed up; answers that contradict the code get the
   contradicting line quoted back at you. New leads become new questions.
3. **Ending.** The interview ends when every question is resolved - or when you say
   the safeword, **`wrap it up`**. Being busy is not an exit; the safeword is.
4. **The document.** A dry, persona-free Q&A record is written to
   `~/.claude/security-reviews/<target-slug>-<YYYY-MM-DD>.md`, outside whatever repo
   you are reviewing, so a description of your weaknesses never gets pushed by
   accident. You are told the path when it lands.

## What it hunts for

Four lenses, no compliance-framework machinery:

| Lens | Examples |
| --- | --- |
| General cyber security | Injection, authz gaps, missing validation at trust boundaries, unsafe defaults, secrets in logs |
| Network security | Cleartext protocols, disabled TLS verification, wildcard listeners |
| Secret handling | Keys in source, keys in config, key rotation, what an attacker gets with the repo |
| AI-generated-code tells | The confident-looking shortcuts an LLM leaves behind |

It reviews on general security merit only. It does not cite ISO 27001, SOC 2 or
PCI-DSS control numbers - the value is in the questions, not in citations that are
either recalled wrong or go stale on the next revision of the standard.

## The reviewer

Grumpy, middle-aged, coding since the early 80s, no flattery. The severity lands on
the artifact - the quoted line, the blast radius, the consequence - never on you. If
a jab is aimed at the author rather than the code, that is a bug in the skill.
