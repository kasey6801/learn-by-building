# Learning by Building: A Framework for Non-Developers Who Want to Ship Things That Matter

---

## Overview

This document describes how I approach building software solutions without being a software developer. I'm sharing it, in the spirit of open source, for executives, technical program managers, and anyone curious about using code as a tool rather than a career. This is not prescriptive. It's simply what works for me, documented honestly in case it's useful to others.

The foundation of my approach is code is a tool, not a profession. As a pilot, I can fly the plane, but I depend on mechanics, air traffic control, ground crews, and countless others to make flying possible. My job is to get us to the destination safely and purposefully; their job is to make sure everything required to do that is working. Working with code is no different. I don't need to be a developer to direct the creation of software; I need to know where I'm going, plan the route, and use the right tools to get there. What I do need is a structured approach, the right tools, and the discipline to plan before I build.

Everything described here was developed through real projects.

---

## The Philosophy: Code as a Tool, Not a Career

My goal is not to learn to code. That will happen as a byproduct, and it's welcome as it does, but it's not what I'm after. What I'm developing is the ability to *work with code and coding tools to deliver solutions*; to turn a practical idea into a working solution using the tools available to me.

That distinction matters to me. "Learning to code" implies a long apprenticeship before anything useful gets produced. "Working with code as a tool" is different: I identify a problem, I plan a solution, and I use AI coding tools to execute that plan, much like understanding the math well enough to set up the problem correctly, then using a calculator to work through it and validate the answer. The calculator doesn't replace the thinking, it executes and confirms it.

The skills I'm building through this approach go beyond any single tool or project. The discipline of structured planning, the habit of scoping carefully, the ability to evaluate technical tradeoffs, and the practice of documenting decisions are all directly applicable to software design and product management. And while I'm currently using Claude and VS Code, the underlying method; plan thoroughly, execute deliberately, reflect and adjust; isn't tied to those tools. It transfers to whatever tools come next.

---

## Choosing the Right Project

I take time choosing what to build. The right project compounds learning at every step; the wrong one just compounds frustration.

Three questions guide how I think about this:

**"What could make life better or easier for myself and others, that can be addressed with data and/or code?"** I'm looking for usefulness here. A project that solves a real problem, even a small one, produces something worth using when done, and provides feedback on whether I built the right thing.

**"Would this be a good learning opportunity?"** I want each project to stretch my understanding in at least one meaningful direction; learning how a new tool works, encountering a type of problem I haven't handled before, or simply practicing the planning process itself with a different kind of challenge.

**What would an MVP or v1 scope look like? Is this overly complex?** This is the constraint I consider carefully. The temptation to build the full vision in v1 is real, and it's the most reliable way to stall. A v1 should do one thing well. Future versions can do more.

These questions take time to answer well. I let ideas develop, stress-test them, and ask myself honestly whether the scope is manageable. Time spent here is never wasted.

---

## The Planning-First Approach

Roughly 80% of my time on any project is invested before a single line of code is written.

I do my planning through structured conversation with Claude in a chat session. The conversation starts with the problem and moves progressively through product decisions: what to build, what technology to use, how the system will be structured, what the user experience will look like, and how to handle edge cases. Each decision builds on the one before it. Claude acts as a combination of teacher, technical architect, product planner, and document author, capturing decisions in a complete, annotated build plan.

By the end of the planning session I have a detailed build plan broken down into phases; a document that describes what to build, in what order, with what tools, and what a successful result looks like at each step. That plan is the primary output of this phase and the primary input to everything that follows.

---

## The Development Workflow

Once the plan is complete, development happens in VS Code using Claude Code. The plan from the chat session becomes the direct input: phase prompts are copied into VS Code, which executes each phase and produces working code.

The separation, planning in Claude chat, building in VS Code is deliberate. The chat session is the right environment for open-ended exploration, decision making, and document creation. VS Code with Claude Code is the right environment for execution: structured, file-aware, and capable of managing a multi-phase build across multiple sessions.

The plan is written to anticipate that handoff. Phase prompts are formatted as copy/paste ready blocks. Verification steps tell me exactly what to look for before moving to the next phase. Context management checkpoints are built into the plan at natural phase boundaries to keep Claude Code's working memory focused and efficient across a long build.

---

## Quality Assurance: Built Into the Plan

I include QA in my plans. Testing is not an afterthought. Test steps are built directly into the build plan, with specific checks defined at each phase. Before moving forward, there's a concrete, observable success criterion: something I can see, confirm, or verify by interacting with the product.

That said, my approach to QA is still evolving. I'm working through what actually catches real problems early, what's practical to execute without deep technical knowledge, and what gives me the most confidence that the build is on track. I'll be refining this as I move through more projects. The goal is a QA approach that's genuinely useful.

---

## An Evolving Practice

Nothing about this approach is fixed. The planning process, the QA strategy, the way I document decisions. All of it will shift as I work through more projects and develop a clearer sense of what actually works.

That's intentional. I'm not trying to follow a specific process: I'm trying to develop a personal practice that gets more effective with each iteration. Each project produces not just a working piece of software but a better understanding of how to run the next project. The documentation I create along the way; the plan, the session summary, the meta documents are a record of that learning and something I can share and build on.

---

## What I'm Developing Along the Way

These projects are primarily a learning opportunity. The skills I'm building extend beyond any individual thing I build:

**Structured planning.** Thinking through a problem completely before committing to a solution is a habit that's valuable in any professional context.

**Scope discipline.** Asking "what does a Vv look like, is it overly complex?" is something I apply to every project. It's directly applicable to product management, project planning, and any effort where over engineering is a temptation.

**Technical literacy.** Working through architecture decisions, technology comparisons, and system design in plain language has given me a much clearer understanding of how software systems are structured, which makes conversations with developers, architects and customers more productive.

**Software design thinking.** Considering edge cases, defining success criteria, and thinking in phases are habits that carry over directly into program/project management and software design. These are skills worth developing.

**A tool-agnostic methodology.** I'm using Claude and VS Code right now, but the method isn't tied to them. The planning discipline, the documentation habits, and the judgment about project selection will remain relevant as tools evolve, and will transfer to whatever comes next.

---

## How This Was Made

This document was created in a session using Claude Cowork: A desktop tool that combines a conversational AI interface with direct access to a workspace folder on my computer.

The reference material was three existing files from a completed project: a fully annotated build plan, a session summary of the 23-prompt planning conversation, and a meta-document recording how the session summary itself was produced. Claude referenced those files directly from the workspace folder.

I provided a conversational brief specifying the audience, the key themes, the title, the filename, and the tone. The document was then generated and saved directly to the workspace folder as a Markdown file accessible to me for review and (extensive) editing.

This process is a small example of the approach described above.

---

*Last updated: April 2026*
