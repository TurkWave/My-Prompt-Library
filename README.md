# Prompt FrameWork

- `(Code)` = needs file-system access
- `(Hybrid)` = chat or CLI ·
- `(Chat)` = chat only.

All prompts write files in English by default, and the conversation follows
you. The exception is `Advertising (Code)` and `Document & Promotion (Code)`,
where output and conversation switch language together (see each prompt's
LANGUAGE section), and either can be requested in more than one language at
once, one file per language.

## Folder Structure

```txt
Prompt FrameWork/
├─ Advertising (Code)/
│  └─ Create advertising texts.md
├─ Brainstorming and Listing (Chat)/
│  └─ Brainstorming And Listing.md
├─ Document & Promotion (Code)/
│  ├─ Creating document texts.md
│  └─ Listing promotional texts.md
├─ FAQ (Code)/
│  └─ FAQ.md
├─ General Prompt Rules files/
│  ├─ Community Standart.txt
│  ├─ Language Standart.txt
│  ├─ Prompt Formatting Standard.md
│  ├─ Prompt Standart Reference.txt
│  ├─ Structural Standard.txt
│  └─ Writing Style Standard.md
├─ License (Code)/
│  ├─ License(Do not change this file)/
│  │  ├─ Licenses/                    (50 blank license drafts + readme.txt)
│  │  └─ Licensor.md
│  ├─ License Checker.md
│  ├─ License Checker Lite.md
│  ├─ License Customizer.md
│  └─ spdx.md
├─ Master (Chat)/
│  └─ Master.md
├─ Multi Step to-do List Generator (Hybrid)/
│  ├─ (Coding Only)Multi-step to-do list generator(Chat).md
│  ├─ (Coding Only)Multi-step to-do list generator.md
│  └─ (General)Multi-step to-do list generator.md
├─ Play Store Fixer (Code)/
│  └─ Play Store Fixer.md
├─ Privacy Policy (Code)/
│  └─ Privacy Policy.md
├─ Project Scanner (Code)/
│  ├─ Latest Regulations and Actions.md
│  └─ Project Scanner.md
├─ Prompt Developer (Chat)/
│  ├─ Md to Xml Converter (Hybrid)/
│  │  └─ md to xml converter prompt.md
│  ├─ Prompt Scaler Correction (Chat)/
│  │  └─ Prompt Scaler Correction.md
│  ├─ Problem Generator.md
│  └─ Prompt Developer.md
├─ Suno (Chat)/
│  └─ Suno Prompter.md
├─ Terms of Use (Code)/
│  └─ Terms of Use.md
└─ README.md
```

---

## Master

- **`Master.md`** is the daily-driver base prompt. A mentor and systems architect: root cause first, a forced verdict in comparisons, and verification for anything time-sensitive. It is also the writing reference the whole library is calibrated against.

## Thinking & Planning

- **`Brainstorming And Listing.md`** runs 5 Whys, then Morphological, then Reverse, then First Principles, then optional Listing. One step per turn, with approval each time.
  - Writes: `Primary progress and project structure.md` (optional Step 5)
- **`(Coding Only)Multi-step to-do list generator(Chat).md`** turns an idea into a task prompt for a *coding* session elsewhere. It doesn't code, it writes the prompt.
- **`(General)Multi-step to-do list generator.md`** does the same for research, writing, planning and analysis.
- **`(Coding Only)Multi-step to-do list generator.md`** does the same for the AI agent.

## Prompt Engineering

- **`Prompt Developer.md`** is deep prompt QA: layer scores, `[SYSTEM]` against `[PROMPT]` findings, evidence required, and a diff report on re-paste.
- **`Problem Generator.md`** is the quick version: an A to E finding template, an `/5` score, and one-to-one solutions.
- **`Prompt Scaler Correction.md`** shortens a prompt without behavior loss. One approval stop after block segmentation.
- **`md to xml converter prompt.md`** turns one Markdown prompt into XML tags, with the text preserved word for word.
  - Writes: converted copies in a separate folder

## Project Documentation

- **`Project Scanner.md`** scans a codebase and fills the 🟢/🟡/🔴 template. Provable facts only, env names and not values.
  - Writes: `project.md`
- **`Latest Regulations and Actions.md`** is the changelog template that ships with the project. Newest on top.
  - Writes: (template)

## Google Play / Store Compliance

- **`Play Store Fixer.md`** is a two-phase Play Store audit and remediation. It inspects the codebase, plans against live Google requirements, then applies fixes for BLOCKING and REQUIRED findings directly, flagging judgment calls before touching code.
  - Writes: fixes applied to the codebase, with the report in chat

## Legal Documents

