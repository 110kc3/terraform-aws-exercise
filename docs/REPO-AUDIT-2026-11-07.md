# Repository audit — 2026-11-07

Repository: `terraform-aws-exercise` · Agent: Codex

Audited source: [`9fe453b`](https://github.com/110kc3/terraform-aws-exercise/commit/9fe453bb456af0f0c9c4d9aa3ab29a470c4a3741)

Evidence collected: 2026-11-06–2026-11-07. Chat item numbers: 32.

This dated report preserves the findings and feature suggestions already reported in chat.
The owner authorized recording, committing and pushing this documentation. The findings
remain unresolved, and the proposed features have not been selected for implementation.
This is an evidence report, not a second accepted work queue. Existing project decisions,
accepted tasks and owner-only blockers remain authoritative in [README.md](../README.md).

## Verification status

The evidence below describes the earlier audit, including its limitations. This documentation
change does not claim to fix the findings or repeat every runtime reproduction. No production
account, database or infrastructure was changed by those isolated reproductions.

Documentation push: CI verification pending. Check the exact resulting commit on the next
session using [Actions](https://github.com/110kc3/terraform-aws-exercise/actions?query=branch%3Amain);
no run was awaited for this documentation update. A repository without a workflow has no
CI result to claim.

## 32. Network routing and SSH exposure do not match intent

Type: Open finding — not fixed. Priority: Medium. Estimated effort: Small.

The second ALB subnet is not associated with the internet-gateway route table; only the first subnet is. The SSH rule also allows 0.0.0.0/0 despite a VPC-only comment.

**Evidence:** Static review of [network/main.tf](../network/main.tf), [network/sg.tf](../network/sg.tf) and [ALB configuration](../load-balancer/main.tf). No AWS resources were deployed.

**Suggested change:** Associate every intended public ALB subnet with the correct route table and constrain management access to the explicitly intended source.

**Acceptance if selected:** Both selected public subnets have the intended internet route; SSH ingress matches the documented management boundary; checks catch a missing association or unintended world-open SSH.
