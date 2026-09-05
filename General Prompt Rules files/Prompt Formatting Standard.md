# Prompt Formatting Standard

## ROLE
You are editing or authoring a prompt file for this library. Apply the
rules below so every prompt in the repository shares one structural
shape, regardless of which folder or output type it belongs to.

## SCOPE
Applies to every `.md` prompt file in this repository, in every folder
(`(Code)`, `(Chat)`, `(Hybrid)`). It governs structure and formatting
only, never the behavioral content of a prompt. For how the prose
itself is written, see `Writing Style Standard.md` in this folder.

## HEADING HIERARCHY
- Exactly one `# Title` at the very top of the file, matching the
  file's own name (drop the extension, keep the casing readable).
  Followed by one blank line.
- Every major functional section (`ROLE`, `CONTEXT`, `TASK`,
  `LANGUAGE`, `SUCCESS CRITERIA`, `WORKING METHOD`, `COMMUNICATION`,
  `CONSTRAINTS`, etc.) is a real Markdown `##` heading. Never a bare
  all-caps line, never a bold-only label standing on its own.
- A sequential or enumerated subdivision inside a major section is a
  `###` heading nested under its parent `##`. That covers a numbered
  layer, a lettered phase or a step (`Phase 1`, `Phase 2`, `Layer 1`).
- Go past `###` only when the section itself is already organized in
  three real levels. See the `PHASE 2` breakdown in `spdx.md` for the
  one legitimate `####` case in this library. Do not manufacture a
  fourth level for a two item list.
- Everything shallower than that stays as **bold** lead-in text or a
  bullet, not a heading. That covers a named rule, a sub-case and a
  short lead-in inside a paragraph. Turning every named idea into its
  own heading is over-tagging. It inflates the outline and buries the
  sections that matter. The "Avoid Over-Tagging" rule in `md to xml
  converter (Cli model).md` says the same thing, and it applies to
  this library's own files, not just to XML conversion.
- Never mix an unmarked plain-text or bold-only label with real
  headings in the same file. Pick one, and it is always the heading
  form.

## SECTION VOCABULARY
Reuse these names verbatim when the concept applies. Do not invent a
synonym for a concept this list already names.
- `ROLE`, who or what the model is for this task. Omit it only when
  the file's title already states it unambiguously, for example a
  short single-purpose converter.
- `CONTEXT`, the situation the prompt operates in.
- `TASK` or `TASK DEFINITION`, what has to be produced.
- `LANGUAGE`, the two-channel rule (see LANGUAGE below). Every file
  that produces written output needs this section stated once, not
  re-derived per file.
- `SUCCESS CRITERIA`, the checklist that defines "done."
- `WORKING METHOD`, the two-phase plan-then-execute pattern (see
  WORKING METHOD PATTERN below), for any task substantial enough to
  need a plan.
- `COMMUNICATION`, how the model writes: voice, punctuation and flow,
  paragraphs, examples and references. Every prompt carries this one,
  chat and code alike, and its content comes from `Writing Style
  Standard.md`. In a code prompt it governs the conversation and the
  prose inside produced documents, never a required output format.
- `BEHAVIOR`, what the model does turn by turn. Chat-style prompts use
  it in place of TASK, SUCCESS CRITERIA and WORKING METHOD.
- `CONSTRAINTS`, hard boundaries phrased as prohibitions or limits,
  placed last.
- `EXAMPLES`, worked input and output pairs, when they materially
  clarify behavior a rule alone cannot pin down.

## LANGUAGE
Every file that can produce a written artifact states the same
two-channel rule, once. Output and files default to English and switch
only on an explicit request or an explicit target-language variable.
Conversation follows whatever language the user is actually writing in,
switching immediately, and never drags the file language along with it.
See `Language Standart.txt` in this folder for the rule in its original
form.

## WORKING METHOD PATTERN
For any task that produces a deliverable through multiple steps:
- **Phase 1, inspect, plan, lock in.** Inspect the actual input before
  proposing anything. Produce a full numbered plan, including
  task-specific success criteria. Present the plan and stop. Do not
  execute until the user responds, and if silence or non-objection
  counts as approval, state that explicitly in the file.
- **Phase 2, execute one step at a time.** Work the steps in order,
  never batched. State the step, do the work, report the concrete
  result before moving on. Define exactly three escalation tiers: a
  minor adjustment (flag and continue), a major adjustment (stop,
  explain, re-propose, wait), and a critical decision point (stop and
  ask directly, never pick silently).

## EVIDENCE & APPROVAL DISCIPLINE
- Never assume a fact the source material does not state. Flag the gap
  instead of inventing content, a feature, a claim or a requirement.
- Every finding or claim that matters to the output cites where it came
  from, a file and line, a quoted source, a fetched page, wherever the
  prompt already has that machinery.
- A judgment call with more than one valid resolution is a question to
  the user, not a silent pick. This rule and the WORKING METHOD's
  "critical decision point" tier are the same rule stated twice, so
  keep them consistent and do not contradict one with the other.

## APPLYING THIS STANDARD TO AN EXISTING FILE
When bringing an existing prompt into line with this standard:
- Touch structure and formatting only: heading markup, heading levels,
  the title line. Never remove, reorder, shorten or drop a single rule
  of the prompt's actual content while doing this pass. Rewording for
  the writing standard is a separate pass, governed by `Writing Style
  Standard.md`, and it preserves every rule's meaning.
- If a file already satisfies every rule above, leave it untouched. Do
  not restructure a compliant file just to make the diff look busier.
- Verify the result with a word-level diff against the original. In a
  structure-only pass the only lines that may change are heading-marker
  lines: added `#`, `##` or `###` prefixes, an added title, an added
  blank line. Any other change means the pass went further than
  formatting and must be reverted to just the structural fix.
