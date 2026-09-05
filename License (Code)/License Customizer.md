# TASK: Custom License Authoring — Requirement-Driven License Drafting

> **What this task is:** it gathers the user's licensing requirements
> (granted rights, restrictions, obligations, term, jurisdiction, …)
> and produces a **custom/adapted license text** — structured with
> headings and numbered clauses (maddeler) — as a clearly-labelled
> draft. It does not audit projects, it does not select or apply
> standard licenses (that is the Licensor task), and it does not
> modify project files. Its sole output is license text.
>
> **What this task is NOT:** it is not a legal counsel substitute.
> Every draft it produces is a starting point that requires
> professional legal review before use. It is also not the place
> where third-party obligations get handled: a draft written here
> governs the licensor's **own** work, and no wording in it can
> reach the code, fonts, data or assets the work borrows from other
> people. Those keep their own licenses and need their own notices —
> see Section 0.4.

## LANGUAGE
**Two separate channels — never conflate them.**

- **File output — the license draft(s) and every file this task produces: English by default.** This does NOT follow the language the user writes in. It changes only when the user **explicitly asks** for the license text in another language.
- **Conversation — requirement questions, plan presentation, clause explanations, approval requests, the Section 6 summary: follows the user.** Use the language the user writes in; switch when the user explicitly asks for another language, or simply starts writing in one. A Turkish conversation NEVER makes the draft Turkish, and the draft language never dictates the conversation language.

State the resolved draft language in one line when presenting the PHASE 1 plan (e.g. "Draft language: English — default").

## OUTPUT FILE (NAMING AND STRUCTURE — MANDATORY, NOT A PREFERENCE)
This task produces exactly one file, and its name is fixed:

```
LICENSE.md
```

- **Fixed name.** Never `custom_license.md`, `license_v2.md`,
  `my-project-license.md`, or a name derived from the project, the
  orientation, or the date. The name does not follow the conversation
  language either — it is `LICENSE.md` in every session, in every
  language.
- **Revisions overwrite the same file.** A revised draft is the same
  deliverable at a later state, not a new artifact. No `_v2`,
  `_final`, `_revised`, `_FINAL_final` suffixes ever appear. The
  version history lives in the conversation, not in filenames.
- **Multiple distinct drafts in one session** (dual licensing, a
  commercial and a community variant): only then does the name take a
  variant segment — `LICENSE.commercial.md`, `LICENSE.community.md`.
  Never used to distinguish revisions of the same draft.

### File structure — two parts, one hard boundary
The file is split into a bare license and everything that is *about*
the license. Nothing is interleaved:

```
[PART 1 — LICENSE TEXT, BARE]
  Title block, preamble, numbered clauses. Nothing above the title.
  No notice, no banner, no meta-comment, no chat context. This part
  is directly usable: the reader copies from the first line to the
  boundary and has a complete license document.

---
<!-- END OF LICENSE TEXT — everything below is not part of the License -->
---

[PART 2 — APPENDIX: NOTES AND EVIDENCE]
  A.1 Draft notice (the 0.1 disclaimer, verbatim)
  A.2 Requirements → clause mapping table (the coverage evidence)
  A.3 Open items — every [PLACEHOLDER] the user must fill
  A.4 Adaptation basis, if any — base license and differing clauses
  A.5 Third-party position (Section 0.4)
```

- **The boundary is structural, not decorative.** The rule + comment
  line above is written exactly as shown, so a reader who opens the
  file cold — and any diff, hash, or reviewer working from the file
  alone — can see where the operative document ends. Never omit it,
  never replace it with a heading alone.
- **Nothing from Part 2 leaks into Part 1.** No bracketed editorial
  asides in the clause text, no "(see mapping table)" cross-references,
  no rationale sentences inside a clause. The clause text stands alone
  (Section 4 drafting rules).