- **`License Checker.md`** is a full license and copyright audit covering files, transitive dependencies, assets and vendored code. Facts only, no risk wording.
  - Writes: `LicenseChecked.md` or `docs/licenses/`
- **`License Checker Lite.md`** is the same, for one ecosystem and 150 or fewer transitive dependencies. No batching, no output-splitting, no truncation-resume logic.
  - Writes: `LicenseChecked.md`
- **`Licensor.md`** reads the audit, picks and applies a **standard** license from `Licenses/`, and builds third-party notices.
  - Writes: `LICENSE`, SPDX headers, notices
- **`Licenses/`** holds 50 official license texts as blank drafts. `readme.txt` is a Turkish guide with per-license copyright lines and header snippets.
  - Writes: (source material)
- **`License Customizer.md`** is for when no standard license fits: a requirement interview, then a **custom** license draft. It needs legal review.
  - Writes: license draft
- **`spdx.md`** turns an audit report into a valid SPDX or SBOM document, then validates it. It transcribes only and adds no findings.
  - Writes: SPDX document
- **`Privacy Policy.md`** scans for provable data collection and interviews for the rest. It has an update mode if a policy already exists.
  - Writes: `Privacy Policy.md`, `privacy-policy.html`, `privacy-summary.txt`
- **`Terms of Use.md`** needs the source, the licence and the privacy policy. It governs *use of the product* and never contradicts the other two.
  - Writes: `Terms.md`
- **`FAQ.md`** writes FAQs by looking at the project and asking questions.
  - Writes: `FAQ.md`

## Content & Promotion

- **`Creating document texts.md`** produces end-user and product documentation from project material: setup, usage, feature reference, interface and design or CLI reference, plus screenshots or captured CLI output as evidence, never mocked. It is a Markdown skeleton with inline HTML, ready to drop into a doc site.
  - Writes: `<ProjectName>/<ProjectName>.md` (one per extra language) plus `<ProjectName>/images/`
- **`Listing promotional texts.md`** produces a short version (roughly 50 to 80 words) and a long version (roughly 250 to 400 words) of promotional and intro text per project, for README, portfolio and LinkedIn use.
  - Writes: `Promotional Texts.md` (or `<ProjectName> - Promotional Texts.md`)
- **`Create advertising texts.md`** produces bullets, a mechanically-checked tagline, and a long narrative per project. The long version requires a sourced differentiator and explicit audience framing.
  - Writes: `Advert Texts.md` (or `<ProjectName> - Advert Texts.md`)
- **`Suno Prompter.md`** produces a Suno Custom Mode payload: title, lyrics, styles, exclude styles and assumptions. It knows the character caps.

## Prompt Standard

Every prompt file in this library follows one structural shape: one `#`
title, `##` for major sections (`ROLE`, `CONTEXT`, `TASK`, `LANGUAGE`,
`SUCCESS CRITERIA`, `WORKING METHOD`, `COMMUNICATION`, `CONSTRAINTS`), and
`###` for numbered sub-steps like `Phase 1` and `Phase 2`.

Every prompt also follows one writing standard, carried in its own
`COMMUNICATION` section: natural prose, no em dash or en dash, one idea per
sentence, paragraphs that do one job each, and examples calibrated so they
are neither too technical to follow nor too shallow to prove anything.

The rule sets themselves, and the general skeleton they are derived from,
live in `General Prompt Rules files/`. See below.

## Loose Files

All in `General Prompt Rules files/`:

- **`Prompt Formatting Standard.md`** holds the heading, section-vocabulary
  and working-method rules every prompt in this repo is held to, in English.
  It is used both to bring existing files into line and to author new ones.
- **`Writing Style Standard.md`** holds the writing rules: voice,
  punctuation and flow, paragraphs, examples and references. It defines the
  `COMMUNICATION` section every prompt carries, and `Master.md` is its
  worked reference.
- **`Structural Standard.txt`** is the same general skeleton condensed to a
  single reference sheet, written in Turkish only.
- **`Language Standart.txt`** is the Turkish note behind the language rule:
  files in English, conversation free by default (see the LANGUAGE exception
  noted at the top for `Advertising (Code)` and `Document & Promotion (Code)`).
- **`Community Standart.txt`** is the Turkish note behind the
  conversational-writing rules: plainer and more natural phrasing,
  controlled punctuation and flow, and calibrated examples and references.
  `Master.md` is the worked reference, and `Writing Style Standard.md` is
  the rule set derived from it.
- **`Prompt Standart Reference.txt`** is the kept instruction note this
  library's standardization work is run from.

## Cli Agent Ai

- opencode
- cline
- claude code
- gemini
- copilot
