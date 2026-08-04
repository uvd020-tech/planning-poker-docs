---
title: Manage games — Planning Poker for Jira
---

# Manage games

The **Games** screen is the home of the app: every game you are allowed to see,
with search, filters, sorting and per-game actions.

[← Documentation home](index.md) · [Game flow](game-flow.md)

---

## The Games screen

**+ New game** sits under the title. Below it is the filter bar, and then the
table of games.

### Search and filters

| Control | What it does |
| --- | --- |
| **Search game by name** | Filters the list by game name as you type |
| **Facilitator** | Shows only games run by a particular person |
| **Status** | **Active** or **Finished** |
| **Access** | **Private** or **Public** |

A game counts as **Finished** when the facilitator closed it with **Save &
finish**, or when every work item in it has a saved estimate.

### The table

| Column | Contents |
| --- | --- |
| **Game** | Name — click it to enter the game |
| **Created** | When the game was created |
| **Updated** | Last activity: a reveal, a saved estimate, an edit |
| **Status** | Active or Finished |
| **Facilitator** | Name and avatar |
| **⋯** | The actions menu, see below |

**Created** and **Updated** are sortable: click the heading to sort, click it
again to flip between oldest and newest first.

Private games appear here only for their facilitator, estimators and
spectators. The screen lists the 500 most recent games.

---

## The ⋯ actions menu

| Action | Available to | What it does |
| --- | --- | --- |
| **Clone game configuration** | Anyone who sees the game | Reuse the game's settings. **Only general configuration** prefills the wizard and lets you pick fresh work items; **Complete game (full duplicate)** copies the backlog too. Votes and estimates are never copied |
| **Copy game URL** | Anyone who sees the game | Copies a direct link to the game room to the clipboard |
| **Export results (CSV)** | Anyone who sees the game | Downloads the game's results as a CSV file |
| **Open report** | Anyone who sees the game | Opens the report, see below |
| **Edit game** | The facilitator of an active game | Opens the game in the wizard — settings and backlog. See [Game flow](game-flow.md#editing-a-running-game) |
| **Delete game** | The facilitator | Deletes the game, its backlog and every vote in it, after a confirmation. This cannot be undone |

---

## Reports

**Open report** shows the outcome of one game:

- three counters at the top — how many work items the game holds, how many are
  estimated, and **SP total**, the sum of the numeric final estimates saved in
  that game;
- a table of **Work**, **Votes** (how many cards were cast) and **Estimate**
  (the final value, if one was saved).

Work item keys and summaries in the report open Jira in a new tab.

**SP total** counts only values that are numbers. Cards such as **∞**, **☕** or
T-shirt sizes are shown in the table but do not add to the total; if nothing
numeric was saved, the counter shows **—**.

### CSV export

The CSV button in the report — and **Export results (CSV)** in the **⋯** menu —
downloads the same data:

| Column | Contents |
| --- | --- |
| **Key** | Work item key |
| **Work item** | Summary |
| **Votes** | Number of cards cast |
| **Final estimate** | The saved value, if any |
| **Cards** | The individual cards that were cast |

The file is generated in your browser from data already on screen.

---

## Deleting a game

**Delete game** in the **⋯** menu removes the game, its work item list and
every vote cast in it. A confirmation dialog appears first.

Deleting a game does **not** touch Jira: estimates already written to work
items stay where they are.

---

[← Game flow](game-flow.md) · [Jira configuration →](jira-configuration.md)
