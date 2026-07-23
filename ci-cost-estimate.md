# CI Cost Estimate

**Purpose.** Section 9 of [`concept.md`](concept.md) argues that the decisive
question for digital sovereignty is not where we are hosted but *how expensive
it would be to leave*, and it names CI as the dominant permanent cost of any
move away from GitHub. This document puts numbers behind that claim.

**Measured on:** 2026-07-23
**Measurement window:** 2025-07-23 – 2026-07-23 (12 months)
**Scope:** the GitHub organizations
[medizininformatik-initiative](https://github.com/medizininformatik-initiative)
and [datasharingframework](https://github.com/datasharingframework), plus the
individual repositories [samply/blaze](https://github.com/samply/blaze) and
[samply/blazectl](https://github.com/samply/blazectl).

---

## 1. Headline

| | |
|---|---|
| Repositories in scope | 133 active, non-fork (123 MII + 8 DSF + 2 samply) |
| …of which run CI at all | **68** |
| Workflow runs per year | ~42.800 |
| **Billable CI minutes per year** | **≈ 2,42 million** |
| Equivalent | 40.300 runner-hours = **4,6 machine-years** |
| Cost today | **€0** — public repositories get unlimited free GitHub-hosted runners |
| Same load at GitHub list price ($0,008/min, standard 2-vCPU Ubuntu) | **≈ $19.400/yr** |

Runners are almost exclusively GitHub-hosted standard 2-vCPU Ubuntu
(`ubuntu-24.04` / `ubuntu-latest`). No macOS or Windows minutes were found —
which matters, because those are billed at 10× and 2×. One notable exception:
a small number of `samply/blaze` jobs already run on **Ubicloud**, i.e. some
CI capacity is *already* being bought from a third party.

---

## 2. Where the minutes go

### By organization

| Organization | Runs/yr | Minutes/yr | Share |
|---|---:|---:|---:|
| samply (blaze + blazectl) | 10.249 | **1.609.500** | 66,5 % |
| medizininformatik-initiative | 30.900 | **793.000** | 32,8 % |
| datasharingframework | 1.500 | **17.200** | 0,7 % |
| **Total** | **~42.800** | **2.419.700** | 100 % |

### By repository (top 20 of 68)

| Repository | Runs/yr | Ø min/run | Minutes/yr |
|---|---:|---:|---:|
| samply/blaze | 9.062 | 177 | **1.601.400** |
| medizininformatik-initiative/fts-next | 7.980 | 39 | 315.200 |
| medizininformatik-initiative/torch | 6.789 | 37 | 251.800 |
| medizininformatik-initiative/fhir-ontology-generator | 1.042 | 84 | 87.200 |
| medizininformatik-initiative/aether | 3.809 | 10 | 37.300 |
| medizininformatik-initiative/dataportal-backend | 2.611 | 14 | 37.300 |
| medizininformatik-initiative/flare | 555 | 20 | 11.300 |
| datasharingframework/dsf | 825 | 11 | 9.300 |
| samply/blazectl | 1.187 | 7 | 8.100 |
| datasharingframework/datasharingframework.github.io | 285 | 20 | 5.700 |
| medizininformatik-initiative/cctb | 1.055 | 5 | 5.400 |
| medizininformatik-initiative/kerndatensatzmodul-GenetischeTests | 86 | 57 | 4.900 |
| medizininformatik-initiative/fhir-data-evaluator | 354 | 13 | 4.500 |
| medizininformatik-initiative/kds-fdpg-layer | 62 | 62 | 3.800 |
| medizininformatik-initiative/mii-testdata | 106 | 32 | 3.400 |
| medizininformatik-initiative/fdpg-api | 690 | 5 | 3.200 |
| medizininformatik-initiative/kerndatensatzmodul-onkologie | 319 | 10 | 3.000 |
| medizininformatik-initiative/mii-process-feasibility | 375 | 7 | 2.800 |
| medizininformatik-initiative/fdpg-webapp | 429 | 6 | 2.500 |
| medizininformatik-initiative/kerndatensatzmodul-proms | 390 | 6 | 2.200 |
| *remaining 48 repositories combined* | ~13.000 | – | 19.300 |

### By workflow — the four heaviest repositories

Per-run cost varies by two orders of magnitude *within* a single repository, so
the workflow view is the one that explains the bill:

| Repository / workflow | Runs/yr | Ø min/run | Minutes/yr |
|---|---:|---:|---:|
| **blaze / `Build`** | 4.063 | **393** | **1.596.000** |
| blaze / `Docs` | 4.071 | 1,1 | 4.600 |
| blaze / everything else | ~1.100 | 1–9 | 1.200 |
| **fts-next / `Build`** | 2.731 | 101 | 274.500 |
| fts-next / `Analyze` | 2.456 | 9,6 | 23.600 |
| fts-next / `Pages` | 2.412 | 6,0 | 14.500 |
| **torch / `Build`** | 3.277 | 76 | 247.400 |
| torch / everything else | ~3.500 | 1–3 | 4.400 |
| **fhir-ontology-generator / test workflows** | 881 | 34–137 | 87.000 |

**One workflow — `Build` in `samply/blaze` — is 66 % of the entire estimate.**
It fans out into a matrix of ~114 jobs per run at roughly 393 billable minutes
in total. Any statement about migration cost is really a statement about this
one repository plus the two `Build` workflows in `fts-next` and `torch`; those
three together are **88 %** of all CI minutes in scope.

---

## 3. What a move would cost

### 3.1 Capacity needed

40.300 job-hours per year is **4,6 continuously busy machines** on annual
average. CI load is not uniform, though: it concentrates in working hours, so
spread over roughly 2.500 genuinely busy hours a year the requirement is
**~16 concurrently busy 2-vCPU runners**. Peak demand is far higher — blaze's
`Build` alone asks for ~114 parallel jobs — so a smaller fleet does not reduce
the annual minute count, it converts money into queue time.

### 3.2 Options

| Option | Infrastructure/yr | Operations | Realistic total/yr |
|---|---|---|---|
| **GitHub, public repos (today)** | €0 | – | **€0** |
| **Managed cheap runners** (Ubicloud, Blacksmith, BuildJet; ~$0,0008–0,002/min) — note this is *not* a sovereignty gain, it still requires GitHub Actions | €2.000–5.000 | negligible | **€2.000–5.000** |
| **Self-hosted runners, fixed fleet** — ~16 slots, e.g. 4 dedicated 8-vCPU servers at a German provider | €3.000–5.000 | 0,2–0,4 FTE | **€20.000–40.000** |
| **Self-hosted runners, autoscaled** (Actions Runner Controller / Woodpecker on Kubernetes) | €1.000–2.000 | 0,3–0,5 FTE, higher skill requirement | **€25.000–45.000** |
| **Self-hosted forge as well** (Forgejo/GitLab incl. HA, backups, spam defence, identity management) | +€1.000–2.000 | +0,2–0,3 FTE | **€40.000–70.000** |

FTE cost assumed at ~€85.000/yr fully loaded (≈ TV-L E13). **Staff, not
hardware, is the dominant recurring cost in every self-hosted variant.**

Codeberg does not change this picture: hosting itself is free (funded by
membership fees and donations), but Codeberg provides no free general-purpose
CI runners, so the runner rows of the table apply unchanged.

### 3.3 One-off migration cost

| Item | Estimate |
|---|---|
| Rewriting CI workflows — 68 repositories with live CI, of which ~10 are non-trivial, at ~1 day average | 3–4 person-months ≈ **€30.000–60.000** |
| Migrating issues, PRs, releases (tooling exists, results imperfect) | 2–4 weeks |
| Reissuing signing identities, release-verification docs, all GitHub URLs | 1–2 weeks |
| Git history, branches, tags | negligible — git is distributed |

### 3.4 Summary for the concept

> Leaving GitHub costs roughly **€40.000 once** and **€25.000–50.000 every
> year** thereafter — and about two thirds of the recurring cost is one
> repository's test matrix.

This is why Section 9 concludes that we stay on GitHub while it works for us,
and why the lock-in rules in Section 9.5 target exactly the dominant item:
**portable build logic** moves the expensive part of a workflow out of the
platform-specific YAML and into the repository, where it survives a migration.

---

## 4. Method

1. **Repository inventory** — `gh repo list` per organization; archived
   repositories and forks excluded.
2. **Run counts** — `GET /repos/{owner}/{repo}/actions/runs?created=>=…`,
   reading `total_count` per repository and per workflow. Includes runs
   triggered from forks and by Dependabot/Renovate, since those consume
   minutes too.
3. **Minutes per run** — the billing endpoint
   (`/actions/runs/{id}/timing`) reports `total_ms: 0` for public
   repositories, because they are free. Minutes were therefore computed from
   the jobs endpoint (`/actions/runs/{id}/jobs?filter=latest`) as
   `ceil((completed_at − started_at) / 60 s)` **per job**, summed over all
   jobs of a run — which is how GitHub bills: per job, rounded up to the
   minute, matrix jobs counted individually.
4. **Sampling** — stratified by workflow, because per-run cost varies ~100×
   within a repository. 8 runs per workflow for the eight largest
   repositories; 30 runs for `blaze / Build`, which dominates the total; 4–10
   runs per repository for the long tail. Averages multiplied by the exact
   annual run count.
5. **Runner class** — taken from each job's `labels`, to catch macOS (10×) and
   Windows (2×) minutes. None were found.

## 5. Accuracy and caveats

- **`blaze / Build`:** 29 usable samples, mean 393 min, median 384, standard
  error ±19 min (**±5 %**). This is the best-measured figure and it carries
  two thirds of the total.
- **Other large workflows:** 8 samples each, roughly **±20–30 %**.
- **Long tail (48 repositories, 19.300 min/yr, 0,8 % of the total):** 4–10
  samples per repository, **±50 %** — irrelevant to the conclusion.
- Overall the total is good to roughly **±15 %**. An earlier, unstratified
  sample of only the most recent runs produced 1,6 M minutes instead of
  2,42 M; the difference is sampling bias, not a change in load, and it
  illustrates why the workflow-stratified method was necessary.
- Prices (GitHub $0,008/min; managed-runner and server prices; FTE rates) are
  list prices from general knowledge, **not** quotes. They must be re-checked
  before being used in a funding application.
- A future shared organization would host **more** repositories than these
  133, so these figures are a lower bound for the target state.
- The estimate reflects current CI practice. It is not a statement about
  necessity: blaze's matrix could presumably be trimmed, and doing so would
  move the migration cost more than any provider choice would.
