# 2 · Computer vision for plaque scoring

**Status:** under way · **Owner:** Han-Jiun Ke

## The question

Can we score plaque assays automatically, as well as a person does, across different host
species?

A plaque assay is read by eye: someone looks at a plate and judges how much lysis happened.
It is slow, it does not scale to the thousands of plates the Foundry generates, and different
people score differently.

## Why it matters

Plaque scoring is the rate-limiting read-out for phage characterization. Automating it well
makes every downstream analysis — including problem 1 — cheaper and more consistent. It also
makes historical data usable, because the same model can rescore old images.

## What already exists

- **A working model and a written report**, delivered September 2026.
- Hundreds of scanned plate images from the lab's phage work.
- A parallel, independently built workflow from Hemaa Selvakumar to compare against.
- Training data with human scores attached.

## First move (continuing work)

1. **Close the loop on the September report** — the model flagged apparent scoring errors in the
   human labels, and those need manual review.
2. **Extend to other host species**, specifically *Klebsiella* and *Pseudomonas*. This is the
   step that makes the work generalizable rather than a single-dataset demo.
3. **Compare against Hemaa's workflow** on the same images. Two independent methods agreeing is
   much stronger evidence than either alone.
4. Decide with Adam and Vivek whether this is a standalone paper or part of the larger
   manuscript.

## What you will learn

Taking a model from "works on my images" to "works on someone else's" — the step most applied
ML projects never survive. Plus validation against human ground truth when the ground truth is
itself noisy.

## The catch

**The model appears to have found errors in the human scoring. That is promising and it is not
proof.**

"The model disagrees with the human" and "the model is right" are different claims. Separating
them needs blind manual review of the disagreements — ideally by someone who does not know which
way the model scored them.

Two further traps:

- **Cross-species transfer is where this will break**, if it breaks. Plaque morphology differs
  between hosts, plate conditions differ, and a model tuned on one species can fail on another in
  ways that look like success on aggregate metrics. Report per-species performance, never pooled.
- **Human labels are the ceiling and they are noisy.** Establishing inter-rater agreement between
  two human scorers tells you what "as good as a person" actually means numerically. Without
  that number you cannot say whether the model has reached it.

## Open questions

- What is human–human agreement on these plates? Nobody has measured it.
- Are the new species' images comparable in resolution, lighting and plate type to the training set?
- Does the scoring need to be a number, a category, or a full segmentation mask? Different
  downstream uses want different things.

## Contacts

Adam and Vivek Mutalik for scope and publication strategy. Hemaa Selvakumar for the comparison
workflow.
