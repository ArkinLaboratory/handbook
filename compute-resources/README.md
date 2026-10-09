# Compute Resources

## Authoritative Documentation

The primary references for group compute resources are maintained by Keith Keller:

- [Computational Resources Google Doc](https://docs.google.com/document/d/1oocMGywoeLx981uwZ5qUxRpXRDmpwQ3LNZZVTpnIGNM/edit) — Servers, Podman containers, Jupyter
- [JupyterHub Google Doc](https://docs.google.com/document/d/1dTrfAeqPZVzjYl8Cxsz6yPZtkSn-XBnebmd-nXFV2bk/edit) — Group JupyterHub instance
- [Server Status Page](https://genomics.lbl.gov/~kkeller/arkingroupServers.html) — Current server specs and availability

## The two tiers

**Group servers** (`niya`, `thar`) are our own interactive Linux machines. No job scheduler, no
allocation accounting, and the lab's working data is already mounted. This is where most people
should do most of their work.

**Shared clusters** — Savio (UC Berkeley), Lawrencium (LBNL) and NERSC (DOE) — are for jobs the
group servers cannot run: GPU training, large parallel workloads, anything that needs a queue.
See **[Clusters](clusters.md)** for which one to use, how to get on each, where the GPUs are,
and realistic onboarding times.

**There are no GPUs on the group servers.** If your project involves training or fine-tuning a
model, that happens on Lawrencium or NERSC, and those take the longest to get access to. Start
early.

## Group server access

Keith creates an account for you on a **local LDAP used only for these compute servers.**

> **You do not need an LBNL LDAP account, an LBL badge, or an LBNL appointment for the group
> servers.** This matters: UC Berkeley students, volunteers and affiliates can get on these
> machines without any LBNL identity. (An LBNL account *is* required for Lawrencium, and for
> CBORG — those are separate.)

To request access: email **Keith Keller** (`kkeller@lbl.gov`), copy your supervisor, and say
what you will be working on. Typical turnaround is about a week. **Follow up once after a
week** — this is expected, not pushy.

```bash
ssh username@servername.lbl.gov
```

`niya` is directly reachable. The other hosts require a UC Berkeley or LBL network address —
Eduroam on campus, or VPN from off campus.

For container workloads we use Podman, not Docker — see Keith's doc above.

These are shared interactive machines with no queue. Check `htop` before launching anything
heavy, and use `nice`. If you saturate the cores mid-afternoon you have taken the machine away
from everyone else.

**Not documented anywhere:** disk quotas on the group servers. Ask Keith before staging a large
dataset.

## Getting Access

See the [Onboarding Checklist](../onboarding/README.md) for initial setup steps, and
[Clusters](clusters.md) for the shared clusters.
