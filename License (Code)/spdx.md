# TASK: SPDX Document Generation — Audit Report → Machine-Readable SBOM

> **What this task is:** it reads a completed license audit report and
> **transcribes** its evidence into a valid **SPDX document** (an SBOM):
> packages, files, relationships, license fields, annotations — then
> validates the result with a real validator. It is a *serialization*
> task. The report is the source of truth; SPDX is the target format.
>
> **What this task is NOT:** it does not scan the project (that is the
> License Checker task), it does not select or apply a license (that is
> the Licensor task), and it does not author license text (that is the
> License Customizer task). It produces no license finding of its own,
> and it never turns a report's uncertainty into a conclusion.

## LANGUAGE
**Three separate channels — never conflate them.**

- **Structural SPDX content — identifiers, license expressions, field
  names, enumerated values, file paths, package names, URLs, checksums:
  never translated, never localized, never reformatted.** These are
  machine-readable tokens. `MIT` stays `MIT`, `NOASSERTION` stays
  `NOASSERTION`, `./src/main.c` stays `./src/main.c`, regardless of any
  language setting anywhere in this document.
- **Free-text SPDX content — `CreatorComment`, `PackageComment`,
  `FileComment`, `AnnotationComment`, `LicenseComment`,
  `DocumentComment`: English by default.** This does NOT follow the
  audit report's language, nor the language the user writes in. It
  changes only when the user **explicitly asks** for the comment fields
  in another language. Text quoted verbatim from the report (a
  copyright statement, a conflicting declaration, an UNCERTAIN reason)
  is reproduced **as written in the report** and is never translated —
  quoting is evidence, and translated evidence is no longer evidence.
- **Conversation — plan presentation, questions, approval requests,
  validation results, the Section 6 summary: follows the user.** Use
  the language the user writes in; switch when the user explicitly asks
  for another language, or simply starts writing in one. A Turkish
  report or a Turkish conversation NEVER changes the document's comment
  language, and the comment language never dictates the conversation
  language.

State the resolved comment language in one line when presenting the
PHASE 1 plan (e.g. "Comment-field language: English — default").

## 0. PRECONDITION (MANDATORY — THE TASK DOES NOT START WITHOUT THIS)
This task REQUIRES a **License Audit Report** — the evidence-based
document produced by scanning the project's files, dependencies and
assets. Every field this task writes comes from that report. Without
it, an SBOM would be a list of plausible-looking assertions with no
evidence behind any of them, which is worse than no SBOM at all: a
consumer cannot tell a transcribed fact from a generated guess.

**Accepted report shapes** (the audit step may emit either):
- **Single file** — `LicenseChecked.md` at the project root.
- **Split set** — `docs/licenses/_index.md` plus one file per ecosystem
  (`npm.md`, `cargo.md`, …). In this shape the report is the WHOLE set:
  `_index.md` carries Sections 1 (incl. 1.1, 1.2, 1.3), 2, 3 (incl.
  3.1), 6 and 9; each ecosystem file carries Sections 1, 2, 4, 5, 7, 8
  and 9 for its own tree. **Read every file in the set.** Reading only
  `_index.md` means the dependency tables were never read — and a
  dependency-less SBOM built from a report that *has* dependencies is
  not an incomplete document, it is a false one. If the link table in
  `_index.md` names a file that is missing or truncated, treat that
  ecosystem as unreported and say so; do not emit packages for it from
  any other source.

Branches:
- **Report absent** → do not plan, do not infer, do not scan. Say
  plainly that the audit report is the precondition and must be
  produced first. Do not offer to scan the project yourself; that is a
  different task.
- **Raw project files offered instead of the report** → not sufficient,
  same branch as above. A manifest is a declaration, not an audit: it
  carries no evidence pointer, no verification depth, and no UNCERTAIN
  reasons — exactly the three things every SPDX field in this document
  is anchored to.
- **A pre-existing SBOM offered instead of the report** (`syft` output,
  a CycloneDX file, an older `.spdx.json`) → not a substitute either.
  It may be read as a *cross-check* in PHASE 3 (see the divergence
  rule), never as the source of fields.
- **Partial gaps within the report** → this does NOT trigger the
  "report absent" branch. A missing version on one row, an
  unrecorded parent edge, an asset with no source: these are handled
  by the NOASSERTION discipline (0.2) and recorded as approximations
  (PHASE 3), never by opening project files to fill in the blank on
  your own authority. The single exception is the narrow file-access
  list in Section 5 — checksums and file existence, nothing else.
- Report present → proceed to 0.1.

## 0.1 TARGET FORMAT — SPEC VERSION AND SERIALIZATION (LOCKED IN PHASE 1)
The spec version and serialization are **chosen once, stated in the
plan, and never changed mid-generation.** Mixing 2.3 field names into a
3.0 document (or the reverse) produces a file that validates under
neither.

| Target | Serialization | Default | Notes |
|---|---|---|---|
| **SPDX 2.3** | JSON (`<name>.spdx.json`) | **yes — this is the default** | Widest tool support. Field names below are normative for this task. |
| **SPDX 2.3** | tag-value (`<name>.spdx`) | on request | Same data model, `Tag: value` lines. Used when the consuming tool asks for it. |
| **SPDX 2.2** | JSON or tag-value | on request | Only when a downstream tool is pinned to 2.2. `licenseConcluded`, `licenseDeclared` and `copyrightText` are **mandatory** in 2.2 where 2.3 made them optional — this task emits them either way, so no field changes; only `spdxVersion` does. |
| **SPDX 3.0** | JSON-LD | on explicit request only | A different data model (Element/Artifact graph, `@context`, `CreationInfo` objects, relationships as first-class elements). **Never emit 3.0 from memory.** If the user asks for 3.0, first retrieve the official 3.0 model/schema from spdx.org and build against the retrieved schema; if it cannot be retrieved, say so and offer 2.3 instead. Do not approximate 3.0 by renaming 2.3 fields. |

If the user does not state a target, use **SPDX 2.3 JSON** and say so
in one line in the plan — a default is acceptable here because the
format is a delivery preference, not a fact about the project. (A
default license identifier would be a fact, and is never assumed — see
0.2.)

**Output file.** One document, written at the project root as
`<project-name>.spdx.json` (or `.spdx` for tag-value) unless the user
names a path. **The SPDX document is never split across files** — the
format has no include mechanism, and a split document is an invalid
document. For a monorepo, see the multi-root rule in Section 1.4.

