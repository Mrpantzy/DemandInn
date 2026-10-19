# Review fixes, October 2026

This log records every change made on the branch `fix/review-oct-2026` to fix the review of the DemandInn site (landing page and Hotel Aurora demo). One commit per numbered item, so any item can be undone on its own.

## How to go back

| I want to… | Command |
| --- | --- |
| See the site exactly as it was before any of these fixes | `git checkout pre-review-fixes` |
| See the site as it was at the end of group N | `git checkout fixes-group-N` (for example `git checkout fixes-group-4`) |
| Undo one item and keep everything else | `git revert <hash>` with the hash from the commit index below |
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

<!-- commit-index:start -->
## Commit index

Every commit on the branch, oldest first. Filled in at the end of each group, so the newest items may still be missing here until their group is tagged.

| Item | Commit | What | Undo |
| --- | --- | --- | --- |
| 0 | `320043f` | Start REVIEW_FIXES.md with how to go back and the team's decisions | `git revert 320043f` |
| 0.3 | `64c78c5` | Use BRAND_LINE for the slogan everywhere | `git revert 64c78c5` |
| 0.4 | `326f583` | Meta description uses the team's value proposition | `git revert 326f583` |
| 0.5 | `f2ae644` | ROI calculator uses the deck's model (EUR 6,064 a year, 3.4x at defaults) | `git revert f2ae644` |
| 0.6 | `f4bd0eb` | Principles: add the opt-in automation line | `git revert f4bd0eb` |
| 0.7 | `ae44869` | Add the competitor line under How we think about it | `git revert ae44869` |
| 0.8 | `21f757c` | Replace the pilot placeholder card with What hotels told us | `git revert 21f757c` |
| 1.1 | `f07c77a` | Footer: mailto contact link, remove placeholder lines | `git revert f07c77a` |
| 1.2 | `a7996e7` | FAQ GDPR answer: remove placeholder, phrase as the pilot plan | `git revert a7996e7` |
| 1.3 | `fe23320` | Demo privacy card: remove placeholder, phrase as the pilot plan | `git revert fe23320` |
| 1.4 | `63cbdf1` | Pilot form posts to PILOT_FORM_ENDPOINT or falls back to mailto | `git revert 63cbdf1` |
| 1.5 | `36becc3` | Header and hero link to Become a pilot | `git revert 36becc3` |
| 2.1 | `8f906c4` | html lang=en, charset utf-8, title and meta inside head | `git revert 8f906c4` |
| 2.2 | `0f7bdf2` | Inline SVG favicon: amber cloche on forest green | `git revert 0f7bdf2` |
| 2.3 | `cd47012` | Open Graph, Twitter card and canonical link | `git revert cd47012` |
| 2.4 | `72a7afb` | noscript message and a fallback when the CDN scripts fail | `git revert 72a7afb` |
| 2.5 | `61cf893` | Add the Vercel Web Analytics script | `git revert 61cf893` |
| 2.7 | `64b664a` | Darken amber chip text to pass 4.5:1 contrast | `git revert 64b664a` |
| 2.8 | `1ea7975` | Demo banner: changes reset when you reload | `git revert 1ea7975` |
| 3 | `2d3eb39` | Allow a fixed demo date from ?date=YYYY-MM-DD | `git revert 2d3eb39` |
| 4.1 | `cf54f22` | Who is coming: count board types in guests, adding up to guests in house | `git revert cf54f22` |
| 4.2 | `490bcb7` | Board table counts guests with a total; landing half board counts rooms | `git revert 490bcb7` |
| 4.3 | `869fed9` | Arrivals and departures in guests and rooms on Today and Demand | `git revert 869fed9` |
| 4.4 | `5656acf` | Cover parts (hotel, room service, walk-in, event) add up to the total | `git revert 5656acf` |
| 4.5 | `35ca56b` | Landing cards use the likely X-Y range format | `git revert 35ca56b` |
| 4.6 | `165b9e2` | Team evening card: Floor instead of Floor and breakfast | `git revert 165b9e2` |
| 5.1 | `077964a` | Waste per cover uses kg, not euros | `git revert 077964a` |
| 5.2 | `368ce2a` | Vegan main without dairy, gluten-free breakfast without bread, recipe tag check on load | `git revert 368ce2a` |
| 5.3 | `0857c19` | Extend simulated history to 8 weeks and count matching weekdays | `git revert 0857c19` |
| 5.4 | `7557e5b` | Head chef rota within Tue-Sun and 40 h; rota check for availability and hours | `git revert 7557e5b` |

