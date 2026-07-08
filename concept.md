# Feedback

* Kosten?
* Module aktivieren - was war damit gemeint?
* Scope was Admins für Regeln aufstellen dürfen
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

- The organization has three admins.
- The lower bound avoids a single point of failure (e.g. losing access if one person is unavailable).
- The upper bound keeps accountability clear and, more importantly, limits the **attack surface**: an Admin can change repository settings, branch protection, and access rights, and can therefore compromise *any* software release in the organization. Every additional Admin is another account that, if taken over, puts every release at risk. Keeping the number of Admins small (and 2FA-protected, see Section 3) is a deliberate security measure.
- Admins are **elected by all members of the organization** for a term of
  **two years**. An election is held every two years; Admins may stand again
  and be re-elected.
- An election will replace all three Admins.
- **Between elections**, the current Admins may fill a vacancy or remove an
  Admin who can no longer serve (or who must be removed for cause) by a
  **majority of the current Admins**. Such an interim appointment lasts only
  until the next regular election.
- Appointments, elections, and removals are recorded by updating the Admin list
  on the organization profile.

---

## 3. Rules for Admins

Every Admin:

- Is appointed and removed as described in Section 2.
- Must secure their GitHub account with **two-factor authentication (2FA)**.
  Organization-wide 2FA enforcement should be enabled in the organization
  settings.
- Uses their **real name** on their GitHub account.
- Is responsible for the tasks reserved to Admins in this document: creating
  repositories, appointing and removing Maintainers, and keeping the
  organization profile and these rules up to date.
- Acts as a point of contact for organizational (non-technical) questions and
  for Code of Conduct concerns.

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

- Maintainers are **appointed and removed by the Admins**.
- By accepting the role, a Maintainer commits to being **reachable** for
  questions, issues, and pull requests concerning their repository.
- **Response time:** a Maintainer responds to issues and pull requests within
  **four weeks**. "Respond" means acknowledging and giving a next step, not
  necessarily resolving the matter.
- A repository may have more than one Maintainer; this is encouraged to share
  the load and to keep response times realistic.
- If a Maintainer is no longer reachable or repeatedly misses the response time,
  the Admins may appoint a replacement or archive the repository.
- The same person can be Maintainer of a repository and Admin of the organization at the same time.

---

## 8. Changing These Rules

These rules can be changed by a **majority of the Admins**. Changes are made via
a pull request to this document so that the history of decisions is visible. The majority is expressed by at least two positive reviews of the pull request.

