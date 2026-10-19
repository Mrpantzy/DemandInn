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

#### 0.3 One slogan, from `BRAND_LINE`
- Files and functions: `index.html`: `BRAND_LINE` constant, `Hero`, `Footer`, `buildEmail`.
- Before: the hero heading and the morning email hard-coded the slogan. `BRAND_LINE` ended with a full stop, so the browser tab read "DemandInn: Tomorrow's covers, forecasted today." and the static `<title>` read the same without the stop.
- After: `BRAND_LINE = "Tomorrow's covers, forecasted today"` feeds the hero heading (the part after the comma stays in italics), the footer, the morning email header and the tab title, which now match the static `<title>` exactly. `og:title` and `twitter:title` are added in 2.3 with the same words. A comment next to the constant says to update the `<head>` too if the slogan changes, because crawlers do not run scripts.
- Undo: `git revert <hash of 0.3>`

#### 0.4 Value proposition as the meta description
- Files: `index.html`, `<meta name="description">` in the head.
- Before: "DemandInn forecasts hotel food and beverage demand from bookings, weather, events and past sales, then recommends what to buy and prepare."
- After (157 characters, the team's sentence shortened): "For small hotel restaurants: F&B forecasting that combines siloed operational data to recommend what to buy and prepare, reducing waste, shortages and costs." The same text is reused for `og:description` and `twitter:description` in 2.3.
- Undo: `git revert <hash of 0.4>`

#### 0.5 ROI calculator uses the deck's model
- Files and functions: `index.html`: new `PRICE_MONTH`, `ROI_DEFAULTS`, `roiModel()`; `RoiCalculator` rewritten with the same section layout and colours.
- Before: three sliders (monthly purchases EUR 18,000, 10% wasted, 20% reduction) showing "EUR 360 per month" against EUR 149.
- After: the deck's inputs, each a slider: rooms (28, the demo hotel), occupancy 75%, 1.6 guests per room, 85% breakfast uptake, EUR 4 food cost per cover, 12% of food wasted (typical range 5 to 15%), 30% waste reduction, 30 minutes of manager time a day at EUR 25 an hour. At the defaults it shows **EUR 6,064 a year: EUR 1,501 of food plus EUR 4,563 of time, against EUR 1,788 (EUR 149 × 12), about 3.4×**. The "assumptions you set, not results we have measured" wording is kept, with the formula spelled out.
- Undo: `git revert <hash of 0.5>`

#### 0.6 Rollout: automation only if the hotel chooses
- Files and functions: `index.html`: `Principles` ("AI recommends. Hotel teams decide.").
- Before: "Suggestions, never silent orders. You can accept, change or remove every line, and your reason stays with it."
- After: the same, plus "Later, and only if you choose, orders can be drafted automatically within limits you set." This matches the deck's fourth stage without dropping the principle.
- Undo: `git revert <hash of 0.6>`

#### 0.7 Competitor line
- Files and functions: `index.html`: `Principles` (intro under "How we think about it").
- Before: no intro line.
- After: "One platform at EUR 149 a month, where stacking separate tools for forecasting, inventory and staffing (such as Tenzo, MarketMan and Planday) costs a small hotel about EUR 400–550." Written with "EUR" like every other price on the site. No comparison table.
- Undo: `git revert <hash of 0.7>`
