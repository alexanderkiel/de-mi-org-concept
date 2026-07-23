# Governance Comparison: openCode vs. Our Org Concept

*Compiled 2026-07-16 from public sources (see links throughout). Compares the
governance of [openCode](https://opencode.de/en/home) with the concept in
[concept.md](concept.md).*

---

## The Fundamental Difference: Elected Community Governance vs. Institutional Operator

The two structures answer the question "who is in charge, and why are they
legitimate?" in opposite ways.

**openCode is top-down and institutionally anchored.** The platform is operated
by [ZenDiS](https://www.zendis.de/en) (Zentrum für Digitale Souveränität der
Öffentlichen Verwaltung, a GmbH owned by the federal government), which took
over responsibility from the BMI in early 2024. Legitimacy comes from the
state: ZenDiS staff make platform decisions, a paid community-management team
runs the community, and there are no elected roles, no member voting, and no
published procedure by which users could change the rules. Users participate
under [terms of use](https://opencode.de/en/about-opencode), not as members of
a self-governing body.

**Our concept is bottom-up and member-governed.** Legitimacy comes from
election: three Admins chosen by all members via STV with a RON option,
two-year terms, a scaling quorum, and a documented bootstrap procedure.
Members are not just users of a service — they are the electorate that
constitutes the governing body, and rule changes happen via reviewable pull
requests (concept.md Section 10). openCode has no equivalent to any of this.

---

## Where the Two Are Surprisingly Similar: Repository Rules

Section 6 of the concept and openCode's
[content requirements](https://opencode.de/de/wissen/rechtssichere-nutzung/anforderungen-an-inhalte)
(already referenced in the concept's notes) overlap heavily in substance:

| Topic                      | openCode                                                  | Our concept (Section 6)                        |
|----------------------------|-----------------------------------------------------------|------------------------------------------------|
| License                    | OSI-approved mandatory                                    | OSI-approved mandatory, Apache 2.0 recommended |
| SBOM                       | Mandatory (SPDX-named, with license/copyright data)       | Mandatory per release (CycloneDX or SPDX)      |
| Signed artifacts           | Checked via badge (≥80% signed tags)                      | Mandatory, with verification docs              |
| Review                     | Badge criterion (≥75% of MRs maintainer-reviewed)         | Mandatory for every change                     |
| Maintenance/responsiveness | Badge criteria (commits, ≤7-day issue response, releases) | Mandatory 4-week response time (Section 8)     |
| Regulatory framing         | Digital sovereignty, BSI Grundschutz                      | NIS2/KRITIS operator enablement                |

The interesting difference is the **enforcement philosophy**. openCode uses a
mix of gatekeeping (license compliance is checked before inclusion, partly
manually by the openCode team) and **incentives**: its
[Badge Programm](https://gitlab.opencode.de/open-code/badgebackend/gitlab-profile)
automatically measures maintenance, review coverage, and signing, and displays
the result in the software catalog — repositories that fall short lose badges,
not their existence. Our concept instead makes the rules **binding with a
sanction ladder**: `COMPLIANCE.md` self-assessment, spot checks, a three-month
grace period, and archiving by Admin majority as the ultimate consequence. Our
rules are stricter (openCode's maintenance criteria are aspirational badge
thresholds; ours are mandatory), but openCode's automated, continuous badge
checking is more scalable than our spot-check model — an automated compliance
dashboard in the openCode style would fit our concept well and keep Admin
workload down.

---

## Other Structural Contrasts

- **Legal entity.** openCode has one from day one — ZenDiS GmbH carries
  liability, contracts, and operations. Our concept currently leaves this open
  (the feedback notes mention TMF or GMDS as candidates), and the feedback
  point "Herstellerhaftung wird nicht über TMF usw. gehen" shows this is
  unresolved. This is the piece openCode has that our concept structurally
  lacks.
- **Platform sovereignty.** openCode runs its own GitLab instance (digital
  sovereignty is its raison d'être); our concept builds on GitHub and treats
  platform risk through account security (2FA, few Admins) rather than
  self-hosting.
- **Separation of powers.** Our Admin/Maintainer split — Admins handle
  organizational matters only and never judge repository content — has no
  analog at openCode, where the operator both sets and enforces all rules and
  also runs the infrastructure.
- **Scale of ambition.** openCode is a cross-organizational *platform*
  (5,300+ users, 2,200+ projects, per
  [ZenDiS](https://www.zendis.de/en/news/presse/opencode-relaunch-vom-softwareverzeichnis-zur-plattform-fuer-die-digitale-souveraenitaet));
  our concept governs *one organization's* namespace. That is why openCode
  needs staff and terms of use where we can get away with three elected
  volunteers.

---

## ZenDiS Headcount

ZenDiS is small — currently around **40–50 people** — and it was tiny until
recently:

- **March 2024:** just **9 employees** total, with about three each working on
  openDesk and openCode — small enough that a Bundestag member publicly
  questioned whether the goals were achievable with that staffing
  ([heise](https://www.heise.de/news/Digitale-Souveraenitaet-Mit-neun-Beschaeftigten-zur-neuen-Behoerden-Office-Suite-9653935.html)).
- **Mid-2026:** the [LinkedIn profile](https://de.linkedin.com/company/zendis)
  lists ZenDiS in the **11–50 employee** bracket with **45 people** associated
  with the company page, and the
  [career FAQ](https://www.zendis.de/en/career/faq) describes the team as
  still growing. ZenDiS itself publishes no official headcount, so ~45 is the
  best available figure.

Note the staffing model: ZenDiS's own staff is mostly product management,
community management, legal, and coordination — the actual development of
openDesk and much of openCode's tooling is contracted out to external
open-source companies. The openCode platform itself is therefore run by only a
slice of those ~45 people, plus contractors.

For our comparison this is encouraging: the operational entity behind a
national open-source platform is a mid-double-digit organization, and
openCode's share of it started at ~3 people. An elected three-Admin model plus
maintainers is not unrealistically lean by comparison — what ZenDiS's staff
provides that our concept doesn't is the paid, continuous capacity for
community management, legal counsel, and compliance tooling.

---

## Bottom Line

Our concept is far more democratic and more precisely specified as a
*governance* document (elections, term limits, CoC enforcement, rule-change
procedure — openCode publishes none of that), while openCode is stronger on
the *operational* side: a legal entity, paid staff, automated compliance
tooling, and platform sovereignty. The most transferable ideas from openCode
are the automated badge/compliance checking and the clarity of having a legal
person behind the organization — both of which the concept's feedback notes
already gesture at.

---

## Sources

- [openCode home](https://opencode.de/en/home)
- [About openCode](https://opencode.de/en/about-opencode)
- [openCode: Anforderungen an Inhalte](https://opencode.de/de/wissen/rechtssichere-nutzung/anforderungen-an-inhalte)
- [openCode Badge Programm documentation](https://gitlab.opencode.de/open-code/badgebackend/gitlab-profile)
- [ZenDiS](https://www.zendis.de/en)
- [ZenDiS press release: openCode relaunch](https://www.zendis.de/en/news/presse/opencode-relaunch-vom-softwareverzeichnis-zur-plattform-fuer-die-digitale-souveraenitaet)
- [Wikipedia: Zentrum für Digitale Souveränität der Öffentlichen Verwaltung](https://de.wikipedia.org/wiki/Zentrum_f%C3%BCr_Digitale_Souver%C3%A4nit%C3%A4t_der_%C3%96ffentlichen_Verwaltung)
- [heise: „Mit neun Beschäftigten zur neuen Behörden-Office-Suite?"](https://www.heise.de/news/Digitale-Souveraenitaet-Mit-neun-Beschaeftigten-zur-neuen-Behoerden-Office-Suite-9653935.html)
- [ZenDiS on LinkedIn](https://de.linkedin.com/company/zendis)
- [ZenDiS career FAQ](https://www.zendis.de/en/career/faq)
