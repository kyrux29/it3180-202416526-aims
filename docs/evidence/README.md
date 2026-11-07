**Command evidence**

These files contain outputs captured while doing the exercises. Each
record includes the actual command, working directory, UTC start time
and exit code. A failing result is expected for bug reproduction,
conflict exercises and rejected direct pushes.

The rebase/reset/reflog practice branches remain local and are not part
of the submitted application snapshots. The reset exercise uses only a
disposable demo file.

The final evidence set also includes the Lab 04 release and tag audits,
Lab 05 regression/backport checks, and the CI failure demonstration.
`ci-demo-merge-blocked.txt` records the rejected merge attempt; the
deliberately broken PR was closed unmerged.

`lab05-audit-pycache-stale.txt` preserves an unexpected cache-related
audit failure. The per-version audit files record the successful reruns
using distinct Python cache directories. An SSH greeting with exit 1
is expected: GitHub authenticates Git access but does not offer a shell.

`final-pr-history.txt` is the snapshot immediately before the final
documentation PR, so it does not include that PR itself. Full links and
the mapping to each lab are in [submission.md](../submission.md).
