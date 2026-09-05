# Prompt FrameWork

- `(Code)` = needs file-system access
- `(Hybrid)` = chat or CLI ·
- `(Chat)` = chat only.

All prompts write files in English by default; the conversation follows you.
Exception: `Advertising (Code)` and `Document & Promotion (Code)` — output and
conversation switch language together (see each prompt's LANGUAGE section),
and either can be requested in more than one language at once, one file per
language.

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
│  └─ Structural Standard.txt
├─ License (Code)/
│  ├─ License(Do not change this file)/
│  │  ├─ Licenses/                    ← 50 blank license drafts + readme.txt
│  │  └─ Licensor.md
│  ├─ License Checker.md
│  ├─ License Checker Lite.md
│  ├─ License Customizer.md
│  └─ spdx.md
├─ Master (Chat)/
│  ├─ Master.md
│  ├─ Master-Synthesis.md
│  └─ Master1.md
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

- **`Master.md`** — The daily-driver base prompt. Mentor / systems architect: root cause first, forced verdict in comparisons, verifies anything time-sensitive.

## Thinking & Planning

- **`Brainstorming And Listing.md`** — 5 Whys → Morphological → Reverse → First Principles → (opt.) Listing. One step per turn, approval each time.
  - Writes: `Primary progress and project structure.md` (optional Step 5)
- **`(Coding Only)Multi-step to-do list generator(Chat).md`** — Idea → task prompt for a *coding* session elsewhere. Doesn't code, writes the prompt.
- **`(General)Multi-step to-do list generator.md`** — Same, for research / writing / planning / analysis.
- **`(Coding Only)Multi-step to-do list generator.md`** — Same goes for the AI agent.

## Prompt Engineering

- **`Prompt Developer.md`** — Deep prompt QA. Layer scores, `[SYSTEM]` vs `[PROMPT]` findings, evidence required, diff report on re-paste.
- **`Problem Generator.md`** — The quick version: A–E finding template, `/5` score, 1-to-1 solutions.
- **`Prompt Scaler Correction.md`** — Shortens a prompt without behavior loss. One approval stop after block segmentation.
- **`md to xml converter prompt.md`** — One Markdown prompt → XML tags. Text preserved word for word.
  - Writes: converted copies in a separate folder

## Project Documentation

- **`Project Scanner.md`** — Scans a codebase, fills the 🟢/🟡/🔴 template. Provable facts only, env names not values.
  - Writes: `project.md`
- **`Latest Regulations and Actions.md`** — Changelog template that ships with the project. Newest on top.
  - Writes: (template)

## Google Play / Store Compliance

- **`Play Store Fixer.md`** — Two-phase Play Store audit and remediation: inspects the codebase, plans against live Google requirements, then applies fixes for BLOCKING/REQUIRED findings directly, flagging judgment calls before touching code.
  - Writes: fixes applied to the codebase; report in chat

## Legal Documents

- **`License Checker.md`** — Full license/copyright audit — files, transitive deps, assets, vendored code. Facts only, no risk wording.
  - Writes: `LicenseChecked.md` or `docs/licenses/`
- **`License Checker Lite.md`** — Same, for one ecosystem and ≤150 transitive dependencies. No batching, no output-splitting, no truncation-resume logic.
  - Writes: `LicenseChecked.md`
- **`Licensor.md`** — Reads the audit, picks + applies a **standard** license from `Licenses/`, builds third-party notices.
  - Writes: `LICENSE`, SPDX headers, notices
- **`Licenses/`** — 50 official license texts as blank drafts. `readme.txt` = Turkish guide with per-license copyright lines and header snippets.
  - Writes: (source material)
- **`License Customizer.md`** — When no standard license fits: requirement interview → **custom** license draft. Needs legal review.
  - Writes: license draft
- **`spdx.md`** — Audit report → valid SPDX / SBOM, then validated. Transcribes only, adds no findings.
  - Writes: SPDX document
- **`Privacy Policy.md`** — Scans for provable data collection, interviews for the rest. Update mode if a policy already exists.
  - Writes: `Privacy Policy.md`, `privacy-policy.html`, `privacy-summary.txt`
- **`Terms of Use.md`** — Needs source + licence + privacy policy. Governs *use of the product*, never contradicts the other two.
  - Writes: `Terms.md`
- **`FAQ.md`** — A prompt that writes FAQs by looking at the project and asking questions.
  - Writes: `FAQ.md`

## Content & Promotion

- **`Creating document texts.md`** — End-user/product documentation from project material: setup, usage, feature reference, interface/design or CLI reference, screenshots or captured CLI output as evidence (never mocked). Markdown skeleton + inline-HTML hybrid, ready to drop into a doc site.
  - Writes: `<ProjectName>/<ProjectName>.md` (one per extra language) + `<ProjectName>/images/`
- **`Listing promotional texts.md`** — Short (~50-80 words) + long (~250-400 words) promotional/intro text per project, for README/portfolio/LinkedIn use.
  - Writes: `Promotional Texts.md` (or `<ProjectName> - Promotional Texts.md`)
- **`Create advertising texts.md`** — Bullets + a mechanically-checked tagline + a long narrative per project. Long version requires a sourced differentiator and explicit audience framing.
  - Writes: `Advert Texts.md` (or `<ProjectName> - Advert Texts.md`)
- **`Suno Prompter.md`** — Suno Custom Mode payload: title / lyrics / styles / exclude styles + assumptions. Knows the char caps.

## Prompt Standard

Every prompt file in this library follows one structural shape — one
`#` title, `##` for major sections (`ROLE`/`CONTEXT`/`TASK`/`LANGUAGE`/
`SUCCESS CRITERIA`/`WORKING METHOD`/`CONSTRAINTS`), `###` for numbered
sub-steps like `Phase 1`/`Phase 2`. The rule set itself, and the
general skeleton it's derived from, live in `General Prompt Rules
files/` — see below.

## Loose Files

All in `General Prompt Rules files/`:

- **`Prompt Formatting Standard.md`** — The heading/section-vocabulary/
  working-method rules every prompt in this repo is held to (English).
  Used both to bring existing files into line and to author new ones.
- **`Structural Standard.txt`** — The same general skeleton, condensed to a
  single reference sheet, written in Turkish only.
- **`Language Standart.txt`** — The Turkish note behind the language rule: files English, conversation free by default (see the LANGUAGE exception noted at the top for `Advertising (Code)` / `Document & Promotion (Code)`).
- **`Community Standart.txt`** — The Turkish note behind the conversational-writing rules: plainer and more natural phrasing, controlled punctuation and flow, calibrated examples and references (`Master-Synthesis.md` is the worked reference).
- **`Prompt Standart Reference.txt`** — The kept instruction note this library's standardization work is run from.

## Cli Agent Ai

- opencode
- cline
- claude code
- gemini
- copilot
