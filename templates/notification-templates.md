# OSS-SIRT Notification Templates

Pre-written messages for each communication point in the
[CVD Policy](./coordinated-vulnerability-disclosure-policy.md) lifecycle.
Replace every `{{PLACEHOLDER}}` before sending. Default handling for all
pre-disclosure material is **TLP:RED**.

Quick map of which template to use when:

| Lifecycle phase            | Template                          | Audience            |
| -------------------------- | --------------------------------- | ------------------- |
| Discover / intake          | 1. Acknowledgement                | Finder              |
| Triage / Validate          | 2. Triage assessment              | Finder              |
| Coordination → Distribute  | 3. Embargoed notification         | Read-in providers   |
| Disclose                   | 4. Public disclosure advisory     | Public              |
| (any, on early leak)       | 5. Embargo-break notice           | Read-in + public    |

---

## 1. Acknowledgement (Discover / intake)

> Send within **2 business days** of receipt. If the report came via GitHub
> private vulnerability reporting, reply on the advisory thread instead of email.

```
Subject: [OSS-SIRT] Received your report — {{TRACKING_ID}}

Hello {{FINDER_NAME}},

Thank you for reporting this to OSS-SIRT. We've received your report and
assigned it the tracking ID {{TRACKING_ID}}. A team member is reviewing it now.

What happens next:
  - We'll triage and validate the report and send you an initial assessment
    within 10 business days.
  - We'll keep you updated as we work toward a fix and a coordinated
    disclosure date.

We are treating the details you sent as confidential (TLP:RED) and will not
share them outside the people needed to resolve the issue until a public
disclosure date is agreed.

Please continue this conversation on {{CHANNEL: this email thread / the GitHub
advisory}}. If anything material changes on your end (for example, you observe
exploitation in the wild, or you intend to publish), please tell us right away.

Our coordinated disclosure policy:
https://oss-sirt.linuxfoundation.org/security/policy

Thank you,
OSS-SIRT
security@oss-sirt.linuxfoundation.org
```

---

## 2. Triage assessment (Triage / Validate)

> Use the branch that matches your determination. State your reasoning so the
> Finder can correct you if the original report was misunderstood.

**2a — Confirmed vulnerability**

```
Subject: [OSS-SIRT] {{TRACKING_ID}} — confirmed, proceeding to remediation

Hello {{FINDER_NAME}},

We've reproduced the issue and confirmed it is a security vulnerability in
{{PROJECT}} {{AFFECTED_VERSIONS}}. Thank you — this is a real finding.

Next steps:
  - We are opening a private advisory and developing a fix.
  - We will request a CVE ID via {{CNA}}.
  - Proposed public disclosure target: {{PD_DATE}} (default planning window is
    up to 90 days; we aim to disclose as soon as a fix can ship). Let us know if
    this timing works for you.

Credit: we credit finders by default. Please tell us how you'd like to be
named ({{name / handle / affiliation}}), or let us know if you prefer to
remain anonymous.

Would you like to be added as a collaborator on the private fix so you can
review it before release?

OSS-SIRT
```

**2b — Not a vulnerability (bug / feature request / works-as-intended)**

```
Subject: [OSS-SIRT] {{TRACKING_ID}} — assessment

Hello {{FINDER_NAME}},

Thank you for the report. After review, we've assessed this as
{{a non-security bug / expected behavior / a feature request}} rather than a
security vulnerability, because {{SPECIFIC_REASONING}}.

{{If a bug:}} Could you please refile this as a regular issue at {{LINK}}?
{{If a feature request:}} If you'd like to see this behavior change, a feature
request at {{LINK}} is the best path.

If we've misunderstood any part of your report, please reply — we're happy to
take another look.

OSS-SIRT
```

---

## 3. Embargoed notification (Coordination → Distribute)

> Sent to read-in providers/downstreams on the embargo list, typically
> **1–30 working days before PD**, scaled to severity and patch complexity.
> Avoid releasing into weekends/holidays; prefer Mon–Wed disclosure.

