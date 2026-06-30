# IP Fraud Database

**Free, open database of fraudulent and abusive IP addresses. Updated every day.**

![License](https://img.shields.io/badge/license-MIT-22c55e)
![Updated](https://img.shields.io/badge/updated-daily-3b82f6)
![Abusive IPs](https://img.shields.io/badge/abusive%20IPs-750k%2B-e11d2c)
![Disposable domains](https://img.shields.io/badge/disposable%20domains-207k%2B-f59e0b)

The open data layer of [ffraud.com](https://ffraud.com). Every IP in this database was flagged as abusive by **at least two independent intelligence sources** and scored by the ffraud engine. No signup, no API key, no rate limits. Drop it straight into a firewall, a WAF, a signup form, or a fraud pipeline.

> We publish our own conclusions, never our sources. What you get is the verdict, computed from billions of observations and community reports. The supply chain stays ours, the answer is yours to use.

## What is inside

| File | Rows | What it is |
|------|------|-----------|
| [`threat-ips/confirmed-abusive.csv`](threat-ips/confirmed-abusive.csv) | ~750,000 | Abusive IPs, each confirmed by 2+ independent sources, with our 0 to 100 fraud score and the number of sources that agreed |
| [`disposable-email-domains.txt`](disposable-email-domains.txt) | ~207,000 | Throwaway and disposable email domains |
| [`ip-intelligence/examples.json`](ip-intelligence/examples.json) | sample | Full per-IP intelligence: fraud score, a plain-English reason, and threat categories |
| [`metadata.json`](metadata.json) | | Live counts and the UTC build time |

## Quick start

```bash
# Confirmed-abusive IPs (firewall, WAF, or your own fraud checks)
curl -s https://raw.githubusercontent.com/FFraud-com/ip-fraud-database/main/threat-ips/confirmed-abusive.csv

# Disposable email domains (block throwaway signups)
curl -s https://raw.githubusercontent.com/FFraud-com/ip-fraud-database/main/disposable-email-domains.txt
```

## Why this one is different

Most lists give you `1.2.3.4, bad` and nothing else. This database tells you **how many independent sources agreed** and gives every IP our **own 0 to 100 fraud score**:

```csv
ip,ffraud_score,independent_sources
80.82.77.33,95,40
2.57.121.25,95,36
193.46.255.86,95,33
```

An IP only makes the list if **2 or more independent sources** flagged it and our engine scored it **50 or higher**. Single-source noise is filtered out. The worst offenders here carry 30 to 40 independent confirmations. For the full picture (a plain-English reason and categories per IP) see [`ip-intelligence/examples.json`](ip-intelligence/examples.json) or query the live API at [ffraud.com](https://ffraud.com).

## Updated every single day

Rebuilt and pushed daily straight from the live ffraud engine. Check [`metadata.json`](metadata.json) for the exact build time and current counts. Star the repo to keep it on your radar.

## Coming soon

- **Network (ASN) reputation**: which whole networks are predominantly malicious, scored and corroborated, with legitimate providers carefully excluded.

## Found a false positive?

[Report it](https://ffraud.com/report) or open an issue. Community corrections feed straight back into the engine and the next daily build.

## License

MIT. Use it anywhere, including commercial products. Fork it, redistribute it, build on it. Attribution appreciated, not required.

---

Built by [ffraud.com](https://ffraud.com), free IP fraud intelligence for everyone.
