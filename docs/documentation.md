# How We Work

This page explains how we document, branch, and review code. If you're new, read it once top to bottom (about 10 minutes). After that, use it as a reference.

---

## The four ideas behind everything

1. **Docs live next to the code.** Same repo, same pull request, same review. If the code changes, the docs change with it.
2. **Agree on the interface before building.** Before writing code, write down what goes in and what comes out: the API route, the database table, the message format. Get that approved first. Then build.
3. **Write down the "what" and the "why", not the "how".** Document things that stay true for a long time: boundaries, data shapes, rules, and trade-offs. Don't explain every internal function. That changes too often and nobody keeps it up to date.

---

## Where docs go

Every repo has a `docs/` folder. `docs/README.md` is the front page and links to everything else.

```
your-repo/
├── docs/
│   ├── README.md          # Start here: links to everything
│   ├── setup.md           # How to run the project locally or in prod
│   ├── architecture/      # Component specs and system overviews
│   ├── adr/               # Decision records (see below)
│   └── diagrams/          # Diagrams
```

**You don't need all of this on day one.** Start with `README.md` and `setup.md`, then add folders when you have something to put in them.

| What | Where | What it's for | When to update |
|---|---|---|---|
| Decision record (ADR) | `docs/adr/` | Why we chose X over Y | Written once per big decision. Rarely edited after. |
| Component spec | `docs/architecture/` | What a component does, its inputs and outputs, and its rules | Whenever its behavior or data shapes change |
| Setup guide | `docs/setup.md` | How to get the project running | When dependencies, ports, or Docker services change |
| Diagram | `docs/diagrams/` | Pictures of data flow, sequences, and topology | When the architecture changes |

---

## Writing a decision record (ADR)

An ADR answers the question your future teammate will ask: *"Why on earth did we do it this way?"*

Write one when you make a choice that is hard to undo, or that people will wonder about later. **Keep it to one page.**

- File name: `docs/adr/0001-short-title.md` (increase the number each time)
- Once accepted, don't rewrite it. If you change your mind, write a new ADR and mark the old one "Superseded".

```markdown
# ADR 0001: Short title of the decision

- **Status:** Proposed | Accepted | Deprecated | Superseded by ADR XXXX
- **Date:** YYYY-MM-DD
- **Who decided:** names

## The problem
What are we trying to solve? Include any limits that matter
(speed, storage, team size, deadlines).

## Options we looked at
1. **Option A:** one-line description
2. **Option B:** one-line description
3. **Option C:** one-line description

## What we chose
Option X, because (the main reason in one or two sentences).

## What we gain
- ...

## What it costs us
- The downside we're accepting
- How we'll live with it
```

---

## Writing a component spec

A spec describes one component: what it's responsible for and what it promises. Save it as `docs/architecture/<component>-spec.md`.

```markdown
# Component name

## What it does
Its one job. Also say what it does NOT do.

## How to talk to it
The inputs and outputs, for example:
- `methodName(Input) -> Result<Output, Error>`

## Rules it always follows
- Example: the same input always gives the same output.
- Example: invalid requests return a clear error and never change any data.

## Edge cases and failures
- What happens when X goes wrong?
- What happens when Y is empty or huge?

## Data formats
Link to the schema files (`.proto`, `.sql`, etc.) that define the data.
```

---

## Diagrams

We use [Excalidraw](https://excalidraw.com). All diagrams go in `docs/diagrams/`.

1. Draw it in Excalidraw.
2. Export as **SVG** and tick **"Embed scene"**. This keeps the diagram editable.
3. Name the file `<what-it-shows>.excalidraw.svg`.
4. Show it in a doc with `![Topology](../diagrams/topology.excalidraw.svg)`.

GitHub shows the image right in the page. To edit it later, drag the `.svg` back into Excalidraw.