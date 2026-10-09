# 4 · Genome → growth phenotype

**Status:** open · **Owner:** —

## The question

Can you predict how fast a microbe grows, and what it can eat, from its genome alone?

Give me a genome sequence and no other information. Tell me the organism's doubling time, and
which carbon and nitrogen sources it can use.

## Why it matters

This is close to the central problem of predictive biology. Most microbes in the environment
have never been cultured, so a genome is often all there is. If you can read physiology off
sequence, you can predict what a community does from metagenomics alone — which is the goal of
a large part of DOE's environmental biology programme, ENIGMA included.

## What already exists

- **Protein language model embeddings already computed at scale** — the lab has generated
  embeddings for very large numbers of genes, with a manuscript in progress.
- **A large in-house phenotype corpus**: measured growth on defined carbon and nitrogen source
  arrays for hundreds of strains, plus genome-wide fitness assays (RB-TnSeq) for a substantial
  subset.
- **Pathway-level annotations** of catabolic capability across tens of thousands of reference
  genomes, from GapMind-style tooling.
- Allied work in the lab on carbon catabolic preference, which has established that several
  physiological traits are taxonomically conserved and co-vary with growth rate and genome size.

## First move

**Join the embeddings to the measured phenotypes in one table.** This sounds like
administration and it is the project's main technical risk: the identifiers will not match, the
strains will be named differently in different datasets, and some of the phenotype data lives
behind access you need to arrange. Budget real time for it, and expect to need help.

**Then find out what the dumbest possible baseline achieves** before touching a large model.
Specifically:

- Genome size alone, as a predictor of dietary breadth.
- Taxonomy alone (predict from genus mean).
- Codon-usage-based doubling-time prediction — there are established tools for this.
- Pathway-annotation counts.

Write those numbers down. They are the bar.

## What you will learn

Representation learning on real biology, large-scale data joining, and the difference between a
model that predicts and a model that explains. Also the experience of being beaten by a simple
baseline, which is formative.

## The catch

**The simple baselines here are unreasonably strong.** Growth rate is already predictable from
codon usage statistics alone. Genome size already predicts how many substrates an organism can
use. Taxonomy already captures a lot, because these traits are conserved.

So a large embedding model does not get credit for beating chance. It has to beat codon usage,
genome size and genus mean — and when it does, you then have to say *what it learned that those
did not*, or the result is uninteresting even if the number is better.

Two further problems:

- **Roughly half of all genes have no functional annotation.** This is the stated barrier in the
  field. An embedding model is in principle a way around it, which is exactly why this is
  interesting — but it also means your pathway-based baselines are built on incomplete
  information, and so is any interpretation you offer.
- **Growth measurements are batch-structured.** Plates, dates, media lots and operators all
  contribute. If your cross-validation splits randomly across rows rather than by batch and by
  organism, you will measure how well you interpolate within a plate, not how well you predict a
  new organism. **Split by organism, at minimum.**

## Open questions

- Which phenotype datasets specifically, and what access does each need? Some may take weeks.
- Are growth measurements comparable across campaigns, or do they need per-batch normalization?
- Is the target growth *rate*, growth *yield*, or binary can-it-grow-on-X? These are different
  problems with different data support. Yield in particular is thinly measured.
- Does this want to predict for a new *organism*, or a new *substrate*, or both? Held-out
  substrate is a much harder and more interesting problem than held-out organism.

## Contacts

Adam for scope. This problem overlaps closely with Hans Carlson's carbon-catabolism work and
with ENIGMA phenotyping — scope it with them before promising anything, and expect the data
access conversation to be the long pole.
