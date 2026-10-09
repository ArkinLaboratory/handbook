# Onboarding Checklist

Welcome to the Arkin Lab. Work through these in order.

> **If you do not have an LBNL appointment** — most undergraduates, UC Berkeley volunteers,
> masters students and visiting researchers — read
> [non-LBNL members](non-lbnl-members.md) alongside this. Several items below assume an LBL
> account, and that page says which ones you can skip and which ones block.

## Week 1: Accounts and Access

- [ ] Get added to the lab Slack workspace (ask Adam or Gwyneth)
- [ ] Create a [GitHub](https://github.com) account if you don't have one
- [ ] Request an invite to the [ArkinLaboratory](https://github.com/ArkinLaboratory) org
- [ ] **Request a group server account** — email Keith Keller (`kkeller@lbl.gov`), copy your
      supervisor. This is a local account; **you do not need an LBNL identity for it.** Takes
      about a week; follow up once. See [Compute Resources](../compute-resources/)
- [ ] LBL badge and VPN — **LBNL appointments only.** See your division admin, or Gwyneth Terry
      (`gaterry@lbl.gov`) for an affiliate appointment. Allow weeks, not days
- [ ] Introduce yourself in the Slack channel for whatever you are working on

## Week 1–2: Compute you will actually need

- [ ] **Savio** (UC Berkeley cluster) — create a MyBRC account with your CalNet ID, sign the
      User Access Agreement, request to join `ac_arkinlab`, set up an OTP token. One to three
      days. Free browser Jupyter at `ood.brc.berkeley.edu` is the gentlest way to learn a cluster
- [ ] **Only if your work needs a GPU:** Lawrencium (LBNL identity + monthly per-user fee) or
      NERSC (separate identity vetting). Both take one to two weeks or more — see
      [Clusters](../compute-resources/clusters.md) and start early

## Week 1–2: AI Tools

Lab-wide resources — set these up regardless of project.

- [ ] Create a CBORG account and get an API key — see
      [CBORG Guide](https://github.com/ArkinLaboratory/ai-skills-workshop/blob/main/ai-resources/cborg.md).
      **Needs an `@lbl.gov` account.** If you don't have one, say so rather than skipping silently
- [ ] Install Claude Desktop — see
      [Claude Setup](https://github.com/ArkinLaboratory/ai-skills-workshop/blob/main/ai-resources/claude-setup.md)
- [ ] (Optional) Get an Anthropic API key for programmatic access

**Never paste a credential into a chat window** — not a KBase token, not a GitHub personal access
token, not an API key. If one leaks, say so immediately so it can be rotated. Nobody gets in
trouble for reporting it.

## If Working with KBase / Lakehouse

- [ ] Create a [KBase account](https://www.kbase.us/) **with your ORCID**. Already have an
      account? Link your ORCID to it — do not create a second one
- [ ] Enable MFA on your ORCID
- [ ] Send your KBase username to Adam — users are added to the KBase group in batches
- [ ] Request lakehouse access — see
      [KBase BER Lakehouse Onboarding](https://docs.google.com/document/d/1p2KZR0y6FDnsHEFYysLazm9R1YXuRSJQAurMacm09RE/edit),
      and sign the community agreement table at the top

## The Predictive Modeling Group (formerly the hack-a-thon)

Fridays 14:30–15:30, IGIB 412K. Open to anyone in the lab.

- [ ] Join the group's Slack channel
- [ ] Read the [group page](../predictive-modeling/) and the [problem board](../predictive-modeling/problems/)
- [ ] Read [working practices](../predictive-modeling/working-practices.md) before your first commit
- [ ] If you own a problem: **write one paragraph, in your own words, stating the question it
      answers**, and commit it to your repo's README. This is the real deliverable of week one

## Your first week, in short

Request the group server account and Savio on day one — they sit in human queues and are the most
common reason new people lose their first month. Everything else can wait a week.
