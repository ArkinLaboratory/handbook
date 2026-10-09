# Working practices

Short, and all of it earned from things that have gone wrong before.

## Repos and git

- **One repo per problem**, in the `ArkinLaboratory` GitHub organization.
- **Branch, then pull request. Never push straight to `main`.** Even working alone — the PR is
  where you explain what you did, and it is the only durable record of your reasoning.
- **A README that states the question before it shows the code.** Anyone opening your repo cold
  should learn, in the first paragraph, what question you are answering and what the current
  answer is.
- **Commit messages say why, not what.** The diff shows what changed.
- **Never commit credentials.** No tokens, keys, cookies, or `.env` files. Add them to
  `.gitignore` before your first commit, not after.
- **Never commit large data.** Data lives on the lab server or the cluster; the repo holds the
  code that reads it and a note saying where it is.

## Notebooks

Notebooks are good for exploring and bad for anything you will run twice.

- Clear outputs before committing, or the diffs become unreadable and you risk committing data
  — or a token printed by an earlier cell.
- Once a notebook does something you rely on, move that logic into a `.py` file the notebook
  imports.
- Never leave a cell that prints a credential, even if you deleted the output. The output is
  stored in the file.

## Data hygiene — the part that actually decides whether a project works

Every dataset in this group was collected by someone solving a different problem than yours.
**Audit before you model.** The most common way projects like these fail is a model trained
confidently on data that cannot answer the question.

Before you fit anything, write down the answers to these:

1. **Where did each row come from?** Which plate, which batch, which person, which month. If you
   cannot say, you cannot safely pool it.
2. **What is missing, and why?** Data missing at random is an inconvenience. Data missing
   *because it failed a threshold* is a different problem entirely — your labels are censored
   and ordinary cross-validation will flatter you.
3. **Are the measurements on a common scale?** A score computed relative to one population is
   not comparable to one computed relative to another. Pooling them is a silent error.
4. **What does the stupid baseline get?** Always build it first: predict the mean, predict from
   one obvious covariate, pick at random. Sometimes it wins, and that is a finding worth
   reporting.

Keep a tidy table of `(observation, condition, value, provenance, batch)` with missingness made
explicit. That table, plus a one-page statement of what is and is not comparable, is a real
deliverable on its own.

## Modeling discipline

- **Baseline first, always.** A number with nothing to compare it to means nothing.
- **Design the cross-validation before you fit.** Random splits are the optimistic number. A
  split that holds out a *group* — a batch, a position, a condition — is the honest one. Report
  both; the gap between them is your generalization estimate.
- **Report uncertainty.** A single correlation coefficient with no confidence interval, on
  fewer than a few hundred points, is not evidence.
- **Small data means small models.** With tens of labels, regularized regression on frozen
  features beats fine-tuning a large model. This is not a consolation prize — it is the
  well-validated right answer in that regime.
- **A negative result that is honest is a contribution.** "This dataset cannot answer this
  question, and here is why" is a real deliverable, and better in four weeks than a
  good-looking number in twelve.

## Asking for help

- **Ask in the channel, not by direct message.** Four people hit the same wall, and the answer
  should be findable by the next person.
- **If you are stuck for more than a day, say so.** Being stuck is normal and cheap to fix on
  Tuesday; it is expensive to discover three weeks later.
- A good question says: what you were trying to do, what you expected, what happened, and the
  exact error. Paste the command and the output — not a paraphrase. **Redact any token first.**

## Weekly meeting

Fridays. Five minutes each on what is blocking you, then one person goes deep for twenty minutes
on a rotation. It is not a status round.

Come with blockers, not accomplishments. If nothing is blocking you, come with the thing you
understand least about your own problem.

## Using AI tools

Encouraged, with one condition: **you are accountable for what you commit.** If you cannot
explain a line you are about to merge, it is not ready, regardless of what wrote it.

For anything agentic, keep the logs. The useful contribution in that area is measurement —
traces, failure modes, cost per useful answer — not impressions.
