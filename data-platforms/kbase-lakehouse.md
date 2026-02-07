# KBase BER Data Lakehouse

The BER Data Lakehouse (BERDL) provides Spark-based access to research data from DOE BER programs including ENIGMA, PROTECT, NMDC, and KBase.

## Access

1. Create a [KBase account](https://www.kbase.us/) with your ORCID
2. Enable MFA on your KBase account
3. Request access to a tenant (e.g., ENIGMA) — contact your PI or the KBase team
4. Access JupyterHub at [hub.berdl.kbase.us](https://hub.berdl.kbase.us/)

Full onboarding guide: [Google Doc](https://docs.google.com/document/d/1p2KZR0y6FDnsHEFYysLazm9R1YXuRSJQAurMacm09RE/edit)

## Tenants

Each DOE program has its own tenant with isolated data:

| Tenant | Program |
|--------|---------|
| enigma | ENIGMA environmental genomics |
| protect | PROTECT contamination research |
| phage_foundry | Phage Foundry |
| nmdc | National Microbiome Data Collaborative |
| kbase | KBase platform data |

## BERDL Table Structure (ENIGMA/CORAL)

BERDL uses three table types, documented in detail in the [BERDL Conventions doc](https://docs.google.com/document/d/1a0CRMl4YH01FHlEX7ky8XgmrTAoGc13RxVrxqrq6E2Y/edit):

- **`sdt_*`** (Static Data Tables): Core entities — locations, samples, reads, assemblies, genomes, genes, ASVs
- **`ddt_*`** (Dynamic Data Tables / Bricks): N-dimensional measurement arrays for large-scale analytical results
- **`sys_*`** (System Tables): Ontology terms, type definitions, process metadata

## CORAL Data Model

The ENIGMA Common Data Model (CDM) is defined as a LinkML schema: [realmarcin/linkml-coral](https://github.com/realmarcin/linkml-coral)

Key stats: 291 columns, 69 semantic microtypes, 46 validation rules. Full provenance tracking from sample collection through sequencing to analysis.

## AI Tools for the Lakehouse

Three existing tools for AI-assisted lakehouse access:

| Tool | Approach | Repo |
|------|----------|------|
| [BERDL-ENIGMA-CORAL](https://github.com/jmchandonia/BERDL-ENIGMA-CORAL) | DuckDB-backed MCP server + CLI tools | Python, uv |
| [lakehouse-skills](https://github.com/cmungall/lakehouse-skills) | Claude skills for REST API + Dremio SQL | Shell + Python |
| [lakehouse-chat](https://github.com/justaddcoffee/lakehouse-chat) | NL→SQL chat interface using Claude | Python |

## Developer Tokens

Many tools require a KBase authentication token:
1. Go to [KBase](https://www.kbase.us/) → Account → Developer Tokens
2. Generate a token
3. Set as environment variable: `export KBASE_TOKEN=your-token-here`