- **Part 2 is never dropped.** A file that is Part 1 only is an
  unreviewed legal document with no warning attached and is not an
  acceptable deliverable. If the user asks for the appendix to be
  removed, refuse on the 0.1 grounds — the appendix carries the
  disclaimer, and with the file named plainly `LICENSE.md`, it is the
  only thing in the artifact that says the text is unreviewed.
- **What the user does with it.** State in one line at delivery: the
  file is review-ready, not use-ready; after a lawyer signs off, the
  user deletes Part 2 and the boundary line, leaving the bare license
  at the project root. This task does not place the file into a
  project (Section 5).

## 0. PRECONDITION (MANDATORY — THE TASK DOES NOT START WITHOUT THIS)
This task REQUIRES a completed **requirements-gathering interview**
(PHASE 1) — a confirmed set of licensing requirements for the work to
be licensed. The task does not start until those requirements have
been elicited, summarized, and approved by the user.

- **If the user gives no requirements and asks directly for a draft:** do not guess or invent a plausible requirement set. Ask the PHASE 1 questionnaire questions first. A draft written from assumed requirements would encode decisions the user never made (e.g. whether commercial use is permitted) into legally relevant text.
- **If the user asks for a standard, off-the-shelf license (MIT, GPL-3.0, Apache-2.0, …):** this task does not do that. State in one line that standard-license selection/application is the separate Licensor task, and do not write the standard text here — not from memory, not from the `Licenses/` folder.
- **If the user asks to "adapt" a standard license** ("make it like MIT but…", "MIT + no-resale", "GPL without section X"): permitted — see the adaptation rules in 0.3 — but the user must be told, on the same line, that the result is no longer the standard license, loses its SPDX identity, and will not be recognised as such by scanners or other parties.
- **Partial requirements are NOT a precondition violation:** if the user provides a requirement set with a gap (e.g. no jurisdiction given), the task proceeds and the gap is recorded as an open item for the user to fill at the end (PHASE 3) — never silently defaulted.

### 0.1 MANDATORY LEGAL DISCLAIMER (EVERY DELIVERY, WITHOUT EXCEPTION)
Every license draft — the first one and every revision — ships with a
clearly visible, unremovable notice. This notice is not part of the
license text itself; it is a delivery label, which is why it lives
below the boundary line and never inside Part 1:

> **DRAFT — NOT LEGAL ADVICE.** This document is an AI-generated draft
> for discussion purposes. It has not been reviewed by an attorney and
> should not be distributed, published, or relied upon as a final
> license. A qualified legal professional must review and finalize it
> before use.

This notice appears:
- in the output file as **A.1**, the first item below the end-of-license boundary (OUTPUT FILE section) — verbatim, never paraphrased or shortened;
- in the chat when the draft is presented (one line);
- in the Section 6 summary (one line).
If the user asks to remove it, refuse — that is not a formatting
preference, it is a safety requirement. Removing the notice would make
an unreviewed legal document look final. Moving it below the license
text is a layout decision and is already handled; deleting it, or
deleting the appendix that holds it, is not the same thing and is
refused.

### 0.2 NEVER DO LIST (ABSOLUTE)
- **Never claim legal validity or enforceability.** No "this is
  enforceable in…", no "this follows the standards of…", no
  "this will hold up in court".
- **Never fabricate legal authority.** No invented case law, statutes,
  or regulatory citations. If a real legal reference is relevant
  (e.g. the EU Software Directive, a national copyright act), it may be
  named only if it is well-known and accurate — and it is still framed
  as background for the user to verify, never as a guarantee.
- **Never copy a standard license text wholesale**, under any framing
  ("just add my name to MIT", "use Apache-2.0 but call it mine").
  Adaptation (0.3) is rewriting around a stated base, not copying.
- **Never draft without requirements** (Section 0).
- **Never write a clause that disposes of rights the licensor does
  not hold.** No blanket ownership or reservation over third-party
  components embedded in the work, no term purporting to relicense
  them, no restriction that contradicts a license they already carry
  (Section 0.4).
