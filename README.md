Personal webpage for Bihan Samarasinghe — Datacenter Engineer (Tailwind CDN quick-start)

Files:
- `index.html` — single-page personal site. Open directly in a browser.

How to use:
1. Open `index.html` in your browser (double-click or `xdg-open` on Linux).
2. Edit the file to update name, email, images, and project details.

Notes:
- This template uses the Tailwind CDN for quick iteration and doesn't require a build step.
- For production, consider a local Tailwind build to purge unused CSS and add asset optimization.

Suggested next steps I can do for you:
- Add a mobile-friendly nav with accessible toggling.
- Replace placeholder images with your photo and update contact email.
- Scaffold a small repo with Tailwind/PostCSS, or convert to a React/Vite app for components and routing.

Git troubleshooting: "src refspec main does not match any"
-----------------------------------------------------
If you see an error like:

	error: src refspec main does not match any
	error: failed to push some refs to 'https://github.com/yourname/yourrepo.git'

This usually means your local branch name doesn't match the branch you're trying to push (for example you are on `master` but ran `git push origin main`), or you don't have any commits on the branch yet.

Quick checks:

```bash
git rev-parse --abbrev-ref HEAD    # shows current branch
git status                         # shows uncommitted changes
git log --oneline -n 5            # view recent commits
git remote -v                      # check remote URL
```

Easy fixes (pick one):

1) Standardize on `main` (recommended):

```bash
git branch -m main                 # rename current branch to main
git fetch origin
git pull --rebase origin main || true
git push -u origin main            # push and set upstream
```

2) Push `master` to remote `main` once:

```bash
git push -u origin master:main     # push local master as remote main
# optionally rename local branch:
git branch -m main
```

3) If remote has commits, integrate before pushing:

```bash
git fetch origin
git pull --rebase origin/main      # rebase onto remote main
# resolve conflicts if any, then
git push
```

4) Make `main` your default for new repos:

```bash
git config --global init.defaultBranch main
```

Safe workflow to avoid surprises:

```bash
git fetch origin
git pull --rebase
git push
```

When rewriting history (rebase) and you need to force-push, prefer:

```bash
git push --force-with-lease
```

If you're unsure which branch to push to, paste the exact commands and output and this README's owner can provide the single command to fix your repo.
