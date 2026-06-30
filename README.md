# ffraud-ipranges

> Open IP-intelligence, published daily by [ffraud.com](https://ffraud.com).
> Free for everyone. MIT licensed. No signup, no rate limits on the data here.

This is the **open data layer** of ffraud — our own derived threat intelligence,
refreshed every day. It is **not** a mirror of anyone else's blocklist: every
number here is computed by the ffraud engine from billions of observations and
community reports. We never republish or name an upstream feed — what you get is
the *conclusion*, which is uniquely ours.

## What's inside

| File | What it is |
|------|-----------|
| `threat-ips/confirmed-abusive.csv` | Every IP confirmed abusive by **2+ independent sources**, with our 0–100 fraud score and how many sources agreed. ~750k IPs. |
| `ip-intelligence/examples.json` | Full per-IP intelligence samples: fraud score, a plain-English reason, and threat categories — the same data our API returns. |
| `disposable-email-domains.txt` | ~207,000 disposable / throwaway email domains. |
| `metadata.json` | Counts + the UTC timestamp of this build. |

> **Coming soon:** `asn-reputation/` — network-level (ASN) reputation. We're
> finishing the vetting so we never mislabel a legitimate provider, then it lands here.

## Quick start

```bash
# Confirmed-abusive IPs (2+ independent sources each) — drop into a firewall/WAF
curl -s https://raw.githubusercontent.com/FFraud-com/ffraud-ipranges/main/threat-ips/confirmed-abusive.csv

# Block disposable-email signups
curl -s https://raw.githubusercontent.com/FFraud-com/ffraud-ipranges/main/disposable-email-domains.txt
```

The IP list is high-precision on purpose: an IP only appears here if **at least
two independent intelligence sources** flagged it *and* our engine scored it ≥50.
Single-source noise is excluded.

## What makes this different

Most lists give you `1.2.3.4 — bad`. ffraud gives you a **score**, a count of
**how many independent sources agree**, and (in the examples + our API) a
plain-English **reason** and **category** — written for a human deciding whether
to block. See `ip-intelligence/examples.json`.

## Honesty & corrections

- Scores are ffraud's own computation. We never name our upstream sources — that's
  our supply chain, not yours to depend on.
- Updated daily via automated export (see `metadata.json` for the build time).
- Think something's a false positive? Open an issue or report it at
  https://ffraud.com/report — community corrections feed straight back in.

## License

MIT — use it in commercial products, fork it, redistribute it. Attribution
appreciated, not required.