- **Never silently change a requirement** during drafting. If a
  requirement is internally inconsistent or impossible to express
  cleanly, STOP, state the problem, and ask — do not quietly write
  the closest reasonable clause.

### 0.3 ADAPTATION RULES (when the user wants a modified standard license)
Adaptation is allowed and is subject to these rules:
1. **The base must be named.** If the draft derives from an existing
   license ("MIT-like", "BSD + patent clause", "GPL but for SaaS"),
   the user is told in one line which license is the basis and which
   clauses differ from it.
2. **The disclaimers in Section 0 hold.** The draft is still
   AI-generated, unreviewed, and no longer the named standard license.
3. **The result must still be self-consistent and complete.** A
   stripped-down standard license is not acceptable if it leaves the
   user without a warranty disclaimer, a liability limitation, or a
   definition of what is being licensed. If the user's request would
   remove a clause that is structurally necessary, say so and offer the
   minimal viable alternative.
4. **No SPDX identity.** Adapted drafts never receive an SPDX
   identifier. If the user asks what identifier to use, answer
   `LicenseRef-<ProjectName>` (a license reference with no
   standardized text) — and one line: adapted text cannot be
   represented by any standard SPDX ID.

### 0.4 THIRD-PARTY COMPONENTS INSIDE THE LICENSED WORK
Almost nothing is licensed in isolation. A codebase pulls in
libraries, a document embeds a font, a dataset merges an external
table — and each of those arrives with a license of its own that the
licensor did not write and cannot rewrite. A custom draft is
authored **over** that layer, never across it.

**Two rules, both absolute:**

1. **The draft never grants what the licensor does not hold.** A
   blanket "all rights in the Licensed Work are reserved to the
   Licensor", "the Licensor is the sole owner of the Licensed Work",
   or a grant clause written as though the whole work were the
   licensor's is factually wrong the moment one third-party component
   ships inside it — and it is wrong in the direction that misleads
   the licensee. Whenever the requirements interview establishes that
   third-party components are present, the draft carries the carve-out
   clauses in Section 4's skeleton (Definitions, 2.8, 4.5). Their
   presence is not a stylistic choice and is not dropped on request
   for brevity; the requirement that produced them can be changed by
   the user, but the clauses cannot be silently omitted while the
   components are still there.
2. **This task does not produce the notices themselves.** Reproducing
   each component's license text and copyright notice into the
   distributed work is a separate, concrete deliverable —
   the `THIRD-PARTY-LICENSES/` folder built by the **Licensor task**
   (its Section 0.3), from an audit report's redistribution
   inventory. Say so in one line when the topic comes up, name the
   task that does it, and do not attempt it here: this task writes
   license text and touches no project file (Section 5), so it can
   neither read the components' license files nor place them.

**When the user says there are none.** "It is all my own code" is
accepted as a requirement like any other and drafted accordingly —
this task does not audit and cannot contradict it. But record it as
a **stated assumption** in the PHASE 3 open-items list, in one line:
"Draft assumes the Licensed Work contains no third-party component;
this was stated, not verified. A license audit would settle it."
That single line is the difference between a user who knows what the
draft rests on and one who does not.

**When it is unknown.** Unknown is not "none". If the user does not
know, the draft keeps the carve-out clauses in place — they cost
nothing when the set turns out to be empty, and they prevent an
overreaching grant when it does not — and the open-items list records
that the component list still needs to be established.

## 1. CONTEXT / DOMAIN

### 1.1 What is being licensed (the subject)
Determines which clause set the draft needs. Established from the
requirements, never assumed:
- **Software** — source code and/or binaries (patent grant and
  copyleft-style clauses may be relevant; "source-available" and
  "commercial" options apply).
- **Documentation / content** — text, docs, media (attribution,
  derivative-work, and remixing clauses relevant; patent clauses are
  not).
