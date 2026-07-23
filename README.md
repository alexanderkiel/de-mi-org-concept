# A shared code organization for German medical informatics

This repository holds the **governance concept** for a joint code organization
that hosts the software and documentation originated in the Medical
Informatics Initiative, with the goal of widening its scope towards German
medical informatics software in general — independent of any single funding
line or initiative.

Nothing here is decided. This is a proposal, written to be argued with, and it
is deliberately lightweight: enough process to be transparent and trustworthy,
not more.

---

## The concept in five points

1. **Three admins, elected by all members** for two-year terms, using the
   Single Transferable Vote so that no single institution can capture all
   three seats. Every ballot carries a "Re-Open Nominations" option, and the
   quorum scales as √n so it stays reachable as the organization grows.
2. **A hard boundary between organizational and content authority.** Admins
   create and archive repositories and appoint maintainers; they have *no*
   say over code, releases, or merges. That belongs to the maintainers alone.
3. **Twelve mandatory rules for software repositories** — SBOMs, signed
   artifacts, CI-only builds, reviewed pull requests, advisories, operator
   documentation, DCO sign-off, and more. They exist because our software runs
   in hospitals subject to **NIS2** and **KRITIS**, where the compliance
   duties fall on the *operator*. The rules make sure every repository hands
   the operator what they need — and shift no regulatory duty or liability
   onto maintainers.
4. **Enforcement is formal and slow.** Maintainers self-assess in a
   `COMPLIANCE.md`; admins only check that assertions exist, never the quality
   of the code. A violation triggers a three-month grace period, and archiving
   by admin majority is the last resort.
5. **Digital sovereignty is treated as an exit-cost question.** We are on
   GitHub, and that is a choice that must stay reversible. The concept fixes
   rules that keep a migration affordable and requires the decision to be
   reviewed every two years.

---

## Contents

| File | What it is |
|---|---|
| [`concept.md`](concept.md) | **The governance concept itself.** Ten sections: organization profile, appointing and electing admins, admin rules and their limits, creating repositories, repository requirements, rules for software repositories, members and Code of Conduct enforcement, maintainers, digital sovereignty, and how these rules are changed. Start here. |
| [`ci-cost-estimate.md`](ci-cost-estimate.md) | **Measured CI load and migration cost.** What the existing repositories actually consume in GitHub Actions minutes, and what leaving GitHub would cost — one-off and per year. The empirical basis for Section 9. |
| [`opencode-comparison.md`](opencode-comparison.md) | **Comparison with openCode**, the federal platform operated by ZenDiS: where the two governance models differ fundamentally (elected community vs. institutional operator) and where their repository rules converge. |
| [`concept-overview.pptx`](concept-overview.pptx) | **A 5-minute overview deck** of the whole concept, with speaker notes. Nine slides. |

---

## Key numbers

| | |
|---|---|
| Admins | 3, elected, two-year terms, majority decisions |
| Mandatory rules for software repositories | 12 (plus recommended practices) |
| Grace period before enforcement | 3 months · 12 months transition for existing repositories |
| Maintainer response time | 4 weeks |
| CI consumed today by the repositories examined | ≈ 2,42 M GitHub Actions minutes per year — see [`ci-cost-estimate.md`](ci-cost-estimate.md) |
| Cost of that CI today | €0 (public repositories) · ≈ $19.400/yr at list price |
| Cost of leaving GitHub | ≈ €40.000 one-off + €25.000–50.000 per year |

---

## Open questions

These are not yet answered by the concept and need a decision:

- **Legal entity and name** — TMF or GMDS as the legal person? Under which
  name does the organization run?
- **Cost and funding** — who pays for the organization, and for CI runners if
  it ever moves off GitHub?
- **Alignment** — coordination with NUM (which hosts its repositories on
  Forgejo) and with existing repositories such as
  [DSF](https://github.com/datasharingframework/dsf),
  [Blaze](https://github.com/samply/blaze), and the
  [MII terminology service](https://gitlab.com/mii-termserv).
- **Appointing admins** — election by members, as the concept proposes, or
  nomination through existing TMF bodies?
- **Enablement** — a training offer to bring existing repositories up to the
  level Section 6 requires.
