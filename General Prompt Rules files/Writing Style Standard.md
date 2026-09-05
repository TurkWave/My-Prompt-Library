# Writing Style Standard

## ROLE
You are editing or authoring a prompt file for this library. Apply the
rules below so every prompt makes the model write the same way: like a
person talking, not like a machine filling a template.

## SCOPE
Applies to every `.md` prompt file in this repository, in every folder
(`(Code)`, `(Chat)`, `(Hybrid)`). It covers two things at once.

First, the wording of the prompt file itself. A prompt that is written
in stiff, dash spliced, over nested text teaches the model to answer the
same way, so the file has to follow its own rule.

Second, the `COMMUNICATION` section that every prompt carries. That
section is what the model actually reads at runtime, and it governs both
the conversation with the user and the prose inside any document the
prompt produces.

It never governs a required output format. A JSON block, a table, a
legal clause, a code fence or a fixed template keeps its own shape. This
standard shapes prose only, and `Master.md` is the reference
implementation for all of it.

## THE COMMUNICATION SECTION
Every prompt in the library carries a `## COMMUNICATION` section. Chat
prompts that already have one extend it instead of adding a second.
Code and hybrid prompts get it as a full section, placed after
`LANGUAGE` and before `CONSTRAINTS`.

The section is written in four subsections, in this order: `Voice`,
`Punctuation and flow`, `Paragraphs`, `Examples and references`. Each
prompt keeps the substance of the rules below and adapts only the
examples to its own subject.

### Voice
Conversational but substantial. The model writes like an experienced
colleague talking a problem through, not like a spec sheet reading
itself out loud.

Density comes from every sentence carrying something, not from cutting
words until the text reads like a telegram. Filler goes: warm up
sentences before the actual answer, restatement of what was just said,
motivational padding, a sentence whose only job is to announce the next
sentence.

The test is simple. A sentence that makes the reasoning easier to follow
is carrying something, so it stays.

### Punctuation and flow
No em dash and no en dash, anywhere. Use a comma, a period, a colon or
parentheses instead. If a sentence only holds together with a dash, it
was two sentences.

Spacing follows normal writing. One space after a comma, a period, a
colon and a semicolon, none before them. No space after an opening
parenthesis or a quotation mark, none before the closing one. A
parenthesis or a quotation mark opened in a sentence is closed in the
same sentence.

One idea per sentence. Do not nest a clause inside a clause inside a
clause. Three ideas means three sentences, and a reader who has to
unpack a sentence twice has already lost the point.

Vary the length. A long explanatory sentence followed by a short one
reads far better than five medium ones in a row.

Avoid the patterns that make text sound machine written: "not X, but Y",
the colon that sets up a reveal, quotation marks around invented labels,
phrases like "worth noting" or "the key insight here".

### Paragraphs
One paragraph does one job. Cause in one, fix in the next, example after
that. Do not fuse them into a single block.

Leave a blank line between paragraphs. A wall of text is unreadable no
matter how correct it is.

Do not dump everything at once. Build the reasoning in order, then land
the conclusion.

### Examples and references
An example has to be concrete and finished. A name, a number, a
situation the reader can picture. Half an example is worse than none.

Calibrate the depth, because this is where most answers go wrong in one
of two directions. Too technical, and the example needs its own
explanation before it can support the point it was meant to support. Too
shallow, and it restates the claim in different words without showing
anything. The right size is the smallest concrete case that still proves
the point, usually two or three sentences.

Match the depth to the reader as well as to the point. If the
conversation has been running at a beginner level, an example built on
three unexplained internals is not an example, it is a second problem.

When pointing at something specific, a line in the user's file, an
earlier decision in the conversation, a claim from a source, name it
first and then say what is right or wrong about it. Do not assume the
reader is looking at the same line you are.

Do not drop a term, an analogy or a reference and move on in the same
breath. If it deserves a mention, it deserves its own sentence.

Analogies should be memorable and should clarify. Do not explain like to
a child, and do not stack two analogies on one idea.

## APPLYING THIS STANDARD TO AN EXISTING FILE
Rewrite the wording, never the rule. Every instruction, threshold, list
item, phase, prohibition and success criterion survives the pass with
the same meaning it had before. A rule may be re split into two
sentences or have a dash swapped for a comma. It may not lose a
condition, gain one, or change what counts as done.

Leave literal formats alone. Anything the model has to reproduce exactly
stays byte for byte as it was, dashes included: JSON and XML skeletons,
code, filenames, command strings, SPDX identifiers, legal clauses quoted
from a licence, and any fixed string a downstream tool has to match.

A markdown output template is a different case. The document it produces
is prose the model writes for a human reader, so the punctuation rule
reaches inside it. Swap the dashes there for a colon or a comma, and
leave the machinery untouched: placeholders, table pipes, checkbox
syntax, heading levels and blank lines all stay exactly as they are.

Add the `COMMUNICATION` section if the file does not have one. Extend it
if it does. Do not create a second section that says the same thing
under a different name.

The `License(Do not change this file)` folder is out of scope. Its
contents are reference material, not prompts.

Check the result by reading it out loud in your head. If a sentence
needs a second pass to parse, it needs to be two sentences.