Group tags so far: `fixes-group-0`, `fixes-group-1`, `fixes-group-2`, `fixes-group-3`, `fixes-group-4`, `fixes-group-5`.
<!-- commit-index:end -->

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

#### 0.8 Customer evidence: "What hotels told us"
- Files and functions: `index.html`: `Principles` (right-hand card next to the Champions 12.3 card).
- Before: a dashed card "In progress · Pilot results coming soon. We are starting pilots with independent hotels…".
- After: the same card style, titled "What hotels told us", with the chip "Phone interviews, 10 Oct 2026", the line "5 of the 10 small hotels we called in the UK and Italy answered", three anonymised findings (walk-in guests make restaurant demand hard to predict from bookings alone; staffing came up as often as stock; most still plan by hand) and a small "Pilot results coming soon." line underneath. No hotel names.
- Undo: `git revert <hash of 0.8>`

### Group 1. Remove placeholders and make the pilot form work

#### 1.1 Footer contact
- Files and functions: `index.html`: `CONTACT_EMAIL` constant, `Footer`.
- Before: "Contact: hello@[your-domain]", "Privacy policy [placeholder]", "Terms [placeholder]".
- After: "Contact: hello@demandinn.example" as an underlined `mailto:` link. The two placeholder lines are gone. **Waiting:** the real address goes into `CONTACT_EMAIL` (top of the script).
- Undo: `git revert <hash of 1.1>`

#### 1.2 FAQ "Is my data safe? What about GDPR?"
- Files and functions: `index.html`: `FAQ_ITEMS`.
- Before: "[Placeholder: confirm with your legal adviser before launch.] The plan is to collect only what the forecast needs, store it in the EU and never sell it. Guest names are not needed."
- After: "For pilots, we collect only what the forecast needs: booking and cover counts, sales by item, recipes and stock. Guest names are not needed. The data is stored in the EU, never sold, and deleted when you ask." Same promises as before, written as the pilot plan. It is still worth a check by a legal adviser before launch.
- Undo: `git revert <hash of 1.2>`

#### 1.3 Demo "Use your own data" → Privacy card
- Files and functions: `index.html`: `DataScreen` (Privacy card).
- Before: "Real pilots: data stored in the EU, never sold, deletable on request [placeholder: confirm with a legal adviser]."
- After: "For pilots, we collect only what the forecast needs. It is stored in the EU, never sold, and deleted when you ask." Matches the FAQ answer in 1.2.
- Undo: `git revert <hash of 1.3>`

#### 1.4 Pilot form sends the email
- Files and functions: `index.html`: new `PILOT_FORM_ENDPOINT` constant (top of the script), `Pilot` (`submit` and the form markup).
- Before: the form only checked the email format and then said "Thank you. This is a demo, so nothing was sent." The intro read "This demo does not send the form anywhere."
- After:
  - With an endpoint in `PILOT_FORM_ENDPOINT` (for example Formspree), the form POSTs `{"email": …, "source": "demandinn-site"}` as JSON with `fetch`. The button shows "Sending…" and is disabled while it waits. On success: "Thanks, we'll email you within two working days to set up the backtest." On failure: "Sorry, that didn't go through. Please try again, or email us at hello@demandinn.example."
  - With no endpoint (the current setting), it opens the visitor's mail app with a message to `CONTACT_EMAIL`, subject "Pilot hotel request", and says so, with the address as a fallback link.
  - The intro now reads "We will write back within two working days to set up the free backtest." Both "demo" sentences are gone. A hidden `source=demandinn-site` field is in the form too.
- Tested locally: wrong format → error message; POST to a local address that does not exist → error message with the contact email; a stubbed successful POST → "Sending…" then the success message, with the right JSON body. The `mailto:` path was not clicked, so as not to open the mail app on the test machine.
- **Waiting:** while `CONTACT_EMAIL` is the `.example` placeholder, pilot requests go nowhere. Add the real address, or a Formspree URL, before sharing the site.
- Undo: `git revert <hash of 1.4>`

