# TASK: Project Licensing — Analysis, Selection, Implementation

> **What this task is:** it reads a license audit report, works out
> which **standard, off-the-shelf** license fits the project, gets
> the user to choose, and then applies that license using the
> drafts in the `Licenses/` folder — filled in, never rewritten.
> It then assembles the **third-party notices** that the code the
> project redistributes requires it to carry (Section 0.3) — a
> second deliverable, independent of which license was chosen.
> It does not produce the audit report, and it does not author
> license text.

## LANGUAGE
**Two separate channels — never conflate them.** *(This is the complete and only statement of the language rule in this document — it is not repeated in Section 5.)*

- **File output — everything this task WRITES into the project (LICENSE file, SPDX headers, copyright lines, README license section, manifest field values, any file content produced): English by default.** It does NOT follow the audit report's language, nor the language the user writes in. It changes only when the user **explicitly asks** for the file content in another language. Official license texts are always reproduced in their original official form and are never translated, regardless of this setting. The same split applies inside the third-party notices deliverable (Section 0.3): the register's own prose — headings, column labels, explanatory lines — is written in the file-output language, while every reproduced copyright line and every reproduced license text stays byte-for-byte as its author wrote it, in its own language.
- **Conversation — plan presentation, recommendations, questions, approval requests, the Section 6 summary: follows the user.** Use the language the user writes in; switch when the user explicitly asks for another language, or simply starts writing in one. A Turkish report or a Turkish conversation NEVER makes the file output Turkish, and the file-output language never dictates the conversation language.

State the resolved file-output language in one line when presenting the PHASE 1 plan (e.g. "File output language: English — default").

## 0. PRECONDITION (MANDATORY — THE TASK DOES NOT START WITHOUT THIS)
This task REQUIRES a "License Audit Report" — a document produced by
scanning the project's files/dependencies/assets, laying out the
current license status — to have been provided, as a mandatory
precondition.

**Accepted report shapes** (the audit step may emit either):
- **Single file** — `LicenseChecked.md` at the project root.
- **Split set** — `docs/licenses/_index.md` plus one file per
  ecosystem (`npm.md`, `cargo.md`, …). In this shape the report is
  the WHOLE set: `_index.md` carries Sections 1 (incl. 1.1 project
  license declarations, 1.2 copyright holders, 1.3 NOTICE files), 2,
  3 (incl. 3.1 vendored code), 6, 9, and the project-wide part of
  Section 10 (redistribution & attribution inventory — vendored and
  asset rows plus the cross-ecosystem totals); each ecosystem file
  carries Sections 1, 2, 4, 5, 7, 8, 9 and its own Section 10
  dependency rows. **Read every file in the set.** Reading only `_index.md` means the dependency tables
  were never read, and the dependency-compatibility filter in
  PHASE 1/d.1 would then run on nothing — which is worse than not
  running it, because it produces a false clean result. If the link
  table in `_index.md` names a file that is missing or truncated,
  treat that as an absent report for that ecosystem and say so.

- If this report was not provided: do not perform any analysis,
  planning, or assumption. Tell the user directly: the report is
  missing, it must be produced/provided first. Without the report,
  license selection would be evidence-free, assumption-based — this
  would violate the task's "never assume" constraint from the start.
- Raw project files provided instead of the report are also not
  sufficient — this task does NOT produce the report, it only uses
  it. Tell the user they need to generate such a report first via a
  separate license audit/scan step; do not attempt to scan on your
  own.
