# DemandInn, version II (23 Oct 2026)

Changes from the team call of 23 Oct 2026, on the branch `version-II`. It starts from `fix/review-oct-2026` (the review fixes, never published).

## Saved versions

- Git tag `saved-live-2026-10-23`: exactly what https://demandinn.vercel.app served on 23 Oct 2026 (branch `main`, commit d6aeb83).
- Git tag `saved-review-fixes-2026-10-23`: the review-fixes branch before version II.
- Copies of both pages: `~/Desktop/Claude/DemandInn-backup-2026-10-23/`.

## What changed

| Team note | Change |
| --- | --- |
| Real market figures | Problem section uses WRAP figures (£318m, 79,000 t, £0.52 per meal, 45% from over-preparation). New "Why now" section: about 2,300 independent hotels in London and 12,000 in England (VisitBritain 2026 × 73%), Simpler Recycling since 31 Mar 2025, the 2030 targets. All linked to their sources. |
| Competitors | New "How we compare" table: DemandInn, Winnow, Orbisk, Leanpath, with their published London results (Marriott Canary Wharf −67%, Novotel ExCeL −45%, TRIBE Canary Wharf −37% and £25,047). |
| How much the hotel saves | New "What a 28-room hotel saves" section: about £13,000 of food thrown away a year, £2,700 saved (21% cut, Champions 12.3), 3.5 hours a week, against £1,548 a year. The ROI calculator now uses the same model in £. In the demo, the Today screen shows "What DemandInn saves you" each month, and the daily briefing includes it. |
| Process for the hotel owner | New "How it works for you, in four steps" section, straight after the hero. |
| Morning email, renamed | Now "Daily briefing", by email, WhatsApp or SMS, with a preview for each. |
| Data input and API logic | New diagram: five inputs (bookings, till, weather, events, team), how each gets in today (CSV) and after the pilot (API), and what comes out. In the demo, "How the connection works" shows example messages from each source. |
| Test CSV | `demandinn-test-data.csv`: 12 months, 14 columns (bookings, covers, walk-ins, weather, temperature, events, groups). The importer recognises every column, shows where it comes from, and says what the file tells us (rain lowers lunch, event days lift dinner…). |
| Live notification for the video | A table for 15 is booked for tomorrow. A notification appears and the numbers move: dinner covers, the order list and its items. |
| Currency and price | £ everywhere. Price £129 a month (about €149). To be confirmed by the team. |

## For the presentation video

- Fixed date, so the numbers are the same every take: `https://demandinn.vercel.app/?date=2026-10-23#/app`
- The booking arrives by itself 4 seconds after the demo opens: `https://demandinn.vercel.app/?date=2026-10-23&demo=booking#/app/today`
- Or click "Simulate a new booking" in the yellow bar at the top of the demo, or "Send a test booking" on the Use your own data screen. "Remove the test booking" undoes it.

## Still to check

- Price of £250 a month (was £129, changed 27 Oct 2026).
- The savings use industry averages (WRAP 2013 at 2011 prices, Champions 12.3). The demo hotel buys more food than the WRAP average, so its monthly saving (about £400 of food) is higher than the landing page's £2,700 a year.
- Competitor prices are not published, except a third-party estimate for Orbisk (FAO).

## Updates, 24 Oct 2026

- Savings card in the demo: aligned columns, and each figure opens its calculation step by step.
- Stock: six items to use within 48 hours (three batches close to their date added to the demo stock).
- Numbers use DM Sans instead of Fraunces, so figures read plainly. Words in headings stay in Fraunces.
- Vercel: Vercel Authentication is off for the demandinn project, so the version II preview opens for anyone without a share link: https://demandinn-git-version-ii-matteoevenacademic-9707s-projects.vercel.app. It was "all except custom domains" before. demandinn.vercel.app is unchanged. To turn it back on: Vercel → demandinn → Settings → Deployment Protection → Vercel Authentication.

## Updates, 27 Oct 2026

- Price is now £250 a month (about €290), up from £129. Every figure that uses it follows: £3,000 a year, about £4,300 a year better off for the 28-room hotel (was £5,700), paid back in about 5 months (was 3). The food saved alone (about £2,700) no longer covers the price on its own, so the "You pay" card now says it covers 91% and the time given back covers the rest. The calculator and the demo's savings card work from the same price.