#### 1.5 "Become a pilot" in the header and the hero
- Files and functions: `index.html`: `NAV_LINKS`, `Hero`.
- Before: the header nav ended with "Pilot". The hero's secondary button read "See a day at Hotel Aurora" (`#day`).
- After: the nav item reads "Become a pilot" (`#pilot`), on desktop and in the mobile menu. It replaces "Pilot" rather than sitting next to it, so there aren't two links to the same place. The hero's secondary button reads "Become a pilot hotel" and links to `#pilot`. "A day at Aurora" is still in the nav.
- Undo: `git revert <hash of 1.5>`

#### 1.6 Grep for leftovers
- Searched `index.html` for `[placeholder`, `[your-`, `TODO` and `lorem` after 1.1 to 1.5. Nothing visible to visitors is left. The only match is the code comment above `CONTACT_EMAIL` explaining the placeholder address. No commit needed.

### Group 2. Head, metadata and small technical fixes

#### 2.1 Language and character set
- Files: `index.html`, first lines and the end of the stylesheets.
- Before: `<html>` with no language, `<meta charset=utf8>` (not a valid name), and the `<head>` closed after the first stylesheet, so `<title>`, the description, the font links and the other styles sat inside `<body>`.
- After: `<html lang="en">`, `<meta charset="utf-8">`, and one `<head>` that holds the title, meta tags, font links and all styles. `<body>` starts at `<div id="root">`. Nothing visible changes. Screen readers and search engines now know the page is in English.
- Undo: `git revert <hash of 2.1>`

#### 2.2 Favicon
- Files: `index.html`, `<link rel="icon">` in the head.
- Before: no favicon (the browser showed a blank page icon).
- After: an inline SVG data URI: the logo's cloche (dome, handle and knob) in amber `#dfa550` on a rounded forest-green `#1b322a` square. No extra file to deploy.
- Undo: `git revert <hash of 2.2>`

#### 2.3 Open Graph, Twitter and canonical tags
- Files: `index.html`, head.
- Before: none, so a shared link showed no picture and a generic title.
- After: `<link rel="canonical" href="https://demandinn.vercel.app/">`; `og:type`, `og:site_name`, `og:title` ("DemandInn: Tomorrow's covers, forecasted today", the same as `<title>`), `og:description` (the meta description from 0.4), `og:url`, `og:image` (the hero chef photo from Unsplash cropped to 1200×630, checked to return a JPEG), its width, height and alt text; `twitter:card summary_large_image`, `twitter:title`, `twitter:description`, `twitter:image`.
- Undo: `git revert <hash of 2.3>`

#### 2.4 Message when scripts cannot run
- Files: `index.html`, top of `<body>` and a one-line check after the CDN scripts.
- Before: with JavaScript off, or if a CDN failed, visitors saw an empty green page.
- After: a `<noscript>` message: "DemandInn needs JavaScript to show this page. Please try another browser, or write to us at hello@demandinn.example." A `<noscript>` only shows when JavaScript is switched off, so there is also a hidden `#boot-fail` message that a one-line script turns on when React, ReactDOM or htm did not load: "The page could not load its scripts. Please check your connection and reload, or write to us at hello@demandinn.example." Tested with a deliberately broken React URL. Static HTML cannot read `CONTACT_EMAIL`, so the address is written in both messages, and comments next to the constant and the messages say to update all three together.
- Undo: `git revert <hash of 2.4>`

#### 2.5 Vercel Web Analytics
- Files: `index.html`, after the CDN scripts.
- Before: no analytics.
- After: `<script defer src="/_vercel/insights/script.js"></script>`. **To do in the Vercel dashboard:** turn on Web Analytics for the project (Project → Analytics → Enable), otherwise the script returns 404 and nothing is counted. Locally the script also returns 404, which is expected and harmless.
- Undo: `git revert <hash of 2.5>`

#### 2.6 Pilot photo background: already in place
- `.pilot-photo` already had `background: var(--forest2)` in the original commit `d6aeb83`. While the lazy-loaded photo arrives, the box shows that forest tone, and the photo loads into it (checked in the browser). No change and no commit.

#### 2.7 Contrast of the small amber chips
- Files: `index.html`, the `.text-terra` utility (used by the "Simulated demo data" and "Built from the live forecast" chips, and by a few amber notes).
- Before: text `#9a6416` on `#fbebc8`: 4.23:1, below the 4.5:1 WCAG AA minimum for small text.
- After: text `#8f5c12`: 4.81:1 on `#fbebc8` and 4.63:1 on the paler `#f7e7c3`. The darkest change that passes, so the colour still reads as the same amber.
- Undo: `git revert <hash of 2.7>`

