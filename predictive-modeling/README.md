# Predictive Modeling Group

The lab's weekly working group on biology, prediction and AI. **This is the continuation of the
Arkin Lab hack-a-thon** — same slot, same spirit, now with a standing set of problems and named
owners. Anyone in the lab is welcome to join any week.

## Schedule

- **When**: Fridays, 14:30–15:30
- **Where**: IGIB 412K, plus Zoom (link in the Slack channel)
- **Format**: five minutes each on blockers, then one person goes deep for twenty minutes on a
  rotation. It is not a status round.

Come with blockers, not accomplishments. If nothing is blocking you, come with the thing you
understand least about your own problem.

## How this works

- **Each core member owns one problem.** Not a task list — one question, yours to carry.
- **Drop-ins are welcome.** You do not need to own a problem to come, and the deep-dive slot is
  usually the most useful hour in the week for anyone doing adjacent work.
- **Work lives in the open.** Code in the `ArkinLaboratory` org, notes here, questions in the
  Slack channel. Work nobody can find did not happen.

## The board

| # | Problem | Mostly about | Owner |
|---|---|---|---|
| 1 | [Active learning for phage–host prediction](problems/01-active-learning.md) | ML, experiment design | — |
| 2 | [Computer vision for plaque scoring](problems/02-plaque-cv.md) | CV, image pipelines | Han |
| 3 | [PhaC — aromatic monomer acceptance](problems/03-phac.md) | Biophysics, structure, regression | — |
| 4 | [Genome → growth phenotype](problems/04-genome-to-growth.md) | Representation learning | — |
| 5 | [Vector-conditioned DNA generation](problems/05-dna-generation.md) | Generative sequence models | — |
| 6 | [Co-scientist and research harnesses](problems/06-research-harness.md) | Agents, tooling, evaluation | — |

Update the Owner column when a problem is claimed. **One name per problem.**

Each statement follows the same shape: the question, what already exists, a first move, what you
will learn, **the catch**, and the open questions nobody has answered yet. Read the catch
section twice — every dataset here was collected by someone solving a different problem, and
knowing what is wrong with it before you start is most of the job.

## Before you start

- [Lab onboarding checklist](../onboarding/README.md) — accounts and access
- [For UC Berkeley students, volunteers and affiliates](../onboarding/non-lbnl-members.md) — if
  you do not have an LBNL appointment, read this instead of guessing
- [Compute resources](../compute-resources/) — group servers, and
  [clusters](../compute-resources/clusters.md) if you need a GPU
- [Working practices](working-practices.md) — git, notebooks, data hygiene, modeling discipline

## Session history

| Session | Date | Topic | Notes |
|---------|------|-------|-------|
| 1 | Feb 2026 | Orientation (3 hr) | Group voted for skills/MCP as the next topic |
| 2 | — | Skills deep dive | [session-notes/](session-notes/) |
| 3 | 9 Oct 2026 | Relaunch as the Predictive Modeling Group | Orientation, introductions, problem claiming |

Session notes go in [`session-notes/`](session-notes/), one file per session, named `YYYY-MM-DD.md`.

## AI skills and tooling

The group's earlier work on AI skills and MCP servers lives on:

- [ai-skills-workshop repo](https://github.com/ArkinLaboratory/ai-skills-workshop) — workshop
  materials, AI resource setup guides, and project issues
- [Hack-a-thon signup sheet](https://docs.google.com/document/d/1YsRqAbdooS0FlwJijlJP_5tPJW5-pA3bBYcTcmQR-Gc/edit) — problem submissions and voting
- [AI 101 task signup](https://docs.google.com/document/d/1hrDxWMo3VsT7PPKdj76HYF9TTq5CIgWl2aJs88dlGGU/edit) — automation tasks people want to tackle

Problem 6 on the board is the formal version of this thread: measuring what agentic research
tooling actually does for a working scientist.

## The one rule that matters most

**If you are stuck for more than a day, say so in the channel.** Being stuck is normal and cheap
to fix on Tuesday. It is expensive to discover three weeks later. Nobody in this group is
expected to already know how to do this.
