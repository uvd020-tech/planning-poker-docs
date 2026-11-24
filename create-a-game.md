---
title: Create a game — Planning Poker for Jira
description: "How to create a Planning Poker game in Jira: game settings, card deck, estimators, and choosing the work items to estimate by filter or JQL."
---

# Create a game

Creating a game takes two steps: the game settings, then the backlog of work
items to estimate. Both steps are shown as tabs at the top of the wizard, so
you can move back and forth before you create the game.

[← Documentation home](index.md) · [Game basics](game-basics.md)

---

## Requirements

Before your first game you need content to estimate:

- at least one Jira project;
- at least one work item in it.

**Check project access.** The app reads Jira with each participant's own
permissions. If a user cannot browse a project in Jira, its work items will not
appear for them in the game either. Review your project permissions before the
session so everyone can see what is being estimated.

---

## Start the wizard

Open **Apps → Planning Poker** (or the **Planning Poker** tab inside a project)
and click **+ New game**.

You can also start from an existing game: the **⋯** menu on the Games screen
offers **Clone game configuration**, which prefills step 1 with that game's
settings and takes you straight to step 2 to pick fresh work items. See
[Manage games](manage-games.md).

---

## Step 1 — New game

| Setting | Required | What it does |
| --- | --- | --- |
| **Name** | Yes | The name shown on the Games screen. Prefilled with a suggestion; make it recognisable so the list stays readable |
| **Private game** | No | Only the facilitator, the estimators and the spectators can see and open this game. Anyone else who follows the link gets a "not found" response |
| **Estimation field** | Yes | Where the final estimate is written: **Original estimate** (selected by default) or **Story point estimate**. A duplicated game keeps the field of the original game. See [Game basics](game-basics.md#estimation-fields) |
| **Card deck** | Yes | The cards the estimators vote with. The available decks depend on the estimation field |
| **Game mode** | Yes | **Live meeting** — everyone estimates together, one work item at a time. **Async (vote by a deadline)** — estimators vote on every work item in their own time, see [Async games](game-flow.md#async-games). Async is part of the paid plan. The mode can't be changed after the game is created |
| **Voting deadline** | Async only | When voting closes and the review starts. Prefilled with two days from now at 17:00. Must be at least 5 minutes and at most 60 days ahead. Can be changed while votes are still being collected |
| **Facilitator** | Yes | Runs the game. Defaults to you; type a name to hand it to someone else |
| **Estimators** | Yes | The people who vote. At least one. If you used a voter list before, a **Last time: …** line appears with a **Use these** button that fills it in again |
| **Spectators** | No | People who watch without voting |

Two behaviours are always on and have no setting:

- the facilitator can reveal the votes at any moment, without waiting for
  everyone;
- an estimator can change their card after the reveal.

When you edit a game that already has saved estimates, the **Card deck** and
**Estimation field** stay editable. A note above them shows how many estimates
are saved, and **Save** asks you to confirm the change. See
[Game basics](game-basics.md#changing-the-deck-or-field-later).

Click the **Add works to game backlog** tab to continue.

---

## Step 2 — Add works to game backlog

This step is a search over your Jira work items. Nothing is searched until you
narrow it down: with empty filters and an empty search box the app shows
*Select a space (or add a filter / type a search) to find work items.*

### Filters

| Control | Notes |
| --- | --- |
| **Work name or key** | Free-text search over the summary and the key. Opens one row above the list |
| **Spaces** | Multi-select over your Jira projects. Preselected with the current project when you opened the app from a project tab |
| **Work type** | Multi-select over work item types |
| **Status** | Multi-select over statuses |
| **Order by** | Rank, Newest, Recently updated, Priority, Key |
| **✕ Clear** | Resets every filter |
| **JQL** | Switches to raw JQL, see below |

The filter dropdowns open one at a time, and the search runs automatically a
moment after you stop typing.

### JQL mode

Turn on the **JQL** toggle to write the query yourself. The field is prefilled
with:

```
sprint in openSprints() ORDER BY rank
```

which returns the work items of your open sprints. Any JQL your Jira accepts
works here — the query runs with your own permissions. A syntax error is
reported back to you as Jira returned it.

### The result list

The list is a table:

| Column | Contents |
| --- | --- |
| **Work** | Key and summary. Both open the work item in Jira in a new tab |
| **Assignee** | Current assignee, or *Unassigned* |
| *Estimation field* | The current value of the field the game estimates into |
| **Priority** | Current priority |
| **Status** | Current status |

Tick the rows you want, or use **Select all** for the whole result. The count
of loaded items is shown above the table. Selected work items stay visible in a
separate block at the top, even when a new search no longer returns them, so
you always see what the game will contain.

A game holds up to **500** work items.

Click **Create game** when the backlog is ready.

---

## Duplicating an existing game

The **⋯** menu on the Games screen has **Clone game configuration**, which
offers two options:

| Option | Result |
| --- | --- |
| **Only general configuration** | Copies the settings into a new game and opens step 2, where you choose the work items |
| **Complete game (full duplicate)** | Copies the settings *and* the backlog into a new game |

Votes and saved estimates are never copied — a duplicated game always starts
unestimated.

---

[← Game basics](game-basics.md) · [Documentation home](index.md) ·
[Game flow →](game-flow.md)