#### 2.8 Demo banner says changes reset
- Files and functions: `index.html`: `AppWindow` (the amber banner above every demo screen).
- Before: "Simulated demo data for Hotel Aurora. Every number is computed live by the forecasting engine. The history is simulated."
- After: the same, plus "Changes reset when you reload." (Orders, waste entries and rota changes live only in the page's memory.) Item 7.10 later swaps the first part for the file name once a CSV is loaded.
- Undo: `git revert <hash of 2.8>`

### Group 3. Fixed demo date for presentations

#### 3 Demo date from the link
- Files and functions: `index.html`: new `parseDateParam()` and `DATE_FROM_LINK`, `TODAY`; the demo banner in `AppWindow`.
- Before: `const TODAY = sod(new Date())`. The demo always showed the real day, so a presentation rehearsed on Monday looked different on Tuesday.
- After: `https://demandinn.vercel.app/?date=2026-10-20#/app` fixes "today" to Tue 20 Oct 2026. Everything in the demo already counts from `TODAY`: the greeting date, the weekday logic, supplier days, bookings, events, the calendar, the rota, the morning email and the landing cards. The date must be `YYYY-MM-DD` and a real calendar date: `2026-02-30`, `20-10-2026` or a missing value fall back to the real today. When a date comes from the link, the banner adds "Demo date fixed to Tue, 20 Oct 2026 by the link." The query string survives moving between the site and the demo, because those links only change the `#` part.
- Tested: `?date=2026-10-24` (a Saturday) → Sat 24 Oct everywhere; `?date=2026-02-30` → falls back to the real date.
- Undo: `git revert <hash of 3>`

### Group 4. Units and labels (guests and rooms)

#### 4.1 Today → "Who is coming" counts guests
- Files and functions: `index.html`: `forecastDay` (the `board` split), `TodayScreen` ("Who is coming" bar and sentence).
- Before (Mon 19 Oct, planning for Tue 20): "29 of 18 rooms include breakfast or half board, 7 are room only". The 29 and 7 are guests, so the sentence compared guests with rooms, and the bar was 29/18 = more than full.
- After: "29 of 37 guests have breakfast or half board, 8 are room only." Computed, not hard-coded. The board split is now rounded with the largest-remainder method, so bed and breakfast + half board + room only always equals the guests in house. Checked on 50 days (20 past, 30 ahead): no mismatch. The bar is now 29/37. (The review expected "7 are room only", but 29 + 7 is 36, not 37: rounding each type on its own lost a guest.)
- Undo: `git revert <hash of 4.1>`

#### 4.2 Demand → "Board type drives the breakfast" counts guests
- Files and functions: `index.html`: `forecastDay` (new `boardRooms`, rooms per board type, largest-remainder rounded to the rooms total), `CoversTab` (the board table), `DayAtHotel` (the landing "Bookings" card).
- Before (Tue 20 Oct): the column "Rooms" showed 17 / 12 / 7, which are guests (18 rooms were booked), and the rows added up to 36. On the landing page, "Half board 12 rooms" was also a guest count.
- After: the column is "Guests" (17 / 12 / 8) with a total row "Total 37 guests in 18 rooms", matching the pipeline strip above ("18 rooms, 37 guests"). The landing card's "Half board" now shows real rooms (6 rooms). Room counts per board type always add up to the rooms booked (checked on 50 days).
- Undo: `git revert <hash of 4.2>`

#### 4.3 Arrivals and departures name their unit
- Files and functions: `index.html`: `TodayScreen` ("Who is coming" tiles), `explainDay` (the "Bookings" line on Demand, the day panel and the assistant).
- Before (Tue 20 Oct): Today said "20 arriving, 15 leaving" (guests, no unit). Demand said "10 arrive and 10 leave" (rooms, no unit). They looked like a contradiction.
- After: Today: "37 guests in house, 18 rooms · 20 guests arriving, 10 rooms · 15 guests leaving, 10 rooms". Demand: "… about 37 guests. 20 guests in 10 rooms arrive, 15 guests in 10 rooms leave." Same numbers, both units, on both screens.
- Undo: `git revert <hash of 4.3>`

#### 4.4 Cover parts add up to the total
- Files and functions: `index.html`: `forecastDay` (new `dining` field; `hotel`, `walkIn` and `roomService` come from one largest-remainder split), `CoversTab`.
- Before (Tue 20 Oct): breakfast 24 = 21 hotel guests + 3 walk-ins + 1 room service (= 25); dinner 25 = 18 + 7 + 1 (= 26). Room service was counted inside "Hotel guests" and again on its own.
- After: breakfast **24 = 20 + 3 + 1**, dinner **25 = 17 + 7 + 1**. Hotel guests in the restaurant + room service + walk-ins + booked event covers always equal the headline number. Checked for all four services on 60 days (20 past, 40 ahead): no mismatch. The Team screen's "Hotel / Walk-in" and the day panel's "Hotel / walk-in" still add up to the covers.
- Undo: `git revert <hash of 4.4>`

#### 4.5 One range format: "likely X–Y"
- Files and functions: `index.html`: `Hero` (the floating "Tomorrow · Hotel Aurora" chip), `HeroCard` (the kitchen order card).
- Before (Tue 20 Oct): "25 dinner covers, ± 7" on the landing page, "likely 18 to 31" in the timeline and the demo.
- After: "25 dinner covers, likely 18–31" on both landing cards. No "±" is left on the site.
- Undo: `git revert <hash of 4.5>`

#### 4.6 Team → evening card: "Floor"
- Files and functions: `index.html`: `TeamScreen` (the `gl` labels now depend on the period).
- Before: both the morning and the evening card called the serving team "Floor and breakfast".
- After: the morning card still says "Floor and breakfast" (the breakfast host is in that group). The evening card says **"Floor"**. The review suggested "Floor and bar", but the evening card already has its own "Bar" row (the bartender), so "Floor and bar" would name the bar twice. **Waiting:** if you prefer the exact wording "Floor and bar", it is a one-word change in `gl`.
- Undo: `git revert <hash of 4.6>`

### Group 5. Calculation bugs

#### 5.1 Waste per cover uses kg
- Files and functions: `index.html`: `computeMetrics`. Shown in `TodayScreen` ("Waste per cover") and `WasteScreen` ("Per cover"); both multiply by 1,000 and print grams, unchanged.
- Before: `wastePerCover = wasteE / covers30`, euros divided by covers, printed as grams: **64 g** (EUR 146.94 / 2,284 covers).
- After: `wastePerCover = wasteKg / covers30`: **10 g** (22.6 kg / 2,284 covers) on both screens. (The 30-day waste itself is rescaled in 7.6, so these numbers change again there.)
- Undo: `git revert <hash of 5.1>`

#### 5.2 Dietary tags agree with the recipes
- Files and functions: `index.html`: `DISHES` (`veg_main`, `bf_cooked`), new `NOT_VEGAN`, `NOT_VEG`, `NOT_GF` and `checkDishTags()`, which runs once on load.
- Before: "Vegetarian main" was tagged vegan and gluten-free but contained cheese and butter. It is the dish vegans are given at lunch and dinner. "Cooked breakfast" was tagged gluten-free but contained bread (spotted while writing the check).
- After:
  - Vegetarian main: rice 90 g, seasonal vegetables 170 g (was 150 g), tomatoes 80 g (was 60 g), herbs 4 g, olive oil 20 g (was 10 g). No cheese or butter, so it is truly vegan and gluten-free. All ingredients are already in stock.
  - Cooked breakfast: the 40 g of bread is replaced by 80 g of potatoes (rösti), so the gluten-free tag is true.
  - `checkDishTags()` warns in the console ("DemandInn recipe check: …") if a dish tagged vegan contains dairy, eggs, meat or fish, a dish tagged vegetarian contains meat or fish, or a dish tagged gluten-free contains bread, pasta, flour or croissant dough. On load it now finds nothing. Tested by adding cheese back to the vegan dish and tagging pasta gluten-free: it reported both.
- Effect on numbers: a little less cheese, butter and bread and a little more vegetables, oil and potatoes are forecast and ordered.
- Undo: `git revert <hash of 5.2>`

#### 5.3 History: 8 weeks, and the weekday count is computed
- Files and functions: `index.html`: new `HISTORY_DAYS = 56`, `buildReservations` (older history), `RES_ACTIVE`, new `sameDowInHistory()`, `explainDay` (the "Past sales" line), `DataScreen` ("History read" and the per-weekday row counts of a loaded CSV).
- Before: Demand said "Calibrated on the last 8 Tuesdays of point-of-sale data", but the simulated bookings only started 32 days back and "Use your own data" said "History read: 28 days (simulated)". Days before −32 had no guests at all, which is why the baselines dropped to a handful of covers.
- After: the simulated history covers 8 weeks. The older stays come from their own random stream, and every one of them checks out by day −32, so all bookings and forecasts from day −31 onwards are **identical** to before (checked: rooms, guests, covers and ranges for days −31 to +62, no difference). "History read" shows "56 days (simulated)". The "Past sales" line counts the matching weekdays in the history ("the last 8 Tuesdays"). When a CSV has been loaded, it counts that weekday's rows in the file instead ("the last 52 Tuesdays of covers in Sample hotel….csv").
- Undo: `git revert <hash of 5.3>`

#### 5.4 Rota respects availability and contract hours
- Files and functions: `index.html`: `EMPLOYEES` (new `days` and `shifts` fields that spell out each availability label, and a comment on how the rota string is indexed), new `ALL_DAYS`, `outsideAvail()` and `rotaProblems()`; a check run on load (console warnings "DemandInn rota check: …"); `RotaCalendar` (a shift outside availability gets the same red dashed outline as a time-off request, the legend says "Time off requested, or outside availability", and the cell label says so).
- Why it was wrong: the rota string is indexed by `Date.getDay()`, so position 0 is **Sunday**. "-PPPPPP" put the head chef on Monday (he is available Tue to Sun) and off on Sunday, with 6 × 7 h = 42 h on a 40 h contract.
- Before: Tomás Rivera, "-PPPPPP": Mon to Sat evenings, 42 of 40 h. Priya Nair, "P--PPPP": Sun and Wed to Sat evenings.
- After: Tomás, "--PPPPP": Tue to Sat evenings, **35 of 40 h**, all within Tue to Sun. Priya, "PP-PPP-": Sun, Mon and Wed to Fri evenings, 35 of 40 h, so every evening still has at least two people in the kitchen. All other rotas were already within their availability and contracts (checked). On the old rota the new check reports exactly the two review findings; on the new rota it reports nothing.
- Effect on the team story: Saturday evening (the wedding dinner) now shows "2 extra pairs of hands" for the kitchen instead of 1, since the head chef is no longer double-booked. The other gaps are unchanged.
- Undo: `git revert <hash of 5.4>`

### Group 6. Dates in the demo

#### 6.1 Year on dates outside the current year
- Files and functions: `index.html`: `fmtDate` (used by every screen).
- Before: no year, so on 19 Oct 2026 the pasta batch showed "use by 24 Sept" next to "60+ days left", which read as expired.
- After: when a date that shows a month falls in another year than the demo's today, the year is added: "24 Sept 2027", "15 Aug 2027" (house wine), "14 Sept 2027" (rice). Dates in the current year stay short ("Thu 22 Oct"). Holds on any date, including around New Year.
- Undo: `git revert <hash of 6.1>`

#### 6.2 Explain panel: weekday only within the week
- Files and functions: `index.html`: new `dayOrDate()`; `ExplainPanel` ("Stock and open orders").
- Before: `"use by " + dowShort(...)` printed a weekday even for dates months away: the house wine showed "use by Sun" while Stock said 15 Aug.
- After: within the next 6 days, the weekday ("use by Thu"). Further out, the date ("best before 15 Aug 2027"). Long-life items say "best before" and fresh items "use by", as on the Stock screen. Open-order arrival days follow the same rule.
- Undo: `git revert <hash of 6.2>`

#### 6.3 Order windows print real dates
- Files and functions: `index.html`: new `winText()`; `ExplainPanel` ("Forecast use" row and the "Demand by day" table), `POLine` (Purchasing), `suggestOrders` (the order reason), `answerFor` (assistant).
- Before (19 Oct): "Forecast use: Fri to Sun, all services" for the house wine, while the window and the table under it covered 10 days (Fri 23 Oct to Sun 1 Nov), with weekday-only rows that repeated Fri, Sat and Sun.
- After: "Fri 23 Oct to Sun 1 Nov (10 days), all services". The table rows show full dates (Fri 23 Oct … Sun 1 Nov) and sum to the same 90 bottles. Purchasing ("90 bottles forecast from Fri 23 Oct to Sun 1 Nov"), the order reason ("expected from Wed 21 Oct to Fri 23 Oct") and the assistant use the same wording. A one-day window says "on Thu 22 Oct". (The window itself changes in 7.1; the labels follow it automatically.)
- Undo: `git revert <hash of 6.3>`
