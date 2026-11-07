**Lab 03 — Bugfixes, conflicts and undo**

**What is a merge base?**

It is a best common ancestor of the commits being merged. Git compares
each side with that ancestor. If both sides change the same area in
different ways, Git may need a person to resolve the conflict.

**Why keep a failing test before the fix?**

It shows the test catches the reported problem. For Issue #7, the test
accepted the first 20 DVDs but failed because adding DVD 21 returned
True. Commit 16bfaf9 adds the test; commit 90850ff changes `>` to `>=`.
PR #8 merges the fix and closes the issue. The test remains to catch a
regression later.

**Why did the discount bugfix target a feature branch?**

The unfinished discount code was on `feature/discount`. PR #10 fixed
that branch first. Total 100 with 20 percent off must be 80, and percent
values outside 0–100 must raise ValueError. After all four tests passed,
PR #9 integrated the feature into master.

**How was the conflict resolved?**

Two branches changed the same add_dvd message: PR #11 changed its
language, while PR #12 added the DVD title. Merging master into the
second branch produced a content conflict in aims/cart.py. The resolved
message kept both changes, conflict markers were removed, and four
tests passed before the branch was pushed.

A separate local rebase exercise also produced and resolved a conflict.
The practice branches were not pushed or merged into the application.

**Why use revert on master and release branches?**

Reset moves a branch pointer and can rewrite shared history. Revert adds
a new commit which reverses a previous change while retaining the old
commits. Here `git revert -m 1` reverses the merge of PR #12 relative to
its first parent. The earlier Vietnamese message remains; the DVD title
is removed from that message. The change goes through a new PR.

**What did the reset/reflog exercise show?**

- Soft reset removed the local demo commit but kept its file staged.
- Mixed reset left the new demo file untracked in the working tree.
- Hard reset removed that tracked demo file from the working tree.
- Reflog still showed the discarded commit. A local rescue branch at
  da92fd0 made the file accessible again.

These operations were limited to an unpublished practice branch. Reflog
can help recover commits; it is not a backup for arbitrary uncommitted
changes.
