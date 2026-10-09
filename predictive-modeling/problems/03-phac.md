# 3 · PhaC — aromatic monomer acceptance

**Status:** open · **Owner:** —

## The question

Can we make PhaC accept aromatic monomers — and is the bottleneck getting the monomer *in*, or
getting the polymer *out*?

PhaC is polyhydroxyalkanoate (PHA) synthase, the enzyme that polymerizes hydroxyacyl-CoA
monomers into polyester. There is a family of them. Broadening what it will accept, especially
toward aromatic monomers, would widen the range of bio-based polymer chemistries reachable from
an engineered host.

The second half of the question is the interesting half, and it is genuinely open. Published
structural work frames the substrate **tunnel** as the engineering handle, which is a
geometric and kinetic hypothesis rather than a recognition one. If the real obstacle is egress
of an aromatic-containing polymer rather than acceptance of an aromatic monomer, then redesigning
the binding pocket is aimed at the wrong residues entirely.

## Why it matters

Bio-based polymers from engineered microbes are a long-standing DOE interest, and aromatic
monomers are the chemistries hardest to reach biologically. It also serves a second purpose for
the lab: standing up real protein-design capability inside KBase.

Keep those two objectives separate. "Make PhaC accept aromatics" and "get a protein design
system running for KBase users" have different success criteria and different timelines.

## What already exists

| Dataset | Scale | Holder |
|---|---|---|
| Directed-evolution screen, high performers | **87 sequences** across 6 monomers, each with a fluorescence z-score | Jake Hilzinger (sheet); library from Kyle Sander |
| Natural PhaC variants | **~60 variants** × 5 monomers | Snigdha Jagarlapudi (since departed) |
| Type III chimeras | **<20** | Cassandra Reyes (departed Aug 2026) |

The six monomers screened: 3-hydroxybutyrate, hexanoic acid, **phloretic acid**, nonanoic acid,
glycolic acid, 5HFC. Published crystal structures: **PDB 9KNK and 9KNL**.

## First move

**Milestone 0 — audit the data. Do this before anything else; it may change the project.**

Write down answers to: Are the z-scores comparable across the six monomers? What was the
selection threshold and the sort gate? What were the library parents and the diversified
positions? How many of the 87 are distinct at the amino-acid level, across how many positions?
**How many have a phloretic-acid measurement specifically?**

Deliverable: a tidy table of `(sequence, monomer, score, provenance, batch)` with explicit
missingness, plus a one-page statement of what is and is not comparable.

**Milestone 1 — the structural question, independent of any ML.** Enumerate tunnels on 9KNK and
9KNL, get bottleneck radii, and compute transport profiles for a small acyl-CoA versus an
aromatic one. Cross-reference the bottleneck-lining residues against the positions the 87
mutants actually hit. Deliverable: a ranked list of 10–20 candidate positions with a
*structural* rationale that owes nothing to the fitness data.

Honest weakness to state up front: there is no CoA-bound PhaC structure, so any ligand pose is
itself a prediction and everything downstream inherits that uncertainty.

**Milestone 2 — regression, honestly cross-validated.** One-hot encoding of mutated positions
plus a zero-shot likelihood score as a feature, ridge regression, nested cross-validation.
Report two CV designs separately: a random split (the optimistic number) and a
**position-held-out split** (train on variants mutating one set of positions, test on others).
The gap between them is your real generalization estimate.

**Milestone 3 — a designed round.** 48–96 variants, **fully measured, no threshold selection**,
containing model proposals, structure proposals, **random library members as controls**, and
replicates for cross-batch calibration. Pre-register the success criterion before ordering.

## What you will learn

Structure-based biophysics, regression under censored data, and what one real
design–build–test round costs in time and money. The modeling here is small; the experimental
design is the hard part.

## The catch — read this twice

**The labels are winners-only.** Only variants passing a score threshold were sequenced, so the
starting and ending library composition is unknown. Named properly: the labels are
right-truncated with an unobserved selection mechanism. Four consequences:

1. **There are no negatives.** A model trained only on winners learns what winners look like,
   which is largely what the *library* looked like — not what makes a winner.
2. **The scores may not be comparable across monomers.** A z-score is relative to some reference
   population. If that population differs by monomer, pooling all six into one regression is a
   silent error.
3. **Selection correlates the label with the covariates.** Ordinary cross-validation will look
   fine and prospective hit rates will not match it.
4. **Enrichment cannot be estimated**, which rules out the one model the field fits reliably
   from selection data: the log-ratio of post- to pre-selection counts.

**And the aromatic data is thin.** Phloretic acid is the only clearly aromatic monomer in the
set, and it accounts for **4 of the 87** high performers — the fewest of any monomer.

Spread across six conditions, 87 sequences is on the order of 10–20 points per condition. **Do
not fine-tune a large model on this.** The evidence is clear that regularized regression on
frozen embeddings beats fine-tuning in this regime; it is the right answer, not a compromise.

**The famous tools mostly solve a different problem.** De novo binder design and backbone
generation build new proteins; this project nudges an existing one with a few dozen measurements
attached. Tool choice should follow from the problem class, not from what is well known.

## Open questions

- Which PhaC — which parent sequence, which class, which host chassis?
- Which aromatic monomers, beyond phloretic acid?
- **What does "more efficient" mean numerically** — incorporation rate, percent aromatic in
  polymer, titre? What is the current baseline and the target? No success criterion has been written down.
- Can the pre-selection library composition be reconstructed at all — even the degenerate codon scheme would help.
- Naming is inconsistent across sources: "5HFC" vs "5FHC", "glycolytic" vs "glycolic" acid. Resolve before building any table.
- The structural basis of PhaEC / PhaRC dimerization was flagged as not established. Does a structure-based approach need it?

## Contacts

**Jake Hilzinger** holds the data, the Drive folders and the institutional memory — start there.
**Kyle Sander** holds the original directed-evolution library and has an authorship interest that
needs settling before the library is used. Adam for scope and for the KBase side.
