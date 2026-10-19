# Review fixes, October 2026

This log records every change made on the branch `fix/review-oct-2026` to fix the review of the DemandInn site (landing page and Hotel Aurora demo). One commit per numbered item, so any item can be undone on its own.

## How to go back

| I want to… | Command |
| --- | --- |
| See the site exactly as it was before any of these fixes | `git checkout pre-review-fixes` |
| See the site as it was at the end of group N | `git checkout fixes-group-N` (for example `git checkout fixes-group-4`) |
| Undo one item and keep everything else | `git revert <hash>` with the hash from the commit index at the bottom of this file |
| Return to the latest work after looking at an older state | `git checkout fix/review-oct-2026` |

Notes:

- `git checkout <tag>` only lets you look at an older state. It does not change the branch or the live site. To publish an older state, open a pull request from it or revert the commits you don't want.
- Most items change `index.html`, the single file that holds the whole site. If a later item edited the same lines, `git revert` of an earlier item can stop with a conflict. In that case, either revert the later items first, or go back to a group tag, which never conflicts.
- A local copy of the original site is also saved outside the repo in `~/Desktop/Claude/DemandInn-backup-2026-10-19/` (the `index.html` of commit `d6aeb83` and the page the live site served on 19 Oct 2026; the two are byte-for-byte identical).

## Decisions from the team (19 Oct 2026)

| Open question | Decision | Effect on the site |
| --- | --- | --- |
| 0.1 Target hotel size | Keep 20–60 rooms | No change. The demo hotel stays at 28 rooms. |
| 0.2 Scope | Keep all services (breakfast, lunch, dinner, bar, team) | No change to the hero, the pilot section or the FAQ. |
| 0.3 Slogan | Keep "Tomorrow's covers, forecasted today" | Used everywhere through `BRAND_LINE` (see 0.3). |
| 0.10 Daily timing | Keep 18:00 | No change to the "A day at Hotel Aurora" timeline. |
| Contact email | A placeholder for now: `hello@demandinn.example` | **Waiting:** replace `CONTACT_EMAIL` with the real address before launch. The `.example` domain can never receive mail, so nothing is sent to a stranger by mistake. |
| Pilot form endpoint | No endpoint yet, use the `mailto:` fallback | `PILOT_FORM_ENDPOINT` is empty. The form opens the visitor's mail app addressed to `CONTACT_EMAIL`. **Until the real email is set, pilot requests go nowhere.** |
| "Who we are" sentence | Drafted by Claude, to confirm | **Waiting:** check the wording of `TEAM_LINE` (see 8.4). |

## Items

### Group 0. Align the site with the team's agreed logic

#### 0.1 Target hotel size: no change
- Decision: keep 20–60 rooms. Nothing to commit. The pilot section still says "independent hotels with 20 to 60 rooms" and Hotel Aurora still has 28 rooms.

#### 0.2 Scope: no change
- Decision: keep breakfast, lunch, dinner, bar and the Team screen. Nothing to commit.

#### 0.9 Team screen: kept
- The Team screen stays in the demo. Its numbers are fixed in 4.6, 5.4 and 7.6.

#### 0.10 Daily timing: no change
- Decision: keep 18:00 (the deck's "ready by 9 pm" is not used). Nothing to commit.
