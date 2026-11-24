---
title: Game basics — Planning Poker for Jira
description: "Roles, card decks, estimation fields and the terms used in Planning Poker for Jira, to read before configuring your first game."
---

# Game basics

Read this before you configure your first game. It covers the roles, the card
decks, the estimation fields and the terms used throughout the interface.

[← Documentation home](index.md)

---

## Terminology

The app uses the current Atlassian vocabulary:

| Term in the app | Means |
| --- | --- |
| **Game** | One estimation session, with its own settings, backlog and participants |
| **Work item** | A Jira issue |
| **Space** | A Jira project |
| **Backlog** | The list of work items added to a game |

---

## Roles

Roles are assigned by the person who creates the game, in step 1 of the wizard.
Participants cannot change their own role.

| Role | Can vote | Can do |
| --- | --- | --- |
| **Facilitator** | Yes | Runs the game: selects the current work item, reveals the votes, starts the timer, saves the final estimate, edits the game, finishes and deletes it |
| **Estimator** | Yes | Picks a card, adds an optional note to the vote |
| **Spectator** | No | Watches the game; the card deck is not shown |

Notes:

- Every game has exactly one facilitator. By default it is the person creating
  the game, but you can hand the role to someone else in step 1.
- At least one estimator is required — the wizard will not let you continue
  without one.
- A user who is neither a facilitator, an estimator nor a spectator joins as an
  observer and cannot vote.
- In a **Private** game, users who were not added to any of the three lists
  cannot open the game at all, even with a direct link.

---

## Card decks

Choose the deck in step 1. It defines the cards the estimators see.

| Deck | Cards |
| --- | --- |
| **Fibonacci** | 1, 2, 3, 5, 8, 13, 21, 34, 55 |
| **Mod. Fibonacci** | 0, ½, 1, 2, 3, 5, 8, 13, 20, 40, 60, 100 |
| **T-shirt** | XXS, XS, S, M, L, XL, XXL |
| **Time estimates** | 1h, 2h, 4h, 6h, 1d, 2d, 3d, 1w |
| **Custom** | Your own values, separated by commas (at least 2) |

Every preset deck also ends with two special cards:

| Card | Meaning |
| --- | --- |
| **∞** | Too large to estimate |
| **☕** | I need a break |

Special cards behave like any other card in the room: they count towards
**Voted N/M**, they appear in the distribution, and they can even come out as
**Most Votes**. What they cannot do is reach Jira — they have no numeric value,
so choosing one as the final estimate keeps it in the game and report only, and
the room says so explicitly.

---

## Estimation fields

The **Estimation field** decides where the final estimate is written in Jira.

| Option | Written to |
| --- | --- |
| **Original estimate** (default) | Time tracking, as the original estimate, in hours |
| **Story point estimate** | The Story Points field of the work item |

A new game starts with **Original estimate** selected. A duplicated game keeps
the field of the game it was copied from.

### Which deck works with which field

Story Points is a numeric Jira field, so the app only offers numeric decks for
it. The wizard enforces this: switching the estimation field to **Story point
estimate** hides **T-shirt** and **Time estimates**, and resets the deck to
Fibonacci if one of them was selected.

| Estimation field | Selectable decks |
| --- | --- |
| Story point estimate | Fibonacci, Mod. Fibonacci, Custom |
| Original estimate | Fibonacci, Mod. Fibonacci, T-shirt, Time estimates, Custom |

### How values are converted

| Chosen card | Story point estimate | Original estimate |
| --- | --- | --- |
| A number (`5`) | `5` | `5h` |
| A time card (`2d`) | not offered | `2d`, as written |
| A T-shirt size | not offered | converted, then written in hours |
| **∞** or **☕** | nothing written | nothing written |

T-shirt sizes are converted on this scale before the write:

| XXS | XS | S | M | L | XL | XXL |
| --- | --- | --- | --- | --- | --- | --- |
| 0.5 | 1 | 2 | 3 | 5 | 8 | 13 |

After a successful save the room reports what actually reached Jira, for
example *wrote 3h to Jira (M → 3h)*.

### Changing the deck or field later

The facilitator can change the **Card deck** and the **Estimation field** of an
active game at any time with **Edit game**, even after estimates are saved.
When the game already has saved estimates:

- a note above the fields shows how many estimates are saved;
- **Save** asks you to confirm the change;
- estimates already written to Jira are not moved or converted — they stay in
  the previous field and scale; only new estimates use the new settings;
- if the deck changes, votes on work items without a saved estimate are
  cleared, so those items are voted on again with the new cards.

---

## Limits

| Limit | Value |
| --- | --- |
| Work items per game | 500 |
| Games listed on the Games screen | 500 most recent |
| Work item summary stored in a game | first 255 characters |

---

[← Documentation home](index.md) · [Create a game →](create-a-game.md)