## 0.2 NEVER-INVENT — THE NOASSERTION DISCIPLINE (ABSOLUTE)
An SBOM's value is that every field can be traced to something. The
single failure mode of this task is a field that looks authoritative
and is actually generated. Therefore:

**Every field is either (a) transcribed from the report, (b) computed
from a file that is actually on disk, (c) supplied by the user, or (d)
`NOASSERTION`. There is no fifth source.**

Categorically forbidden, regardless of how plausible the value would
be or who asks:
- **Fabricated checksums.** A SHA1/SHA256 is computed by hashing the
  actual file, or the field is omitted. Never write a hash-shaped
  string. A wrong checksum is undetectable by eye and silently breaks
  every downstream integrity check.
- **Fabricated download locations.** `PackageDownloadLocation` is a URL
  evidenced by the report (the registry link it already recorded) or
  `NOASSERTION`. Never construct `https://registry.npmjs.org/<name>/-/…`
  by pattern from the package name.
- **Fabricated purls or other external references.** An `ExternalRef`
  is written only when the report's evidence establishes the ecosystem
  **and** the exact name/version. Pattern-generated purls are the same
  class of error as pattern-generated URLs.
- **Fabricated suppliers or originators.** `PackageSupplier` /
  `PackageOriginator` come from an evidenced author/organization field
  or from the report's Section 1.2 holders table — otherwise
  `NOASSERTION`. A registry account name is not a supplier unless the
  report recorded it as one.
- **Fabricated license identifiers.** Never "correct" a license the
  report left UNCERTAIN into the license the package "obviously" uses.
  Never resolve a CONFLICT the auditor refused to resolve.
- **Fabricated timestamps.** `Created` is the actual current UTC time,
  read from the system clock (`date -u +%Y-%m-%dT%H:%M:%SZ`), never
  typed from memory, never taken from the conversation's assumed date.
- **Fabricated namespaces.** See the `DocumentNamespace` rule in
  PHASE 2; a domain is never invented.
- **Fabricated relationships.** A dependency edge is written only where
  the report records it. An unrecorded edge is handled by the
  unrecorded-parentage rule (Section 1.3), which states the
  approximation in the document itself.
- **Fabricated validation results.** Never write or say "valid SPDX"
  unless a validator actually ran and passed. See PHASE 3.

**Never silently upgrade a status.** `UNCERTAIN` in the report is
`NOASSERTION` in the document, every time, with the report's reason
carried into the comment field. `CONFLICT` never becomes a concluded
license. This is not conservatism for its own sake: `licenseConcluded`
means *an analyst concluded this*, and no analyst did.

**Never silently drop a row.** Every row in the report's tables becomes
an element in the document, or appears in the PHASE 3 exclusion list
with a reason. Silence is the one unacceptable outcome — a consumer
reading the SBOM cannot see what is missing.

## 0.3 `NONE` vs `NOASSERTION` vs A VALUE (CLOSED DECISION TABLE)
These two are not synonyms and are not interchangeable. `NONE` is a
**positive assertion of absence** — "there is no license here" /
"there is no copyright notice here". `NOASSERTION` is **the absence of
an assertion** — "this was not determined". Writing `NONE` where the
truth is `NOASSERTION` fabricates a finding; writing `NOASSERTION`
where the report positively evidenced absence discards one.

| Situation in the report | License field | Copyright field |
|---|---|---|
| A license is recorded with evidence | the SPDX expression | — |
| A copyright statement is recorded verbatim | — | the statement, **verbatim** |
| Row exists, status `UNCERTAIN` (no evidence, unreachable source, single-source where dual was required, template-only header, private registry) | `NOASSERTION` | `NOASSERTION` |
| Row exists, status `CONFLICT` | `licenseDeclared` = the declared value; `licenseConcluded` = `NOASSERTION` | per evidence, else `NOASSERTION` |
| Report positively evidences that the file/package carries **no** license text and none is claimed (e.g. an explicitly public-domain dedication is *not* this case — that is `CC0-1.0`) | `NONE` | — |
| Report positively evidences that a file carries **no** copyright notice (scanned, header present, no notice) | — | `NONE` |
| The report never covered this item at all | the item is not emitted; it goes in the PHASE 3 exclusion list | — |

The last row matters: `NOASSERTION` means "we looked and could not
determine". Emitting an element the auditor never examined, with every
field `NOASSERTION`, manufactures the appearance of coverage. If it
was not audited, it is not in the document — it is in the exclusion
list.

## 0.4 PROVENANCE BLOCK (MANDATORY — EVERY DOCUMENT, WITHOUT EXCEPTION)
Every document this task writes carries, in `CreatorComment`, a
provenance statement. This is not decoration; it is what lets a
consumer calibrate how much the fields are worth:

> This SPDX document was generated by an AI-assisted process from the
> license audit report `<report path(s)>` dated `<report date>`. License
> and copyright fields are **transcribed from that report**, not
> independently re-verified against upstream sources. Fields the report
> left unresolved are recorded as `NOASSERTION`. `<N>` approximations
> are documented in the element comments. This document has not been
> reviewed by a human.

Rules:
- The `Creator` list always contains a `Tool:` entry naming the
  generating process and this task's version. A `Person:` or
  `Organization:` creator is written **only** from evidence or from
  what the user states about themselves — never inferred from a
  copyright holder name in the report. (A copyright holder is who owns
  the code, not who made the SBOM.)
- If the user asks to remove the provenance statement: decline. It is
  a correctness requirement, not a formatting preference. A document
  whose fields are transcribed but which claims nothing about its own
  provenance reads as independently verified.
- The same statement appears in one line in the chat when the document
  is delivered, and in the Section 6 summary.

## 0.5 LICENSE EXPRESSION RULES
Every license-bearing field carries a **valid SPDX license expression**,
`NONE`, or `NOASSERTION`. Nothing else is legal in these fields — not
"MIT License", not "Apache 2.0", not "see LICENSE", not an empty
string.

**(a) Valid expression grammar.** An expression is: a license ID from
the SPDX License List; a `LicenseRef-<idstring>`; an ID followed by
`WITH <exception-id>` where the exception is on the SPDX Exceptions
List; or several of these joined by `AND` / `OR`, with parentheses for
grouping. Operators are uppercase. `MIT OR Apache-2.0` is valid;
`MIT or Apache-2.0`, `MIT/Apache-2.0`, `MIT, Apache-2.0` are not.