- **Database / dataset** — extraction, reuse, and redistribution
  of data (database-specific rights clauses may be relevant).
- **Fonts / assets** — embedding, bundling, and renaming restrictions.
- **Mixed** — the draft is structured so each subject is addressed
  by its own clause group; one blanket clause over a mixed work is
  avoided.

Whichever subject applies, establish separately whether the work
**embeds third-party components** — libraries, fonts, icons, sample
data, generated runtime code. This is a distinct fact from what the
work is, it changes which clauses the draft needs, and it is
established from the requirements interview (question 13), never
assumed either way. See Section 0.4.

### 1.2 License orientation (the family the user wants)
The draft's character is set by the orientation the user confirms:
- **Permissive-style** — broad grant; main condition is attribution.
- **Reciprocal / copyleft-style** — derivative works must be
  distributed under the same terms.
- **Weak-copyleft-style** — the copyleft attaches to modifications of
  the licensed work itself, not to linked code.
- **Source-available / business-source-style** — code is visible but
  commercial use or redistribution is restricted.
- **Proprietary / commercial-style** — all rights reserved except the
  granted license; usage, redistribution, and modifications controlled;
  often fee- or number-of-users-conditioned.
- **Content-style** — permissions for reuse, remixing, attribution,
  and commercial/non-commercial distinction.

### 1.3 The parties
- **Licensor** (the one granting rights): the copyright holder(s), in
  the exact legal name(s) they will use.
- **Licensee** (who receives the grant): anyone (worldwide,
  royalty-free) or a defined class (employees, customers, named
  companies) — from the requirements.
- If the licensor's legal name is unknown, it is a **[PLACEHOLDER]** —
  never the user's chat handle or an invented name.
- **Third-party rights holders are not parties to this license.**
  They are named nowhere in the draft as licensors and grant nothing
  through it; their components are referenced as a class, and the
  register that lists them lives outside this document (Section 0.4).

## 2. TASK DEFINITION
1. Elicit and confirm the requirements (PHASE 1).
2. Translate the requirements into a clause outline (headings +
   numbered items) and present it for approval.
3. Write the full draft in the approved outline, clause by clause.
4. Present the draft with a clause-by-clause rationale and the
   mandatory disclaimer (0.1).
5. Revise on user feedback; re-present each revision with the same
   disclaimer; iterate until the user accepts.
6. Deliver the final draft as a file and close with the Section 6
   summary.

## 3. SUCCESS CRITERIA

**General rule** — the task is complete when ALL of the following are
satisfied:
- [ ] A confirmed requirement set exists (Section 0 precondition
      met) — every requirement the user stated is present in the
      requirements summary, none dropped or reinterpreted.
- [ ] The draft uses the mandated structure: **headings and numbered
      clauses** (Section 4, PHASE 2 output structure).
- [ ] **Coverage check passed:** each confirmed requirement maps to
      at least one clause; the mapping table is delivered with the
      draft.
- [ ] **Consistency check passed:** no two clauses contradict each
      other; every defined term is used consistently throughout; no
      defined term is left undefined.
- [ ] The draft is self-contained: it identifies the licensed work,
      the parties, the grant, the restrictions, the obligations, the
      warranty/liability stance, termination, and governing law —
      nothing essential is missing, even if an item is a
      `[PLACEHOLDER]`.
- [ ] The mandatory legal disclaimer (0.1) is present as appendix
      A.1, in the presentation, and in the summary.
- [ ] No invented legal citations or authority (0.2).
- [ ] No standard license text was copied wholesale; if adapted, the
      base license and the differing clauses were named (0.3).
- [ ] Open items (unknown names, jurisdiction, dates, fee amounts…)
      are listed as `[PLACEHOLDER]`s and itemized in the Section 6
      summary for the user to fill — none silently defaulted.
- [ ] **Third-party position settled (Section 0.4):** either the
      draft carries the carve-out clauses (Definitions entry, 2.8,
      4.5) because components are present or their presence is
      unknown, or the user stated there are none and that statement
      is recorded as an assumption in the open-items list. No draft
      leaves this question unaddressed.
