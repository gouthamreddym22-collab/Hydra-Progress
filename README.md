# HYDRA Progress Tracker

This directory holds the progress tracker for HYDRA.

## Local viewing

Open `tracker.html` in any browser — it works as a local file with no server required.

## GitHub Pages hosting (optional)

1. Initialize this directory as a git repo: `git init && git add . && git commit -m "initial tracker"`
2. Create a GitHub repo (e.g., via `gh repo create hydra-progress --public`)
3. Push: `git remote add origin <url> && git push -u origin main`
4. Enable Pages: `gh api repos/<owner>/<repo>/pages -X POST -f source.branch=main -f source.path=/`
5. Tracker will be live at `https://<owner>.github.io/hydra-progress/`

## Other hosting

Any static file host works. The tracker is self-contained — no build step, no external dependencies, no JS bundler.

## Updating

The DATA block near the top of `tracker.html`'s `<script>` tag is the source of truth for what renders. Edit:

- `generated_at` — today's date.
- `source` — short attribution explaining the snapshot.
- `overall_percent` — weighted average across modules.
- Per-module `percent` + `submodules[].percent` + `issues[]` + `confidence`.

The `/hydra-handoff` slash command updates this file at session close. The `/hydra-test` slash command writes a module's `confidence` field after a test pass.
