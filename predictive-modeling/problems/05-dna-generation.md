# 5 · Vector-conditioned DNA generation

**Status:** open · **Owner:** —

## The question

Can a generative model write DNA that actually works in the host and vector we intend to put it
in?

Genome-scale DNA language models can generate plausible sequence. The open question is whether
generation can be *conditioned* on context — this plasmid backbone, this host, this expression
requirement — and whether the output is any good.

## Why it matters

Synthesis is cheap now; design is the bottleneck. If a model can propose constructs that work
in a specific context, it shortens the design half of every build–test cycle in the lab. It is
also the most exploratory problem on this board, which makes it the best fit for someone
comfortable with an unclear endpoint.

## What already exists

- Exploratory work on conditioning a genome-scale DNA generative model on vector context, with
  written handoff notes and a starting pipeline.
- Access to the lab's sequence data and vector collections.

## Where it lives

Handoff notes at `https://genomics.lbl.gov/~anoonan/`, with machine-readable versions on the
lab server. Ask Adam for current state and for the model access specifics.

## First move

**Get generation running, reproduce what the notes describe, then stop.**

Then spend most of your effort on the thing that is actually the project: **build the evaluation.**
Before generating anything you intend to act on, you need a score that distinguishes a good
sequence from a plausible one. Candidate components:

- Does it preserve the structural features it should — reading frames, regulatory elements,
  restriction sites you need or must avoid?
- Is it synthesizable? Repeats, extreme GC content and hairpins make sequences expensive or
  impossible to order, and vendors have published constraints you can encode.
- Does it look like the host's own sequence by codon usage and k-mer statistics?
- Does an independent model — not the one that generated it — score it as plausible?

Each of those is a proxy. Being explicit about what each does and does not measure is the
contribution.

## What you will learn

Generative sequence modeling, and the much rarer skill of evaluating a system whose output you
cannot assess by eye. The evaluation-design problem here generalizes to every generative model
you will ever work with.

## The catch

**Generation is the easy half. Evaluation is the whole problem.**

A generative model will hand you an unlimited supply of confident, plausible nonsense, and
nothing about the output will tell you which is which. Sequence that scores well under the
generating model's own likelihood is not evidence — that is circular, and a model's likelihood
mostly reflects what its training distribution looked like.

Two specific traps:

- **Self-evaluation.** Never score generated sequence with the model that generated it, or with
  a close sibling trained on the same data. Use an independent measure.
- **No ground truth.** Unlike the other problems here, there is no labelled test set telling you
  which generated sequences work. Until something is synthesized and tested, every claim is a
  proxy claim, and the writeup must say so.

The honest framing: this project's deliverable is most likely **a well-argued evaluation
framework plus a small set of candidate designs**, not a demonstration that generated DNA works.
The latter needs a bench round that may not happen this semester.

## Open questions

- Which model, and is it accessible at the scale needed? Generation at genome scale needs a GPU.
- What is the specific design target — a promoter, a gene, a whole operon, a plasmid? The
  evaluation differs completely between those.
- Is there any historical set of constructs that *did* and *did not* work in this lab? That
  would be a real validation set and is worth hunting for before anything else.
- Is a synthesis round plausible this semester, and at what budget? That determines whether the
  project ends at proposals or at results.

## Contacts

Adam for scope and model access.