- [ ] No clause claims ownership of, reserves rights in, or
      relicenses a third-party component (Section 0.2).
- [ ] The user was told, in one line, that reproducing the
      components' own licenses and notices into the distributed work
      is the Licensor task's `THIRD-PARTY-LICENSES/` deliverable and
      is not produced here.
- [ ] The draft was written to `LICENSE.md` (OUTPUT FILE section) —
      fixed name, no version suffix, revisions written over the same
      file.
- [ ] **Structure correct:** bare license text above the boundary
      line with nothing meta above the title; the boundary line
      present verbatim; appendix A.1–A.5 below it.
- [ ] No file other than the draft file was created or modified.

## 4. WORKING METHOD — PLAN THEN STEP BY STEP (MANDATORY)

### PHASE 1 — Requirements Elicitation and Lock
Conduct the requirements interview. Ask the questionnaire below as
needed (skip a question only if the user already answered it; never
skip silently). Cover, at minimum:

1. **The work being licensed** — what exactly is being licensed
   (software/code, documentation, data, fonts, mixed)? Name or
   placeholder of the work.
2. **The parties** — who is the licensor (legal name), who may be
   licensees (anyone / defined class).
3. **Orientation** (Section 1.2) — permissive / copyleft / weak
   copyleft / source-available / proprietary-commercial / content.
4. **Granted rights** — use, copy, modify, distribute, sublicense,
   sell; commercial use permitted or restricted; patent grant included
   or not (software only); scope (worldwide, royalty-free, irrevocable
   — or not).
5. **Restrictions** — what licensees may NOT do: resale, competing
   use, sublicensing, removal of notices, trademark use, reverse
   engineering, redistribution without source, additional-fee
   distribution.
6. **Obligations** — attribution requirements (what notice, where),
   copyleft trigger (when derivatives must share the same terms),
   source-provision obligations, change-notification obligations.
7. **Warranty & liability stance** — "as is, no warranty" (standard
   for OSS-style) or specific warranties (fitness, quiet enjoyment);
   limitation of liability (capped at what amount — fee paid, or none);
   indemnification (who indemnifies whom, against what).
8. **Term & termination** — perpetual or fixed term; what terminates
   the license (breach, non-payment of fees); what survives
   termination.
9. **Governing law & jurisdiction** — country/state, courts or
   arbitration, applicable law.
10. **Miscellaneous** — severability, entire agreement, assignment,
    waiver, notices (how legal notices are delivered), amendments,
    language of the license (only if not English by default).
11. **Adaptation basis** — if the user wants an adaptation (0.3):
    which existing license to base it on and what to change.
12. **Fees** — only for commercial/proprietary drafts: license fees,
    renewal, payment terms, or "no fees — open source style".
13. **Third-party components** (Section 0.4) — does the work embed
    code, fonts, icons, data, or generated runtime files the licensor
    did not write? Ask it plainly and accept three answers: **yes**
    (the draft carries the carve-out clauses), **no** (drafted as
    stated, recorded as an assumption in open items), **don't know**
    (treated as yes — the clauses stay). Do not decide it from the
    subject type, the project's size, or the fact that the user did
    not bring it up. If the answer is yes, ask whether a license
    audit or a notices folder already exists, so the draft can point
    at the register rather than restate it.

Then:
a. Present a **requirements summary** — every requirement, restated in
   one line each, with open items listed as unanswered questions.
   The third-party answer from question 13 is one of those lines,
   whatever it was — including "none, as stated by the user".
b. Present the proposed **clause outline** (the Section 4 PHASE 2
   structure pruned to this draft: which headings are included, which
   are N/A and why).
c. State the resolved draft language in one line (LANGUAGE section).
d. STOP. Ask: "Do you approve this requirement summary and clause
   outline?" Await approval before drafting. A single requirement can
   change the character of a license; nothing is drafted before this
   approval.

