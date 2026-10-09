# Arkin Lab Handbook

Central documentation for the Arkin Laboratory at UC Berkeley / Lawrence Berkeley National Laboratory.

## Section 1: Getting Started

**Just arriving at the lab?** Start here:

- [Onboarding Checklist](onboarding/README.md) — accounts, system access, communication channels
- [For UC Berkeley students, volunteers and affiliates](onboarding/non-lbnl-members.md) — the
  path if you do not have an LBNL appointment. Most undergraduates and volunteers need this one.

## Section 2: Compute Resources

- [Compute Resources](compute-resources/) — group servers (`niya`, `thar`), access, Podman, JupyterHub
- [Clusters](compute-resources/clusters.md) — Savio, Lawrencium and NERSC: which to use for what,
  where the GPUs are, and how long access really takes
- [Computational Resources Google Doc](https://docs.google.com/document/d/1oocMGywoeLx981uwZ5qUxRpXRDmpwQ3LNZZVTpnIGNM/edit) — detailed server and Podman setup (Keith)
- [JupyterHub Google Doc](https://docs.google.com/document/d/1dTrfAeqPZVzjYl8Cxsz6yPZtkSn-XBnebmd-nXFV2bk/edit) — group JupyterHub instance
- [Keith's Server Page](https://genomics.lbl.gov/~kkeller/arkingroupServers.html) — server specs and status

### AI Resources

The lab uses several AI platforms for research:

- **CBORG** ([cborg.lbl.gov](https://cborg.lbl.gov)) — LBL's multi-model AI portal, free for
  `@lbl.gov` accounts. Access to Claude, open-source models, and specialized scientific tools.
  **Requires an LBL account** — if you do not have one, see
  [non-LBNL members](onboarding/non-lbnl-members.md).
- **Claude** — direct API access for building AI skills and MCP servers.
- **Berkeley Campus AI** ([ai.berkeley.edu](https://ai.berkeley.edu)) — UC Berkeley's shared AI tools.

Setup guides and API documentation are maintained in the
[ai-skills-workshop repo](https://github.com/ArkinLaboratory/ai-skills-workshop/tree/main/ai-resources)
under `ai-resources/`.

## Section 3: Predictive Modeling Group (formerly the Hack-a-thon)

The lab's weekly working group on biology, prediction and AI. **Fridays 14:30–15:30.** Open to
everyone in the lab; core members each own one problem.

- [Predictive Modeling Group](predictive-modeling/) — schedule, the problem board, session notes
- [The problem board](predictive-modeling/problems/) — six problem statements, one owner each
- [Working practices](predictive-modeling/working-practices.md) — git, notebooks, data hygiene,
  modeling discipline. Worth reading even if you are not in the group.
- [ai-skills-workshop repo](https://github.com/ArkinLaboratory/ai-skills-workshop) — the AI
  skills and MCP materials this group grew out of

## Section 4: KBase BER Data Lakehouse

The KBase program is standing up a data lakehouse that links KBase capabilities to AI and bridges
to wider DOE resources. KBase, other projects and the Arkin Lab are moving data into this
lakehouse under common governance so we gain a network effect of cross-referencable data on a
platform supporting scalable analysis and AI. Our goal is to get all Arkin Lab and associated
project data into this lakehouse.

| Resource | Description |
|----------|-------------|
| [hub.berdl.kbase.us](https://hub.berdl.kbase.us) | JupyterHub for lakehouse queries (Spark, SQL) |
| [BERDL-ENIGMA-CORAL](https://github.com/jmchandonia/BERDL-ENIGMA-CORAL) | DuckDB-based MCP server for querying ENIGMA CORAL data in BERDL |
| [lakehouse-skills](https://github.com/cmungell/lakehouse-skills) | Claude skills for REST + Dremio lakehouse queries |
| [lakehouse-chat](https://github.com/justaddcoffee/lakehouse-chat) | Natural language chat interface for BERDL |
| [linkml-coral](https://github.com/realmarcin/linkml-coral) | ENIGMA Common Data Model as LinkML schema |

### Key Docs

- [BERDL Conventions](https://docs.google.com/document/d/1a0CRMl4YH01FHlEX7ky8XgmrTAoGc13RxVrxqrq6E2Y/edit) — lakehouse table and data structure standards
- [KBase BER Lakehouse Onboarding](https://docs.google.com/document/d/1p2KZR0y6FDnsHEFYysLazm9R1YXuRSJQAurMacm09RE/edit) — account setup and access (Elisha Wood-Charlson)

> Two known rough edges in the Lakehouse onboarding guide, so nobody is confused by them: part of
> the install sequence sits under a heading marked DEPRECATED while the troubleshooting section
> below it still refers to the same commands, and the LLM API key step requires CBORG and
> therefore an LBL account. Ask before following either.

## Section 5: General Reference Docs

| Document | Maintained By | Focus |
|----------|---------------|-------|
| [Computational Resources](https://docs.google.com/document/d/1oocMGywoeLx981uwZ5qUxRpXRDmpwQ3LNZZVTpnIGNM/edit) | Keith Keller | Servers, Podman, Jupyter |
| [JupyterHub](https://docs.google.com/document/d/1dTrfAeqPZVzjYl8Cxsz6yPZtkSn-XBnebmd-nXFV2bk/edit) | Keith Keller | Group JupyterHub instance |
| [Server Status](https://genomics.lbl.gov/~kkeller/arkingroupServers.html) | Keith Keller | Current server specs and availability |

## Section 6: Leaving the Group

- [Offboarding Checklist](offboarding/checklist.md) — account cleanup and knowledge transfer.
  **Read this before you leave, not after.** The handover notes are the part that matters.