**(b) The report's expression is carried as-is.** If the report
recorded `MIT OR Apache-2.0`, the field is `MIT OR Apache-2.0` — both
options, in that order. **Never collapse a disjunction to one branch.**
In particular, the audit's "risk class follows the most restrictive
option" rule is a *classification* device for the report's own risk
column; it says nothing about which license applies, and it must not
leak into an SPDX field. Collapsing `MIT OR GPL-3.0-only` to
`GPL-3.0-only` states that the recipient's choice was already made.

**(c) Deprecated identifiers are not silently rewritten.** SPDX has
deprecated the bare GNU identifiers: `GPL-2.0`, `GPL-3.0`, `AGPL-3.0`,
`LGPL-2.1`, `LGPL-3.0` each split into `-only` and `-or-later`. The
difference is substantive — whether future FSF versions apply — so it
is **not** a normalization the model performs on its own.
  - If the report's evidence settles it (the quoted license text or
    header says "either version 3 of the License, or (at your option)
    any later version" → `-or-later`; "version 3 only" → `-only`), use
    the settled value and note the evidence in the element comment.
  - If the evidence does not settle it, **ask the user once**, in
    PHASE 1, listing every affected package. Do not default to either
    variant, and do not emit the deprecated bare ID as a compromise —
    a deprecated ID makes the document validate with warnings and
    encodes the ambiguity as if it were a decision.
  - The same rule applies to any other deprecated ID the report
    carries (e.g. `BSD-2-Clause-FreeBSD`, `eCos-2.0`, `Nunit`,
    `wxWindows`): confirm the current replacement against the SPDX
    License List rather than from memory.

**(d) Free-text licenses become `LicenseRef-`, and a `LicenseRef` is
never dangling.** Where the report recorded a custom, proprietary, or
non-derivable license (including its
`Verified (non-structural statement)` rows and its
`LicenseRef-Proprietary-<name>` tags), the document uses the same
`LicenseRef-` identifier — and **every `LicenseRef-` used anywhere in
the document must have a matching entry in
`hasExtractedLicensingInfos` carrying `extractedText`.** The
`extractedText` is the actual license text, obtained from:
  1. the in-project file the report cited as evidence (read it — this
     is an allowed read under Section 5), or
  2. the corresponding draft in the `Licenses/` folder if the report's
     identifier maps to one (e.g. `LicenseRef-Proprietary` →
     `Licenses/Proprietary.txt`), or
  3. the verbatim statement the report quoted, when that statement *is*
     the whole of the license terms (a one-line "All rights reserved."
     notice, for instance) — recorded as-is, with `licenseComment`
     stating that the extracted text is the quoted notice and not a
     full license document.

  If none of the three yields text, **do not emit the `LicenseRef`.**
  Use `NOASSERTION` and record the reason in the element comment. A
  `LicenseRef` with no `extractedText` is a validation error and an
  unresolvable reference for every consumer.
  `LicenseRef-` idstrings follow the same charset as SPDXIDs — letters,
  digits, `.`, `-` — so `LicenseRef-Proprietary-my_lib` becomes
  `LicenseRef-Proprietary-my-lib`.

**(e) `dataLicense` is always `CC0-1.0`.** This is fixed by the spec
for SPDX 2.x and describes the SBOM metadata, not the project. It is
never set to the project's license, and never omitted.

**(f) `AND` is not invented to express uncertainty.** If two sources
disagree, that is a `CONFLICT` → `NOASSERTION` (0.3), not
`A AND B`. `AND` means both licenses apply simultaneously; using it to
mean "one of these, we're not sure which" states something false.

## 1. CONTEXT / DOMAIN

### 1.1 The document model
An SPDX 2.x document is four kinds of thing plus a header:

- **The document itself** (`SPDXRef-DOCUMENT`) — spec version, data
  license, name, namespace, creation info.
- **Packages** — units of distribution: the project itself, each
  dependency, each vendored third-party subtree.
- **Files** — individual files, always belonging to a package.
- **Relationships** — the edges: what describes what, what contains
  what, what depends on what.
- **Annotations** and **extracted licensing info** — the side-channels
  for findings and for non-list licenses.

Everything this task writes is one of these. Nothing in the report is
"summarized" into prose inside the document; the document is not a
report.

### 1.2 Report section → SPDX element (the transcription map)
This is the load-bearing mapping of the whole task. Every report
section has exactly one destination:

| Audit report section | Becomes | Notes |
|---|---|---|
| **1.1** Project-level license declarations | the **root package**'s `licenseDeclared` | Two disagreeing rows = `VIOLATION` → see 1.5. |
| **1.2** Copyright holders observed | the root package's `copyrightText` | Multiple holders → all of them, joined by newlines, **verbatim** as recorded (no normalization of casing, spelling or legal suffix — the audit deliberately did not normalize them, and neither does this task). "None found" → `NOASSERTION`. |
| **1.3** NOTICE files present | `File` entries + `fileComment` noting NOTICE presence | Contents are not interpreted, exactly as in the audit. |
| **2** Critical findings (VIOLATION / CONFLICT) | **Annotations** (`annotationType: OTHER`) on the affected element | See 1.5. Findings never become license values. |
| **3** Project files | `File` entries under the root package | `licenseConcluded`, `licenseInfoInFiles`, `copyrightText` per 0.3. |
| **3.1** Vendored / in-tree third-party code | a **separate Package** per subtree | `CONTAINS` from root. Its license is **never** inherited from the project — that is the whole point of the audit's separate section. |
| **4** Direct dependencies | `Package` per row | `<root> DEPENDS_ON <package>`. |
| **5** Transitive dependencies | `Package` per row, deduplicated by `name@version` | Edges from the "Used by" column; see 1.3. |
| **6** Assets | `File` under the root package by default; a `Package` when the asset arrives as a distributable third-party bundle with its own license file | Decided per row in PHASE 1, stated in the plan. |
| **7.1** Genuine unknowns | already reflected as `NOASSERTION` on their elements | The reason string is carried verbatim into the element comment. |
| **7.2** Soft flags (stale registry metadata) | the element's `packageComment` | The license value is **not** downgraded — a soft flag is a flag, not an unknown. The flag text is carried so the consumer sees it. |
| **8** Inactive code | `File` entries with a `fileComment` marking them inactive | Default is to include them with the label; excluding them is a judgment about what ships, which this task does not make. If the user prefers exclusion, that is a PHASE 1 decision and appears in the exclusion list. |
| **9** Conclusion (counts) | nothing | The counts are re-derived from the emitted elements in PHASE 3 and reconciled against this section. A mismatch is a transcription bug, not a note. |

