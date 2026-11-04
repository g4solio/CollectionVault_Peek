# Issue tracker: GitHub

Issues and specs live in GitHub Issues, worked with the `gh` CLI from inside a clone.

- Create: `gh issue create --title "..." --body "..."`, with a heredoc for multi-line bodies.
- Read: `gh issue view <n> --json number,title,body,labels,comments`.
- Sub-issues: `gh issue create --parent <parent> ...`, or `gh issue edit <parent> --add-sub-issue <child>`.
- Blocking: GitHub's native issue dependencies. An issue is unblocked when every blocker is closed.
- Claim: `gh issue edit <n> --add-assignee @me`, the session's first write.
- Close: `gh issue comment <n> --body "<what was done and where>"`, then `gh issue close <n>`.
- Labels: `triage-labels.md`.

A larger piece of work gets a map issue: notes, the decisions so far, and the fog (what is still unknown), with child issues as the tickets. The next ticket to take is the first open child with no open blocker and no assignee.
