# Arkin Lab Handbook

Central documentation for the Arkin Laboratory at UC Berkeley / Lawrence Berkeley National Laboratory.

## Section 1: Getting Started

**Just arriving at the lab?** Start here with the onboarding checklist:

- [Onboarding Checklist](onboarding/README.md) — Account setup, system access, communication channels

## Section 2: Compute Resources

Group compute infrastructure for your daily work:

- [Compute Resources Directory](compute-resources/) — Servers, containers, JupyterHub overview
- [Computational Resources Google Doc](https://docs.google.com/document/d/1oocMGywoeLx981uwZ5qUxRpXRDmpwQ3LNZZVTpnIGNM/edit) — Detailed server and Podman setup (Keith)
- [JupyterHub Google Doc](https://docs.google.com/document/d/1dTrfAeqPZVzjYl8Cxsz6yPZtkSn-XBnebmd-nXFV2bk/edit) — Group JupyterHub instance
- [Keith's Server Page](https://genomics.lbl.gov/~kkeller/arkingroupServers.html) — Server specs and status

### AI Resources

The lab uses several AI platforms for research:

- **CBORG** ([cborg.lbl.gov](https://cborg.lbl.gov)) — LBL's multi-model AI portal (free for @lbl.gov accounts). Access to Claude, open-source models, and specialized scientific tools.
- **Claude** — Direct API access for building AI skills and MCP servers.
- **Berkeley Campus AI** ([ai.berkeley.edu](https://ai.berkeley.edu)) — UC Berkeley's shared AI research tools and resources.

Detailed setup guides and API documentation are maintained in the [ai-skills-workshop repo](https://github.com/ArkinLaboratory/ai-skills-workshop/tree/main/ai-resources) (under `ai-resources/`).

## Section 3: Projects and Workshops

Project-specific content, organized by initiative.

### Hack-a-thon / AI Skills

Weekly collaborative sessions to learn tools, solve problems, and build AI capabilities:

- [Hack-a-thon Directory](hackathon/) — Schedule, session notes, project tracking
- [ai-skills-workshop Repo](https://github.com/ArkinLaboratory/ai-skills-workshop) — Full workshop materials and resources
- [Hack-a-thon Signup](https://docs.google.com/document/d/1YsRqAbdooS0FlwJijlJP_5tPJW5-pA3bBYcTcmQR-Gc/edit) — Problem submissions and voting
- [AI 101 Task Signup](https://docs.google.com/document/d/1hrDxWMo3VsT7PPKdj76HYF9TTq5CIgWl2aJs88dlGGU/edit) — Automation tasks people want to tackle

### KBase BER Data Lakehouse (Future Workshop)

The KBase program is standing up a data lakehouse that will powerfully link to KBase capabilities and AI and bridge to wider DOE resources. KBase, other projects and Arkinlab are moving data into this lakehouse under common governance so we can gain a "network effect" of cross-referencable data on a platform supporting scalable analysis and AI. Our goal is to get all Arkinlab and associated project data into this lakehouse. These tools and resources are the beginning of the infrastructure to access all this. We will be getting the lab trained in its use and programming.

#### Lakehouse Resources

| Resource | Description |
|----------|-------------|
| [hub.berdl.kbase.us](https://hub.berdl.kbase.us) | JupyterHub for lakehouse queries (Spark, SQL) |
| [BERDL-ENIGMA-CORAL](https://github.com/jmchandonia/BERDL-ENIGMA-CORAL) | DuckDB-based MCP server for querying ENIGMA CORAL data in BERDL |
| [lakehouse-skills](https://github.com/cmungell/lakehouse-skills) | Claude skills for REST + Dremio lakehouse queries |
| [lakehouse-chat](https://github.com/justaddcoffee/lakehouse-chat) | Natural language chat interface for BERDL |
| [linkml-coral](https://github.com/realmarcin/linkml-coral) | ENIGMA Common Data Model as LinkML schema |

#### Key Docs

- [BERDL Conventions](https://docs.google.com/document/d/1a0CRMl4YH01FHlEX7ky8XgmrTAoGc13RxVrxqrq6E2Y/edit) — Lakehouse table and data structure standards
- [KBase BER Lakehouse Onboarding](https://docs.google.com/document/d/1p2KZR0y6FDnsHEFYysLazm9R1YXuRSJQAurMacm09RE/edit) — Account setup and access

## Section 4: General Reference Docs

External documentation that applies group-wide:

| Document | Maintained By | Focus |
|----------|---------------|-------|
| [Computational Resources](https://docs.google.com/document/d/1oocMGywoeLx981uwZ5qUxRpXRDmpwQ3LNZZVTpnIGNM/edit) | Keith Keller | Servers, Podman, Jupyter |
| [JupyterHub](https://docs.google.com/document/d/1dTrfAeqPZVzjYl8Cxsz6yPZtkSn-XBnebmd-nXFV2bk/edit) | Keith Keller | Group JupyterHub instance |
| [Server Status](https://genomics.lbl.gov/~kkeller/arkingroupServers.html) | Keith Keller | Current server specs and availability |

## Section 5: Leaving the Group

Offboarding checklist for departing members:

- [Offboarding Checklist](offboarding/checklist.md) — Account cleanup and knowledge transfer