### 1.3 Relationships — only edges the report evidences
- `SPDXRef-DOCUMENT DESCRIBES <root package>` — always present. A 2.x
  document without a `DESCRIBES` relationship is incomplete.
- `<root> CONTAINS <file>` — for every emitted file.
- `<root> DEPENDS_ON <direct dependency>` — from report Section 4.
- `<parent> DEPENDS_ON <child>` — for transitive rows **whose "Used by"
  column names the parent**. One edge per recorded parent.
- **Unrecorded parentage rule.** If a transitive row has no recorded
  parent, do not invent one and do not guess from ecosystem knowledge.
  Emit `<root> DEPENDS_ON <package>` and attach a mandatory
  `packageComment`: *"Parent edge not recorded in the source audit
  report; attached to the root package as a transitive dependency of
  unrecorded parentage."* This is a documented approximation: it is
  counted in PHASE 3, stated in the provenance block, and listed in the
  Section 6 summary. It is never silent.
- `<root> CONTAINS <vendored package>` — vendored subtrees are
  contained, not depended upon; they ship inside the tree.
- `GENERATED_FROM` — only where the report explicitly records a
  generated/derived asset and its source.
- No other relationship type is emitted. `STATIC_LINK`, `DYNAMIC_LINK`,
  `BUILD_DEPENDENCY_OF`, `DEV_DEPENDENCY_OF` and friends encode build
  facts the audit does not establish; asserting them from a manifest's
  `devDependencies` key is an inference, and inference is out of scope
  unless the report itself recorded the distinction (npm/cargo reports
  often do — if the report has a dependency-kind column, use
  `DEV_DEPENDENCY_OF` / `OPTIONAL_DEPENDENCY_OF` / `TEST_DEPENDENCY_OF`
  accordingly and say so in the plan).

### 1.4 Multi-root (monorepo) shape
When the report is a split set covering several ecosystems, decide in
PHASE 1 and state the choice:
- **One document, multiple root packages** (default) — one package per
  ecosystem workspace, each `DESCRIBES`-related to the document, each
  with its own dependency subgraph. Preferred: it keeps the repository
  representable in a single file, which is what the format expects.
- **One document per ecosystem** — only when the user needs separately
  consumable SBOMs (e.g. per-artifact publishing). Each document gets
  its own unique `documentNamespace`; they are not fragments of one
  document and must not cross-reference by bare SPDXID (that requires
  `ExternalDocumentRef`, which this task emits only if the user asks
  for the linked shape and the namespaces are known).

### 1.5 Findings are recorded as annotations, never as values
The audit's `VIOLATION` and `CONFLICT` items are contradictions between
sources. SPDX has exactly one honest place for them:

```
Annotator: Tool: <this task>
AnnotationDate: <ISO 8601 UTC>
AnnotationType: OTHER
SPDXREF: <the element the finding concerns>
AnnotationComment: <the finding, restated factually, naming BOTH sources verbatim>
```

- `annotationType: REVIEW` is **not** used — it asserts that a review
  occurred. None did.
- The annotation restates the two contradicting sources and nothing
  else. No severity, no "risk", no recommendation, no adjective. This
  is the same discipline the audit itself operates under, and it
  survives the format change: an SBOM that scores findings is asserting
  a legal judgment its evidence does not support.
- A `VIOLATION` at project level annotates `SPDXRef-DOCUMENT` **and**
  forces the root package's `licenseConcluded` to `NOASSERTION`, since
  the project's own declarations contradict each other.

### 1.6 Audit status → license fields (the core mapping)
`licenseDeclared` is *what the package's own metadata says*.
`licenseConcluded` is *what an analyst concluded after review*. This
task concludes nothing the report did not already conclude on evidence,
so the two fields diverge exactly where the audit's verification
diverged.

| Audit status (closed set) | `licenseDeclared` | `licenseConcluded` | Mandatory comment content |
|---|---|---|---|
| `Verified (registry)` — Class 1 | the report's SPDX expression | same expression | "Single-source verification (registry declaration), audit Class 1." |
| `Verified (registry, stale-unverified)` | the report's SPDX expression | same expression | the stale flag, carried verbatim from report Section 7.2 |
| `Verified (dual-source)` — Class 2/3 | the registry-declared expression | same expression | "Dual-source verified (registry + repository LICENSE)." |
| `Verified (non-structural statement)` | `LicenseRef-…` if the report derived one **and** extracted text is obtainable (0.5d), else `NOASSERTION` | same | the quoted statement, verbatim |
| `CONFLICT` | the registry-declared expression | **`NOASSERTION`** | both declarations, quoted separately + an OTHER annotation (1.5) |
| `UNCERTAIN` — any reason | `NOASSERTION` | `NOASSERTION` | the report's reason, verbatim |
| Private/Internal package | `NOASSERTION` | `NOASSERTION` | "Private registry; external verification not applicable." |
| `VIOLATION` — project level | root package: the manifest-declared expression | root package: **`NOASSERTION`** | annotation on `SPDXRef-DOCUMENT` naming both contradicting sources |

Two consequences worth stating outright:
- A Class 1 package gets a concluded license from a single registry
  field. That is the audit's rule, and the comment says so, so a
  consumer can weigh it. This task does not re-verify it and does not
  pretend it was dual-sourced.
- A copyleft dependency next to a permissively-licensed project
  produces **no** finding, **no** annotation and **no** field change.
  The audit explicitly declines that judgment; the SBOM records both
  licenses side by side and leaves the compatibility conclusion to the
  reader, exactly as the report did.

## 2. TASK DEFINITION
1. Confirm the audit report exists and read it **in full** (every file,
   if it is a split set).
2. Establish the target spec version and serialization (0.1), the
   comment language, the document name, and the namespace source.
3. Build the element inventory: root package(s), files, dependency
   packages, vendored packages, assets — each traced to a report row.
4. Resolve the open questions that cannot be defaulted: the
   `-only`/`-or-later` choice for any GNU-family identifier (0.5c), the
   namespace host, any asset that could reasonably be a file or a
   package.
5. Present the plan and STOP for approval (PHASE 1).
6. Generate the document: header, packages, files, relationships,
   annotations, extracted licensing info (PHASE 2).
