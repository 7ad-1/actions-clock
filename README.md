# actions-clock

Public "clock" repository that fires scheduled workflow runs on the private
[`7ad-1/trading-bot`](https://github.com/7ad-1/trading-bot) repository.

**Why:** GitHub has a known bug (community discussion
[#201354](https://github.com/orgs/community/discussions/201354)) where
`schedule:` cron triggers are never registered for private repositories on
personal **free** accounts — `workflow_dispatch` works, cron never fires.
Public repositories' schedules work fine and have unlimited Actions
minutes, so this tiny public repo keeps the time and dispatches the private
bot repo on the same cadence.

**Cost:** $0 (public repo = unlimited minutes; each dispatch costs the
private repo ~1–2 of its 2,000 free monthly minutes, same as planned).

**Secret:** `CLOCK_PAT` — a GitHub PAT with `repo` + `workflow` scope,
used only to call `gh workflow run` on the private repo.

If GitHub fixes schedule-in-private-repo: delete this repo and restore
`on: schedule` in the bot's own workflows.
