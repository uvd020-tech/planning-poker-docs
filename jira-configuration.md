---
title: Jira configuration — Planning Poker for Jira
---

# Jira configuration

Planning Poker needs no settings of its own — there is no admin screen to fill
in. What it does need is a Jira field it is allowed to write to. This page
covers that, and the Jira permissions the participants need.

[← Documentation home](index.md) · [Manage games](manage-games.md)

---

## How the app writes the estimate

When the facilitator saves a final estimate, the app writes it to Jira **as the
facilitator**, using their own Jira permissions, into the field chosen for the
game:

| Estimation field of the game | Jira target |
| --- | --- |
| **Story point estimate** | The Story Points field of the work item — the app looks for a field named *Story Points* or *Story point estimate* on your site |
| **Original estimate** | The original estimate of the work item's time tracking, in hours |

If the direct write fails because the field is not on the work item's edit
screen, the app makes one more attempt for Story Points: it writes through the
board the work item belongs to, into the estimation field configured on that
board. Only if both attempts fail does it report an error — and the message
names the cause.

---

## Making Story Points writable

### Company-managed projects

The Story Points field exists on the site, but it has to be on the screen used
by the work item type you estimate.

1. Go to **Project settings > Screens**. (A site admin can do the same from
   **Jira settings > Issues > Screens**.)
2. Open the screen scheme, and find the screen used by the work item type you
   estimate — usually the **Edit** screen of *Story*, *Task* or *Bug*.
3. Click the screen, and add the **Story Points** field with the
   **Select Field** search box.
4. If your project uses the new issue layout, open **Issue layout** and make
   sure **Story Points** is in a visible section, not under *Hidden when
   empty*.
5. Return to the game and click **Save estimate** again.

### Team-managed projects

Team-managed projects use the **Story point estimate** field, and it appears
only when estimation is switched on.

1. Go to **Project settings > Features**.
2. Turn on **Estimation**.
3. Under **Estimation**, select **Story points** as the unit.
4. Return to the game and click **Save estimate** again.

### Estimation on the board

The board fallback works when the board of the project has an estimation
field set:

1. Open the board, then **Board settings > Estimation**.
2. Set **Estimation Statistic** to **Story Points**.

This is what lets the app save an estimate even when the field is missing from
the edit screen.

---

## Making Original estimate writable

**Original estimate** is part of Jira's time tracking.

1. A site admin enables time tracking in **Jira settings > Issues > Issue
   features > Time tracking**.
2. In a company-managed project, add the **Time tracking** field to the edit
   screen of the work item types you estimate, exactly as described above for
   Story Points.
3. In a team-managed project, turn on **Project settings > Features >
   Estimation** and choose **Time** as the unit.

Values are written in hours, for example `5h`. Cards from the **Time
estimates** deck are written as they are (`2d`, `1w`).

---

## Permissions the team needs

The app never grants access to anything a user could not already open in Jira.
So participants need, in the projects being estimated:

| Permission | Why |
| --- | --- |
| **Browse projects** | To see the work items in the backlog and in the game room |
| **Edit issues** | For the facilitator only — to write the final estimate |

If a participant is missing **Browse projects**, they will join the game but
see nothing to estimate. If the facilitator is missing **Edit issues**, Jira
rejects the write and the app shows the error.

---

## What the app asks for at install

The app requests the Jira scopes it needs to read the backlog and write a
single field: read access to projects, work items, JQL and users, write access
to work items, board read access for the estimate fallback and the *Go to
Board* link, and Forge storage for the games themselves.

It declares no external permissions. That means the platform itself prevents it
from making any outbound network call — see the [Privacy Policy](privacy.md).

---

[← Manage games](manage-games.md) · [FAQ →](faq.md)