7. Validate it with a real validator, reconcile the counts against the
   report, and deliver with the approximation and exclusion lists
   (PHASE 3).
8. Summarize (Section 6).

## 3. SUCCESS CRITERIA

**General rule** — the task is complete when ALL of the following are
satisfied:
- [ ] An audit report existed and was read in full (Section 0
      precondition met); for a split set, every ecosystem file was read
      and none was silently skipped.
- [ ] The document parses. For JSON: it is well-formed and the top-level
      structure is complete (no truncated object, balanced braces and
      brackets). For tag-value: every element block is complete.
- [ ] **A real validator ran and its verbatim output was reported.** If
      no validator was available, that is stated explicitly and the
      document is labelled "not machine-validated — manual checklist
      only" in the delivery, in PHASE 3, and in the Section 6 summary.
- [ ] Mandatory document fields present: `spdxVersion`, `dataLicense`
      (= `CC0-1.0`), `SPDXID` (= `SPDXRef-DOCUMENT`), `name`,
      `documentNamespace`, `creationInfo.created`,
      `creationInfo.creators` (≥1).
- [ ] At least one `DESCRIBES` relationship exists and every root
      package is described.
- [ ] Every package has `name`, a unique `SPDXID`, and
      `downloadLocation` (a URL, `NONE`, or `NOASSERTION`).
- [ ] `filesAnalyzed` is set deliberately on every package, and where
      it is `false`, `packageVerificationCode` and `licenseInfoFromFiles`
      are **absent** (the spec forbids them there).
- [ ] Where `filesAnalyzed` is `true`, `packageVerificationCode` is
      present and was **computed** by the documented algorithm (PHASE 2),
      not written by hand.
- [ ] Every `SPDXID` matches `SPDXRef-[a-zA-Z0-9.\-]+`, is unique in the
      document, and every reference (relationships, annotations,
      `documentDescribes`) resolves to an element that exists.
- [ ] Every license field is a valid SPDX expression, `NONE`, or
      `NOASSERTION` — no free text anywhere (0.5a).
- [ ] Every `LicenseRef-` used has a matching
      `hasExtractedLicensingInfos` entry with non-empty `extractedText`
      (0.5d). Zero dangling references.
- [ ] No deprecated GNU identifier was emitted, and no `-only`/
      `-or-later` choice was made without evidence or a user answer
      (0.5c).
- [ ] **Traceability check passed:** every emitted element maps to a
      report row, and every report row maps to an emitted element or
      appears in the exclusion list with a reason. The reconciliation
      table is delivered.
- [ ] **Count reconciliation passed:** the document's package/file/
      unknown counts match the report's Section 9 conclusion counts, or
      each difference is explained by a named row in the exclusion or
      approximation list.
- [ ] Every `UNCERTAIN` row became `NOASSERTION` — none was resolved to
      a license (0.2).
- [ ] Every `CONFLICT` and `VIOLATION` became an annotation, and none
      became a license value (1.5).
- [ ] Every approximation is documented **inside** the document (element
      comments), not only in the chat.
- [ ] The provenance block (0.4) is present in `CreatorComment`, in the
      chat delivery, and in the summary.
- [ ] No checksum, URL, purl, supplier, timestamp or namespace was
      invented (0.2).
- [ ] **No file other than the SPDX document was created or modified.**
      The audit report was not edited; no project file was touched.

**Task-specific criteria:** add concrete criteria for this project in
the PHASE 1 plan — e.g. "all 14 GPL-family packages received an
explicit `-only`/`-or-later` value from the user", "the 3 vendored
subtrees in report 3.1 are separate packages, none inheriting the root
license". Derive them from the report's actual content; do not invent
them.

## 4. WORKING METHOD — PLAN THEN STEP BY STEP (MANDATORY)

### PHASE 1 — Read, Inventory, Plan, Lock
Nothing is written to disk in this phase.

a. **Read the report in full.** Every section, every table, every file
   of a split set. Record the report's own path(s) and date — they go
   into the provenance block.

b. **Build the element inventory** — counts, from the report, not from
   the project:
   - root package(s): 1, or one per workspace for a monorepo (1.4)
   - files: report Sections 3, 1.3, 6 (assets kept as files), 8
   - dependency packages: Sections 4 + 5, deduplicated by `name@version`
   - vendored packages: Section 3.1
   - annotations: Section 2 findings
   - `LicenseRef` entries needed, and whether extracted text is
     obtainable for each (0.5d) — a `LicenseRef` with no obtainable
     text is decided **now**, not discovered mid-generation

c. **Resolve what cannot be defaulted.** Collect these into one
   question block and ask them together, once:
   1. **GNU `-only` / `-or-later`** — list every affected package and
      the project itself; state the consequence in one line; do not
      default (0.5c).
   2. **`documentNamespace` host** — derive from the project's
      evidenced repository or homepage URL if the report records one.
      If it does not, ask for a domain. If the user has none, use the
      SPDX-documented fallback form
      `https://spdx.org/spdxdocs/<document-name>-<uuid>` and say so.
      **Never invent a domain**, and never reuse a namespace across two
      documents — the namespace is what makes SPDXIDs globally unique.
   3. **Ambiguous assets** — any Section 6 row that could reasonably be
      a file or a package (1.2).
   4. **Inactive code** — include with a label (default) or exclude
      (listed) (1.2).
   5. Anything the report leaves genuinely two-way and no rule above
      settles.

d. **Present the plan.** It contains, concretely:
   - Target spec version + serialization + output file path (0.1), and
     the comment-field language in one line (LANGUAGE).
   - Source report path(s) and date.
   - The element inventory from (b), with numbers.
   - The status distribution that will result: how many packages get a
     concluded license, how many get `NOASSERTION`, and why — broken
     down by the 1.6 table's rows. This is the number the user is most
     likely to be surprised by, and it is better surprised before
     generation than after.
   - The relationship plan, including **how many transitive packages
     will use the unrecorded-parentage approximation** (1.3).
   - Which findings become annotations (1.5).
   - `filesAnalyzed` decision per package class, and whether checksums
     will be computed (see PHASE 2) — with the file count that implies.
   - The exclusion list: every report row that will **not** become an
     element, with its reason.
   - The task-specific success criteria (Section 3).
   - The open questions from (c).

