# IP Fraud Database

**Free, open database of fraudulent and abusive IP addresses and networks. Updated every day.**

![License](https://img.shields.io/badge/license-MIT-22c55e)
![Updated](https://img.shields.io/badge/updated-daily-3b82f6)
![Abusive IPs](https://img.shields.io/badge/abusive%20IPs-750k%2B-e11d2c)
![Fraudulent networks](https://img.shields.io/badge/fraudulent%20networks-600%2B-8b5cf6)
![Disposable domains](https://img.shields.io/badge/disposable%20domains-207k%2B-f59e0b)

The open data layer of [ffraud.com](https://ffraud.com). Every IP here was flagged by **at least two independent intelligence sources**, scored by the ffraud engine, and tagged with the **threat category** and **infrastructure type** we detected. No signup, no API key, no rate limits. Drop it straight into a firewall, a WAF, a signup form, or a fraud pipeline.

> We publish our own conclusions, never our sources. The supply chain stays ours, the answer is yours to use.

## What is inside

| File | Rows | What it is |
|------|------|-----------|
| [`threat-ips/confirmed-abusive.csv`](threat-ips/confirmed-abusive.csv) | ~750,000 | Abusive IPs, each confirmed by 2+ independent sources, with our 0 to 100 fraud score, the **threat category** (c2, malware, botnet, brute-force, web-attack, scanner, phishing, spam) and the **infrastructure type** (proxy, vpn, tor, datacenter, mobile) when known |
| [`asn-reputation/fraudulent-networks.csv`](asn-reputation/fraudulent-networks.csv) | ~600 | Networks (ASNs) where the IPs we observed were overwhelmingly malicious and proxy-heavy. The bulletproof-hosting and proxy-operation signature |
| [`disposable-email-domains.txt`](disposable-email-domains.txt) | ~207,000 | Throwaway and disposable email domains |
| [`ip-intelligence/examples.json`](ip-intelligence/examples.json) | sample | Full per-IP intelligence: score, a plain-English reason, and categories |
| [`metadata.json`](metadata.json) | | Live counts and the UTC build time |

## What you get per IP

```csv
ip,ffraud_score,sources,category,type
80.82.77.33,95,40,c2,proxy
2.57.121.25,95,36,c2,proxy
193.46.255.86,95,33,c2,proxy
```

- **ffraud_score**: our own 0 to 100 score.
- **sources**: how many independent intelligence sources flagged it. An IP only makes the list at 2 or more. The worst here carry 30 to 40.
- **category**: what it was caught doing (c2, malware, botnet, brute-force, web-attack, scanner, phishing, spam).
- **type**: the infrastructure when we can see it (proxy, vpn, tor, datacenter, mobile).

## Quick start

```bash
# Confirmed-abusive IPs, with category and type
curl -s https://raw.githubusercontent.com/FFraud-com/ip-fraud-database/main/threat-ips/confirmed-abusive.csv

# The worst networks
curl -s https://raw.githubusercontent.com/FFraud-com/ip-fraud-database/main/asn-reputation/fraudulent-networks.csv

# Disposable email domains
curl -s https://raw.githubusercontent.com/FFraud-com/ip-fraud-database/main/disposable-email-domains.txt
```

## Help build it: report and submit IPs

This database grows with the community. If you run servers, fail2ban, a WAF, or your own honeypots, send us the IPs that hit you and we publish them:

- **Report or bulk-submit** at [ffraud.com/report](https://ffraud.com/report).
- **Open an issue** here with a list of IPs and what they did.

We review, dedupe, score, and roll confirmed reports into the next daily build, with credit if you want it. Every report protects the next person that IP attacks.

## A note on the networks list

`fraudulent-networks.csv` reflects the share of each network's IPs that **we observed** as malicious. It is a measurement of observed traffic, not a legal judgment of any operator. Run a listed network and think it is wrong? [Tell us](https://ffraud.com/report) and we recheck on the next build.

## Updated every single day

Rebuilt and pushed daily from the live ffraud engine. See [`metadata.json`](metadata.json) for the build time and current counts. Star the repo to keep it close.

## License

MIT. Use it anywhere, including commercial products. Fork it, redistribute it, build on it. Attribution appreciated, not required.

---

Built by [ffraud.com](https://ffraud.com), free IP fraud intelligence for everyone.
