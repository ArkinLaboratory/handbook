# Compute resources

Four systems. They are not interchangeable. Read the summary, get the two easy accounts
started, and come back to the rest when you actually need a GPU.

**The lab servers have no GPUs.** If your project involves training or fine-tuning a model,
that happens on Lawrencium or NERSC — and those take the longest to get onto.

## Summary

| System | What it is | Can you get on? | GPUs | Onboarding |
|---|---|---|---|---|
| **Arkin Lab** (`niya`, `thar`) | Lab-owned interactive Linux hosts, no scheduler | Yes — the normal path | None found | ~1 week |
| **Savio** (UC Berkeley) | Campus Slurm cluster, ~600 nodes | Yes, via `ac_arkinlab` | Many, but low-priority queue for us | 1–3 days |
| **Lawrencium / Einsteinium** (LBNL) | Lab Slurm cluster; best GPUs of the four | Harder — needs LBNL identity, ~$25/user/month | Best: H100/H200/A40, plus a free partition | 1–2 weeks |
| **NERSC** (DOE) | Perlmutter, national facility | Yes, but slowest — own identity vetting | 7,168 A100s | 1–2 weeks |

## 1. Arkin Lab servers — start here

Hosts `niya` and `thar`, plus a fileserver. Administered by **Keith Keller**, who creates
accounts on a local LDAP used only for these machines.

- **Access:** email Keith, copy Adam. ~1 week. One follow-up is normal.
- **Reaching them:** `niya` is directly reachable; other hosts need a UC Berkeley IP.
- **What lives here:** the lab's working data under `/usr2/people/`. Project handoff notes are
  published at `https://genomics.lbl.gov/~anoonan/` with machine-readable versions on the host.
  **Read the notes for your problem before your first Friday.**
- **Good for:** learning Unix, exploring data, writing and debugging code, quick analyses,
  hosting a small dashboard (ask Keith for a proxy).
- **Not good for:** anything GPU. These are shared interactive machines with no queue — check
  `htop` before launching something heavy, and use `nice`. If you eat all the cores at 4pm on a
  Tuesday you have taken the machine from everyone else.
- **Unknown:** disk quotas are not documented. Ask Keith before staging a large dataset.

## 2. Savio — the easiest cluster

UC Berkeley's institutional cluster, run by Berkeley Research Computing. Slurm. Our project is
**`ac_arkinlab`**.

- **Access:** self-service, 1–3 days. See [the onboarding checklist](../onboarding/README.md).
- **Gentlest on-ramp anywhere here:** Open OnDemand at `ood.brc.berkeley.edu` — browser Jupyter,
  free, no SSH.
- **GPUs:** physically plentiful. `savio3_gpu` has A40 (48 GB), TITAN RTX, 2080Ti and V100
  nodes; `savio4_gpu` has RTX A5000 (24 GB) and L40 (46 GB). **The catch:** a Faculty Computing
  Allowance reaches them only through the `savio_lowprio` queue — preemptible, and you may wait.
  You must name the GPU type explicitly: `--gres=gpu:A40:1`.
- **Walltime:** `savio_normal` allows 72 hours. The 10-day queue is CPU-only and capped at 4 cores.
- **Good for:** learning Slurm, CPU-parallel work, modest GPU jobs you are not in a hurry about.
- **Help:** `brc-hpc-help@berkeley.edu`

## 3. Lawrencium and Einsteinium — where the GPUs are

LBNL's cluster; Einsteinium is the GPU side. This is where the lab's real ML training runs,
under the project **`pc_phiml`**.

**Getting on is the hard part.** You need an LBNL identity, separate from CalNet. Without an
existing LBNL affiliate appointment, that comes first through Gwyneth, and it is a multi-week
process. There is also a standing **~$25 per user per month** charge, so do not request an
account speculatively, and tell Gwyneth when you no longer need it.

> **If you are not a US person:** the Foreign Visits and Assignments process applies and
> typically takes **about 60 days**. Start now if Lawrencium is in your future at all. For this
> semester, plan on the Arkin lab servers and Savio.

**GPU partitions, in the order you should use them:**

