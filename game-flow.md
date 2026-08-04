---
title: Game flow — Planning Poker for Jira
---

# Game flow

A game is played in rounds. Each round covers one work item and ends when the
facilitator saves a final estimate for it.

[← Documentation home](index.md) · [Create a game](create-a-game.md)

---

## Joining a game

There are two ways in:

- **From the Games screen.** Open **Apps → Planning Poker** or the
  **Planning Poker** tab in a project, find the game and click its name.
- **From a link.** The facilitator copies it with **⋯ → Copy game URL** and
  shares it. The link opens the game room directly.

The app has no built-in chat, audio or video. Agree on a call or a channel
before you start — the discussion between the reveal and the final estimate is
where planning poker does its work.

Which game you can open depends on its **Private** setting. A public game can
be opened by anyone with access to the app; a private game only by its
facilitator, estimators and spectators. Everybody else gets *Game not found or
deleted.*

---

## The game room

The room has two parts:

- **Top** — the current work item under the heading *Now estimating*, the card
  deck, the voting status and, after the reveal, the results.
- **Bottom** — the game backlog as a table: **Work**, **Assignee**, the
  estimation field, **Priority**, **Status** and **Result**. The current row is
  highlighted. The facilitator switches the current work item by clicking a
  row.

Work item keys and summaries are links — they open the work item in Jira in a
new tab, so the game stays open in the tab you are in.

The room refreshes itself every few seconds. Polling stops while the browser
tab is in the background and resumes as soon as you come back to it; the fields
taken live from Jira (assignee, priority, status, current estimate) refresh
about once a minute.

---

## Voting

**Pick a card.** Your card is highlighted for you but stays hidden from
everybody else until the reveal.

**Add a note** (optional, up to 200 characters) in the field under the deck to
explain your vote — for example *"assumes the API is already there"*. Notes are
hidden exactly like the cards and appear for everyone under **Notes** after the
reveal.

**Voting status** lists everyone expected to vote and their state — *voted* or
*waiting* — with a summary line above it. When the last person has voted, the
facilitator sees a green banner saying the results can be revealed, and the
other participants see a quieter line saying the team is waiting for the
facilitator.

**Spectators** do not see the deck. If you expected to vote and cannot, check
the estimator list of the game — see [FAQ](faq.md#why-cant-i-vote).

### The timer

The facilitator can run a round timer of **30s**, **60s** or **2 min**, and
stop it early with **Stop**. The remaining time is shown to everyone. When the
timer runs out the votes are revealed automatically, so treat it as a
soft deadline for the round rather than a hard cut-off.

### Suggest estimate

**💡 Suggest estimate** is a shortcut for the facilitator. It searches your own
Jira site for work items whose summary shares keywords with the current one and
that already have a story point value, takes the median of what it finds and
snaps it to the nearest card in the game's deck. The result reads *Looks like 5
— based on 12 similar work items*; hovering it shows the work items behind the
number.

It is a JQL search inside your own Jira, run with your permissions. No AI or
external service is involved, and nothing leaves Atlassian. If your site has no
Story Points field, or nothing similar is estimated yet, the app says so and
the round continues as normal.

---

## Revealing the votes

The facilitator clicks **Reveal votes**. Every card is turned over at once,
together with the notes.

The results block shows:

| Element | When it appears | What it means |
| --- | --- | --- |
| **Most Votes** | From 3 votes onwards, when a single card leads | The most frequent estimate, shown large |
| *"The votes are split: 5 and 13 (2 votes each). Discuss and revote."* | Two or more cards tie for the lead | There is no single answer yet — discuss and run another round |
| **Voted N/M** | Always | How many of the game's estimators have cast a card |
| Distribution | Always | One row per card, `3x 5`, most frequent first; ties keep the deck order |
| **Notes** | When someone left a note | Author and note text |

**∞** and **☕** take part in all of this like any other card.

With one or two votes the **Most Votes** block is hidden — a single vote is not
a majority — while the count, the distribution and the notes are still shown.

**Re-vote** clears the votes for the current work item and starts a fresh round
with hidden cards. Use it after a discussion, or whenever the votes were split.

An estimator can also change their card after the reveal; the results update
live for everyone.

---

## Saving the final estimate

After the reveal the facilitator gets a **Final estimate** selector, prefilled
with the leading card, and a save button. The button is labelled:

| Label | When |
| --- | --- |
| **Save estimate** | The default label |
| **Save & next** | Other work items are still unestimated — saving opens the next one automatically |
| **Save & finish** | This is the last unestimated work item — a confirmation dialog appears, and saving closes the game |

What happens on save:

1. The value is written to the Jira field chosen for the game — the Story
   Points field, or the original time estimate. See
   [Game basics](game-basics.md#how-values-are-converted) for the conversion
   rules.
2. The value is recorded in the game and appears in the **Result** column and
   in the report.
3. The room confirms with **✓ Estimate saved** and states what was written, for
   example *wrote 3h to Jira (M → 3h)*.

If Jira refuses the write, the app shows the reason instead of a silent
success. The usual cause is a field that is not on the work item's screen — see
[Jira configuration](jira-configuration.md).

If the final estimate is **∞** or **☕**, nothing is written to Jira: the room
says *kept in game only (non-numeric card — nothing written to Jira)*, and the
value is still kept in the game and its report.

---

## Editing a running game

The facilitator can change a game while it is being played, from **Edit game**
in the room or from the **⋯** menu on the Games screen. It opens the same
wizard as creation, with two tabs — **Edit game** for the settings and **Edit
backlog** for the work items — and one **Save** for both.

Two rules protect what is already done:

- a work item that already has a saved estimate cannot be removed from the
  game; if you deselect it, it is put back and marked *estimated*;
- the card deck and the estimation field are locked once any estimate has been
  saved in that game.

---

## Finishing a game

A game finishes when the facilitator saves the estimate for the last
unestimated work item and confirms **Save & finish**.

A finished game opens on a **Game finished** screen listing every work item
with its final estimate. From there:

- **Go to Board** — shown when you opened the app from a project tab; it opens
  that project's board.
- **Go to Games** — shown when you opened the app from the Apps menu.

A finished game is read-only. Voting, revealing, re-voting, the timer, saving
estimates and every kind of editing are rejected. Its report and CSV export
stay available.

---

[← Create a game](create-a-game.md) · [Documentation home](index.md) ·
[Manage games →](manage-games.md)
