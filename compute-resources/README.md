# Compute Resources

## Authoritative Documentation

The primary references for group compute resources are maintained by Keith Keller:

- [Computational Resources Google Doc](https://docs.google.com/document/d/1oocMGywoeLx981uwZ5qUxRpXRDmpwQ3LNZZVTpnIGNM/edit) — Servers, Podman containers, Jupyter
- [JupyterHub Google Doc](https://docs.google.com/document/d/1dTrfAeqPZVzjYl8Cxsz6yPZtkSn-XBnebmd-nXFV2bk/edit) — Group JupyterHub instance
- [Server Status Page](https://genomics.lbl.gov/~kkeller/arkingroupServers.html) — Current server specs and availability

## Quick Reference

Group servers are Linux machines accessible via SSH from the LBL network (or VPN). You need an LBL LDAP account.

```bash
ssh username@servername.lbl.gov
```

For container workloads, we use Podman (not Docker) — see Keith's doc above for setup.

For JupyterHub access, go to the group's JupyterHub instance (URL in the Google Doc) and authenticate with your LBL credentials.

## Getting Access

See the [Onboarding Checklist](../onboarding/README.md) for initial setup steps.
