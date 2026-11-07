**Lab 05 — Hotfixes across release lines**

**Release first or upstream first?**

Release first starts with the version affected users actually run. It
keeps the patch focused on that code, but the fix must then reach every
affected development and release line. Upstream first fixes development
first, reducing the chance of forgetting upstream; backporting may be
harder when the old code is different. Either approach needs tests on
the versions that receive the fix.

**Why separate the fix and the version bump?**

Only the behavior fix and its regression test should be cherry-picked.
The 1.0.x line moves to 1.0.1, while master and release/lab05 must keep
1.1.0. Picking the version bump as well would bring the wrong version
number into those lines.

**What does cherry-pick -x add?**

It records the source commit SHA in the new commit message. This lets
the same fix be traced across branches even though its destination
commits have different identities. `git cherry` can compare equivalent
patches, while `git tag --contains` only checks ancestry of the exact
source commit. Neither command replaces testing the behavior.

**How can a missed release/lab05 backport be found?**

Run the case-insensitive search check at v1.1.0 or the release branch:
searching for `lion` in `The Lion King` must return one item. A missing
backport returns zero. Check the branch history for its cherry-pick too;
finding the fix on master alone does not establish that the release has
it.

**Why wait before tagging 1.1.0?**

The release/lab05 branch is created before the hotfix so that the lab
practices maintaining an existing release line. Tag v1.1.0 is published
only after the backport and verification. If it had already been
published, the patch would need a new version such as 1.1.1 rather than
moving the old tag.

**Verification results**

The original 1.0.0 reproduces the case-sensitive search bug. Patched
1.0.1, 1.1.0 and master each find one item for `lion`; their suites pass
with 5, 8 and 8 tests respectively. The 1.0.0-to-1.0.1 diff contains only
search.py, test_search.py, the version file and CHANGELOG.

Source fix `67f59dcd9e668d5384694a7182fc3a48ac312575` is recorded by
two cherry-pick commits: `41d1df4` on master and `68bf454` on
release/lab05. PRs #19, #20 and #21 update the affected lines; Issue #18
is closed. The version bump to 1.0.1 stays on release/lab04.

GitHub Actions passes on the correct code. The deliberately broken
total_cost in PR #23 makes the test job fail and blocks merging; that
PR is closed without merging. See [the submission index](submission.md)
for links, raw evidence and cache isolation during tag audits.
