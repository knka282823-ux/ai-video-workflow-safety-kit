# AI Video Workflow Safety Kit

AI Video Workflow Safety Kit is an open-source safety template for AI-assisted video production workflows.

This project helps creators, educators, small teams, and non-engineers build safer AI content pipelines.

The main goal is simple:

> Prevent runaway AI loops, uncontrolled API spending, unsafe auto-repair, and quality-check failures in AI-assisted video production.

---

## Why this project exists

AI video production workflows often involve many steps:

* topic research
* fact checking
* script writing
* translation
* voice generation
* video generation
* subtitle creation
* social post creation
* quality checks
* publishing

When these steps are connected with AI agents, serious problems can happen.

For example:

* an AI keeps trying to repair the same error again and again
* API costs increase unexpectedly
* logs become too large to review
* the system hides errors instead of explaining them
* scripts, audio, subtitles, and videos become inconsistent
* non-engineers are forced to make technical decisions they do not understand

This toolkit provides safer workflow patterns for those problems.

---

## Core safety concept

This project is built around one important idea:

> AI should help repair workflow problems, but it must not run forever.

Instead of allowing unlimited self-repair, this toolkit uses a safer pattern:

1. Detect the problem
2. Repair once
3. Run checks again
4. If the check passes, continue
5. If the check fails again, stop
6. Show a short human-readable repair report

---

## Key safety rules

### 1. No infinite self-healing

Auto-repair must never run until success.

Unsafe pattern:

```text
fail
repair
fail
repair
fail
repair forever
```

Safe pattern:

```text
fail
repair once
re-check
pass or stop
```

---

### 2. Human-readable short summaries

Large logs should not be shown directly to users.

Instead, the system should generate a short report such as:

```text
Status: FIX_NEEDED

Problem:
The English script does not match the original script in one numeric claim.

File:
scripts/example_script_en.txt

Next action:
Review the suggested repair.
```

---

### 3. Repair in a safe area first

AI should not directly rewrite important production files.

A safer pattern is:

1. Create a repair copy or branch
2. Apply the AI repair
3. Run safety checks
4. Show the result
5. Merge only after approval

---

### 4. Keep script, audio, subtitles, and video aligned

AI video production must check that:

* the translated script matches the original script
* generated audio follows the final script
* subtitles match the audio
* video output matches the intended script
* free and paid versions are not mixed
* publishing assets are consistent

This is especially important when creators are producing content in a language they do not fully understand.

---

### 5. Track cost and retries

Each workflow should record:

* number of AI calls
* retry count
* repair attempts
* estimated cost
* failed checks
* final decision

This helps prevent unexpected API spending.

---

## Planned components

This repository will include simple templates such as:

```text
.github/workflows/safety-gate.yml
scripts/preflight.py
scripts/audit.py
scripts/make_boss_summary.py
scripts/repair_once.py
docs/safety-rules.md
docs/video-workflow-checklist.md
examples/sample_project/
```

---

## Example workflow

```text
User saves a file
↓
GitHub Actions runs safety checks
↓
preflight.py checks required files
↓
audit.py checks risky patterns
↓
AI review checks consistency
↓
repair_once.py suggests one safe repair if needed
↓
make_boss_summary.py creates a short report
↓
User sees only OK / FIX_NEEDED / STOP
```

---

## Example decision format

```text
Status: STOP

Reason:
Audio and subtitles do not match.

Affected file:
output/subtitles_en.srt

Next action:
Regenerate or correct the subtitle file before publishing.
```

---

## Who this project is for

This project is for:

* creators using AI video tools
* educators building AI media workflows
* small teams automating content pipelines
* non-engineers using AI agents
* developers building safer AI automation systems
* teams that need cost-aware AI workflow checks

---

## What this project is not

This project is not a complete video generation platform.

It does not replace tools such as:

* video generators
* voice generators
* translation systems
* editing software
* publishing platforms

Instead, it provides a safety layer around AI-assisted workflows.

---

## Project goals

The project aims to provide:

* safer AI repair patterns
* simple preflight checks
* audit scripts
* GitHub Actions templates
* cost and retry limits
* short human-readable reports
* beginner-friendly workflow safety examples
* consistency checks for script, audio, subtitle, and video workflows

---

## Roadmap

### Phase 1

* Add safety rule documentation
* Add basic preflight check template
* Add basic audit script template
* Add short summary generator

### Phase 2

* Add GitHub Actions safety gate
* Add one-time repair pattern
* Add sample project folder

### Phase 3

* Add script/audio/subtitle consistency examples
* Add cost tracking examples
* Add beginner-friendly setup guide

---

## License

This project is released under the MIT License.

---

## Project status

Early planning stage.

This repository will focus on safety patterns, example scripts, and workflow templates for AI-assisted content production.

Contributions, feedback, and improvement ideas are welcome.
