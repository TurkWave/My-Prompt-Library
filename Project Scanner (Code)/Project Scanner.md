# Project Scanner

## TASK

Inspect the project files in hand (codebase, config files, dependency files like package.json/requirements.txt/pyproject.toml/pom.xml/*.csproj, folder structure, .env.example, README, existing migration/ORM files, CI/CD config files, etc.), fill in the `Project.md` template below, and save the filled version to the project root directory under the name `project.md`.

## RULES

1. **Fill in only the information you can actually detect.** Write down things that are explicitly visible/provable in the codebase, config files, or dependencies. Do not add guesses, assumptions, or "it's probably like this" type of information.
2. **Leave blank any field you are not sure about or cannot clearly extract from the codebase.** Leaving it blank is better than writing "-" or making up something generic.
3. **In cases where multiple plausible interpretations can be drawn, conflicting signals exist, or critical decisions are involved** (e.g., unclear topics such as which architectural decision was intentional, auth strategy, deploy trigger), ask me as a question instead of filling it in; do not guess and write.
4. **Preserve the structure, headings, section order, and emoji markers (🟢 CORE, 🟡 EXTENDED, 🔴 ADVANCED) of the template verbatim.** Do not delete, rename, or merge any headings.
5. Even if a section seems completely irrelevant to the project (e.g., if a small script project has no CI/CD), **do not delete** that section; leave it blank as it is.
6. Update code blocks (Folder Structure, Installation, Environment Variables) according to the actual project structure — write the folders/commands/env variables that actually exist in the project instead of placeholder content. Write **only the names, not the values** of the env variables (do not leak secrets).
7. In subjective/decision-based sections like "Coding Rules", "Architectural Decisions", "Error Handling Strategy", detect and write the patterns that are **actually applied** in the codebase (e.g., describe a global error handler if one actually exists); otherwise leave blank.
8. At the very top of the template, before the `CORE` section, there is a **"Project Summary"** section. Keep this section concise and brief: a fluent paragraph of 3-5 sentences explaining only what the project does and which main technologies it was built with, without going into detail. Do not use bullet points, and do not enter technical details (folder structure, version numbers, architectural decisions, etc.) — someone reading it without knowing the project at all should be able to understand what it is.
9. **Language:** every file you create or update (`project.md`, `Latest Regulations and Actions.md`, and any other output file) is **always written in English**, no matter which language I use in the conversation — file content never switches language. Only the conversation itself can change: reply in English by default, and switch to another language only if I explicitly ask for it or if I write to you in that language. Section headings, emoji markers, and the template's field names always stay exactly as written in the template.
10. When you finish the process, give me a brief summary: which sections you were able to fill out, which ones you left blank because you couldn't find clear evidence, and any questions you want me to clarify, if any.

## TEMPLATE (fill in using exactly this structure)

```markdown
# Project.md

- **Usage:** Small/personal project → fill in only the `CORE` section.
- As the project grows and the codebase becomes complex → open and fill in the relevant `EXTENDED` section.
- When team / prod / real users come into play → open and fill in the `ADVANCED` section.
- **Do not delete** the sections you don't fill out, leave them blank — it shows when you will need them.

---

## 💾 Where the Latest Adjustments are Saved
- The place where the latest changes are written;
- [Latest Regulations and Actions.md](Latest%20Regulations%20and%20Actions.md)

---

## 📌 Project Summary
[Explain what the project does and which main technologies it was built with, in a fluent paragraph of 3-5 sentences, without going into detail.]

---

## 🟢 CORE (fill in every project)

## Project Description
- Project name:
- What it does (1-2 sentences):
- Who it is for:

## Tech Stack
- Backend:
- Frontend:
- Database:
- ORM:

## Folder Structure
```txt
src/
├─ modules/
├─ shared/
├─ infrastructure/
├─ config/
└─ tests/

```

## Installation

```bash
# commands to run after clone

```

## Environment Variables

```env
# .env.example
DATABASE_URL=

```

## Coding Rules

### Allowed

* [rule]

### Forbidden

* [rule] — [reason]

---

## 🟡 EXTENDED (open as the project grows)

## Architectural Decisions

> Write a 1-sentence "why" next to each choice — you will need it in 6 months.

* [Decision] — [reason]

## Fine Tuning

* Realtime:
* Cache:
* Queue:
* Container:
* Auth: (Authentication / Authorization)
* Storage: (File Storage)

## API Contract

* Style: (REST / GraphQL / RPC)
* Versioning: (e.g., `/v1/`)
* Response format: (success/error envelope standard)

## Database / Migration Strategy

* Migration management: (automatic / with review)
* Naming convention:

## State Management (Frontend)

* Global state tool:
* Server state / cache tool:

## Error Handling Strategy

* Global error handling approach:
* Custom exception structure:

## Dependencies

* Dependencies:

---

## 🔴 ADVANCED (team / prod level)

## Debug & Observability

* Monitoring:
* Logging:
* Testing:

## Security

* Rate limiting:
* CORS policy:
* Input validation: (Zod / Joi / class-validator etc.)

## CI/CD

* Pipeline tool:
* Deploy trigger: (push to main / manual)

## Environments

* dev / staging / prod differences:

## Cloud

* Provider:
* Services:

## Versioning / Release

* Semantic versioning:
* Changelog management:

## Team Conventions

* Commit format: (e.g., Conventional Commits)
* Branch naming: [format]
* PR template / code review rules:

## Coding Standards

* Formatter: [tool and setting]
* Linter: [tool]
* Import order: [tool]

---

```

Now scan the project and create the `project.md` file according to the rules above.

---