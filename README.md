# Prompt Library

- `(Code)` = needs file-system access
- `(Hybrid)` = chat or CLI
- `(Chat)` = chat only

Two language channels, kept separate. Generated files default to English
whatever language the conversation runs in, and switch only on an explicit
request. The conversation itself follows whatever language you write in.

Four prompts couple the two channels instead: `Advertising (Code)`,
`Document & Promotion (Code)`, `Privacy Policy (Code)` and `Terms of Use
(Code)`. In those the file switches language together with the conversation
(see each prompt's LANGUAGE section). `Advertising (Code)` and
`Document & Promotion (Code)` also take more than one target language at
once, producing one file per language.

## Folder Structure

```txt
Prompt Library/
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
├─ Master (Hybrid)/
│  └─ Master(Chat).md
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

- **`Master(Chat).md`** is the daily-driver base prompt. A mentor and systems architect: root cause first, a forced verdict in comparisons, and verification for anything time-sensitive. It is also the writing reference the whole library is calibrated against.

## Thinking & Planning

- **`Brainstorming And Listing.md`** runs 5 Whys, then Morphological Analysis, then Reverse Thinking, then First Principles, then an optional Systems Thinking and Listing step. One step per turn, with approval each time.
  - Writes: `Primary progress and project structure.md` (optional Step 5 only)
- **`(Coding Only)Multi-step to-do list generator(Chat).md`** turns a coding idea into a task prompt you paste into another AI session. Chat only, no file access. The generated prompt forces a plan-then-step-by-step method with a single approval gate.
- **`(General)Multi-step to-do list generator.md`** does the same for research, writing, planning, analysis and decision work, and decides up front whether the generated prompt needs a verification step.
- **`(Coding Only)Multi-step to-do list generator.md`** is the agent edition. It reads the actual codebase read-only, picks one project, suggests concrete candidate tasks with evidence, then composes one multi-task prompt with an explicit execution order. Output goes to chat, never a file.

## Prompt Engineering

- **`Prompt Developer.md`** is deep prompt QA: three layer scores, `[SYSTEM]` against `[PROMPT]` findings, evidence required for every finding, and a diff report when you re-paste an edited version. An optional Application Mode writes the approved `[SYSTEM]` fixes back to the file.
- **`Problem Generator.md`** (titled "Prompt Audit Template") is the quick version: an A to E finding template, an `/5` score, and a one-to-one solution list, delivered in a single copy-paste block. It runs in two turns, standby then audit.
- **`Prompt Scaler Correction.md`** shortens a prompt with no behavior loss, tightening wording in place. One approval stop, after block segmentation.
  - Writes: `<original-filename> - Shortened.md`
- **`md to xml converter prompt.md`** maps one Markdown prompt onto XML tags and reorders the blocks, with the text preserved word for word.
  - Writes: the converted prompt as a single code block

## Project Documentation

- **`Project Scanner.md`** scans a codebase and fills the 🟢/🟡/🔴 template. Provable facts only, env names not values.
  - Writes: `project.md`
- **`Latest Regulations and Actions.md`** is the changelog template that ships with the project. Newest entry on top.
  - Writes: (template)

## Google Play / Store Compliance

- **`Play Store Fixer.md`** is a two-phase Play Store audit and remediation. It inspects the codebase, plans against live Google requirements, then applies fixes for BLOCKING and REQUIRED findings directly, flagging judgment calls before touching code.
  - Writes: fixes applied to the codebase, with the report in chat

## Legal & Compliance Documents

- **`License Checker.md`** (v7) is a full license and copyright audit covering project files, the whole transitive dependency tree, assets and vendored code. Facts and evidence only, no risk wording.
  - Writes: `LicenseChecked.md` at the project root, or a split set under `docs/licenses/`
- **`License Checker Lite.md`** (v7-lite) is the same audit for a single ecosystem with 150 or fewer transitive dependencies. No batching, no output splitting, no truncation-resume logic.
  - Writes: `LicenseChecked.md`
- **`Licensor.md`** reads the audit report, recommends and applies a **standard** license from `Licenses/` unmodified, and assembles the third-party notices the shipped code requires as a second mandatory deliverable.
  - Writes: `LICENSE`, SPDX headers, the manifest license field, the README license section, and `THIRD-PARTY-LICENSES/`
- **`Licenses/`** holds 50 official license texts as unfilled drafts. `readme.txt` is a Turkish guide with per-license placeholder lists, copyright lines and header snippets.
  - Writes: (reference material, never modified)
- **`License Customizer.md`** is for when no standard license fits: a requirements interview, then a **custom** license draft. It needs legal review.
  - Writes: `LICENSE.md` (bare license text above a hard boundary line, a notes and evidence appendix below it)
- **`spdx.md`** transcribes an audit report into a valid SPDX document or SBOM, then validates it with a real validator. It transcribes only and adds no findings of its own.
  - Writes: `<project-name>.spdx.json` (or the tag-value form)
- **`Privacy Policy.md`** audits the codebase for provable data collection across four phases, including actually running the project, then interviews for what only the data controller knows. It has an update mode when a policy already exists. Conversation and files switch language together.
  - Writes: `privacy-policy.md` (publishable text plus a working-notes zone) and `privacy-policy.audit.md` (internal evidence base)
- **`Terms of Use.md`** reads the repository for evidence, checks the `LICENSE` for contradictions, refers out to the privacy policy, and ties every clause to strong evidence. Conversation and file switch language together.
  - Writes: `Terms.md` (publishable text plus a working-notes zone)
- **`FAQ.md`** writes an end-user FAQ from the project, one decision per turn, mapping every answer back to the artifacts that prove it.
  - Writes: `faq.md` (publishable) and `faq-proof.md` (evidence, coverage maps, gap list)

## Content & Promotion

- **`Creating document texts.md`** produces end-user product documentation from project material: what it is, setup, task-by-task usage, a feature reference, and an interface or CLI reference, with real screenshots or captured CLI output as evidence, never mocked. It is a Markdown skeleton with inline HTML, ready to drop into a doc site. Conversation and files switch language together, and more than one language can be requested at once.
  - Writes: `<ProjectName>/<ProjectName>.md` (or one `<ProjectName>.<lang>.md` per language) plus `<ProjectName>/images/`
- **`Listing promotional texts.md`** produces a short version (roughly 50 to 80 words) and a long version (roughly 250 to 400 words) of intro text per project, for README, portfolio and LinkedIn use. Conversation and files switch language together.
  - Writes: `Promotional Texts.md` (or `<ProjectName> - Promotional Texts.md`)
- **`Create advertising texts.md`** produces benefit bullets, one mechanically-checked tagline, and a long narrative per project. It runs a mandatory market check first, and the long version requires a sourced differentiator and explicit audience framing. Conversation and files switch language together.
  - Writes: `Advert Texts.md` (or `<ProjectName> - Advert Texts.md`)
- **`Suno Prompter.md`** (v18) produces a Suno Custom Mode payload: title, lyrics, styles, exclude styles, and an assumptions note. It knows the per-version character caps and fills every unspecified field itself.

## Prompt Standard

Almost every prompt file follows one structural shape: a single `#` title,
`##` for major sections (`ROLE`, `CONTEXT`, `TASK`, `LANGUAGE`, `SUCCESS
CRITERIA`, `WORKING METHOD`, `COMMUNICATION`, `CONSTRAINTS`, and `EXAMPLES`
where it helps), and `###` for numbered sub-steps like `Phase 1` and
`Phase 2`. Chat-style prompts use `BEHAVIOR` in place of `TASK`, `SUCCESS
CRITERIA` and `WORKING METHOD`. Two files sit outside this shape on
purpose: `md to xml converter prompt.md` is written in the XML tags it
teaches, and `Suno Prompter.md` keeps its own numbered layout.

Every prompt also carries a `COMMUNICATION` section holding one writing
standard: natural prose, no em dash or en dash, one idea per sentence,
paragraphs that each do one job, and examples calibrated so they are
neither too technical to follow nor too shallow to prove anything.

The rule sets themselves, and the skeleton they derive from, live in
`General Prompt Rules files/`. See below.

## Loose Files

All in `General Prompt Rules files/`:

- **`Prompt Formatting Standard.md`** holds the heading, section-vocabulary
  and working-method rules every prompt in this repo is held to, in English.
  It is used both to bring existing files into line and to author new ones.
- **`Writing Style Standard.md`** holds the writing rules: voice,
  punctuation and flow, paragraphs, examples and references. It defines the
  `COMMUNICATION` section every prompt carries, and `Master.md` is its
  worked reference.
- **`Structural Standard.txt`** is the same skeleton condensed to a single
  reference sheet, written in Turkish only.
- **`Language Standart.txt`** is the Turkish instruction note behind the
  language rule. It defines both channel behaviours: files in English with
  the conversation free (the default), and the two channels switching
  together (the four exceptions named at the top of this file).
- **`Community Standart.txt`** is the Turkish note behind the
  conversational-writing rules: plainer and more natural phrasing,
  controlled punctuation and flow, and calibrated examples and references.
  `Master.md` is the worked reference, and `Writing Style Standard.md` is
  the rule set derived from it.
- **`Prompt Standart Reference.txt`** is the kept instruction note this
  library's standardization work is run from.

## CLI Agents

The `(Code)` and `(Hybrid)` prompts are written to run in a CLI coding
agent with file-system access. Tested targets:

- opencode
- cline
- claude code
- gemini
- copilot
