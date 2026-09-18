# WORKFLOW.md

## 1. What did the rejected push error message tell you, and why did it happen?
Git said the remote had commits I didn't have locally and refused to push. This happened because I didn't fetch before pushing, so my branch was behind the other clone's already-pushed commit.

## 2. What's the actual difference between how you resolved Task 3 (merge) vs Task 4 (rebase)?
The merge created a new commit joining both histories, with my changes as `HEAD` and the incoming side labeled `origin/...`. The rebase instead replayed my commit on top of the remote's history (no new commit, briefly detached HEAD), so the conflict markers were flipped — `HEAD` was the remote's version this time.

## 3. What one habit would have avoided both rejected pushes in this lab?
Running `git fetch` before starting work and before pushing would have caught the divergence early. Both rejections happened simply because a clone pushed without first checking if the remote had moved.

## 4. Which approach - merge or rebase - would you default to on a shared team branch, and why?
I'd default to merge on a shared branch because it never rewrites commits others may have already pulled. Rebase rewrites history, which is only safe for commits nobody else has seen yet.
