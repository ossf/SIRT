# Security Policy

The Open Source Security Incident Response Team (**OSS-SIRT**) coordinates the
disclosure of security vulnerabilities for this project. Thank you for helping
keep our users safe.

Our full **Coordinated Vulnerability Disclosure (CVD) Policy** — including our
lifecycle, embargo handling, and timelines — is published at:
**https://oss-sirt.linuxfoundation.org/security/policy**

## Reporting a vulnerability

**Please do not open a public issue, pull request, or discussion for a security
problem.** Use one of the private channels below.

### Preferred — GitHub private vulnerability reporting

Use the **"Report a vulnerability"** button on this repository's **Security**
tab. This keeps the report private, lets us collaborate with you on a draft
advisory, and supports private patch development. This is our preferred intake
whenever the project is on GitHub.

### Alternative — encrypted email

If GitHub reporting is unavailable, email
**security@oss-sirt.linuxfoundation.org**. The address supports transport
encryption (MTA-STS / STARTTLS); for end-to-end protection you may use our
OpenPGP key linked from the policy page. We would rather receive your report
than have you blocked by encryption — when in doubt, send it.

### What to include

- Affected project, component, and version(s)
- Environment (OS, architecture, platform, configuration)
- Reproduction steps; proof-of-concept or screenshots if available
- Impact and how the issue could be exploited
- Any embargo/disclosure timing you would like us to honor
- Whether and how you wish to be credited

Reports may be made anonymously, but we then cannot send you status updates.

## What to expect

| Stage           | Commitment                                                      |
| --------------- | --------------------------------------------------------------- |
| Acknowledgement | Within **2 business days**                                      |
| Initial triage  | Initial assessment within **10 business days**                  |
| Communication   | Ongoing status updates through remediation                      |
| Confidentiality | Embargoed reports handled as **TLP:RED** until public disclosure |
| Credit          | Finder credited by default; anonymity honored on request        |
| Disclosure      | Coordinated; default planning target is PD within **90 days**, negotiated shorter where a fix can ship sooner |

## Our process at a glance

We follow a nine-phase lifecycle:

```
Discover → Triage → Validate → Coordination → Patch → Test → Document → Distribute → Disclose
```

Case details remain private (TLP:RED, need-to-know) through the embargo; the
patch and full advisory are released together at Public Disclosure. The process
itself is open and reviewable — see the policy linked above.

## Safe harbor

Good-faith research conducted in line with our policy is authorized; we will not
pursue or support legal action for such reports. This is not a bug bounty and
confers no expectation of payment. Do not access more data than necessary, do
not degrade service for others, and do not disclose before the agreed date.

_Full policy: https://oss-sirt.linuxfoundation.org/security/policy_
