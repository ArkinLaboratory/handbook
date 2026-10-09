# 1 · Active learning for phage–host interaction prediction

**Status:** open · **Owner:** —

## The question

Which phage–host pairs should we test next, so that each experiment teaches us the most?

Testing every phage against every host does not scale: the matrix is large, each measurement
costs bench time, and most pairs are uninformative. Active learning is the formal version of
scientific taste — a model that, given what you already know, proposes the next experiment
that will most reduce your uncertainty.

## Why it matters

The Phage Foundry's purpose is finding phages that kill specific pathogens. If a model can cut
the number of assays needed to characterize a new phage or a new clinical isolate, that
shortens the path from a patient sample to a candidate therapy. It is also the most
transferable method on this board — the same loop applies to any expensive measurement.

## What already exists

- A working active-learning pipeline built by Avery Noonan, with written handoff notes.
- Phage–host susceptibility data from the Phage Foundry, including large strain × phage
  matrices for clinically relevant species.
- Sequence features and embeddings already computed for many of the relevant genomes.

## Where it lives

- Handoff notes: `https://genomics.lbl.gov/~anoonan/`, with machine-readable versions on the
  lab server under `/usr2/people/anoonan/`.
- Ask Adam for the current data locations and for an introduction to the Phage Foundry side.

## First move

**Reproduce the existing result end to end before changing anything.** You should be able to
run the pipeline, get the same numbers the notes report, and explain what each stage does.
That is week one or two, and it is not busywork — it is how you find out what the code actually
assumes.

Then: extend to a second dataset, and add exactly one new selection strategy. The scoped
extensions are (a) new acquisition strategies, including ones based on structural diversity or
feature-set identity, (b) strategies for choosing the *initial* labelled set, and (c) measuring
how much the choice of seed and holdout changes the answer.

## What you will learn

The full experimental loop — model, acquisition function, experiment, update — plus the
statistics of comparing strategies honestly. This is a method, not a one-off result, and it is
the most portable thing on this board.

## The catch

**Clever acquisition functions often beat random selection by very little, and the margin is
dataset-specific.** The literature is full of papers reporting gains that do not survive a
careful baseline.

So the honest version of this project is mostly about the baseline:

- Random selection, implemented properly, with the same budget and the same number of rounds.
- Repeated over many random seeds, because a single run tells you almost nothing — the variance
  between seeds is usually larger than the difference between strategies.
- Reported with uncertainty, not as a single learning curve.

If you do not do this, you will convince yourself of an improvement that is not there. If you
do, you may find the improvement is real but small — which is still a result, and a publishable
one if you characterize *when* it helps.

## Open questions

- Which datasets, specifically, and are they on a common scale? (The same caution as everywhere
  else here: data collected in different campaigns may not pool.)
- Is there a held-out set that was never used for model development, or does everything need
  re-splitting?
- Can any proposed experiment actually be run at the bench this semester, or is this
  retrospective only? The answer changes what counts as success.

## Contacts

Adam, for scope and data access. The Phage Foundry team for the experimental side.
