---
title: Privacy Policy — Planning Poker for Jira
---

# Privacy Policy

**App:** Planning Poker for Jira Cloud

**Last updated:** 5 August 2026

[← Documentation home](index.md)

## Summary

Planning Poker is an [Atlassian Forge](https://developer.atlassian.com/platform/forge/)
app. It runs entirely on Atlassian's infrastructure. It has no servers of its
own, makes no outbound network calls, and sends no data to any third party.
Everything the app stores stays inside the Forge platform, within your
Atlassian instance's data boundary.

The app declares no external permissions (no egress), which is what makes this
guarantee verifiable rather than a promise.

## What the app stores

To run an estimation game, the app stores the following in Forge storage:

| Data | Why |
| --- | --- |
| Game settings — name, card deck, estimation field, privacy flag, options | To run the game as configured |
| Participants — Atlassian account IDs and display names of the facilitator, estimators and spectators, plus the facilitator's avatar URL | To show who is in the game and who may vote |
| Work items — Jira key and summary of the items being estimated | To show the backlog of the game |
| Votes — account ID, display name, the card chosen, the optional note, and the time the vote was cast | To reveal the votes and compute results |
| Timestamps — when a game was created, last changed and finished | To sort and filter the list of games |
| Final estimates | To show results and reports |
| The last voter list you used | To offer it when you create the next game |

The app does **not** store passwords, email addresses, payment details, or the
contents of Jira work items beyond the key and summary shown above.

## What the app reads from Jira

The app reads data from Jira only to display it to you, using your own Jira
permissions. It never shows a user anything they could not already see in Jira.
This includes:

- work item summaries, keys, statuses, priorities, assignees and existing
  estimates;
- the lists of projects, work item types and statuses used by the backlog
  filters;
- the results of user searches, when you pick a facilitator, estimators or
  spectators;
- the list of Jira field definitions, to locate the Story Points field on your
  site;
- the boards of a project, to build the **Go to Board** link and to save an
  estimate when the field is missing from the work item's screen.

## What the app writes to Jira

Only the final estimate agreed by your team, and only when the facilitator
clicks **Save estimate**. It is written to the field selected when the game was
created: the story point estimate field, or the original time estimate.

## Estimate suggestions

The **Suggest estimate** feature runs a JQL search over your own Jira site for
work items whose summary shares keywords with the current one and that already
carry a story point value. It takes the median of those values and snaps it to
the nearest card in the game's deck. The search runs against your Jira instance
with your own permissions. No AI or machine-learning service is involved, and
no data leaves Atlassian.

## Logs

When a Jira request fails, the app writes a diagnostic message to the Forge
logs operated by Atlassian: the work item key, the HTTP status and the error
text returned by Jira. Votes, notes and participant names are never logged.
Logs are retained by Atlassian under the Forge platform's own policy.

## Analytics and tracking

The app contains no analytics, no tracking pixels, no advertising and no
third-party scripts. It does not profile users and makes no automated decisions
about them.

## Data retention and deletion

- Deleting a game removes the game, its work item list and every vote cast in
  it. This cannot be undone.
- Uninstalling the app removes its stored data according to Atlassian's Forge
  storage lifecycle.
- To request deletion of data associated with your site, contact us at
  [uvd020@gmail.com](mailto:uvd020@gmail.com).

## Where data is stored

In Forge's key-value storage, operated by Atlassian. Hosting location and
residency follow the Atlassian Cloud infrastructure your site runs on. See the
[Atlassian Trust Center](https://www.atlassian.com/trust) for details.

## Your rights

Since the app processes data on behalf of your organisation, requests for
access, correction or deletion of personal data are best raised with your own
Jira administrator, who controls the site. We will assist administrators with
any such request — contact [uvd020@gmail.com](mailto:uvd020@gmail.com).

## Changes to this policy

Material changes will be published on this page with an updated date above.

## Contact

Vudia — [uvd020@gmail.com](mailto:uvd020@gmail.com)
