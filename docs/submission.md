# IT3180 lab submission

Student: **Vũ Trọng Quốc Khánh**, student ID **202416526**, GitHub **kyrux29**.

Repository: [it3180-202416526-aims](https://github.com/kyrux29/it3180-202416526-aims).
The five `release/labXX` branches are the submitted snapshots. Later
development and the combined evidence index are on `master`.

| Lab | Submission branch | Tag / commit | Work |
| --- | --- | --- | --- |
| 01 | [release/lab01](https://github.com/kyrux29/it3180-202416526-aims/tree/release/lab01) | v0.1.0 / `6b39202` | Bootstrap, ignore rules, restore/staging/amend exercises, package refactor; [answers](answers-lab01.md) |
| 02 | [release/lab02](https://github.com/kyrux29/it3180-202416526-aims/tree/release/lab02) | v0.2.0 / `701a063` | Protected master, two local clones, PR template, cart printing, title search, UML, three merge methods; [answers](answers-lab02.md) |
| 03 | [release/lab03](https://github.com/kyrux29/it3180-202416526-aims/tree/release/lab03) | v0.3.0 / `2d8c983` | Issue, test before fix, feature-targeted bugfix, conflicts, reset/reflog, revert; [answers](answers-lab03.md) |
| 04 | [release/lab04](https://github.com/kyrux29/it3180-202416526-aims/tree/release/lab04) | v1.0.0 baseline `4855267`; current v1.0.1 `dad5385` | Annotated tags, version banner, CHANGELOG, protection, GitHub Release and audit; [answers](answers-lab04.md) |
| 05 | [release/lab05](https://github.com/kyrux29/it3180-202416526-aims/tree/release/lab05) | v1.1.0 / `c424d6b` | Category search, 1.0.x hotfix, two traced cherry-picks, three-line audit; [answers](answers-lab05.md) |

**Lab 01: environment and refactor**

The initial and refactored programs both total `63.89 $`. [PR #1](https://github.com/kyrux29/it3180-202416526-aims/pull/1)
moved Cart and DVD into `aims` and updated main.py. Generated Python
caches are ignored and untracked. The lab01 branch was created from the
merged master checkpoint; master has advanced since then.

Initial pushes used authenticated HTTPS. SSH was also configured and
verified during the final audit using an Ed25519 deploy key restricted
to this repository, rather than an account-wide SSH key. The local alias
is `github-it3180-202416526`; origin now uses it. GitHub's successful SSH
greeting exits with code 1 because it offers no shell. Private key
material stays outside the repository.

**Lab 02: PRs and merge methods**

Six PRs had merged at the lab02 checkpoint. [PR #4](https://github.com/kyrux29/it3180-202416526-aims/pull/4)
used a merge commit, [PR #5](https://github.com/kyrux29/it3180-202416526-aims/pull/5)
used squash, and [PR #6](https://github.com/kyrux29/it3180-202416526-aims/pull/6)
used rebase and merge. See [use-case.svg](use-case.svg) for the UML
diagram. A real attempt to push a new commit directly to master was
rejected with GH006.

This uses the slides' solo setup: required approvals are zero, with
stale review dismissal and protection applying to admins. The cart-print
PR records a self-check followed by an empty-cart fix. There is **no
peer Changes requested → Approved review**: one account cannot approve
its own PR. The second clone is another working copy of the same
student, not a second reviewer.

**Lab 03: bugs, conflicts and undo**

- [Issue #7](https://github.com/kyrux29/it3180-202416526-aims/issues/7)
  is closed by [PR #8](https://github.com/kyrux29/it3180-202416526-aims/pull/8).
  Test `16bfaf9` precedes fix `90850ff`; the cart rejects DVD 21.
- [PR #10](https://github.com/kyrux29/it3180-202416526-aims/pull/10)
  targets feature/discount; [PR #9](https://github.com/kyrux29/it3180-202416526-aims/pull/9)
  then integrates the corrected feature into master.
- Concurrent message changes in PRs #11 and #12 produced a real merge
  conflict. A separate unpublished practice branch produced a rebase
  conflict. Both were resolved and captured.
- [PR #13](https://github.com/kyrux29/it3180-202416526-aims/pull/13)
  reverts merge `7a1367c` with `git revert -m 1`, preserving shared history.
- Soft, mixed and hard resets affected a disposable local demo file.
  Reflog recovery created local rescue/undo-practice at `da92fd0`.
  Practice branches were not pushed into the submission.

The release/lab03 snapshot passes four tests.

**Lab 04: baseline and later development**

Six annotated tags are pushed: v0.1.0, v0.2.0, v0.3.0, v1.0.0, v1.0.1
and v1.1.0. Published tags were not moved. Original v1.0.0 passes four
tests and has no sorting. Sorting was added to master after that baseline
through [PR #15](https://github.com/kyrux29/it3180-202416526-aims/pull/15).
The maintenance update advances release/lab04 to v1.0.1; v1.0.0 still
identifies the original commit. Neither maintenance version has sorting.

The release/* rule requires PRs, includes admins, and blocks force
pushes and deletion. A real direct release push was rejected. GitHub
Releases for [1.0.0](https://github.com/kyrux29/it3180-202416526-aims/releases/tag/v1.0.0),
[1.0.1](https://github.com/kyrux29/it3180-202416526-aims/releases/tag/v1.0.1)
and [1.1.0](https://github.com/kyrux29/it3180-202416526-aims/releases/tag/v1.1.0)
include ZIP archives made from their exact tags.

**Lab 05: one fix across three lines**

On v1.0.0, searching for `lion` in `The Lion King` returns zero matches.
[PR #19](https://github.com/kyrux29/it3180-202416526-aims/pull/19)
starts from release/lab04, adds a failing regression test, fixes the
search, and releases 1.0.1. The behavior fix is separate from the version
bump. [PR #20](https://github.com/kyrux29/it3180-202416526-aims/pull/20)
and [PR #21](https://github.com/kyrux29/it3180-202416526-aims/pull/21)
carry only that fix with cherry-pick -x to master and release/lab05.
[Issue #18](https://github.com/kyrux29/it3180-202416526-aims/issues/18) is closed.

| Line | Version | Lowercase search matches | Tests | Sorting |
| --- | --- | --- | --- | --- |
| release/lab04 | 1.0.1 | 1 | 5 pass | Absent |
| release/lab05 | 1.1.0 | 1 | 8 pass | Present |
| master | 1.1.0 | 1 | 8 pass | Present |

Source fix: `67f59dcd9e668d5384694a7182fc3a48ac312575`.
Destination commits: `41d1df4` on master and `68bf454` on release/lab05.
The 1.0.0 → 1.0.1 diff contains exactly four files: CHANGELOG, the version
file, search.py and test_search.py. Version 1.1.0 was tagged only after
its backport passed verification.

Rapid tag switching exposed a stale timestamp-based Python bytecode
cache: one import reported 1.0.1 while the file said 1.1.0. The failed
audit is retained as lab05-audit-pycache-stale.txt. Audits were repeated
with separate `-X pycache_prefix` directories for each ref; all three
reported the expected version and one match. Generated local bytecode
was then removed before running the main demo.

**CI extension**

[PR #22](https://github.com/kyrux29/it3180-202416526-aims/pull/22)
adds GitHub Actions on master. The test job runs eight tests with Python
3.12. Master requires that check and an up-to-date branch. The first
successful run is [42367330301](https://github.com/kyrux29/it3180-202416526-aims/actions/runs/42367330301).

[PR #23](https://github.com/kyrux29/it3180-202416526-aims/pull/23)
deliberately made total_cost return zero. Its [CI run](https://github.com/kyrux29/it3180-202416526-aims/actions/runs/42367455946)
failed and an actual merge attempt was rejected by branch policy. It
was closed unmerged and its branch deleted. Master keeps the correct
code. CI was added after the release snapshots, preserving those tags.

**Reproduce the current checks**

```bash
git fetch origin --prune --tags
git switch master
git pull --ff-only
python3 -m unittest discover -s tests -v
python3 main.py
git log --oneline --graph --all
git diff --stat v1.0.0 v1.0.1
git log --all --oneline --grep='cherry picked from'
git cherry master release/lab04
```

For older versions, use separate worktrees or a distinct Python cache
prefix for each ref. Raw outputs, including expected failures, are
indexed in [evidence/README.md](evidence/README.md). Their UTC times are
actual execution times. Submit the repository link on LMS and select
the requested release branch when presenting each lab.
