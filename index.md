---
title: Planning Poker for Jira — Documentation
---

# Planning Poker for Jira

Planning Poker for Jira Cloud is an estimation app for agile teams. The team
votes on a work item in secret, all cards are revealed at once, and the agreed
number is written into the Jira field you chose when the game was created.

The app is built on [Atlassian Forge](https://developer.atlassian.com/platform/forge/)
and runs entirely on Atlassian infrastructure. It has no servers of its own and
makes no outbound network calls — see the [Privacy Policy](privacy.md).

---

## Documentation

| Page | What it covers |
| --- | --- |
| [Game basics](game-basics.md) | Roles, card decks, estimation fields, terminology |
| [Create a game](create-a-game.md) | The two-step wizard: settings and backlog |
| [Game flow](game-flow.md) | Joining, voting, revealing, saving the estimate, finishing |
| [Manage games](manage-games.md) | Games list, actions menu, editing, reports, CSV export |
| [Jira configuration](jira-configuration.md) | Making the estimation field writable, permissions |
| [FAQ](faq.md) | Frequently asked questions |
| [Privacy Policy](privacy.md) | What is stored, read and written |
| [Security Policy](security.md) | Architecture, access control, vulnerability reporting |
| [Support](support.md) | How to reach us and what to include |

---

## Where to find the app

Once installed, Planning Poker appears in two places in Jira. Both open the
same **Games** screen:

| Entry point | Path |
| --- | --- |
| Jira top navigation | **Apps → Planning Poker** |
| Project (space) sidebar | The **Planning Poker** tab inside a project |

The difference is only a convenience: when you open the app from inside a
project, that project is preselected in the **Spaces** filter on the backlog
step. Games themselves are global — a game is not tied to one project, and its
backlog may contain work items from several projects at once.

Anyone with access to the app can create a game. No global or project-level
configuration is required before the first game.

---

## Quick start

1. Open **Apps → Planning Poker** and click **+ New game**.
2. **Step 1 — New game.** Enter a name, pick the **Estimation field** and the
   **Card deck**, choose the **Facilitator**, and add at least one
   **Estimator**. See [Create a game](create-a-game.md).
3. **Step 2 — Add works to game backlog.** Find the work items with the
   filters, the search box or a raw **JQL** query, tick them, and click
   **Create game**.
4. Invite the team. On the **Games** screen, open the **⋯** menu of your game
   and choose **Copy game URL**, then paste the link into your chat or call.
   The app has no built-in chat — agree on Zoom, Meet, Slack or a meeting room
   separately.
5. In the game room everyone picks a card. The facilitator clicks
   **Reveal votes**, the team discusses, then the facilitator picks the
   **Final estimate** and clicks **Save estimate**.
6. Repeat for every work item. Saving the estimate for the last one finishes
   the game. See [Game flow](game-flow.md).

---

## Before you start

- Create at least one Jira project and one work item to estimate.
- Make sure every intended participant can see those work items in Jira. The
  app reads and writes Jira with each user's own permissions, so a user who
  cannot browse a project will not see its work items in the game.
- Check that the estimation field you plan to use can actually be written to.
  This is the single most common source of errors — see
  [Jira configuration](jira-configuration.md).

---

Next: [Game basics →](game-basics.md)