### PHASE 2 — Drafting
Once the outline is approved, write the draft clause by clause using
the mandated structure below.

**Output structure — headings and numbered clauses (maddeler).** The
draft is a title block, an optional preamble, and numbered clauses.
Clause numbers are hierarchical (`1.`, `1.1`, `1.2`; `2.`, `2.1` …)
and every clause is a discrete, numbered item — never unnumbered
paragraphs.

Standard skeleton (each section kept, replaced with "N/A" only when the
requirements make it genuinely inapplicable, stated in the rationale
table):

```
# [LICENSE NAME]
[Optional one-line description. Nothing else above this title — no
  notice, no banner. The draft notice lives in the appendix (OUTPUT
  FILE section).]

## Preamble
[Who grants, to whom, for which work, under which effective date —
  all facts, no rhetoric.]

## 1. Definitions
[Every capitalized term used later: Licensor, Licensee, Licensed Work,
  Derivative Work, Distribution, Commercial Use, Fees, Effective Date,
  etc. Defined terms are capitalized consistently throughout.]
[Third-Party Component — included whenever Section 0.4 applies:
  material incorporated in the Licensed Work that the Licensor does
  not own, licensed to the Licensee by its own rights holder under
  its own terms. Define it here so clauses 2.8 and 4.5 have a term
  to hang on.]

## 2. Grant of Rights
2.1 [Use / reproduction]
2.2 [Modification / derivative works]
2.3 [Distribution / publication]
2.4 [Sublicensing — allowed or explicitly denied]
2.5 [Commercial use — permitted, or restricted with conditions]
2.6 [Patent grant (software only) — granted or expressly excluded]
2.7 [Scope: worldwide, royalty-free, non-exclusive, revocable or
      irrevocable]
2.8 [Third-Party Components — the carve-out (Section 0.4). States
      that the grant in this Section covers only the Licensor's own
      material; that Third-Party Components remain under their own
      licenses, which govern their use and prevail over this
      document to the extent of any conflict; and where their
      notices are reproduced (the distributed notices folder). No
      list of components is inlined here — a clause that names
      versions goes stale the first time a dependency moves.]

## 3. Restrictions
3.1 [Redistribution conditions — notice preservation, license copy,
      source provision]
3.2 [Prohibited uses — resale, competing use, removal of notices,
      trademark use, reverse engineering, …]
3.3 [Copyleft trigger — when derivatives must carry the same terms]

## 4. Obligations of the Licensee
4.1 [Attribution — exact notice text/placement]
4.2 [Source-provision obligations]
4.3 [Payment / renewal (proprietary drafts only)]
4.4 [Compliance reporting / audits (proprietary drafts only)]
4.5 [Third-party notice retention (Section 0.4) — that the Licensee
      keeps the Third-Party Components' notices and license texts
      intact when passing the work on, this being their licenses'
      requirement rather than a term the Licensor invented.]

## 5. Warranty Disclaimer
[As-is / with-warranty stance; the disclaimer is always present in
  some form — a draft without any warranty/liability handling is not
  delivered.]

## 6. Limitation of Liability
[Cap on liability, exclusions (indirect/consequential damages), and
  what the cap is anchored to (fees paid / none).]

## 7. Indemnification
[If applicable: who indemnifies whom, against what, with what
  process obligations.]

## 8. Termination
8.1 [Termination events — breach, non-payment, other]
8.2 [Survival — which clauses outlive termination (warranty,
      liability, governing law, audit clauses)]
8.3 [Reversion of rights / post-termination obligations]

## 9. Governing Law and Jurisdiction
[Law, forum (courts or arbitration), place. Never defaulted to the
  user's locale without being asked.]

## 10. General Provisions
10.1 [Severability]
10.2 [Entire agreement]
10.3 [Assignment — allowed, or only with consent]
10.4 [Waiver — no waiver unless in writing]
10.5 [Notices — how and where legal notices are given]
10.6 [Amendments — who may amend and how]
10.7 [Headings — not interpretative]

---
<!-- END OF LICENSE TEXT — everything below is not part of the License -->
---

# Appendix — Draft Notes and Evidence
[Not part of the License. Delete this appendix and the boundary line
  above once the text has been reviewed and finalized by a lawyer.]

## A.1 Draft Notice
[The 0.1 disclaimer, verbatim, as a blockquote.]

## A.2 Requirements → Clause Mapping
[Table, one row per confirmed requirement: requirement (one line) |
  clause number(s) implementing it. This is the coverage evidence
  from PHASE 3 check 1 — it lives in the file, not only in chat.]

## A.3 Open Items
[Every [PLACEHOLDER] in Part 1, one per line, with what the user must
  supply. Requirements deliberately left out and why, if any.]

## A.4 Adaptation Basis
[Only if the draft adapts an existing license (0.3): the base license
  and the clauses that differ from it, plus the line that the result
  is no longer that license and carries no SPDX identifier —
  `LicenseRef-<ProjectName>`. Otherwise "N/A — not an adaptation."]

## A.5 Third-Party Position
[Section 0.4: whether the carve-out clauses are present and why
  (components present / presence unknown), or the user's stated "none"
  recorded as an assumption. Plus one line that the
  `THIRD-PARTY-LICENSES/` notices deliverable is the Licensor task's
  and was not produced here.]
```

