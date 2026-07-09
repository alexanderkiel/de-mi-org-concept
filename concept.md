# Feedback

* Kosten?
* Module aktivieren - was war damit gemeint?
* Nicht unbedingt MII (unter welchem Namen soll die Org laufen?)
* NUM Koordinierungsstelle?
* Wo liegen noch andere Repos? (DSF, Blaze, https://gitlab.com/mii-termserv, ...?)

# Organization Governance

**Scope:** This document defines the basic rules and governance for a GitHub organisation that hosts the software and documentation originated in the Medical Informatics Initiative with the goal to widen the scope towards German Medical Informatics software independent of any concrete funding or initiative. It is intentionally lightweight. Its goal is to keep the organization maintainable, transparent, and trustworthy without imposing heavy process.

---

## 1. Organization Profile (Homepage)

The organization profile (the `.github` repository `README`) must, at minimum:

- Name the current **Admins** by their GitHub handle and real name.
- Link to this governance document and to the Code of Conduct.
- Describe in one or two sentences what the organization is for.

The list of Admins on the profile is the authoritative public record of who currently holds administrative responsibility.

---

## 2. Appointing Admins

- The organization has **three** Admins.
- Having three rather than one avoids a single point of failure (e.g. losing access if one person is unavailable) and lets decisions be taken by a clear majority (two of three).
- Not having more keeps accountability clear and, more importantly, limits the **attack surface**: an Admin can change repository settings, branch protection, and access rights, and can therefore compromise *any* software release in the organization. Every additional Admin is another account that, if taken over, puts every release at risk. Keeping the number of Admins small (and 2FA-protected, see Section 3) is a deliberate security measure.
- Admins are **elected by all members of the organization** for a term of
  **two years**. A single election fills all three Admin seats at once; Admins
  may stand again and be re-elected. The full election procedure — who may vote
  and stand, how votes are cast and counted, and what happens in edge cases — is
  described in *Electing the Admins* below.
- **Between elections**, the current Admins may fill a vacancy or remove an
  Admin who can no longer serve (or who must be removed for cause) by a
  **majority of the current Admins**. Such an interim appointment lasts only
  until the next regular election.
- Appointments, elections, and removals are recorded by updating the Admin list
  on the organization profile.

### Electing the Admins

The organization is large — several hundred members drawn from many different
institutions — and it will keep growing. An election method that works for a
handful of people does not automatically work at this scale: with many voters
organized into institutional groups, a simple "vote for three, the top three
win" ballot would let a single large institution or coalition capture **all
three** Admin seats and leave a large minority with no representation at all.
The procedure below is designed specifically to avoid that outcome, to keep the
ballot secret, and to remain legitimate as the organization grows.

**When elections happen.** A regular election is held every **two years**, in
the same calendar month as the previous regular election, and it fills all
three Admin seats simultaneously. The outgoing Admins remain in office until the
newly elected Admins have been recorded on the organization profile and have
been granted their access, so that the organization is never left without
Admins during the handover.

**Who may vote (the electorate).** Every member of the organization on a fixed
**cut-off date** — announced together with the call for the election, and set a
few weeks before voting opens — is eligible to vote. Using a cut-off date fixes
the electorate in advance and prevents last-minute additions from being made in
order to influence the result. Each eligible member has exactly one vote.

**Who may stand (candidates).** Any member may stand for election, including the
current Admins. Candidates nominate themselves during a **nomination period**
that opens with the call for the election and closes before voting begins.
Because every Admin must use their real name and secure their account with 2FA
(see Section 3), the same requirements apply to anyone standing for the role.

**How votes are cast and counted: the Single Transferable Vote (STV).** The
election uses the **Single Transferable Vote**, a ranked, proportional method.
Instead of picking a fixed number of candidates, each voter **ranks** the
candidates in order of preference: `1` for their most preferred candidate, `2`
for the next, and so on. A voter may rank as many or as few candidates as they
wish; unranked candidates simply receive no preference from that voter.

The count then proceeds in rounds:

1. A **quota** is calculated — the minimum number of votes a candidate needs in
   order to be guaranteed one of the three seats. (Concretely this is the
   *Droop quota*: the total number of valid votes divided by four — that is,
   *seats + 1* — and then rounded down and increased by one. The exact formula
   does not need to be understood by voters; the counting tool applies it.)
2. Every ballot is first counted for its **first preference**. Any candidate who
   reaches the quota is **elected**.
3. If an elected candidate received **more** votes than the quota, those
   *surplus* votes are not wasted: the surplus is transferred, proportionally,
   to the **next preference** marked on those ballots.
4. If no remaining candidate reaches the quota, the candidate with the **fewest**
   votes is **eliminated**, and each of their ballots is transferred to its next
   still-available preference.
5. Steps 3 and 4 repeat until three candidates have reached the quota and are
   elected.

The effect of transferring both surplus and eliminated votes is that almost
every ballot ends up helping to elect *someone*, and the three winners
collectively reflect the range of preferences in the organization. In practical
terms this means a cohesive minority of roughly a third of the voters can secure
**one** of the three seats, rather than being shut out entirely — which is
exactly the property a large, institutionally diverse organization needs.

**The voting tool.** The election is run with **[OpaVote](https://www.opavote.com)**,
an established online service purpose-built for STV and other ranked elections.
OpaVote is used because it (a) implements STV correctly, so the count is not
done by hand, (b) provides a **secret ballot**, so no one can see how an
individual voted, and (c) publishes a full, reproducible record of the count
that anyone can audit. Each eligible member receives a single personal voting
link. Note that OpaVote's guarantee rests on trusting the service and the
published ballots rather than on cryptographic proof; for an organization of
named professionals in a reputational field this trust model is considered
acceptable, and it is the price of getting a proportional method that resists
bloc capture.

**Quorum.** For the result to be valid, a minimum number of eligible members
must cast a valid ballot. Rather than a fixed percentage — which becomes
impossible to reach as the organization grows — the quorum **scales with the
size of the electorate**: at least the **square root of the number of eligible
members** (rounded up) must vote. For today's roughly 350 members this is about
**19** voters; if the organization grows to a thousand members it rises only to
about **32**. This keeps the bar high enough to give the result legitimacy, yet
low enough that it stays realistically reachable at any size. If the quorum is
**not** met, the election is void, the outgoing Admins remain in office, and a
new election is called within a reasonable period.

**Too few candidates.** If exactly three eligible candidates stand, they are
elected unopposed. If **fewer than three** stand, those who stood are elected
and the remaining seat(s) are filled as interim vacancies by the mechanism for
between-election appointments described above, until candidates can be found.

**Ties.** If two candidates are tied at the point where one of them must be
elected or eliminated, the tie is resolved by OpaVote's standard tie-breaking
rule (which looks back at earlier counting rounds); if a tie still cannot be
broken, it is decided **by lot**.

**Administration and recording.** The election is organized by the outgoing
Admins, who set up the ballot in OpaVote, announce the call, cut-off date, and
nomination and voting periods, and publish the result. Because the outgoing
Admins may themselves be candidates, the actual counting is performed by
OpaVote rather than by them, and they may delegate the administrative work to a
member who is **not** standing. Once the result is final, the Admin list on the
organization profile is updated accordingly (see Section 1).

---

## 3. Rules for Admins

Every Admin:

- Is appointed and removed as described in Section 2.
- Must secure their GitHub account with **two-factor authentication (2FA)**.
  Organization-wide 2FA enforcement should be enabled in the organization
  settings.
- Uses their **real name** on their GitHub account.
- Is responsible for the tasks reserved to Admins in this document (see
  *Scope and limits of Admin authority* below).
- Acts as a point of contact for organizational (non-technical) questions and
  for Code of Conduct concerns.

### Scope and limits of Admin authority

Admin authority is limited to **organizational** matters. Concretely, an Admin
may only:

- create repositories,
- appoint and remove Maintainers,
- archive repositories, and
- keep the organization profile and these governance rules up to date.

**Appointing or removing a Maintainer and archiving a repository each require a
majority of the Admins** (a majority means at least two of the three Admins).
Archiving effectively ends a project and is too consequential for one Admin to
decide alone. Creating a repository and routine profile updates may be done by a
single Admin.

Admins have **no authority over the contents of a repository**. What goes into
a repository — its code, documentation, branching details, releases, and which
issues or pull requests are accepted — is the sole responsibility of that
repository's Maintainers. Admins do not set rules for individual repositories;
the only rules they establish are the organization-wide governance in this
document (changed as described in Section 8).

Admin rights should be used sparingly. Day-to-day work on a repository is the
responsibility of its Maintainers, not the Admins.

---

## 4. Creating Repositories

- New repositories are created **only by Admins**.
- A repository is created when there is a clear **relevance to the
  infrastructure** of the initiative (see Section 5).
- Members who want a new repository request it from an Admin, stating its
  purpose and proposing at least one Maintainer.

---

## 5. Repository Requirements

### 5.1 Code of Conduct

Every repository is covered by the organization's Code of Conduct, the
[Berlin Code of Conduct](https://berlincodeofconduct.org/en). A `CODE_OF_CONDUCT`
file (or a link to it) must be present or inherited from the `.github`
repository.

### 5.2 Relevance and Type

A repository is created only if it is relevant to the infrastructure of the
initiative. To keep the organization navigable, each repository should clearly
belong to one of the following types (extend this list as needed):

- **Software** – source code of a tool or service. Such repositories
  additionally require:
  - a documented **branching** model (e.g. a protected default branch),
  - **releases** with version tags and a changelog,
  - **installation instructions**.
- **KDS modules** – core data set (Kerndatensatz) modules and their
  specifications.
- **Process models** – descriptions of organizational or technical processes.
- **Architecture** – architecture documentation and decisions.
- **Distributions** – bundled deliverables, either:
  - **software products**, or
  - **documents**.
- **Requirements management** – collection and tracking of requirements.

### 5.3 Maintainer

Every repository has at least one **Maintainer** (see Section 7). A repository
without an active Maintainer is a candidate for archiving.

### 5.4 README

Every repository has a `README` that explains:

- **Content** – what the repository contains.
- **Function** – what it is for, who it is aimed at, and how to get started
  (or where to find installation instructions for software repositories).

---

## 6. Members (Users)

- All members use their **real name** on their GitHub account so that
  contributions and discussions are attributable.
- Members are added to the organization by Admins, normally on request and with
  a stated purpose.
- All members must abide by the Code of Conduct.

---

## 7. Maintainers

- Maintainers are **appointed and removed by a majority of the Admins**. No
  single Admin can appoint or remove a Maintainer on their own. This applies to
  every Maintainer appointment, including replacing an unresponsive Maintainer
  and appointing an Admin as Maintainer (see below).
- By accepting the role, a Maintainer commits to being **reachable** for
  questions, issues, and pull requests concerning their repository.
- **Response time:** a Maintainer responds to issues and pull requests within
  **four weeks**. "Respond" means acknowledging and giving a next step, not
  necessarily resolving the matter.
- A repository may have more than one Maintainer; this is encouraged to share
  the load and to keep response times realistic.
- If a Maintainer is no longer reachable or repeatedly misses the response time,
  the Admins may appoint a replacement or archive the repository.
- The same person can be Maintainer of a repository and Admin of the
  organization at the same time. The two are distinct **roles, not persons**:
  authority over a repository's contents comes only from the Maintainer role,
  and being an Admin confers no additional say over those contents. Because
  every Maintainer appointment requires a majority of the Admins, an Admin
  cannot grant themselves this content authority unilaterally.

---

## 8. Changing These Rules

These rules can be changed by a **majority of the Admins**. Changes are made via
a pull request to this document so that the history of decisions is visible. The majority is expressed by at least two positive reviews of the pull request.