- **`es0` — free.** 12 nodes × 4× 2080Ti (11 GB). These **incur no Service Unit charges**, which
  makes this the best place in the lab to debug a training script. 11 GB is tight, but a script
  that crashes crashes just as informatively on a small GPU. Get it working here first.
- **`es1` — the workhorse.** 30 nodes × 4× A40 (48 GB), plus an A100 node and V100s. 48 GB holds
  most protein language models. ~16 SU per GPU-hour.
- **`es2` — heavy.** H200 (141 GB) and H100 (80 GB). Substantially faster, ≥28 SU per GPU-hour.
  Move here only once a run is validated and you need the speed or the memory.
- **`es3`** (RTX PRO 6000 Blackwell, 96 GB) is newest, but its queue settings are not yet
  configured for all users. Do not plan around it.

**Walltime:** `lr_normal` allows 3 days. Nothing here runs a week unattended, so **learn to
checkpoint and resume on day one.** This is the most common way new users lose work.

**Request:** `https://mylrc.lbl.gov/` · **Help:** `scienceithelp@lbl.gov`, office hours Weds 10:30–noon.

Note: SSH certificate issues were announced in July 2026 with no all-clear found since. Treat
PIN+OTP as the primary login method.

## 4. NERSC — the national facility

DOE's supercomputing center, at Berkeley Lab but administratively separate from it. The machine
is **Perlmutter**: 1,792 GPU nodes × 4 A100 = 7,168 GPUs (1,536 nodes at 40 GB, 256 at 80 GB).

- **Access:** neither CalNet nor LBNL identity works. NERSC issues its own account and does its
  own identity verification, which **can take up to a week** before Adam can approve you. Then a
  password link that expires in 24 hours, an AUP to sign, and MFA. Budget 1–2 weeks.
- Joining an existing allocation is the fast path. Getting a *new* allocation is an annual
  proposal cycle, not an onboarding step.
- **Accounts:** `https://iris.nersc.gov` · `accounts@nersc.gov`
- **Filesystems — the part that bites people.** `$SCRATCH` is large (20 TB/user) and **purged on
  a schedule**. It is a workspace, not storage. Anything you keep goes to the Community File
  System. The lab already has several TB of embeddings sitting on purge-eligible scratch —
  learn from that rather than repeat it. **Decide where output goes before you generate it.**
- **Queues:** `regular` allows 48 hours. For single-GPU work use the `shared` QoS so you are
  charged for one GPU, not all four on the node. `preempt` charges a quarter rate after 2 hours.
- Jupyter is available in a browser; containers via Shifter or podman.
- **Good for:** very large embedding or inference jobs. **Overkill for:** anything you are still
  debugging.

## Which system for which task

| Task | Use | Why |
|---|---|---|
| Learning Unix, exploring lab data | Arkin `niya` | No paperwork, data already mounted |
| Learning how a scheduler works | Savio Open OnDemand | Browser Jupyter, free, no SSH |
| Debugging a training script | Lawrencium `es0` | Free GPU hours — break things here |
| Fine-tuning a protein language model | Lawrencium `es1` (A40 48 GB) | Where the lab actually does this |
| A very large embedding job | NERSC Perlmutter | Only if the scale warrants it |
| Quick data wrangling | Arkin `niya` | No queue, no accounting |
| Hosting a dashboard | Arkin `thar` + proxy from Keith | Clusters cannot host persistent services |

## Five habits worth forming now

1. **Checkpoint everything.** No system here runs a job for a week. A training loop that cannot
   resume from disk will eventually cost you days.
2. **Know where your output lives before you make it.** Scratch gets purged. Home has quotas.
3. **Debug on the free tier.** Lawrencium `es0` costs nothing. A crash there is free.
4. **The lab servers are shared and have no queue.** `htop` first, `nice` always.
5. **Ask after a week, not after a month.** Account requests sit in human queues. One follow-up
   is normal; silently waiting three weeks is how people lose their first month.

## To verify

- Current Service Unit balance on Savio `ac_arkinlab`.
- Whether any Arkin lab host has a usable GPU — no evidence either way was found. Ask Keith.
- `es_normal` walltime on Einsteinium:
  `sacctmgr show qos name=es_normal,es2_normal format=name,maxtres,maxwall,mintres`
