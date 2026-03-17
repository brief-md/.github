# BRIEF.md

An open format for persistent, portable, user-defined project context.

---

## The Problem

When you plan a complex project in an AI chat, decisions get made, constraints get set, direction gets clear. As the conversation grows, the AI compacts it to manage the context window, keeping what it thinks matters, which isn't always what matters to you.

Starting a new session means re-explaining the project, or copying across old conversations, which fills the new context with stuff you don't need.

Come back to the project after a break and the same problem exists for you personally, the intent and decisions are somewhere in your head, or scattered across documents and chat histories.

**BRIEF.md is a simple fix.** A structured file that captures what matters, decisions, intent, constraints, open questions, chosen by you. It lives in your project folder, persists across sessions, and gives any tool the context it needs from the start.

---

## How It Works

README explains how a project works. BRIEF.md captures what it is and why it exists.

Projects already use files like README.md, CONTRIBUTING.md, and package.json to help tools understand them. BRIEF.md extends that convention to intent and reasoning. Like Git stores the history of your code, BRIEF.md stores the history of your thinking.

### The Format

A `BRIEF.md` file sits at the root of any project. Plain markdown. No lock-in.

The example below shows the minimum structure. See the specification for the full format.

```markdown
**Project:** New Project
**Type:** project
**Created:** 2026-03-16

# What This Is
A short description of what this project is.

# Why This Exists
The reason this project exists and what it is trying to achieve.

# Key Decisions
- A decision that was made and should be remembered
- Another decision with the reason behind it

# Open Questions
- Something that still needs to be resolved
- A question that needs an answer before moving forward
```

The file is useful the moment it exists. You decide what goes in it.

The format supports hierarchy. Tools that implement it can walk up the directory tree, picking up context from each parent BRIEF.md they find, so a single project carries its own context and a collection of projects carries the bigger picture around it.

```
company/
    BRIEF.md              # top level context
    project-a/
        BRIEF.md          # can inherit company context, adds its own
        feature-x/
            BRIEF.md      # can inherit both, adds feature-level detail
```

-> [Read the full specification](https://github.com/brief-md/spec)

---

### The MCP Server

Think of **brief-mcp** as a note taker while you chat, and a boot loader that fires when you start a new session.

As you chat, it builds your project's scaffolding as BRIEF.md files in the background, capturing the decisions, constraints, and open questions that matter to you. When you return to a project after a break, you have a clean structured record to come back to rather than digging through chat histories or trying to piece things together from memory. It starts briefed.

Because BRIEF.md is just a file, any tool can read it. Plan in ChatGPT, code in Cursor, review in Claude — all referencing the same BRIEF.md means rather than hunting through a lengthy document or chat history to find what actually matters, it's already distilled and ready.

```bash
npx brief-mcp ~/your-projects
```

-> **[Get started with brief-mcp](https://github.com/brief-md/brief-mcp)**

---

## How It Differs

Memory solutions like Graphiti and DevContext automatically capture context from your sessions and store it in knowledge graphs or databases. They are powerful but require infrastructure and decide what to remember. BRIEF.md is a plain text file, no complex setup, no black box, that captures what you decide matters and is readable without any tooling.

---

## Beyond the Basics

The core format works for any project in any domain, whether that is a film production, a legal case, a research study, a software product, a music release, an architectural brief, or a business venture. BRIEF.md is built to extend, type guides add domain-specific structure and extensions let communities define the vocabulary and metadata that matters in their field.

The MCP server is the first tool in a growing ecosystem. Integrations with creative software, voice capture, chat-based collaboration, and export tools are all on the roadmap, each built on the same principle: your context, your file, readable by any AI-enabled tool. Context belongs to the project, not the AI tool. AI tools shouldn't own the thinking — the project should.

---

## Contributing

We're early. The spec and MCP are the foundation, the ecosystem is what gets built on top.

If you want to build an integration, write a type guide for your domain, or contribute to the core tools, start here:

If you want to add BRIEF.md support to your tool or service, we'd love to hear from you.

-> [CONTRIBUTING.md](https://github.com/brief-md/.github/blob/main/CONTRIBUTING.md)
-> [hello.briefmd@gmail.com](mailto:hello.briefmd@gmail.com)

---

## Licence

Specification: **CC-BY 4.0** - Tools: **MIT**

---

*BRIEF.md - [Specification](https://github.com/brief-md/spec) - [White paper](https://doi.org/10.5281/zenodo.18614773)*