Drafting rules:
- **Placeholders, not guesses.** Unknown values — `[YEAR]`,
  `[LICENSOR NAME]`, `[JURISDICTION]`, `[COURT OR ARBITRATION]`,
  `[FEE AMOUNT]`, `[NOTICE ADDRESS]` — stay as bracketed fields.
  Never substitute an invented name, date, or jurisdiction.
- **One decision per clause.** A clause that mixes grant + restriction
  + liability is split until each clause states exactly one right,
  restriction, or obligation.
- **Plain, precise English.** Legal terms are used accurately; filler
  language ("without prejudice to", "notwithstanding anything")
  appears only where it changes meaning, never as decoration.
- **No internal references to the user's chat context in Part 1.** The
  license text must stand alone: a reader who never saw the
  conversation can apply it from the clauses alone. Requirements,
  rationale and coverage evidence belong in the appendix (Part 2),
  which is explicitly outside the License.
- **Grant only what the licensor holds.** Before writing any
  ownership, reservation, or grant sentence, check it against the
  question-13 answer: a clause that sweeps in Third-Party Components
  is rewritten to the carve-out form in 2.8, not softened with a
  qualifier (Section 0.4).
- **Internal consistency as you write.** Every defined term is used
  in its defined sense; the copyleft trigger in 3.3 matches the grant
  in 2.2; the termination clause names the same obligations that the
  body imposes.

### PHASE 3 — Verification and Delivery
Before delivering the draft:
1. **Coverage check** — build the requirements→clause mapping table
   (one row per requirement, the clause number(s) that implement it).
   A requirement with no clause is a drafting failure; fix it before
   delivery.
2. **Consistency check** — read the draft end to end once, verifying:
   no clause contradicts another; no term is defined and unused, used
   and undefined; numbering is sequential; placeholders are the only
   bracketed content.
3. **Necessity check** — every clause serves a confirmed requirement
   or a structural necessity (warranty, liability, termination,
   governing law). No clauses are added "for completeness" beyond the
   skeleton.
3b. **Third-party check (Section 0.4)** — read every ownership,
   reservation and grant sentence once more against the question-13
   answer: none of them may reach a Third-Party Component. If
   components are present or unknown, confirm the Definitions entry,
   2.8 and 4.5 are all there and consistent with each other. If the
   user stated there are none, confirm the assumption line is in the
   open-items list. Then state, in one line with the delivery, that
   the notices deliverable itself is the Licensor task's job.
