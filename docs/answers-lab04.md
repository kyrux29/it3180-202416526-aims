**Lab 04 — Releases and configuration audit**

**Why not merge a release branch back into master?**

A maintenance branch can have its own version and release notes. Merging
the entire branch could bring an old version number or release-specific
changes into development. In this course, fixes are carried across as
separate commits through PRs, rather than merging the whole release.

**How is this different from GitFlow?**

GitFlow normally uses develop for integration and main for published
releases, with release/hotfix merges between those lines. This exercise
integrates work on master and keeps release/labXX as submission and
maintenance lines. The two models have different merge policies.

**Why choose 1.0.0 instead of 0.4.0?**

The course chooses the first stable baseline at this point. SemVer uses
0.y.z during initial development; 1.0.0 marks the initial stable public
contract. Finishing the fourth lab does not itself impose this number;
it is a release decision made by the exercise.

**How do a tag and a release branch differ?**

A published tag identifies one exact version and must not be moved.
A release branch can advance through reviewed hotfixes. After patch
1.0.1, release/lab04 will move forward while tag v1.0.0 still identifies
the original release. Annotated tags also include a message and tagger.

**How can the baseline be checked?**

Run the tests at the tag, read `aims/__init__.py`, inspect CHANGELOG and
list the tracked files. The 1.0.0 baseline has four passing tests and no
cart sorting. Sorting is developed on master only after this release.
`git log A..B` shows commits reachable from B but not A. A worktree lets
the old version run alongside the development checkout without edits
to the original tag.