- **Exception — partial gaps within the report:** if the report
  exists but some fields are missing/insufficient (e.g. a dependency
  list exists but version/license info is missing, or a file table
  exists but part of it wasn't scanned), this does NOT trigger
  Section 0 — if the file list and the basic license status are
  present and only version/dependency detail is missing, this counts
  as a partial gap. If the file list or dependency scan is entirely
  absent, the report is considered invalid and Section 0's "report
  not provided" branch applies. In the partial-gap case, complete the
  missing item in PHASE 1 step (b) by examining the relevant project
  files; which files may be opened and under what triggers is
  governed entirely by Section 5's file-access list (do not reject
  the report).
  Difference: if the report is ABSENT, stop; if the report EXISTS but
  one item is missing, verify that item from the project file (per
  Section 5's triggers) and continue.
- **Exception — a report with no Section 10.** A report produced by
  an older checker version, or by a different tool, may list
  dependencies and assets without the redistribution/attribution
  inventory that Section 0.3 consumes. That is a **partial gap, not
  an absent report**: the dependency and asset tables are there, only
  the per-item `shipped` / `build-only` split and the verbatim
  copyright lines are missing. Derive them yourself in PHASE 1 step
  (b) from the manifest's runtime/dev sections, the build or bundler
  configuration, and the components' own installed license files
  (Section 5 trigger (g)) — deriving them is mandatory, and doing so
  is not "producing the report", it is completing one field of it.
  Say in the plan that the split was derived rather than read, and
  which evidence each derivation rests on. Never skip Section 0.3
  because the report did not hand you the list.
- Proceed to Section 1 once the report has been provided.

**Source priority hierarchy (applies when multiple sources
conflict — regardless of whether it's license text, SPDX
identifier, or compliance rule):** the license's official text /
the licensor's official source > SPDX/OSI license definition >
the project's official repository metadata > package registry
metadata > other sources. If a conflict exists at the same tier
(e.g. two official sources contradict each other), STOP and
report the conflict to the user — do not auto-select.

**Mandatory external verification (real lookups, never from
memory).** Two checks, both performed before the plan is presented:
1. **Draft integrity.** The candidate license's text in
   `Licenses/<SPDX>.txt` is compared against its official source
   (spdx.org/licenses, opensource.org, or the licensor's own site —
   gnu.org, apache.org, mozilla.org, eclipse.org, openfontlicense.org,
   opendatacommons.org, as listed in `Licenses/readme.txt` Section 8).
   If the local draft diverges from the official text in substance,
   **STOP and report it** — per the hierarchy above the official text
   wins, but this task does not silently swap in a downloaded text and
   does not edit the local draft. The user decides.
2. **Compatibility claims.** Any statement that license A is or is
   not compatible with license B is verified against an authoritative
   source (gnu.org/licenses/license-list.html, the licenses' own
   texts, SPDX). Never asserted from memory, never inferred from a
   license's reputation.

If a lookup cannot be performed (no network, source unreachable),
say so explicitly in the plan — "compatibility of X with Y could not
be externally verified" — and do not present the unverified claim as
established fact.

## 0.1 LICENSE SOURCE — THE `Licenses/` FOLDER (SINGLE SOURCE OF TRUTH)

### 0.1.1 The folder is the only source
Every license this task can recommend or apply comes from the
`Licenses/` folder shipped alongside this prompt: 50 license drafts
plus `readme.txt`, the reference guide.

- **File name = SPDX identifier.** `MIT.txt` → `MIT`,
  `Apache-2.0.txt` → `Apache-2.0`, `CC-BY-SA-4.0.txt` →
  `CC-BY-SA-4.0`. The one exception is `Proprietary.txt` (see 0.1.5).
- **A license that is not a file in `Licenses/` cannot be recommended
  and cannot be applied.** If the user names one (`SSPL-1.0`,
  `Elastic-2.0`, `BSD-1-Clause`, `Parity`, …), say plainly that it is
  not in the folder, list the closest available alternatives that
  are, and stop. Do not fetch it from the internet, do not
  reconstruct it from memory, do not approximate it with a similar
  license.
- **Read the actual file before proposing it.** Never describe or
  apply a license from memory when its text is on disk. The
  placeholder list in `readme.txt` is cross-checked against the file
  itself, not trusted blindly.

### 0.1.2 NO CUSTOM LICENSING — ABSOLUTE
This task applies **standard, known, off-the-shelf licenses only.**
Categorically forbidden, with no exception and regardless of who
asks:
- writing a license text, in whole or in part;
- editing, shortening, extending, reordering, modernising or
  "cleaning up" the wording of a draft;
- merging two licenses, or grafting a clause from one onto another;
- adding a rider, exception, carve-out, "commercial use requires
  permission" note, or any custom term to a license file;
- producing a "MIT-like", "modified BSD", or "MIT + no-resale" text.

A license altered by even one word is no longer that license: SPDX
matching breaks, automated scanners misidentify it, and the legal
position becomes undefined. If the user asks for a custom or modified
license, decline that specific request in one sentence, state that
this task only applies unmodified standard licenses, and offer the
closest standard license in `Licenses/`. Do not produce the modified
text "as a draft", "as an example", or "just to show what it would
look like".

### 0.1.3 TEMPLATE INTEGRITY — FILL IN ONLY, NEVER RESTRUCTURE
The draft is copied **byte for byte** and only placeholder fields are
substituted. Five rules, all mandatory:

**(a) Fill the placeholder, delete the brackets.**
Only these are substituted: `[YEAR]`, `[COPYRIGHT HOLDER]`,
`[ORGANIZATION]`, `[SOFTWARE NAME]`, `[EMAIL]`, `[PROJECT URL]`,
`[DEVELOPMENT GROUP]`, `[INSTITUTION]`, `[RESERVED FONT NAME]`,
`[JURISDICTION]`. The brackets go with the placeholder: `[YEAR]`
becomes `2025`, never `[2025]`. Everything else is untouched — not
one word, not one line break, not one blank line, no re-wrapping.
**A bracket is not automatically a placeholder.** Official texts use
brackets for links and cross-references too — `[Notices](#notices)`
in `BlueOak-1.0.0.txt` is a Markdown link, not a field. Substitute
only the ten names listed above, and confirm against the
`Yer tutucular` line of the license's `readme.txt` block before
touching anything.

**(b) Placeholders inside a "how to apply" appendix are NOT filled.**
Several drafts (`Apache-2.0`, `GPL-2.0`, `GPL-3.0`, `AGPL-3.0`,
`LGPL-2.1`, `LGPL-3.0`, `MulanPSL-2.0`, …) carry brackets only in a
trailing instructional appendix (`APPENDIX: How to apply the Apache
License to your work`, `How to Apply These Terms to Your New
Programs`, and equivalents). Those brackets are **part of the
official license text** and stay exactly as they are —
`Copyright [yyyy] [name of copyright owner]`,
`Copyright (C) <year>  <name of author>`. You copy that boilerplate
*out* of the appendix, fill it in, and place it in the **source file
headers**; you never fill it in inside the LICENSE file.
(`Licenses/readme.txt`, Section 2, states this explicitly.)

**(c) The license author's own copyright line is never touched.**
`Copyright (C) 2007 Free Software Foundation, Inc.` in the GNU
drafts, `Copyright (C) 2004 Sam Hocevar` in `WTFPL.txt`, and every
similar line belong to the license document itself, not to the
project being licensed. Changing one corrupts the license text.

**(d) A draft with no placeholders gets nothing added.**
**34 of the 50 drafts have no fillable field in the license text at
all.** For those the LICENSE file is a **verbatim copy** and **no
copyright line is inserted into it** — the copyright notice belongs
in the source file headers and the README section instead.

Do not decide this from memory. `readme.txt` marks it explicitly in
each license's block, and the ÖRNEK 1 heading is the signal:

| ÖRNEK 1 heading in `readme.txt` | Meaning |
|---|---|
| `► ÖRNEK 1 — Lisans dosyasındaki telif satırı (doldurulmuş):` | 16 licenses. The text has a real placeholder; this line **is written into the LICENSE file**, in place of that placeholder. |
| `► ÖRNEK 1 — Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır):` | 34 licenses. **Nothing is written into the LICENSE file.** The line shown is for the source-file header (ÖRNEK 2) and the README note (ÖRNEK 3) only. |

Cross-check the heading against the block's `Yer tutucular` line and
against the draft file itself; all three must agree before you write
anything. Never "helpfully" prepend a `Copyright (c) 2025 …` line to
a placeholder-free LICENSE file — `readme.txt` Section 6 lists that
as a named mistake.

**(e) Nothing but the license text goes in the LICENSE file.**
No explanatory heading, no preamble, no "This project is licensed
under…" sentence, no comment, no attribution footer, no project name
banner, no date stamp. Explanations belong in the README.
(`Licenses/readme.txt`, Section 6, first two entries.)

### 0.1.4 MANDATORY POST-WRITE VERIFICATION
After the LICENSE file is written, verify it against its source draft
before reporting the step complete:
1. Written file and `Licenses/<SPDX>.txt` have the **same line
   count**.
2. A line-by-line comparison shows differences **only** on lines that
   originally contained a `[PLACEHOLDER]`, and on each such line the
   difference is exactly the substituted value.
3. No line was added at the top or the bottom.

State the result explicitly in the step report — e.g. "LICENSE
verified against `Licenses/MIT.txt`: 21 lines both sides, 1 line
differs (line 3, `[YEAR]`/`[COPYRIGHT HOLDER]` substituted)" — never
a bare "done". **If any check fails: revert the file, report what
diverged, and do not proceed** to the remaining implementation steps.

### 0.1.5 SPDX IDENTIFIER NORMALIZATION (file name ≠ manifest value)
The draft's file name is not always the identifier that belongs in a
manifest or an `SPDX-License-Identifier` header.

- **GNU family — the version suffix is mandatory.** SPDX has
  deprecated the bare identifiers. `GPL-2.0.txt` → `GPL-2.0-only` or
  `GPL-2.0-or-later`; likewise `GPL-3.0`, `AGPL-3.0`, `LGPL-2.1`,
  `LGPL-3.0`. **Which one is the user's decision, not yours** — the
  difference is substantive (whether future FSF versions apply). Ask
  it once, together with the license selection, with the consequence
  of each stated in one line. Do not default to either.
  (`Licenses/readme.txt`, Section 6, "Sürüm ayrımını atlamak".)
- **`Proprietary.txt` has no SPDX identifier.** Use
  `LicenseRef-Proprietary` in manifests and headers. It is **not**
  OSI-approved — see Gate 4 in Section 0.2.
- Every other file name is used as-is: `MIT`, `MIT-0`, `Apache-2.0`,
  `ISC`, `0BSD`, `BSD-2-Clause`, `BSD-3-Clause`, `MPL-2.0`,
  `OFL-1.1`, `CC-BY-4.0`, `BlueOak-1.0.0`, `MulanPSL-2.0`,
  `LPPL-1.3c`, `Beerware`, `WTFPL`, `Zlib`, `Unlicense`, …
- The `-only`/`-or-later` choice changes the **manifest field and the
  header text**, not which file is copied — the LICENSE file is the
  folder's draft either way.

### 0.1.6 REFERENCE MAPPING — `Licenses/readme.txt` SECTION 5
`readme.txt` Section 5 holds a numbered reference block `[01]`–`[50]`,
one per license. Once the license is selected, locate its block and
use it — do not invent notice wording.

| readme.txt item | Goes into | Handling |
|---|---|---|
| `Yer tutucular` field | — | The authoritative list of which placeholders this draft has. Cross-check against the file itself. |
| **ÖRNEK 1** — copyright line | Depends entirely on which of the two ÖRNEK 1 headings the block carries | `Lisans dosyasındaki telif satırı (doldurulmuş)` → written **into** the LICENSE draft, in place of its placeholders. `Telif satırı (LICENSE'a YAZILMAZ; ÖRNEK 2/3'te kullanılır)` → **nothing goes into the LICENSE file**; the line is used only in ÖRNEK 2 and ÖRNEK 3. Read the heading before acting (rule 0.1.3d). |
| **ÖRNEK 2** — source file header / notice | Every project-owned source file | Used **verbatim** as the pattern, with the real year / holder / software name substituted, adapted only to the file's comment syntax (`//`, `#`, `/* */`, `<!-- -->`, `;`). The legal wording is never paraphrased, shortened, reordered, or translated. |
| **ÖRNEK 3** — README license note | The project README's license section | Used as the **content model**, then written in the file-output language (see LANGUAGE — English by default). The `readme.txt` samples are written in Turkish; carry over their substance (which license, the one obligation worth naming, the link to the LICENSE file) — not their Turkish wording. SPDX identifiers, license names and URLs inside them are reproduced unchanged. |

Report the block number used, e.g. "reference: `Licenses/readme.txt`
[33] MIT License".

## 0.2 APPLICABILITY GATES (HARD — A REQUESTED LICENSE CAN BE REFUSED)
Some licenses in `Licenses/` are simply wrong for certain projects.
The gates are checked **twice**: before a license enters the
recommendation list, and again before implementation if the user
picks one directly.

**Behaviour when a gate blocks a license the user asked for: STOP —
do not apply it.** State which gate it hit and why, in one or two
sentences, citing the evidence (the project's type, the named
dependency, the `readme.txt` line). Re-present only the licenses that
pass. Never substitute a "closest match" on your own authority.
- Gates marked **ABSOLUTE** are not unlocked by insistence: repeat
  the reason once, and hold. Applying a license the project cannot
  legally or sensibly carry is not a service to the user.
- Gates marked **soft** are warnings: after the warning is given, an
  explicit informed selection by the user is honoured, and the
  warning is recorded in the Section 6 summary.

### Gate 1 — Wrong medium (ABSOLUTE)
| License | Valid for | Never for |
|---|---|---|
| `CC-BY-4.0`, `CC-BY-SA-4.0`, `CC-BY-ND-4.0`, `CC-BY-NC-4.0`, `CC-BY-NC-SA-4.0`, `CC-BY-NC-ND-4.0` | Documentation, articles, media, non-software content | **Source code.** `readme.txt` Section 6 says it outright: CC licenses are not designed for code and carry no patent grant; Creative Commons itself does not recommend them for software. |
| `OFL-1.1` | Font files / font projects | Anything that is not a font |
| `ODbL-1.0` | Databases and datasets | Software |
| `LPPL-1.3c` | LaTeX packages and classes | Anything outside the LaTeX ecosystem |

A project may still use one of these for a **subset** — docs under
`CC-BY-4.0`, bundled fonts under `OFL-1.1` — alongside a real
software license for the code. That is normal and allowed. What is
forbidden is applying them **as the project's software license**.

### Gate 2 — Superseded; legacy maintenance only (ABSOLUTE for new licensing)
`Apache-1.1` and `BSD-4-Clause` carry advertising/endorsement clauses
that modern practice abandoned; `BSD-4-Clause` is additionally
GPL-incompatible for exactly that reason, and `readme.txt` marks
`Apache-1.1` "Yeni projeler için ÖNERİLMEZ". They are applicable only
when the project **already** carries that license and is being
maintained — which must be evidenced from the audit report's
project-level license declarations. Never proposed to a project that
is choosing a license for the first time.

### Gate 3 — No legal certainty (soft; blocked for commercial/organisational use)
`WTFPL` and `Beerware` are joke-origin licenses: no conventional
warranty disclaimer, no patent grant, doubtful enforceability, and
`WTFPL` is not OSI-approved. If the target use case is commercial,
organisational, or "not yet determined", they do not enter the
recommendation list at all. They may be applied only for a personal
or throwaway project **and** on the user's explicit, informed
selection. When the user wants "as free as possible" *with* legal
certainty, offer `0BSD`, `MIT-0`, `Unlicense` or `CC0-1.0` instead.

### Gate 4 — `Proprietary.txt` is not a drop-in license (ABSOLUTE conditions)
`Licenses/readme.txt` Section 9 is unambiguous: it is **not** an OSI
open-source license, it is a **general-purpose contract draft**, it
is **"olduğu gibi kullanılmaya uygun değildir"** (not fit for use as
is), and it **requires legal review**. Therefore:
- It is never the automatic answer to "closed source". For a project
  that is simply not being open-sourced, the correct and usually
  sufficient outcome is **no open-source LICENSE file plus an
  explicit all-rights-reserved statement** — offer that first.
- If the user selects it anyway: fill `[YEAR]`, `[COPYRIGHT HOLDER]`,
  `[JURISDICTION]` and `[EMAIL]` per 0.1.3, and state in the plan
  **and** in the final summary, one line each, that the text is an
  unreviewed template and that an IP lawyer must review it before
  distribution. Never present it as "ready to use".
- `[JURISDICTION]` is **asked of the user**. It is never guessed from
  locale, interface language, or an email domain.

### Gate 5 — Dependency incompatibility (ABSOLUTE)
Technical incompatibilities established by the licenses' own terms —
not judgment calls, and each verified per Section 0's external-
verification rule before being asserted:
- A strong-copyleft dependency (`GPL-2.0`, `GPL-3.0`, `AGPL-3.0`,
  `CECILL-2.1`, `EUPL-1.2`, `OSL-3.0`, `Sleepycat`) linked into the
  distributed work blocks a permissive project license for that
  combined distribution.
- `GPL-2.0-only` + `Apache-2.0` is incompatible (patent-clause
  conflict); `GPL-3.0` + `Apache-2.0` is compatible.
- `GPL` + `CDDL-1.0` and `GPL` + `BSD-4-Clause` are incompatible.
  (`readme.txt` Section 6, "Uyumsuz lisansları birleştirmek".)
- An `AGPL-3.0` dependency in a network-served application extends
  its source-provision obligation to the whole work.
Each exclusion is stated in one sentence naming the specific
dependency, per PHASE 1/d.1 — never a silent drop.

### Gate 6 — Ecosystem/context mismatch (soft — flag, do not block)
`Vim`, `Ruby`, `Python-2.0`, `Sleepycat`, `PostgreSQL`, `MS-PL`,
`MS-RL`, `CDDL-1.0`, `CECILL-2.1`, `EUPL-1.2`, `MulanPSL-2.0`,
`NCSA`, `ECL-2.0`, `AFL-3.0`, `OSL-3.0`, `Artistic-2.0` are tied to a
specific project, vendor, jurisdiction or community. They are not
wrong, but choosing one outside its home context surprises downstream
users and some corporate license scanners. They enter the
recommendation list only when the project has a concrete reason —
Perl → `Artistic-2.0`, EU public sector → `EUPL-1.2`, .NET /
Microsoft ecosystem → `MS-PL`, academic institution → `ECL-2.0` or
`NCSA`, Chinese ecosystem → `MulanPSL-2.0` — and that reason is
stated on the same line. Otherwise prefer the mainstream equivalent.

## 0.3 THIRD-PARTY NOTICES — THE SECOND MANDATORY DELIVERABLE

### 0.3.1 Two obligations, and only one of them is about the project's own code
Selecting a license settles what **others** may do with the code the
project wrote. It settles nothing about what the project already owes
to the code it ships from other people. These are two independent
obligations, and this task carries out both:

- **Outbound** — the LICENSE file, the SPDX headers, the manifest
  field, the README section. Governed by Sections 0.1, 0.2 and the
  PHASE 2 implementation steps.
- **Inbound** — every third-party component the project redistributes
  stays under its own license, and virtually every one of those
  licenses conditions redistribution on carrying the component's
  copyright notice and license text along with it. `MIT`, `ISC`,
  `BSD-2-Clause`, `BSD-3-Clause`, `Apache-2.0`, `Zlib`,
  `BlueOak-1.0.0`, `OFL-1.1`, `CC-BY-*` and every copyleft license
  say so in their own text. Satisfying that is what the
  `THIRD-PARTY-LICENSES/` folder in 0.3.3 is for.

**The inbound obligation does not follow from the outbound choice.**
A proprietary, closed-source, all-rights-reserved application carries
it exactly as much as an `MIT` one — more visibly, if anything, since
nothing else in its distribution discloses the borrowed code. None of
these is a reason to skip the step: "the project is closed source",
"it is only a framework", "it is only a build tool" (that is what the
`shipped` / `build-only` evidence in 0.3.2 decides — never a guess),
"the package is tiny", "everyone ships it".

**Scope of the claim being made.** Reproducing a notice is a
mechanical act: copy what the upstream author wrote. This task does
that and states what it copied. It does not opine on whether the
result makes the project compliant, and it does not give legal
advice — the same limit that governs everything else in this
document.

**If the user removes this deliverable from the plan**, that is
honoured — but it is written down, not quietly dropped: the plan and
the Section 6 summary each record one line, "third-party notices: not
produced at the user's instruction — N redistributed components
remain without a reproduced notice." Silence here would leave the
user believing the licensing work was finished.

### 0.3.2 The redistribution set — what the folder must cover
The input is the audit report's **Section 10 (Redistribution &
Attribution Inventory)**, whose rows already carry the redistribution
status, the notice source path and the verbatim copyright line.

