---
title: Planning Poker for Jira — User Guide
---

# Planning Poker for Jira

Estimate your backlog together, right inside Jira. Everyone votes in secret,
votes are revealed at once, and the agreed estimate is written straight into
the Jira work item.

This app runs entirely on Atlassian infrastructure. No data is sent to any
external server — see the [Privacy Policy](privacy.md).

---

## Install

1. Open **Atlassian Marketplace** and install **Planning Poker** into your
   Jira Cloud site.
2. Open Jira. The app appears in two places:
   - **Apps** menu in the left navigation — for estimation across spaces;
   - a **Planning Poker** tab inside any project (space).

Both open the same screen. Anyone with access to the app can create a game.

---

## Quick start

1. Open **Planning Poker** and click **+ New game**.
2. **Step 1 — settings.** Give the game a name, pick a card deck and the
   estimation field, choose who runs the game and who votes.
3. **Step 2 — Add works.** Find the work items to estimate: filter by space,
   type and status, search by name or key, or switch to **JQL** for a raw
   query. Tick the items, then click **Create game**.
4. Share the game with your team: on the **Games** screen, open the **⋯** menu
   and choose **Copy game URL**. Anyone who opens the link lands directly in
   the game.
5. In the game room, everyone picks a card. When all votes are in, the
   facilitator clicks **Reveal votes**, the team agrees on a number, and the
   facilitator clicks **Save estimate** — the value goes into Jira.

---

## Screens

### Games

The list of all games you can see, with search by name and filters by
**Facilitator**, **Status** and **Access**. Click **Created** or **Updated** to
sort, and click again to flip the direction.

The **⋯** menu on each row offers:

| Action | What it does |
| --- | --- |
| Clone game configuration | Reuse the settings of an existing game. You pick fresh work items on the next step, or duplicate the whole game with its backlog. |
| Copy game URL | Copies a direct link to that game. |
| Export results (CSV) | Downloads the results as a CSV file. |
| Open report | Opens the game report. |
| Edit game | Available to the facilitator of an active game. |
| Delete game | Removes the game and all of its votes. |

### Creating a game

**Card deck** — Fibonacci, Mod. Fibonacci, T-shirt, Time estimates, or Custom
(your own comma-separated values). Every deck also ends with `∞` (too large to
estimate) and `☕` (I need a break).

**Estimation field** — where the final estimate is saved:

- **Story point estimate** — the standard story points field;
- **Original estimate** — written to time tracking, in hours.

The two settings work together: **Story point estimate** accepts numeric decks
only, so **T-shirt** and **Time estimates** are selectable only when the game
saves to **Original estimate**.

**Private game** — only the facilitator, estimators and spectators can see it.

**Facilitator** — runs the game: reveals votes, saves estimates, edits and
finishes the game. By default this is you, but you can hand it to someone else.

**Estimators** — the people who vote. At least one is required. **Spectators**
watch without voting.

Two things are always on and need no setting: the facilitator can reveal the
votes at any moment, and a voter can change their card even after the reveal.

### The game room

The current work item is shown at the top, with the card deck below it.

- **Pick a card** to vote. Your card stays hidden until the reveal.
- **Add a note** (optional) to explain your vote — notes appear to everyone
  after the reveal.
- Can't put a number on it? Pick `∞` — it counts as a vote but is left out of
  the numeric result.
- **Voting status** shows who has already voted and who you're still waiting
  for. When everyone has responded, the facilitator sees a banner.
- **Timer** — the facilitator can run a 30 s, 60 s or 2 min round.

After **Reveal votes** the room shows:

- **Most Votes** — the most frequent estimate, shown once at least three people
  have voted;
- if several cards tie, a line such as *"The votes are split: 5 and 13
  (2 votes each). Discuss and revote."*;
- **Voted N/M** — how many of the assigned voters have cast a card;
- the full distribution, e.g. *3x 5*, *2x 8*.

The facilitator then picks the **Final estimate** and saves it. The button is
labelled **Save & next** while unestimated items remain, and **Save & finish**
on the last one — which closes the game.

**Re-vote** clears the votes for the current item and starts a new round.

### Suggest estimate

**💡 Suggest estimate** looks for work items in your own Jira that have a
similar summary and already carry a story point value, then proposes the most
common one. It is a search inside your Jira site — nothing is sent anywhere
else, and no AI model is involved.

### Editing a live game

The facilitator can open **Edit game** from the **⋯** menu or from inside the
room. It opens the same wizard used for creation, with two tabs: **Edit game**
for the settings (name, privacy, deck, estimation field, facilitator,
estimators, spectators) and **Edit backlog** for the work items. **Save** stores
both at once.

Two rules apply:

- a work item that already has a saved estimate cannot be removed;
- the deck and the estimation field are locked once an estimate has been saved
  in that game, so recorded values keep their meaning.

### Finished games

Saving the estimate for the last work item finishes the game. A finished game
is read-only: no voting, no reveals, no editing. You can still open its report
and export the results.

### Report

The report lists every work item with its votes and final estimate, plus
**SP total** — the sum of the numeric estimates saved in that game. **CSV**
downloads the same data.

---

## Troubleshooting

### "Story Points field is not on the appropriate screen"

Jira refused the write because the estimation field isn't available on that
work item's screen. This is a Jira configuration matter, not an app error.

Ask a Jira administrator to add the field to the screen used by that work item
type:

1. **Project settings → Screens** (or **Jira settings → Issues → Screens** for
   company-managed projects).
2. Find the screen used by the work item type you are estimating.
3. Add **Story point estimate** (or **Original estimate**) to it.
4. Retry **Save estimate**.

In team-managed projects the equivalent setting lives under
**Project settings → Features → Estimation**.

### A non-numeric card was chosen as the final estimate

`∞` and `☕` have no numeric meaning, so nothing is written to Jira. The value
is still kept in the game and shown in the report.

T-shirt sizes are different: they are converted to numbers before the write —
XXS 0.5, XS 1, S 2, M 3, L 5, XL 8, XXL 13 — and saved to **Original estimate**
in hours. The room shows what was actually written, for example *M → 3h*.

### Someone can't vote

Check the game's voter list. Only the people listed as **Estimators** can vote;
everyone else joins as a spectator and the deck stays hidden. The facilitator
can change that list in **Edit game**, on the settings tab.

### The screen doesn't update after an install or upgrade

Reload the page with **Ctrl+Shift+R** (**Cmd+Shift+R** on macOS) to clear the
cached app frame.

---

## Good to know

- The theme follows your Jira profile: switch Jira to dark mode and the app
  follows.
- The room refreshes automatically. Polling pauses while the browser tab is in
  the background and resumes the moment you come back.
- Clicking a work item key or summary opens it in Jira in a new tab, so you
  never lose your place in the game.

---

## Support

Questions, bugs and feature requests: see [Support](support.md).

[Privacy Policy](privacy.md)