e. **STOP.** End with: "Do you approve this plan, or would you like
   changes?" Await approval. **This is the only approval gate.** The
   document is not written before it. If the user approves the plan but
   leaves a (c) question unanswered, PHASE 2 does not begin for the
   affected elements — an unanswered `-only`/`-or-later` question is
   not a formatting detail, and it is not resolved by picking one.

### PHASE 2 — Generation (Post-Approval)

Generate in a fixed order so that a truncated write is resumable:
**document header → extracted licensing info → root package(s) → other
packages → files → relationships → annotations.**

#### 2.1 Minting SPDXIDs
- Charset is strict: `SPDXRef-` followed by letters, digits, `.` and
  `-` **only**. Underscore, `@`, `/`, `+`, `~` and spaces are not
  allowed and are replaced with `-`.
- Patterns:
  - root package → `SPDXRef-Package-<sanitized-project-name>`
  - dependency → `SPDXRef-Package-<sanitized-name>-<sanitized-version>`
  - vendored → `SPDXRef-Package-vendored-<sanitized-path>`
  - file → `SPDXRef-File-<sanitized-relative-path>`
- **Collisions after sanitization are real** — `@acme/core` and
  `acme-core` sanitize to the same string. On a collision, append
  `-2`, `-3`, … in first-appearance order and record it in the ID map.
  Never reuse an ID: two elements sharing an SPDXID makes every
  relationship pointing at it ambiguous.
- Keep an **ID map** (original name/path → SPDXID) as you go. It is
  delivered with the document in PHASE 3 and is what makes the
  traceability check mechanical rather than a re-reading exercise.

#### 2.2 File entries
- `fileName` is **relative to the package root and prefixed `./`** —
  `./src/main.c`, not `src/main.c`, not an absolute path, not a
  Windows-style path. Backslashes become forward slashes.
- `checksums` — SPDX 2.x requires **SHA1** on every file entry. Compute
  it from the actual file (`sha1sum <path>`, or the platform
  equivalent); add SHA256 as a second entry when it is equally cheap.
  **If a file cannot be read to hash it** (deleted since the audit,
  permission denied, path unresolvable): the file entry is **not
  emitted** — it goes to the exclusion list with the reason. Never
  write a placeholder or pattern-shaped hash (0.2).
- `licenseConcluded` / `licenseInfoInFiles` / `copyrightText` per 0.3
  and 1.6.
- `fileComment` carries: the inactive-code label (Section 8 rows), the
  NOTICE-file label (Section 1.3 rows), and any per-file approximation.

#### 2.3 Package entries
- `filesAnalyzed`:
  - **Root package** → `true` **only if** the report's file table is
    complete for it and every listed file was hashed. Otherwise
    `false`, with a `packageComment` stating why.
  - **Dependency packages** → `false`. The audit does not unpack
    dependency trees (`node_modules` and friends are explicitly out of
    its scope), so their files were never analyzed. Claiming otherwise
    would be the same class of error as a fabricated checksum.
  - **Vendored packages** → `true` if their files are in the report's
    3.1 table and hashable; otherwise `false`.
  - Where `filesAnalyzed` is `false`, **omit** `packageVerificationCode`
    and `licenseInfoFromFiles` entirely. Emitting them alongside
    `filesAnalyzed: false` is a spec violation, not a stylistic choice.
- `packageVerificationCode` — computed, never authored. The algorithm:
  1. take every file in the package (excluding any SPDX document file
     inside the package, and any file you deliberately exclude);
  2. compute each file's SHA1 as lowercase hex;
  3. sort those hex strings in ascending byte order;
  4. concatenate them with **no separator**;
  5. the verification code is the SHA1 of that concatenated string.
  Excluded files are listed in `packageVerificationCodeExcludedFiles`.
- `downloadLocation`: the registry/repo URL the report already recorded
  as evidence; `NOASSERTION` when it recorded none; `NONE` only when
  the package is genuinely not downloadable from anywhere (the root
  package of a private project, for instance) and the report supports
  that.
- `externalRefs` — a purl is emitted only when the ecosystem, name and
  version are all established by the report. When any component is
  missing, omit the whole `externalRefs` entry: a partial purl is worse
  than none, because it resolves to the wrong artifact instead of to
  nothing.
- `supplier` / `originator`: `Person: <name>` or `Organization: <name>`
  from evidence, else `NOASSERTION` (0.2).
- `packageComment` carries the verification-depth sentence from 1.6,
  the report's `UNCERTAIN` reason where applicable, the stale flag, the
  unrecorded-parentage note, and nothing else.

#### 2.4 Document header
- `spdxVersion`: `SPDX-2.3` (or as locked in 0.1).
- `dataLicense`: `CC0-1.0` — always (0.5e).
- `SPDXID`: `SPDXRef-DOCUMENT`.
- `name`: the document name, typically `<project-name>` or
  `<project-name>-<version>`.
- `documentNamespace`: per PHASE 1 (c.2). The UUID, if used, is
  **generated by a command** (`uuidgen`, or
  `python -c "import uuid;print(uuid.uuid4())"`), never hand-typed — a
  hand-typed UUID is not random and may collide.
- `creationInfo.created`: actual UTC now, `YYYY-MM-DDThh:mm:ssZ`, read
  from the system clock.
- `creationInfo.creators`: `Tool: <this task>-<version>` always; a
  `Person:`/`Organization:` entry only per 0.4.
- `creationInfo.comment`: the provenance block (0.4).
- `creationInfo.licenseListVersion`: emitted **only** if the SPDX
  License List version in use was actually confirmed against
  spdx.org/licenses. Otherwise omit the field — it is optional, and a
  guessed version number misrepresents which list the identifiers were
  checked against.

