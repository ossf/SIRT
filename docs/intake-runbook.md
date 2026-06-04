# OSS-SIRT Intake Runbook (one page)

Step-by-step actions for the responder on duty, keyed to the nine-phase
lifecycle in the [CVD Policy](./coordinated-vulnerability-disclosure-policy.md).
Templates referenced below are in
[notification-templates.md](./notification-templates.md). Default handling for
all pre-disclosure material is **TLP:RED / need-to-know**.

```
Discover → Triage → Validate → Coordination → Patch → Test → Document → Distribute → Disclose
```

### 1. Discover — intake & acknowledge  ⏱ ack within 2 business days
- Confirm the channel: **GitHub private vulnerability reporting** (preferred) or
  `security@oss-sirt.linuxfoundation.org`. If it arrived the "wrong" way (public
  issue, wrong list), move it private and continue — don't penalize the Finder.
- Assign a tracking ID; record reporter, date, project, claimed versions.
- Send **Template 1 (Acknowledgement)**. Set the report to TLP:RED.

### 2. Triage — is it a security issue?
- Compare against prior risk assessments, threat models, and bug bars.
- Decide: vulnerability / non-security bug / feature request / works-as-intended.
- Send **Template 2a or 2b**. If not a vulnerability, explain reasoning and close.

### 3. Validate — confirm & reproduce
- Reproduce the issue; confirm affected versions and impact.
- Open a **private** GitHub Security Advisory; add the Finder as collaborator if
  they wish to stay involved. Engage the Owner and any needed maintainers.

### 4. Coordination — embargo & disclosure date
- Identify read-in **Collaborators** (need-to-know only); formally read them in.
- Decide whether an embargo is required; agree the **Public Disclosure (PD)**
  date with the Finder. Default planning window: **up to 90 days**; aim shorter.
- Prepare the **leak contingency** (Template 5): what to tell Consumers if
  details surface early.

### 5. Patch — develop the fix privately
- Develop and test the fix on a private branch / temporary private fork so the
  fix isn't visible before users can apply it. Create a patch or work-around
  that addresses the **root cause (CWE)**.

### 6. Test — verify
- Run regression, smoke, and relevant tests; confirm the issue is resolved with
  no new regressions. Prepare (but do not cut) the release.

### 7. Document — advisory & identifiers
- Request a **CVE ID** via the appropriate CNA (MITRE is CNA of last resort).
- Capture: affected/fixed versions, CWE, **CVSS v4.0** score (v3.1 for legacy
  comparison), Consumer actions, and patch location.
- Draft the advisory (**Template 4**) and a machine-readable **OSV** record.

### 8. Distribute — stage for simultaneous availability
- Stage patch + documentation so all Consumers get the fix at PD.
- If an embargo list applies, send **Template 3 (Embargoed notification)** to
  read-in providers, typically **1–30 working days** before PD. Monitor replies
  for qualification problems. Prefer a **Mon–Wed** PD; avoid holidays.

### 9. Disclose — go public  ⏱ on the PD date
- Publish the GitHub Security Advisory (populates the Security tab), cut the
  release, and publish **Template 4** to release notes / security-announce; for
  high-impact issues, the general community channel too.
- Reference the CVE ID; link the OSV record. Flip private patch branches public.
- Credit the Finder per their preference. Reclassify case material from TLP:RED.

---

**If the embargo breaks at any point:** stop, notify the read-in group, and
publish **Template 5** with whatever guidance helps Consumers protect
themselves — even before a full fix is ready. Then resume from the current
phase on an accelerated timeline.

**Escalate to the OSS-SIRT lead when:** active exploitation in the wild, the
Finder intends to publish early, the issue spans multiple projects/vendors
(multi-party coordination), or a PD date is at risk of slipping.