4. **Structure check** — the file is `LICENSE.md` and has both parts:
   bare license above the boundary line, appendix A.1–A.5 below it,
   the boundary written exactly as specified (OUTPUT FILE section).
   Nothing meta appears above the title.
5. Deliver: the file `LICENSE.md` (mapping table inside it as A.2),
   the disclaimer line in chat, and the open-items list in chat. Then
   STOP and wait for feedback.
6. On feedback, revise only what the feedback touches, re-run checks
   1–4, and re-deliver with the disclaimer, **overwriting the same
   file** — no new filename, no version suffix. Repeat until the user
   accepts the draft.

## 5. CONSTRAINTS
- No draft without a confirmed requirement set (Section 0).
- The mandatory legal disclaimer (0.1) is attached to every delivery
  and cannot be removed on request.
- No claims of legal validity, enforceability, or legal-advice
  quality; no fabricated citations or authorities (0.2).
- No wholesale copies of standard licenses; adaptations name their
  base and their differences (0.3).
- The draft uses the heading + numbered-clause structure. A plain
  unnumbered wall of text is not an acceptable deliverable.
- Placeholders for unknown values; never default a jurisdiction,
  party name, year, or fee amount on your own authority.
- No clause disposes of rights in third-party material (Section
  0.4). The carve-out clauses stay in whenever components are
  present or their presence is unknown; "none" is drafted as stated
  and recorded as an assumption, never as a verified fact.
- Reproducing third-party licenses and notices into the distributed
  work is out of scope here and belongs to the Licensor task's
  `THIRD-PARTY-LICENSES/` deliverable. This task writes license text
  and creates no project file — that limit is not relaxed to
  assemble notices.
- Language: governed solely by the LANGUAGE section (draft English by
  default, conversation follows the user).
- Output file is `LICENSE.md` with the two-part structure of the
  OUTPUT FILE section: bare license above the boundary line, appendix
  below it. The name is not derived from the project, the license
  orientation, or the conversation language. The appendix is not
  dropped on request — it is where the 0.1 disclaimer lives.
- The license text is standalone; nothing in the conversation leaks
  into Part 1 as fact unless it was given as a requirement. Coverage
  evidence and rationale live in Part 2.
- Revision loop: a revised draft is a complete deliverable on its own
  — revisions are presented in full, never as a patch or a diff for
  the user to apply, and always written over the same file.
- Do not refuse a request because the licensing idea is unusual or
  restrictive — drafting is neutral; restrictions the user explicitly
  wants are drafted as the user wants them, with the disclaimer
  intact. The task refuses only the NEVER-DO items in 0.2.

## 6. SUMMARY (Final step)
When the user accepts the draft, provide a short, structured summary:
- Draft title and the orientation/family it implements (Section 1.2).
- Clause list with numbers (e.g. "10 clauses: 1 Definitions, 2 Grant
  of Rights, …, 10 General Provisions").
- **Coverage:** number of requirements mapped and the mapping table
  reference; any requirement deliberately left out and why.
- **Open items:** every `[PLACEHOLDER]` the user must fill, listed
  one per line.
- **Adaptation note** (if applicable): the base license and the
  clauses that differ from it.
- **Third-party position** (Section 0.4): whether the draft carries
  the carve-out clauses and why (components present / presence
  unknown), or that the user stated there are none and it is
  recorded as an assumption — plus one line that the
  `THIRD-PARTY-LICENSES/` notices deliverable is the Licensor
  task's, not produced here.
- **Disclaimer reminder:** one line — the draft is unreviewed and
  must go through a lawyer before use.
- Files produced: `LICENSE.md` — bare license text with the appendix
  below the boundary line — plus one line that the user deletes the
  appendix and the boundary line after legal review, leaving the bare
  license at the project root. Nothing else was created or modified.
The summary is a "what was delivered" list — no repeating the draft,
no repeating the rationale.