```
Subject: [TLP:RED][EMBARGO until {{PD_DATE}}] {{CVE_ID}} in {{PROJECT}}

CONFIDENTIAL — TLP:RED. Do not redistribute outside your organization's
need-to-know responders. Public disclosure is embargoed until {{PD_DATE}}
{{TIME + TZ}}.

Summary
  - Identifier: {{CVE_ID}}
  - Project/component: {{PROJECT}} / {{COMPONENT}}
  - Affected versions: {{AFFECTED_VERSIONS}}
  - Fixed versions: {{FIXED_VERSIONS}}
  - Weakness (root cause): {{CWE_ID}} — {{CWE_NAME}}
  - Severity: {{CVSS_V4_SCORE}} ({{CVSS_V4_VECTOR}})
    [legacy: CVSS v3.1 {{CVSS_V31_SCORE}}]
  - Reporter credit: {{CREDIT or "withheld at reporter request"}}

Description
{{Plain-language description of the issue and impact. Where helpful, note the
affected code path and the configurations/settings in which a deployment is or
is NOT affected, so providers can judge their own exposure.}}

Mitigation / work-around
{{Available work-around, or "none — patch required."}}

Patch availability
{{How and where the patch will be made available at PD, e.g., release tag,
package version, advisory link.}}

What we ask of you
  - Prepare your update so you can ship promptly at public disclosure.
  - Keep this information TLP:RED until {{PD_DATE}}.
  - Reply to this thread with any patch problems or qualification issues —
    someone on OSS-SIRT is monitoring for replies.

Public disclosure date: {{PD_DATE}} {{TIME + TZ}}

OSS-SIRT
security@oss-sirt.linuxfoundation.org
```

---

## 4. Public disclosure advisory (Disclose)

> Publish at PD. For GitHub projects, publishing the draft Security Advisory
> populates the Security tab; also announce to {{security-announce list}} and,
> for high-impact issues, the general community channel. Include the CVE ID and
> link the OSV record. Structure follows a standard advisory template: title,
> summary, identifiers, impact/status, mitigation, acknowledgement, references,
> revision history.

```
Title: {{CVE_ID}}: {{SHORT_DESCRIPTIVE_TITLE}} in {{PROJECT}}

Summary
{{1–3 sentence plain-language summary of the vulnerability and its impact.}}

Identifiers
  - CVE: {{CVE_ID}}
  - GHSA: {{GHSA_ID}}
  - OSV: {{OSV_LINK}}
  - Weakness: {{CWE_ID}} — {{CWE_NAME}}

Severity
  - CVSS v4.0: {{SCORE}} ({{VECTOR}})
  - CVSS v3.1 (legacy): {{SCORE}} ({{VECTOR}})

Affected and fixed versions
  - Affected: {{AFFECTED_VERSIONS}}
  - Fixed in: {{FIXED_VERSIONS}}

Impact
{{What an attacker can do, under what conditions, and who is affected. Note any
configurations that are not affected.}}

Remediation
  - Upgrade to {{FIXED_VERSIONS}}.
  - {{Work-around, if any, for users who cannot upgrade immediately.}}

Acknowledgements
{{Reported by {{CREDIT}}. / Reported privately to OSS-SIRT.}}
Thanks to all who assisted with validation and remediation.

References
  - Advisory: {{ADVISORY_URL}}
  - Patch / release: {{RELEASE_URL}}
  - {{Additional links}}

Revision history
  - {{DATE}}: Initial publication.
```

---

## 5. Embargo-break notice (early leak contingency)

> Use if the issue is published or exploited before PD. Disclosure may be
> accelerated; publish whatever helps Consumers protect themselves even without
> a complete fix.

```
Subject: [OSS-SIRT] {{CVE_ID}} in {{PROJECT}} — disclosure accelerated

OSS-SIRT is aware that information about {{CVE_ID}} in {{PROJECT}} has become
public ahead of the planned disclosure. To help users protect themselves, we
are sharing the following now:

  - Affected versions: {{AFFECTED_VERSIONS}}
  - Status: {{patch available at {{LINK}} / patch in progress, ETA {{DATE}}}}
  - Interim mitigation: {{WORK-AROUND, or specific configurations that reduce
    exposure}}

We will update this advisory as remediation becomes available:
{{ADVISORY_URL}}

OSS-SIRT
security@oss-sirt.linuxfoundation.org
```
