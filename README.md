# PhishGuard — URL Threat Scanner

A browser-based tool that analyzes a URL's structure and flags patterns commonly used in phishing links. Built as a student cybersecurity group project.

**Live demo:** `https://YOUR-USERNAME.github.io/phishing-url-detector` *(update after enabling GitHub Pages)*

## What it does

PhishGuard doesn't rely on a live database of known-bad sites. Instead, it inspects the *structure* of a URL — the tricks phishing links commonly use — and produces a weighted risk score (0–100) with a plain-English breakdown of what it found.

## Checks performed

| # | Check | Why it matters |
|---|-------|-----------------|
| 1 | IP address as domain | Legitimate sites use readable domain names, not raw IPs |
| 2 | `@` symbol in URL | Browsers ignore text before `@`, hiding the real destination |
| 3 | Unusual URL length | Long URLs can bury a fake domain or extra parameters |
| 4 | Subdomain count | Excess subdomains fake belonging to a trusted brand |
| 5 | Hyphens in domain | `paypal-secure-login.com` is not `paypal.com` |
| 6 | HTTPS presence | Missing encryption removes a layer of trust |
| 7 | URL shortener | Shorteners hide the real destination until you click |
| 8 | Suspicious keywords | Words like "verify" or "confirm" create false urgency |
| 9 | Brand impersonation | Brand name in the URL, but not the brand's real domain |
| 10 | Double-slash redirect | A hidden `//` mid-path can silently redirect elsewhere |
| 11 | Risky TLD | `.tk`, `.xyz`, etc. are cheap and heavily abused |

Each check has a weight (e.g. an IP-as-domain counts more than URL length). The final score is the sum of failed checks' weights, divided by the total possible weight.

## Scoring

| Score | Verdict |
|-------|---------|
| 0–24 | Likely Safe |
| 25–54 | Suspicious |
| 55–100 | Likely Phishing |

## Tech stack

Vanilla HTML, CSS, and JavaScript. No frameworks, no backend, no dependencies — it runs entirely in the browser as a single file.

## Running it locally

1. Clone the repo: `git clone https://github.com/YOUR-USERNAME/phishing-url-detector.git`
2. Open `index.html` in any browser. That's it — no build step, no server required.

**Team:**
- Aarav Tamang
- Lucky Chaudari
- Biraj Karki
- Simon Bhattarai
## Limitations & future improvements

This is a heuristic-based tool, not a live threat-intelligence service — it can produce false positives and false negatives. Possible next steps:
- A backend (e.g. Flask) to check URLs against real phishing blocklists
- Logging scanned URLs for analysis
- Browser extension version for real-time warnings

## Disclaimer

For educational purposes only. Do not rely on this as your sole method of judging whether a link is safe.
