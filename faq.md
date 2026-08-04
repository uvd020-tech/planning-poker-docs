---
title: FAQ — Planning Poker for Jira
---

# Frequently asked questions

[← Documentation home](index.md) · [Support](support.md)

---

## Getting started

### Where do I find the app after installing it?

In two places, both opening the same **Games** screen: **Apps → Planning
Poker** in the Jira top navigation, and the **Planning Poker** tab inside a
project. See [Documentation home](index.md#where-to-find-the-app).

### Is there anything to configure before the first game?

No. The app has no admin or project settings screen. You only need a Jira
project with work items, and an estimation field the app is allowed to write
to — see [Jira configuration](jira-configuration.md).

### Do I have to create a game inside a specific project?

No. Games are global. Opening the app from a project tab only preselects that
project in the **Spaces** filter; a single game's backlog can hold work items
from several projects.

---

## Playing

### How do I invite my team?

Open the **⋯** menu of the game on the Games screen and choose **Copy game
URL**, then share the link. Anyone who may see the game can also find it on the
Games screen without a link.

### Why can't I vote?

Because you are not on the game's estimator list. Only the facilitator and the
people added as **Estimators** get the card deck; everyone else joins as a
spectator. The facilitator can add you through **Edit game → Edit game** tab.

### Can I change my card after the votes are revealed?

Yes. Pick another card and the results update for everyone straight away.

### What do the ∞ and ☕ cards mean?

**∞** means *too large to estimate*, **☕** means *I need a break*. They count
as votes and appear in the distribution, but they have no numeric value, so
choosing one as the final estimate keeps it in the game and the report without
writing anything to Jira.

### The reveal says "The votes are split" — what now?

Two or more cards got the same number of votes, so there is no single answer.
Discuss the difference — the notes people left with their votes usually explain
it — and click **Re-vote** for a new round.

### Why is there no "Most Votes" number?

It appears from three votes onwards. With one or two votes there is no majority
worth calling a result, so the room shows only the count, the distribution and
the notes.

### What happens when the timer runs out?

The votes are revealed automatically. The facilitator can also reveal them at
any moment without waiting for the timer or for the last voter.

### Can we estimate without meeting?

The app is built for a live round: everyone votes at the same time and the
facilitator reveals. There is no asynchronous mode. The app also has no chat or
call of its own — use your usual meeting tool alongside it.

---

## Estimates and Jira

### I clicked Save estimate and got an error about the field not being on the screen

Jira refused the write because the estimation field is not available on that
work item type's edit screen. This is a Jira configuration matter, not an app
fault. Follow [Jira configuration](jira-configuration.md#making-story-points-writable);
in team-managed projects the setting lives under
**Project settings → Features → Estimation**.

### Where exactly is the estimate written?

Into the field selected in step 1 of the wizard: the Story Points field, or the
original estimate of the work item's time tracking. Nothing else in Jira is
modified.

### Can I change the deck or the estimation field of a running game?

Only until the first estimate is saved. After that both are locked, because
changing them would give the values already written to Jira a different
meaning. Everything else — name, privacy, facilitator, estimators, spectators,
backlog — stays editable.

### Why are T-shirt sizes only available with Original estimate?

Story Points is a numeric Jira field, so the app offers only numeric decks for
it. With **Original estimate** the sizes are converted before the write —
XXS 0.5, XS 1, S 2, M 3, L 5, XL 8, XXL 13 — and saved in hours. The room
reports what was actually written.

### Does deleting a game remove the estimates from Jira?

No. Deleting a game removes the game, its backlog and its votes. Estimates
already written to work items stay in Jira.

---

## Access and data

### Who can see a game?

A public game — anyone who can open the app. A **Private** game — only its
facilitator, estimators and spectators; for anyone else it does not appear in
the list and a direct link returns *Game not found or deleted.*

### Can a user see work items they have no access to?

No. Every read goes through Jira with that user's own permissions.

### Does the app send our data anywhere?

No. It is a Forge app running on Atlassian infrastructure with no servers of
its own, and it declares no external permissions, so the platform blocks
outbound calls entirely. See the [Privacy Policy](privacy.md).

### Does "Suggest estimate" use AI?

No. It runs a JQL search over your own Jira for similar, already estimated work
items, takes the median and snaps it to the nearest card in the deck. No model
and no external service are involved.

---

## Troubleshooting

### The screen is blank or shows an old version after an update

Reload the page with **Ctrl+Shift+R** (**Cmd+Shift+R** on macOS) to clear the
cached app frame.

### A teammate's vote is not showing up

The room refreshes every few seconds, and polling pauses while the browser tab
is in the background. Switching back to the tab refreshes it immediately.

### The game says it is finished and nothing can be changed

A finished game is read-only by design — voting, revealing, the timer and
editing are all rejected. Its report and CSV export remain available. To
estimate the same work items again, clone the configuration into a new game
from the **⋯** menu.

---

Still stuck? See [Support](support.md).

---

[← Jira configuration](jira-configuration.md) · [Documentation home](index.md) ·
[Privacy Policy →](privacy.md)
