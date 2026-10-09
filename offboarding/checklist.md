# Offboarding Checklist

When someone leaves the group, work through this list. **Start it two weeks before the last day,
not on the last day** — the handover items below are the ones that actually matter, and they take
longer than the account cleanup.

## Knowledge transfer — do this first

- [ ] **Write a handoff document per active project**: current state, where the data lives, what
      works, what is broken, what you would do next, and what you tried that failed. The failures
      are the most valuable part and the part nobody writes down
- [ ] Commit it somewhere findable — the project repo, or `predictive-modeling/session-notes/`
- [ ] Make sure every path you reference is one a remaining member can actually reach
- [ ] Name a specific person as the contact for each project, and tell them
- [ ] If you have an in-progress manuscript, state its status and where the draft lives
- [ ] Ensure any shared data or notebooks are accessible to remaining group members
- [ ] Update any documentation you maintained

A good model for this: `https://genomics.lbl.gov/~anoonan/` plus machine-readable project notes
on the server — written for a person who does not already know the project.

## Accounts and access

- [ ] Transfer ownership of any repos under your personal GitHub to `ArkinLaboratory` (or archive)
- [ ] Remove from `ArkinLaboratory` GitHub org
- [ ] Remove from lab Slack channels
- [ ] Remove SSH keys from group servers (`niya`, `thar`)
- [ ] Revoke KBase lakehouse access if applicable
- [ ] Revoke CBORG API key if applicable
- [ ] **Close cluster accounts that carry a standing charge** — a Lawrencium account bills per
      user per month until a closure ticket is filed. Note the date you filed it
- [ ] Check for data on purge-eligible scratch (NERSC `$SCRATCH`, cluster scratch) and move
      anything worth keeping to durable storage before it vanishes
- [ ] If you are renewing an allocation on the way out, say explicitly who inherits it

## If you are staying on as an affiliate

- [ ] Confirm which access you keep and for how long, in writing, with Gwyneth
- [ ] Be explicit about what you will and will not be available for. "Available for questions" and
      "mentoring new students" are different commitments and should not be assumed from each other