- **In:** every row whose status is `shipped`.
- **In:** every row whose status is `UNCERTAIN`. Attributing a
  component that turns out not to ship costs a paragraph; omitting one
  that does ship defeats the whole deliverable. They go in, and the
  plan states in one line that they were included on that basis and
  that the evidence did not settle whether they ship.
- **Out:** rows marked `build-only`. The exclusion is listed by name
  in the plan and in the folder's `LICENSE.txt`, never applied
  silently — a reader must be able to see what was left out and
  disagree with it.
- **Dedup by `component@version`.** Two versions of the same package
  are two entries: their upstream copyright lines can differ, and
  each version's own shipped text is the one that governs it.
- If the report has no Section 10, derive the set per the Section 0
  exception before going further.
- If the derived set is empty, that is a legitimate outcome: state it
  with its evidence ("0 runtime dependencies, no vendored subtree, no
  third-party asset") and skip 0.3.3–0.3.8. An empty set is asserted
  from evidence, never from not having looked.

### 0.3.3 Output layout (fixed — do not improvise a different one)
```
<project root>/THIRD-PARTY-LICENSES/
├── LICENSE.txt                index + attribution register (0.3.6)
├── <SPDX>.txt                 one file per distinct license in the set
├── <SPDX>.txt
└── NOTICE-<component>.txt     verbatim copy of a component's own NOTICE
```
- File names follow the `Licenses/` folder convention exactly —
  `MIT.txt`, `Apache-2.0.txt`, `BlueOak-1.0.0.txt`, `ISC.txt`. A
  license with no SPDX identifier is named
  `LicenseRef-<component>.txt`.
- `NOTICE-<component>.txt` exists only for components that actually
  ship a `NOTICE` file of their own (report Section 10, field 4).
  Apache-2.0 §4(d) is what makes this necessary: the notice travels
  with the work. It is copied verbatim; nothing is merged into it.
- The folder never contains the project's own LICENSE, and the
  project's own LICENSE never absorbs any of this. They are separate
  files answering separate questions.

### 0.3.4 What goes inside a `<SPDX>.txt` — and how the text is deduplicated
Each `<SPDX>.txt` has two parts, separated by a rule:

**Part A — the components this license covers**, one entry each:
the component name and version, its copyright notice **verbatim**,
and the path the notice was read from. Nothing is normalized here:
not `(c)` vs `©`, not the spelling of a name, not a date range, not a
missing final period.

**Part B — the license terms**, reproduced from a real upstream copy,
complete and unedited, with the name of the component the copy was
taken from and its path recorded on the line above it.

**The deduplication rule, and the check that licenses it.** Upstream
`MIT` files across forty packages are usually the same text with a
different copyright line. Reproducing forty near-identical copies
helps no one; asserting they are identical without looking is worse.
So:
1. Compare the candidate texts **byte for byte, after excluding each
   file's copyright line(s)**. Actually perform the comparison — this
   is a file operation, not an impression.
2. If they match, Part B carries that text **once**, and Part A
   carries every component's own copyright line. The terms are
   reproduced in full; the copyright notices are reproduced in full;
   only redundant repetition of identical terms is dropped.
3. If they do **not** match — a modified clause, an added exception, a
   different license version — they are **separate blocks** inside the
   same file, each with its own Part A entry and its own Part B, and
   the divergence is named in the plan. A component whose license text
   was altered upstream is a fact the user needs to see, not a wrinkle
   to smooth over.
4. State the comparison result in the step report with numbers, e.g.
   "`kleur@4.1.5/license` vs `@capacitor/core@7.6.8/LICENSE`:
   identical after line 1, 21 lines both sides — one shared Part B."

### 0.3.5 Where the reproduced text comes from (and where it never comes from)
Source hierarchy, in order — stop at the first that produces a text:
1. **The component's own license file as installed in this project at
   the resolved version** — the path in report Section 10, field 2
   (`node_modules/<pkg>/LICENSE`, `<pkg>-<ver>.dist-info/LICENSE`, a
   jar's `META-INF/LICENSE`, a vendored subtree's `COPYING`, an
   asset's adjacent `OFL.txt`). Copied byte for byte. This is the
   strongest source available: it is the text that author shipped
   with that exact version.
2. **The component's official repository or registry page at that
   exact version tag** — only when nothing is installed on disk.
   Record the URL and the tag; a fetch without a version is not
   evidence (the same version-lock discipline the audit report uses).
3. **Nothing.** If neither produces a text, the component is recorded
   in `LICENSE.txt` under **"Unresolved — license text not
   obtainable"**, with its SPDX identifier, the evidence that
   identifier rests on, and what was attempted. It is raised in the
   plan and again in the Section 6 summary. An unresolved entry is an
   honest gap; a manufactured one is a false attribution.

**`Licenses/` is not a source for third-party texts.** Those fifty
drafts are unfilled, holder-less templates for licensing *this*
project's own work. Filling `Licenses/MIT.txt`'s
`[YEAR] [COPYRIGHT HOLDER]` with an upstream author's name would
fabricate a notice that author never wrote — and it would be
indistinguishable, in the delivered file, from a real one. Do not do
it under any framing, including "the text is the same anyway".

There is exactly **one** permitted use of the folder here, and it is
read-only: **byte-comparing** a reproduced text against
`Licenses/<SPDX>.txt` to confirm it is the standard license rather
than a modified variant. If that comparison shows a divergence beyond
the copyright/holder line, report it — and still reproduce the text
**as found upstream**, because what the project ships is what the
upstream author wrote, not what the standard says it should have
been.

### 0.3.6 `LICENSE.txt` — the register
Written in the file-output language (LANGUAGE section — English by
default), around content that is never translated:

1. **What this folder is** — one short paragraph: these are the
   licenses and copyright notices of third-party components
   redistributed with this project, reproduced as their authors wrote
   them; the project's own license is the root LICENSE file and is
   not affected by anything here.
2. **The attribution register** — one row per component:
   `component | version | SPDX | copyright notice (verbatim) |
   license text file in this folder | source the notice was read
   from`. Every row in the redistribution set appears exactly once.
   A component whose upstream text carries no copyright line gets
   `no copyright notice in the upstream license text` — that is a
   real and common state, and it is written as such rather than
   filled in from a manifest `author` field.
3. **Excluded as build-only** — the component names and the one-line
   reason, so the exclusion can be inspected and challenged.
4. **Unresolved** (only if 0.3.5 step 3 fired) — component, SPDX id,
   what was tried.
5. **Obligations this folder does not by itself discharge** (only if
   0.3.9 applies) — one line each, quoting the clause that says so.

No legal conclusions, no compliance claims, no recommendations, no
invented generation metadata. A date or a version identifier may be
recorded only if it is a real, verifiable value.

### 0.3.7 Getting the folder into what the user actually distributes
A notices folder that only ever exists in the source tree reaches
nobody. Two placements, both stated in the plan with their paths:

- **Source of truth:** `<project root>/THIRD-PARTY-LICENSES/`.
- **Artifact copy:** wherever this project's distributed artifact can
  carry it, decided from the project's actual build layout — the
  manifest scripts, the bundler/packager configuration, the platform
  project files — never from a habit about "projects like this":
  | Project shape | Where the copy goes |
  |---|---|
  | Web / hybrid app whose build copies a web root | that web root (`www/`, `public/`, `dist/`, `src/assets/`) — the copy step then carries it into the packaged app |
  | Android | `app/src/main/assets/` (or the module's assets dir) |
  | iOS / macOS app | the bundle's resources group |
  | Desktop installer (Electron, Tauri, …) | the packaged resources directory |
  | JVM artifact | `src/main/resources/META-INF/` |
  | Published npm / PyPI / crates package | inside the packaged tree, plus the manifest entry that includes it (`files`, `MANIFEST.in`, `include`) — a file not listed there is not published |
  | Container image | a `COPY` line into the image, at a documented path |
  If the build copies a directory into the artifact (`npx cap copy`,
  a bundler `publicDir`, a Gradle `assets` merge), the copy is placed
  where that step will pick it up, and the plan says which step
  carries it.
- **If the artifact layout cannot be determined from evidence, ask.**
  One question in the PHASE 1 plan, listing the candidate paths found
  and what each would mean. Do not guess a path, and do not skip the
  artifact copy because the answer was not obvious.
- **README pointer** — one line inside the README's license section
  (the same section the outbound step writes), naming the folder and
  what it contains. This is a pointer, not a second register.
- **Wiring a licenses screen into the application's UI is outside
  this task's scope.** State in one line where the file ships in the
  artifact so the user can link to it from their own UI if they want;
  do not write UI code to display it.

### 0.3.8 Post-write verification (mandatory — mirrors 0.1.4)
The folder is not reported complete until all six checks have been
run and their **numeric** results stated. "Created the notices
folder" is not a step report.

1. **Coverage.** Entries in the `LICENSE.txt` register == count of
   `shipped` + `UNCERTAIN` rows in the redistribution set. State both
   numbers. Not equal → not complete.
2. **No orphans, either direction.** Every SPDX identifier in the
   register has a matching `<SPDX>.txt` in the folder; every
   `<SPDX>.txt` in the folder is referenced by at least one register
   entry.
3. **Text fidelity.** Each reproduced license text is byte-compared
   against the source it was copied from; report per file, with line
   counts, as in 0.1.4.
4. **Dedup honesty.** For every Part B shared across components, the
   0.3.4 comparison was actually run and its result is quoted.
5. **Notice fidelity.** Every copyright line in the register is
   present verbatim at the `path:line` recorded next to it.
6. **Artifact copy.** The copy is present at the planned path and
   matches the root folder file-for-file (names and sizes listed).
   If the copy was skipped, the reason is stated here rather than
   omitted.

Any check that fails: say what diverged, and do not report the
deliverable complete.

### 0.3.9 Obligations a notices folder does not by itself discharge
Some licenses in the shipped set ask for more than a reproduced text.
Reproduce the text as normal, and additionally name — one line each,
in the plan and in the Section 6 summary — what remains and which
artifact would satisfy it. Naming what a license's own text requires
is reading, not legal advice; the line quotes the clause and stops
there.

- **`Apache-2.0`** — §4(d): a component's own `NOTICE` contents must
  travel with the distribution. Discharged inside this deliverable by
  the `NOTICE-<component>.txt` copy (0.3.3); if the component ships
  no NOTICE, say so rather than inventing one.
- **`GPL-*`, `LGPL-*`, `AGPL-*`, `MPL-2.0`, `EPL-*`, `CDDL-1.0`,
  `OSL-3.0`, `EUPL-1.2`, `CECILL-2.1`, `MS-RL`, `Sleepycat`** —
  source-provision, written-offer, or same-license obligations that
  no notices file can satisfy. Name the component, the clause, and
  what would satisfy it (published corresponding source, a written
  offer, per-file source availability). Do not draft the offer text
  here.
- **`OFL-1.1`** — the Reserved Font Name restriction and the
  no-standalone-sale condition ride along with the font.
- **`CC-BY-*`** — the attribution format the license itself
  specifies, including the link and the "modified" indication when
  the asset was altered.
- **Modified upstream text** (0.3.5) — the fact that a component's
  license diverges from the standard, so the user can look at it.

This subsection is about **inbound** obligations and runs no matter
which license passed the Section 0.2 gates. Gate 5 decides what the
project may license its own code as; 0.3 is what the project owes
regardless of that answer.

## 1. CONTEXT / DOMAIN
The report is project-specific — it may come back clean (0
findings), or it may contain dependency/asset license conflicts;
do not assume in advance, act according to the report's actual
content.

Your task: determine the appropriate license(s) for the project
by examining this report AND, if needed, the project files
themselves; clarify critical choices with the user; and actually
apply the approved licensing to the project (including which
content goes into which file).

**Project medium (determines Gate 1 in Section 0.2):** software /
font / dataset / documentation-or-content / LaTeX package / mixed.
Derived from evidence — the manifest and ecosystem, the file
extensions dominating the report's file table, the presence of
`.ttf`/`.otf`/`.ufo` sources, a `data/` tree of `.csv`/`.json`
records, a docs-only repository. If the evidence is mixed (code +
docs + bundled fonts), say so and license each part with its own
appropriate license rather than forcing one license across all of
them. If the medium cannot be determined from evidence, ask — do
not assume "software" by default.

**Target use case:** [TO BE FILLED IN BY THE USER: commercial/
closed-source | open source | not yet determined — either is
possible]
If this information was not given and is not explicitly stated
in the report or in prior user input, ASK the user immediately
after reviewing the report (PHASE 1/a) and before starting the
plan draft (PHASE 1/e), as a separate and mandatory stopping
point — do not assume. Do not proceed to PHASE 1/e until an
answer is received; this is an earlier stop, independent of the
plan-approval STOP in Section 4/g. A wrong assumption here
invalidates the entire license selection.

## 2. TASK DEFINITION
1. Review the given license audit report and (if necessary) the
   raw project files.
2. Based on the report's findings (UNCERTAIN files, VIOLATION/
   CONFLICT items if any, dependency licenses and their
   compatibility if any), plus the project's medium and target use
   case, determine the license options appropriate for the project
   — **drawn exclusively from the `Licenses/` folder** (Section
   0.1) and **filtered through the applicability gates** (Section
   0.2).
3. Clarify the critical license choice with the user (see Phase
   1, Analysis Order step). Recommend; never select.
4. Apply the approved license to the project: correct content in
   the correct files (LICENSE file, SPDX headers, manifest field,
   README section, etc. — according to the project's language/
   ecosystem), using the `Licenses/` draft **unmodified except for
   its placeholders** (Section 0.1.3) and the notice wording from
   its `readme.txt` reference block (Section 0.1.6).
5. Verify the written LICENSE against its source draft (Section
   0.1.4).
6. Assemble the third-party notices deliverable (Section 0.3): build
   the redistribution set from the report's Section 10, reproduce
   each component's own license text and copyright notice into
   `THIRD-PARTY-LICENSES/`, place the artifact copy, and run the
   Section 0.3.8 verification. This step is carried out whichever
   license was selected in step 3 — including when the answer was
   "closed source, no open-source license".
7. Summarize all changes made, with provenance (Section 6).

## 3. SUCCESS CRITERIA

**General rule** — the task is complete when ALL of the following
are satisfied:
- [ ] A license audit report existed and was reviewed (Section 0
      precondition met).
- [ ] The selected license does not conflict with the dependency/
      asset licenses identified in the report (if dependencies
      exist), or this step is marked N/A (if no dependencies
      exist).
- [ ] The license status has been clarified for EVERY licensable
      file in the project — no file remains marked "UNCERTAIN"
      without a stated reason (either an SPDX header was added, the
      reason it wasn't was explicitly justified, or the file was
      excluded from implementation scope per the UNCERTAIN-exclusion
      rule below — that exclusion satisfies this criterion, it does
      not violate it). Scope: files are divided into
      the following classes — project source files, third-party/
      vendored files, generated/build files, binary files,
      configuration/metadata files, assets. The project SPDX/
      copyright header is applied only to files owned and
      licensable by the project (typically project source files);
      other classes are outside the "EVERY file" scope and are
      reported with a separate status (their original licenses
      are preserved, or they are marked out of scope).
- [ ] If a file's license status cannot be verified from the
      report or project sources, the UNCERTAIN status is not
      forcibly resolved; the file is excluded from the
      implementation scope, the reason is stated, and the
      necessary evidence is requested from the user.
- [ ] A valid LICENSE file exists at the project root (file name
      per ecosystem convention: `LICENSE`, `LICENSE.txt`, `COPYING`
      for the GNU family) and its content is the `Licenses/` draft,
      not a fabricated, abbreviated or remembered text.
- [ ] **Template integrity verified (Section 0.1.4):** the written
      LICENSE file and `Licenses/<SPDX>.txt` have identical line
      counts, and differ only on lines that originally held a
      `[PLACEHOLDER]`. The verification result is stated
      explicitly, with numbers, in the step report.
- [ ] The selected license passed every applicability gate in
      Section 0.2 — or, for a soft gate, the warning was given and
      the user selected it anyway, and that is recorded.
- [ ] No custom, modified, merged or partially-rewritten license
      text was produced anywhere (Section 0.1.2).
- [ ] The notice wording came from the license's `readme.txt`
      reference block, and the block number is reported.
- [ ] The license field in the manifest file (csproj/
      package.json/pyproject.toml/Cargo.toml, etc., per the
      project's ecosystem) has been filled in — for ecosystems
      without a manifest license field (like Go), this step is
      N/A, skipped with the reason stated.
- [ ] **Third-party notices produced (Section 0.3):**
      `THIRD-PARTY-LICENSES/` exists at the project root with a
      `LICENSE.txt` register and one `<SPDX>.txt` per distinct license
      in the redistribution set — or the deliverable is marked
      "N/A — nothing third-party is redistributed" with the evidence
      for that, or "not produced at the user's instruction" with the
      count of components left without a notice. One of the three,
      never an unmentioned absence.
- [ ] **Every component in the redistribution set appears exactly
      once** in the register, with its copyright line reproduced
      verbatim from a real source at a recorded `path:line`, and a
      pointer to the license text file that covers it.
- [ ] **No third-party license text was synthesized** — not from
      `Licenses/`, not from memory, not by filling a template with an
      upstream author's name (Section 0.3.5). Components whose text
      could not be obtained are listed as Unresolved rather than
      approximated.
- [ ] **Section 0.3.8 verification ran and its six numeric results
      are stated** — coverage count, orphan check, per-file byte
      comparison, dedup comparison, notice fidelity, artifact copy.
- [ ] The artifact copy is placed at a path derived from the
      project's actual build layout, or its absence is explained
      (Section 0.3.7) — and the README license section points at the
      folder.
- [ ] Any obligation the notices folder does not by itself discharge
      (Section 0.3.9) is named in one line, with the clause it comes
      from.
- [ ] No license was actually applied without user approval.
- [ ] The post-implementation summary lists line by line what was
      written to which file — no generic statement like
      "licensing was done."

**Task-specific criteria:** in the Phase 1 plan, add concrete
criteria specific to this project (e.g. "the selected license
does not conflict with [dependency X]'s copyleft condition,"
"if VIOLATION exists in the report, the user was separately
notified before implementation"). Derive these from the initial
review of the report, do not fabricate them out of thin air.

## 4. WORKING METHOD — PLAN THEN STEP BY STEP (MANDATORY)

### PHASE 1 — Review, Plan, Lock
Once the report's existence has been confirmed, before making any
assumption:

a. Review the ENTIRETY of the license audit report (critical
   findings, file table, dependencies, assets, uncertain items,
   conclusion section).
b. If the report is partially insufficient (see Section 0
   exception — e.g. file contents are not in the report, only
   status is), examine the relevant project files and complete
   the missing item.
c. Determine whether dependencies exist or not — this determines
   whether the "dependency license compatibility first filter"
   step below enters the plan (mandatory step if they exist,
   skip this step if not, state in one line in the plan why it
   was skipped: "N/A — 0 dependencies").

c.1 **Build the redistribution set (Section 0.3.2).** From the
   report's Section 10, separate the third-party items into
   `shipped` + `UNCERTAIN` (the set the notices deliverable must
   cover) and `build-only` (excluded, listed by name). If the
   report carries no Section 10, derive the split now from the
   manifest's runtime/dev sections, the build/bundler
   configuration and the components' installed license files, per
   the Section 0 exception and Section 5 trigger (g), and say in
   the plan that it was derived rather than read.
   This step is **independent of step (c)**: it runs for a project
   with zero declared dependencies too, because vendored subtrees
   and third-party assets ship without ever appearing in a
   manifest. Only an evidenced empty set skips 0.3 — and the
   evidence is stated.

d. **Analysis order (the license recommendation is formed in
   this order):**
   1. **Dependency license compatibility first filter.** If the
      project has copyleft (like GPL, AGPL) dependencies, this
      technically restricts which licenses can be selected (e.g.
      distributing under MIT while a GPL dependency is present
      creates a rights violation). Derive this constraint FIRST,
      then reflect it in the recommendation list — if a
      constraint exists, state in one sentence why a license was
      excluded from the list; don't silently drop it.
   2. **Infer from project context:** project **medium** (the
      Section 1 field — software / font / dataset / content /
      LaTeX; this is what Gate 1 keys off, so establish it before
      anything else), project type (library vs. application — a
      library prefers avoiding copyleft, an application can be
      more flexible), target audience (is commercial use expected
      — from the "Target use case" field in Section 1),
      distribution form (will source be published openly, or only
      compiled binaries; is it served over a network, which is
      what makes `AGPL-3.0` relevant). Inference may only be
      made if based on a signal directly evidenced in the report
      or project files (e.g. concrete evidence like an
      "application" folder structure + presence of a web
      framework in the dependency list); if no evidence exists,
      do not infer, ask the user. **If the "Target use case" field
      in Section 1 is explicitly "not yet determined" or the user's
      answer is ambiguous/undecided:** do not narrow the candidate
      list by commercial-use inference; present both permissive
      (e.g. MIT/Apache-2.0) and copyleft-compatible (e.g. GPL-3.0)
      candidates with their trade-offs stated evenly, and flag that
      the recommendation is provisional pending a firmer answer.
   3. **Applicability gates.** Run every candidate through
      Section 0.2 before it reaches the user. A license blocked by
      an ABSOLUTE gate never appears in the list; a license
      blocked by a soft gate appears only with its warning
      attached on the same line. State each exclusion in one
      sentence naming the gate — never drop a license silently.
   4. **Present the recommendation + list together:** First a
      justified recommendation ("I recommend X for these
      reasons"), then briefly list 2–6 genuinely applicable
      license candidates. **Every candidate must be a file that
      exists in `Licenses/`** (Section 0.1.1) — a license not in
      the folder is not a candidate, however suitable it might
      otherwise be. By default 2–4 candidates suffice; 5–6 only
      when meaningful trade-offs exist. If fewer than 2 compatible
      candidates remain (dependency filter in d.1, or the gates in
      d.3), show only the available candidates and state why — do
      not add an incompatible or gate-blocked license just to fill
      the count. For each option, in one line: dependency
      compatibility, copyleft vs. permissive, commercial
      use/patent status. Anchor each line to
      `Licenses/readme.txt` Section 4 (the copyleft/patent/category
      comparison table) rather than to recollection.
   5. **Source the facts, do not recall them.** The copyleft
      strength, patent clause and category of every candidate come
      from `Licenses/readme.txt` Section 4 and the license text
      itself; compatibility claims are externally verified per
      Section 0. If a claim cannot be verified, say so instead of
      asserting it.
   6. The decision stays with the user — at this step you
      recommend, you do not select; the final selection is
      settled at the end of PHASE 1, together with plan approval.
      **Exception, and it is not a selection:** if the user names a
      license blocked by an ABSOLUTE gate, you do not implement it.
      That is a refusal to act, not a substitution — you never pick
      a different license in its place on your own authority.

e. **Plan content — produce a COMPLETE plan consisting of
   numbered, concrete steps.** An actionable plan includes the
   following items (do not add an item that has no counterpart
   in the project):

   1. List the UNCERTAIN files from the report. If a file's
      status cannot be verified from the report or project
      sources, do not forcibly resolve the UNCERTAIN status;
      state the reason for excluding the file from the
      implementation scope and request the necessary evidence
      from the user (see Section 3).
   2. Per the analysis order in step (d), derive the license
      candidates (2–6, default 2–4) and their trade-offs, present
      the recommendation.
   3. [If applicable] Verify dependency license compatibility.
   4. Present the critical license choice to the user (per the
      threshold in the "Interim Changes and Critical Decisions"
      section below). If the user selects an incompatible or
      inapplicable license, halt implementation; prove the reason
      for the incompatibility, re-present only the compatible
      alternatives, and do not change the selection or proceed
      with a default alternative without new user approval.
   5. Derive the implementation steps based on the approved
      license:
      - **LICENSE file:** the source draft
        (`Licenses/<SPDX>.txt`), the file name to be created at the
        project root (per ecosystem convention — `LICENSE`,
        `LICENSE.txt`, or `COPYING` for the GNU family), the exact
        placeholder→value substitutions to be made, and the
        `readme.txt` reference block number. If the draft has no
        placeholders, state that explicitly: "verbatim copy, no
        substitutions, no copyright line added to the LICENSE file"
        (Section 0.1.3d).
      - **SPDX identifier to be used in metadata:** the normalized
        value per Section 0.1.5 — including the `-only` /
        `-or-later` choice for the GNU family, which is asked of the
        user at this point and never defaulted.
      - **SPDX header injection:** which format for which file
        types (e.g. `// SPDX-License-Identifier: MIT`), how many
        files it will affect.
      - **Copyright line injection:** a line in the format
        `Copyright (c) <year> <name>`, in the exact wording of the
        license's `readme.txt` ÖRNEK 1/ÖRNEK 2 block (some
        licenses use `Copyright (C)`, some `Copyright` with no
        mark, some append `All rights reserved.` — follow the
        block, do not normalize).
        **Source order for YEAR/NAME:** (1) the audit report's
        "Copyright Holders Observed" table (Section 1.2), which is
        already evidence-backed — if it lists exactly one holder,
        use it and do not re-derive; (2) if that table is absent,
        empty, or lists more than one holder, fall back to project
        files under Section 5 trigger (e): existing copyright
        headers, the manifest `author`/`authors` field, `AUTHORS`/
        `CONTRIBUTORS`, VCS history. If the YEAR/NAME information
        can be reliably verified this way, do not ask the user —
        use the verified value and report it at plan approval. **YEAR and
        NAME are verified independently, not as one atomic check:**
        if only one of the two cannot be verified, request only
        that one from the user once at this step; if both cannot
        be verified, request both together. Do not substitute an
        unverified YEAR with the current calendar year or any other
        default — an unverifiable YEAR is asked, never assumed,
        consistent with this task's "never assume" constraint. If
        files clearly show different copyright holders
        (e.g. different files already have different `Copyright`
        comments or different author information), do not use a
        single-owner assumption; present the ownership list to
        the user and do not change copyright lines without
        approval. Apply the obtained/verified value together with
        the header to all relevant files in the same step.
      - **Manifest/package file update:** determine the correct
        field per the project's ecosystem:
        - `.csproj` → `PackageLicenseExpression`
        - `package.json` → `"license"`
        - `pyproject.toml` → `[project] license` /
          `license-expression`
        - `Cargo.toml` → `license`
        - `go.mod` — Go has no manifest field, the root
          `LICENSE` alone suffices, skip this step and state why
          it was skipped.
        If multiple manifests exist (multi-language/polyglot
        repo), identify each manifest's ecosystem separately; the
        LICENSE file may be shared, but manifest license fields
        are updated only in their respective ecosystems.
      - **README license section:**
        - If the file is absent, draft a short section to add
          (heading + one-sentence license statement + link to the
          LICENSE file), create the file with only that section.
        - If the file is present, NEVER rewrite or replace the
          file's existing content. Insert the license section as
          a clearly delimited block prepended to the very top of
          the file (e.g. a `## License` heading followed by the
          one-sentence statement + link to the LICENSE file, then
          a horizontal rule `---` separating it from the file's
          existing content) so it reads as a distinct, separable
          section rather than a merged rewrite. If the file
          already contains a license section anywhere in the
          body, do not duplicate it at the top — update that
          existing section in place instead, still without
          touching the rest of the file's content.
      - **Dependency license note (if applicable):** if
        third-party dependencies exist and are listed in the
        report, verify in one line whether their licenses
        conflict with the project license (already filtered in
        step (d), here just reflect it in the plan).
      - **Third-party notices folder (Section 0.3):** the
        redistribution set as counts — how many components are
        `shipped`, how many `UNCERTAIN` and therefore included,
        how many excluded as `build-only` (named) — and the
        distinct licenses across that set, each with the number of
        components carrying it. Then: the exact folder path to be
        created, the `<SPDX>.txt` files it will contain, which
        components will need a `NOTICE-<component>.txt`, the source
        each text will be copied from (installed path or versioned
        URL), any component whose text could not be located, the
        artifact-copy path with the build step that carries it (or
        the question to the user if the layout is not evidenced),
        and the one-line README pointer. If any obligation from
        Section 0.3.9 applies, one line per component naming it.
        This sub-item is part of every plan: it is marked N/A only
        with the evidence that nothing third-party is
        redistributed.
      For each sub-item: **where, what, how** — file path,
      content to be added, format.
   6. Summary step (see Section 6).

f. Add the task-specific criteria from Section 3 to the plan.
g. Present this complete plan to the user and STOP. Do not
   execute any step yet. End the plan with a clear question:
   "Do you approve this plan, or would you like changes?" Await
   user approval/correction. **Plan approval alone is not license
   selection approval** — before PHASE 2 begins, there must be an
   explicitly user-selected license name. Plan approval + explicit
   license selection together authorize the transition to PHASE
   2; if the plan is approved only as a recommendation and the
   license name is not yet settled, PHASE 2 does not begin.
   **Combined-message handling:** if a single user message contains
   both plan approval and an explicit license name/selection, both
   are considered granted and PHASE 2 begins. If the message
   contains only general approval language ("continue," "looks
   good," "approved") without naming a license, PHASE 2 does not
   begin — the license name is requested separately before
   proceeding.

### PHASE 2 — Execute One by One, Testing Each Step
Once the plan is approved, execute the steps one by one, for as
long as they are logically dependent on each other. You may apply
independent, mechanical, low-risk changes together in the same
step (e.g. writing the LICENSE file + injecting SPDX headers into
multiple files, operations with no decision branching between
them) — but state each change separately in the result report.
Steps involving decision branching or that depend on each other
(e.g. manifest detection → manifest update) are not merged. For
each step:
a. State which step you are on and what you will examine/attempt.
b. ACTUALLY examine/check/produce that step — do not reason
   about it abstractly — then report the concrete result (what
   was found, what worked, what didn't) before moving to the next
   step. Create the LICENSE file **by copying
   `Licenses/<SPDX>.txt` and substituting only its placeholders
   (Section 0.1.3), then running the Section 0.1.4 verification and
   reporting its numeric result**; inject the SPDX header +
   copyright line into each target file (placed at the first
   syntactically permissible location in the file; do not break
   or place these below mandatory startup structures required for
   the file to function, such as a shebang (`#!`), an XML/HTML
   declaration, an encoding declaration, or a BOM), update the
   manifest file, add the license section to the README (create
   it if absent, add it in an appropriate place if present) —
   these are concrete production steps, not skippable through
   reasoning. The third-party notices folder is built the same
   way: **open each component's own license file at the
   recorded path and copy it**, run the 0.3.4 comparison before
   sharing a text between components, write `LICENSE.txt` from
   the values actually read (never from the SPDX identifier
   alone), place the artifact copy, then run the Section 0.3.8
   checks and report their six numeric results. Writing this
   folder is a production step of the same standing as the
   LICENSE file — not an optional extra to be dropped once the
   license work looks finished.
c. Only then move to the next numbered step.
Never skip ahead, never silently merge steps. If the user requests
plan changes, update only the requested part and re-present the
plan — never execute an unapproved plan.

### INTERIM CHANGES AND CRITICAL DECISIONS

**Plan level (during PHASE 2 execution):**
- **Minor plan correction** (a step requires a small fix/
  additional check, an ordering change that doesn't change the
  approach): briefly state it, apply the correction, continue —
  do not wait for approval.
- **Major plan change** (a step's finding invalidates the
  original approach, a fundamentally different direction is
  needed): STOP, explain why the original plan is no longer
  valid, propose a revised approach, await user approval.
- **Critical decision points** (a genuine trade-off choice, an
  ambiguous situation with multiple valid directions, an
  unexpected finding with no clear resolution — ESPECIALLY which
  license to select, how to handle VIOLATION/CONFLICT if present
  in the report): STOP and ask the user directly — e.g. "License
  X is more permissive but potentially incompatible with
  dependency Y, license Z is more restrictive but fully
  compatible, which would you like?" — do not silently choose.

**Implementation detail level (secondary decisions — header
format, which files to exclude, manifest field name, etc.):**
decisions at this level do NOT COUNT as critical decision points,
are not asked of the user, and are auto-resolved with the
following logic:
- **If there is a single correct answer** (e.g. if the manifest
  has no license field at all, the field name to add is standard
  — undisputed) → don't build a criteria table, apply directly,
  state the justification in one sentence.
- **If multiple valid approaches exist** (e.g. whether to add the
  header to the top of every file, or only to "original" files —
  both defensible) → break it down as "If X: approach A. If Y:
  approach B," state which applies under which condition, then
  state WHICH one was applied given the project's actual
  condition.
- The choice between these two is made automatically — the user
  is not asked "which would you like," because this is a
  secondary implementation detail, not the license selection
  itself. The distinction comes from the critical/secondary
  divide: license SELECTION and handling of VIOLATION/CONFLICT
  are always asked of the user; implementation details like
  header format are never asked.

## 5. CONSTRAINTS
- No step (including analysis) starts without the report being
  provided — Section 0 is a mandatory precondition (except for
  the partial-gap exception).
- Only open project files in the following cases: (a) the relevant
  entry is missing from the file table, (b) the license identifier
  is missing, (c) the version field is missing for a listed
  dependency, (d) the report has a partial gap per Section 0's
  exception and the missing item requires project-file verification
  to complete PHASE 1 step (b), (e) the copyright HOLDER or YEAR
  needed for the copyright line is not established by the report
  (report Section 1.2 absent, empty, or ambiguous) — manifest
  `author`/`authors` field, existing file headers, `AUTHORS`/
  `CONTRIBUTORS`, and VCS history are all in scope for this
  trigger, or (f) the project type / ecosystem needed for the
  applicability gates (Section 0.2) and the manifest field name is
  not derivable from the report — manifest files, the root
  directory listing, and the README are in scope for this trigger,
  or (g) the third-party notices deliverable (Section 0.3) needs
  something the report does not carry: the redistribution split when
  the report has no Section 10, or a component's own license text,
  `NOTICE`, or verbatim copyright line. In scope for this trigger:
  manifests and lockfiles, build/bundler/packager configuration and
  platform project files (for the `shipped` / `build-only`
  evidence and the artifact path), and the components' own installed
  license documents wherever they live — `node_modules/<pkg>/`,
  `site-packages/`, `vendor/`, a jar's `META-INF/`, a vendored
  subtree, an asset's adjacent license file. Those installed
  documents are the third-party authors' own files, read read-only
  as the source for reproduction; nothing in them is ever treated as
  a statement about this project's own license.
  Do not look at project files without justification outside these
  seven triggers. Reading is always read-only; nothing is modified
  outside the approved implementation steps.
- `Licenses/` and `Licenses/readme.txt` are **not** project files
  and are not governed by the triggers above. They are this task's
  own reference material and are read freely, as often as needed.
- Never assume — verify everything that is verifiable (dependency
  license texts, SPDX identifiers, license compatibility rules) —
  if multiple sources exist, cross-verify per the source priority
  hierarchy in Section 0, report conflicts without hiding them.
- Do not cut corners — no statements like "it's probably MIT," 
  either prove it or mark it UNCERTAIN/as a question.
- Language: governed solely by the LANGUAGE section at the top of
  this document (file output English by default, conversation
  follows the user) — the rule is not restated here.
- User approval MUST be obtained before a license is actually
  written to a file — no LICENSE file or header is written
  without Phase 1 approval.
- The dependency compatibility step is mandatory only if the
  report contains dependencies; if not, this step is skipped but
  explicitly stated in the plan as "N/A — 0 dependencies," not
  silently omitted.
- Do not make the license SELECTION yourself — recommend, the
  decision rests with the user; this constraint follows the same
  principle as "critical decision points" in Section 4 — the
  repetition in both places is intentional.
- Only licenses present in `Licenses/` may be recommended or
  applied, unmodified, filled in per Section 0.1.3. No custom,
  merged, edited or newly-written license text, under any framing
  (Section 0.1.2). **This governs the outbound choice only.** The
  third-party notices deliverable reproduces licenses that are
  already in force on code the project ships; a component's license
  is reproduced from its own upstream text even when that license
  has no file in `Licenses/` (Section 0.3.5). Reproducing an
  existing license is not selecting or authoring one, and the
  folder's fifty drafts are never the source for it.
- The third-party notices deliverable (Section 0.3) is produced for
  every project with a non-empty redistribution set, whichever
  license the user selected and whether or not the project is open
  source. It is skipped only on evidenced emptiness, or on the
  user's explicit instruction — and that instruction is recorded in
  the plan and the summary with the count of components left
  unattributed, never absorbed in silence.
- Never manufacture a third-party copyright notice. A holder, a
  year, or a license text that could not be read from the
  component's own file or its versioned upstream is reported
  Unresolved (Section 0.3.5) — the same "never assume" rule that
  governs the project's own copyright line.
- A license blocked by an ABSOLUTE gate in Section 0.2 is not
  applied, even on request. Refusing it is not the same as choosing
  a different one: state the reason, re-present the passing
  candidates, and wait.
- Do not make assumptions specific to a project language/
  framework; for every project, first identify the project
  structure (manifest file, directory structure), then adapt the
  steps accordingly.

## 6. SUMMARY (Final step of Phase 2)
Once implementation is complete, provide a short, structured
summary:
- Selected license, its normalized SPDX identifier (Section 0.1.5),
  and a one-sentence rationale.
- **Provenance:** the source draft used (`Licenses/<SPDX>.txt`) and
  the reference block consulted (`Licenses/readme.txt` [NN]).
- **Placeholders filled:** each one and the value it received
  (`[YEAR]` → 2025, `[COPYRIGHT HOLDER]` → …), or "none — verbatim
  copy" when the draft had no placeholders.
- **Integrity check result** (Section 0.1.4), with the numbers:
  line counts compared, which lines differed.
- Files created/modified (path + what changed, as a list).
- **Third-party notices (Section 0.3):** the folder path; how many
  components the register covers and how many were excluded as
  `build-only`; the `<SPDX>.txt` files written with the component
  count behind each; any `NOTICE-<component>.txt` copies; the
  artifact-copy path (or why there is none); the Section 0.3.8
  results in numbers; any Unresolved component; and any obligation
  from Section 0.3.9 that remains outside the folder, one line each.
  If the deliverable was skipped, the reason and the count of
  unattributed components, in one line.
- How many files had headers/copyright lines injected.
- Any soft-gate warning the user chose to accept (Section 0.2
  Gates 3 and 6), and the `Proprietary.txt` legal-review notice if
  Gate 4 applied — one line each.
- If anything could not be applied or requires manual user review
  (a dependency license conflict, an out-of-ecosystem step such as
  the manifest being skipped in Go, a file excluded for UNCERTAIN
  status), state it in one line.
The summary is not a long report, it's a "what was done" list —
no repeating rationale, no repeating the plan.
