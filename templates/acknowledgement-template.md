# Acknowledgement Template (Discover / intake)

The first reply OSS-SIRT sends a Finder. Goal: confirm receipt, set
expectations, and signal confidentiality — within **2 business days** of
receipt. Pick the variant matching the channel the report arrived on. Replace
every `{{PLACEHOLDER}}` before sending.

This is the standalone version of **Template 1** referenced in the
[Intake Runbook](.docs//intake-runbook.md) (step 1, Discover) and
[Notification Templates](./templates/notification-templates.md).

---

## Variant A — Email reply

> Use when the report arrives via `security@oss-sirt.linuxfoundation.org`.

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

Please keep this conversation on this email thread. If anything material changes
on your end — for example, you observe exploitation in the wild, or you intend
to publish — please tell us right away.

Our coordinated disclosure policy:
https://oss-sirt.linuxfoundation.org/security/policy

Thank you,
OSS-SIRT
security@oss-sirt.linuxfoundation.org
```

---

## Variant B — GitHub private vulnerability reporting reply

> Use when the report arrives through a repository's GitHub private
> vulnerability reporting. Post as a comment on the draft advisory thread; the
> channel is already private, so there's no need to repeat encryption guidance.

```
Hi @{{FINDER_HANDLE}},

Thanks for reporting this through GitHub private vulnerability reporting —
we've received it and a team member is reviewing it now. We're tracking this
as {{TRACKING_ID}}.

What happens next:
  - We'll triage and validate and post an initial assessment here within
    10 business days.
  - We'll keep this advisory updated as we work toward a fix and a coordinated
    disclosure date.

This advisory and discussion stay private (TLP:RED) until we agree on a public
disclosure date. If you'd like to review or help with the fix, let us know and
we'll add you as a collaborator on the advisory.

Please flag anything material right away — especially active exploitation or
any plan to publish.

Policy: https://oss-sirt.linuxfoundation.org/security/policy

— OSS-SIRT
```

---

## Variant C — Anonymous / no-reply-address report

> Use when the Finder gave no contact details. Post this where they can see it
> if a thread exists (e.g., GitHub); otherwise keep it on file to show the
> acknowledgement was attempted. There is no one to email.

```
Subject: [OSS-SIRT] Report received — {{TRACKING_ID}}

Thank you for your report. We've received it and assigned tracking ID
{{TRACKING_ID}}, and a team member is reviewing it now. We're treating the
details as confidential (TLP:RED) until a coordinated disclosure date is agreed.

Because the report did not include contact details, we're unable to send you
status updates. If you'd like to follow the issue or be credited, you can reach
us at security@oss-sirt.linuxfoundation.org and reference {{TRACKING_ID}}.

Policy: https://oss-sirt.linuxfoundation.org/security/policy

— OSS-SIRT
```

---

### Fill-in checklist

- `{{TRACKING_ID}}` — assigned at intake (runbook step 1).
- `{{FINDER_NAME}}` / `{{FINDER_HANDLE}}` — as the Finder identified themselves.
- Confirm the report is set to **TLP:RED** before replying.
- Start the clock: initial assessment is due within **10 business days**
  (Template 2a/2b).
