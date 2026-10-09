# 6 · Co-scientist and research harnesses

**Status:** open · **Owner:** —

## The question

What makes an AI research assistant genuinely useful to a working scientist — and what does it
cost?

Not "is it impressive." Where does it help, where does it fail, how does it fail, and what is
the price per useful answer.

## Why it matters

This lab builds KBase, which thousands of scientists use, and is actively putting agentic
tooling in front of them. Decisions about what to build are currently being made on impressions.
Measured evidence about where these systems actually help a scientist would influence real
engineering choices — which makes this the most immediately *useful-to-the-lab* problem on the
board, even though it looks the least like biology.

## What already exists

- **KBase's co-scientist agents** running on the BER Data Lakehouse.
- **A semantic catalog** of the Lakehouse's tables and columns, which is what grounds the
  agents' queries in real data.
- **An onboarding guide** (Elisha Wood-Charlson's) to get you onto the Lakehouse.
- Trace logs from previous user sessions, and an ongoing usage study.

## First move

1. **Get onto the Lakehouse.** Follow the onboarding guide. Expect this to take a few days and
   to involve at least one thing that does not work as written — note those, they are data.
2. **Point the agent at a real question**, ideally one drawn from problems 1–5 so that someone in
   this group can tell you whether the answer is right.
3. **Log everything.** Every run: the question, the trace, what it got right, where it went
   wrong, how long it took, and roughly what it cost. Build the log as a structured file from
   day one, not as notes you will tidy later.

After three or four weeks of that you will have something nobody currently has: a catalogue of
failure modes with frequencies attached.

## What you will learn

How to build and judge an agentic research setup — tool design, grounding, evaluation,
cost accounting. This is a skill the lab will be using for the next decade, and very few people
have it yet.

## The catch

**It is equally easy to be dazzled and to be dismissive, and both are worthless.**

The failure mode specific to this problem is producing opinions instead of measurements. "It's
pretty good" and "it hallucinates" are both unfalsifiable and both already widely believed. The
contribution is traces, categorized failure modes, and cost per useful answer.

Three things to watch:

- **Grounding failures are quiet.** The most dangerous output is a confident, well-formatted,
  wrong answer — often because a query silently returned nothing and the model filled the gap
  from its own priors. You will only catch these if you check answers against the data yourself,
  which is why running questions whose answers someone in the group already knows matters.
- **Cost is real and easy to ignore.** Agentic runs can be expensive. Track it, because "useful
  but ten times the price of a graduate student doing it by hand" is a finding.
- **Scope drift.** There is no natural endpoint here. Pick a fixed question set and a fixed
  number of runs before you start, and resist expanding mid-stream.

## Open questions

- What is the question set? A fixed, written set of 10–20 real research questions with known or
  checkable answers would make this project rigorous instead of anecdotal. That set does not
  exist and building it is a legitimate first deliverable.
- What counts as a "useful answer"? Needs a rubric, written down before the runs.
- Can previous session traces be reused, or does everything need generating fresh?
- Known rough edges in the onboarding guide: part of the install sequence sits under a heading
  marked DEPRECATED while the troubleshooting below still refers to it, and the LLM key step
  requires an LBL account. Ask before following those steps.

## Contacts

Adam for scope — this is the area he is personally most interested in. Elisha Wood-Charlson for
Lakehouse access and onboarding.