#### 2.5 Shape reference — SPDX 2.3 JSON
```json
{
  "spdxVersion": "SPDX-2.3",
  "dataLicense": "CC0-1.0",
  "SPDXID": "SPDXRef-DOCUMENT",
  "name": "my-project-1.4.0",
  "documentNamespace": "https://example.com/spdx/my-project-1.4.0-<uuid>",
  "creationInfo": {
    "created": "2026-08-18T09:14:22Z",
    "creators": ["Tool: spdx-task-1.0"],
    "comment": "<provenance block, Section 0.4>"
  },
  "packages": [
    {
      "name": "my-project",
      "SPDXID": "SPDXRef-Package-my-project",
      "versionInfo": "1.4.0",
      "downloadLocation": "https://github.com/acme/my-project",
      "filesAnalyzed": true,
      "packageVerificationCode": { "packageVerificationCodeValue": "<computed sha1>" },
      "licenseConcluded": "MIT",
      "licenseDeclared": "MIT",
      "licenseInfoFromFiles": ["MIT", "NOASSERTION"],
      "copyrightText": "Copyright (c) 2019 Jane Doe",
      "supplier": "NOASSERTION"
    },
    {
      "name": "some-gpl-lib",
      "SPDXID": "SPDXRef-Package-some-gpl-lib-1.4.0",
      "versionInfo": "1.4.0",
      "downloadLocation": "https://pypi.org/project/some-gpl-lib/1.4.0/",
      "filesAnalyzed": false,
      "licenseConcluded": "GPL-3.0-or-later",
      "licenseDeclared": "GPL-3.0-or-later",
      "copyrightText": "NOASSERTION",
      "comment": "Dual-source verified (registry + repository LICENSE). Or-later variant established from the header quoted at audit Section 4.",
      "externalRefs": [
        { "referenceCategory": "PACKAGE-MANAGER", "referenceType": "purl",
          "referenceLocator": "pkg:pypi/some-gpl-lib@1.4.0" }
      ]
    }
  ],
  "files": [
    {
      "fileName": "./src/main.c",
      "SPDXID": "SPDXRef-File-src-main.c",
      "checksums": [{ "algorithm": "SHA1", "checksumValue": "<computed>" }],
      "licenseConcluded": "MIT",
      "licenseInfoInFiles": ["MIT"],
      "copyrightText": "Copyright (c) 2019 Jane Doe"
    }
  ],
  "hasExtractedLicensingInfos": [
    {
      "licenseId": "LicenseRef-Proprietary-my-project",
      "extractedText": "<the actual license text — never empty>",
      "name": "My Project Proprietary License",
      "comment": "Extracted text taken from LICENSE:1-40, cited as evidence at audit Section 1.1."
    }
  ],
  "relationships": [
    { "spdxElementId": "SPDXRef-DOCUMENT", "relationshipType": "DESCRIBES",
      "relatedSpdxElement": "SPDXRef-Package-my-project" },
    { "spdxElementId": "SPDXRef-Package-my-project", "relationshipType": "CONTAINS",
      "relatedSpdxElement": "SPDXRef-File-src-main.c" },
    { "spdxElementId": "SPDXRef-Package-my-project", "relationshipType": "DEPENDS_ON",
      "relatedSpdxElement": "SPDXRef-Package-some-gpl-lib-1.4.0" }
  ],
  "annotations": [
    {
      "annotator": "Tool: spdx-task-1.0",
      "annotationDate": "2026-08-18T09:14:22Z",
      "annotationType": "OTHER",
      "comment": "CONFLICT recorded at audit Section 2: registry declares MIT; repository LICENSE at tag v1.4.0 contains BSD-3-Clause text. Both recorded; not resolved."
    }
  ]
}
```
Annotation placement: in JSON, a document-level annotation lives in the
top-level `annotations` array; an annotation about a package or file
goes in **that element's own** `annotations` array. In tag-value, the
`SPDXREF:` tag names the target.

#### 2.6 Shape reference — SPDX 2.3 tag-value
```
SPDXVersion: SPDX-2.3
DataLicense: CC0-1.0
SPDXID: SPDXRef-DOCUMENT
DocumentName: my-project-1.4.0
DocumentNamespace: https://example.com/spdx/my-project-1.4.0-<uuid>
Creator: Tool: spdx-task-1.0
Created: 2026-08-18T09:14:22Z
CreatorComment: <text>...</text>

PackageName: my-project
SPDXID: SPDXRef-Package-my-project
PackageVersion: 1.4.0
PackageDownloadLocation: https://github.com/acme/my-project
FilesAnalyzed: true
PackageVerificationCode: <computed sha1>
PackageLicenseConcluded: MIT
PackageLicenseDeclared: MIT
PackageCopyrightText: <text>Copyright (c) 2019 Jane Doe</text>

Relationship: SPDXRef-DOCUMENT DESCRIBES SPDXRef-Package-my-project
```
Multi-line values are wrapped in `<text>` … `</text>` delimiters.
Element blocks are separated by a blank line, and a block's tags stay
together — a tag written after an intervening block silently attaches
to the wrong element.

#### 2.7 Incremental write and truncation
The document is one file and must end structurally complete; a
half-written JSON is not a partial document, it is an unparseable one.
- Write incrementally in the fixed order above, so work already done
  survives an interruption.
- **If a write is truncated:** do not restart from scratch and do not
  append onto a broken tail. Re-open the file, find the last
  **complete** element object/block, truncate the file to the end of
  that element, and resume from the next unwritten element. Log one
  line: `"Resumed after truncation — last complete element: <SPDXID>."`
- Before validation, always run a structural close check: for JSON,
  braces and brackets balance and the file parses; for tag-value, no
  block ends mid-tag.

### PHASE 3 — Validation, Reconciliation, Delivery

#### 3.1 Machine validation (attempted before anything is claimed)
Try the available validators, in this order, until one runs:

| Tool | Invocation | Covers |
|---|---|---|
| `pyspdxtools` (spdx-tools ≥ 0.8) | `pyspdxtools -i <file>` | full 2.x schema + semantic rules |
| `sbom-utility` | `sbom-utility validate -i <file>` | schema validation, SPDX + CycloneDX |
| `ntia-conformance-checker` | `ntia-checker -f <file>` | NTIA minimum-elements conformance |
| SPDX tools-java | `java -jar tools-java.jar Verify <file>` | full 2.x verification |

Rules:
- Report the validator's **verbatim output**, pass or fail. Not a
  paraphrase, not "validation passed".
- **On failure, fix the document and re-run** — a validation failure is
  a defect in the generated file, not a note to hand to the user. The
  loop repeats until it passes or until a failure is genuinely
  unfixable within the constraints (e.g. a required field whose only
  honest value is one the validator rejects), which is then stated
  explicitly with the validator's message.
- **If no validator is installed or reachable:** say so plainly, run
  the manual checklist below, and label the delivery
  **"not machine-validated — manual checklist only"** — in the chat, in
  PHASE 3, and in the Section 6 summary. Never write or say "valid
  SPDX" on the strength of a checklist (0.2).

#### 3.2 Manual checklist (always run, validator or not)
- Document parses / every block closes (2.7).
- Mandatory header fields present; `dataLicense` is `CC0-1.0`.
- `documentNamespace` is an absolute URI, unique, and contains no
  fragment (`#`) — the spec forbids one.
- Every SPDXID matches `SPDXRef-[a-zA-Z0-9.\-]+` and is unique.
- Every relationship/annotation reference resolves to an element that
  exists in this document.
- ≥1 `DESCRIBES` relationship; every root package described.
- Every package: `name`, `SPDXID`, `downloadLocation` present.
- No package has `filesAnalyzed: false` together with
  `packageVerificationCode` or `licenseInfoFromFiles`.
- Every file has a SHA1 checksum, and every checksum was computed.
- Every license field is a valid expression / `NONE` / `NOASSERTION`.
- Every `LicenseRef-` has a non-empty `extractedText`.
- No deprecated license identifier present.
- No `NONE` written where the report's evidence supports only
  `NOASSERTION` (0.3).

#### 3.3 Reconciliation against the report (mandatory)
Build and deliver a reconciliation table — this is the artifact that
proves the document is a transcription and not a generation:

| Report section | Rows in report | Elements emitted | Excluded (reason) | Approximated |
|---|---|---|---|---|
| 3 Project files | 128 | 126 files | 2 (unreadable — see list) | 0 |
| 4 Direct deps | 31 | 31 packages | 0 | 0 |
| 5 Transitive deps | 214 | 214 packages | 0 | 47 (unrecorded parentage) |
| 3.1 Vendored | 3 | 3 packages | 0 | 0 |
| 6 Assets | 12 | 12 files | 0 | 0 |

- Numbers that do not reconcile with the report's Section 9 conclusion
  counts are a **transcription bug**: find it and fix it before
  delivery. Do not deliver with an unexplained delta and a note.
- Deliver alongside it: the **ID map** (2.1), the **exclusion list**
  (every dropped row + reason), and the **approximation list** (every
  element carrying a documented approximation).

#### 3.4 Cross-check against a pre-existing SBOM (only if one was given)
If the user supplied an existing SBOM (`syft` output, an older
document), compare and **report divergences without resolving them**:
packages present there but not in the report, license values that
differ, versions that differ. Each divergence is one line, factual. The
report remains the source of truth for this document's fields; a
divergence is information for the user, not a reason to change a field.

#### 3.5 Delivery
Deliver: the document path, the validator output, the reconciliation
table, the ID map, the exclusion list, the approximation list, and the
provenance line (0.4). Then STOP.

On feedback, change only what the feedback touches, re-run 3.1–3.3 in
full, and re-deliver. A regenerated document is a complete deliverable
on its own — never a diff for the user to apply.

## 5. CONSTRAINTS
- **No generation without the audit report** — Section 0 is a hard
  precondition. The task does not scan the project to make up the
  difference.
- **Write scope: the SPDX document file only.** No project file is
  created, modified, moved or deleted. The audit report is **read-only**
  — findings are never written back into it, and a report row is never
  "corrected" to make the document cleaner. `Licenses/` is read-only
  reference material (used only for `extractedText` under 0.5d).
- **Project files are opened for exactly two reasons:** (a) computing a
  checksum for a file the report already lists, and (b) reading the
  license text a `LicenseRef` needs for `extractedText` (0.5d) when the
  report cited that file as evidence. Nothing else justifies opening a
  project file — not filling a missing version, not identifying an
  unknown asset, not resolving an UNCERTAIN row. Those are audit work,
  and re-doing audit work here would produce evidence that never went
  through the audit's verification rules.
- **Never invent a field value** (0.2). `NOASSERTION` is always
  available and is always the correct answer when evidence is absent.
- **Never resolve what the audit left unresolved** — no UNCERTAIN
  becomes a license, no CONFLICT becomes a conclusion, no `-only`/
  `-or-later` is chosen by default.
- **No risk interpretation, no severity, no recommendation** — not in a
  comment, not in an annotation, not in the chat summary. Words like
  "clean", "safe", "risky", "critical", "high risk" do not appear. A
  count is a fact; an adjective is a judgment, and this task makes
  none. A copyleft dependency beside a permissive project is recorded,
  not flagged.
- **Never claim validity without a validator run** (3.1).
- **One document, never split** (0.1). If the output is large, it is
  still one file; size is handled by incremental writing (2.7), not by
  fragmentation.
- **Never mix spec versions.** The version locked in PHASE 1 governs
  every field name and every enumerated value in the file.
- **Do not translate structural content**; do not translate quoted
  evidence (LANGUAGE).
- **User approval is required before the document is written** — the
  PHASE 1 gate. Regenerating after feedback does not reopen it; a
  change of spec version, serialization, or scope does.
- **Ecosystem-agnostic.** Do not assume npm, or Python, or any single
  toolchain. The report names the ecosystems; the document follows the
  report.
- If the user asks for a field this task will not fabricate (a purl for
  a package whose version the report never established, a checksum for
  a file that is gone), decline that specific field in one sentence,
  emit `NOASSERTION` or omit it, and continue. That is a refusal to
  invent, not a refusal to work.

## 6. SUMMARY (Final step)
Once the document is delivered and accepted, provide a short,
structured summary:
- **Document produced:** path, spec version, serialization,
  `documentNamespace`.
- **Source:** the audit report path(s) and date it was transcribed
  from.
- **Contents in counts:** packages (root / direct / transitive /
  vendored), files, relationships, annotations,
  `hasExtractedLicensingInfos` entries.
- **License field outcome:** how many elements carry a concluded
  license and how many carry `NOASSERTION`, broken out by the reason
  categories in 1.6 — e.g. "182 concluded, 26 NOASSERTION (19
  UNCERTAIN, 4 CONFLICT, 3 private registry)".
- **Findings carried as annotations:** VIOLATION count, CONFLICT count
  — counts only, no adjective.
- **Approximations:** each one, one line (e.g. "47 transitive packages
  attached to the root package — parent edge not recorded in the
  report").
- **Exclusions:** each report row not represented, with its reason.
- **Validation result:** the tool that ran and its verdict, or
  "not machine-validated — manual checklist only".
- **Provenance line** (0.4): one line — transcribed from the named
  report, not independently re-verified, not human-reviewed.
- **Files created/modified:** the document path. Nothing else was
  created or modified.

The summary is a "what was delivered" list — no repeating the
document, no repeating the plan, no interpretation of what the license
distribution means.
