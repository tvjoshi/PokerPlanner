# PokerPlanner Release Plan

## Document Status

- **Product:** PokerPlanner
- **Document:** Release Plan
- **Version:** 0.1
- **Status:** Draft
- **Owner:** Product Manager
- **Primary Goal:** Define the release path from documentation through MVP, Version 1, and future product expansion.

---

## 1. Release Strategy

PokerPlanner should be released in small increments.

The goal is not to wait for a perfect application. The goal is to create visible working software quickly, then improve it through repeated feedback.

Each release should produce one of the following:

- A usable product improvement.
- A deployed demo.
- A learning milestone.
- A documented decision that reduces uncertainty.

---

## 2. Release Principles

1. **Ship thin vertical slices.**  
   Prefer working end-to-end behavior over isolated infrastructure work.

2. **Keep MVP small.**  
   MVP includes only the no-login planning poker workflow.

3. **Avoid accounts until the anonymous flow works.**  
   Authentication, dashboard, teams, and history are post-MVP features.

4. **Deploy early.**  
   The first deployed version does not need to be complete. It only needs to prove the deployment path.

5. **Commit frequently.**  
   Every meaningful change should end with a Git commit or a documented reason why not.

6. **Update `DEVLOG.md`.**  
   Each development session should record what was built, learned, blocked, and planned next.

---

## 3. Release Map

| Release | Name | Goal | Status |
|---|---|---|---|
| v0.0 | Project Foundation | Docs, repo structure, initial product direction | Planned |
| v0.1 | MVP | Complete no-login Planning Poker workflow | Planned |
| v0.2 | MVP Hardening | Responsive UX, accessibility, recovery, summary | Planned |
| v0.3 | Public Beta Readiness | Deployment polish, telemetry, tests, docs | Planned |
| v1.0 | Public Web Release | Stable production-quality first release | Planned |
| v1.x+ | Future Product | Accounts, teams, dashboard, history, integrations | Future |

---

# 4. v0.0 - Project Foundation

## Goal

Create the project foundation so development can begin from clear product direction and a clean repository structure.

## Scope

- Repository created.
- `README.md` exists.
- `DEVLOG.md` exists.
- `/docs` folder exists.
- Product documents added:
  - `PRD.md`
  - `MVP.md`
  - `UX_FLOW.md`
  - `BACKLOG.md`
  - `RELEASE_PLAN.md`
- Initial commit pushed to GitHub.

## Out of Scope

- Application code.
- Deployment pipeline.
- UI design system.
- Architecture decisions beyond what is necessary to start.

## Acceptance Criteria

```gherkin
Feature: Project foundation

Scenario: Product docs are added to repository
  Given the PokerPlanner repository exists
  When the docs are added under the docs folder
  Then PRD.md, MVP.md, UX_FLOW.md, BACKLOG.md, and RELEASE_PLAN.md are present

Scenario: Foundation work is committed
  Given the documentation files are present
  When the changes are committed and pushed
  Then GitHub contains the latest project foundation files
```

## Demo

Open GitHub and show the repository with `README.md`, `DEVLOG.md`, and the `/docs` folder.

## Learning Focus

- Repo hygiene.
- Documentation-first product workflow.
- Small commits.
- Clear handoff between Product Manager, Architect, DevOps, and Pair Programmer roles.

---

# 5. v0.1 - MVP

## Goal

Deliver the smallest useful version of PokerPlanner that supports a real Planning Poker session without login.

## Version 0.1 Scope

v0.1 includes:

1. Create session.
2. Optional session name.
3. Configurable room-level estimation deck at creation.
4. Unique shareable session link.
5. Join session with display name.
6. Join as voter or spectator.
7. Display participants and states.
8. Start round with optional round name.
9. Render estimation deck as vote buttons.
10. Select one vote per voter per round.
11. Hide vote values before reveal.
12. Show who has voted and who has not voted.
13. Reveal votes.
14. Display median after reveal.
15. Record final estimate.
16. Start re-vote.
17. Start next round.
18. End session.
19. Basic invalid link handling.

## v0.1 Out of Scope

v0.1 does not include:

- Authentication.
- User accounts.
- Dashboard.
- Session history.
- Team management.
- Team-level decks.
- Delegated ownership.
- Native mobile app.
- Work tracking integrations.
- Chat, comments, voice, or video.
- Paid tier.
- Donations.
- AI features.

## v0.1 Suggested Development Slices

### Slice 1 - Create Session Skeleton

**Outcome:** Scrum Master can create a session and land in an active room.

Included backlog stories:

- P0-001 Create a Session Without Login.
- P0-002 Configure Estimation Deck at Session Creation.

Demo:

```text
Create a session named Sprint 24 Planning with deck 1, 2, 3, 5, 8 and land in the active room.
```

---

### Slice 2 - Share and Join

**Outcome:** Another user can open the session link and join the room.

Included backlog stories:

- P0-003 Generate and Copy Shareable Session Link.
- P0-004 Join Session With Display Name.
- P0-005 Join as Voter or Spectator.

Demo:

```text
Create a room, copy the link, open it in another browser, join as voter, and join another browser as spectator.
```

---

### Slice 3 - Room State

**Outcome:** Room clearly shows Scrum Master, voters, spectators, and basic states.

Included backlog stories:

- P0-006 Display Active Room Participants and States.

Demo:

```text
Show one Scrum Master, two voters, and one spectator in the room with correct roles.
```

---

### Slice 4 - Start Round and Vote

**Outcome:** Scrum Master can start a round and voters can select one hidden vote.

Included backlog stories:

- P0-007 Start a Voting Round With Optional Round Name.
- P0-008 Render Deck Values as Vote Buttons.
- P0-009 Keep Votes Anonymous Before Reveal.

Demo:

```text
Start a round named US-1234, select vote buttons from two browsers, and verify vote values stay hidden before reveal.
```

---

### Slice 5 - Reveal and Median

**Outcome:** Scrum Master can reveal votes and see the median.

Included backlog stories:

- P0-010 Reveal Votes.
- P0-011 Display Median After Reveal.

Demo:

```text
Submit votes 2, 3, and 8, reveal them, and verify the median displays as 3.
```

---

### Slice 6 - Final Estimate and Multiple Rounds

**Outcome:** Scrum Master can record a final estimate and continue to the next item.

Included backlog stories:

- P0-012 Record Final Estimate.
- P0-013 Start Re-Vote for Current Round.
- P0-014 Start Next Round.

Demo:

```text
Reveal votes, record final estimate 5, start a re-vote, then start a second round with a clean voting state.
```

---

### Slice 7 - End Session and Error States

**Outcome:** Scrum Master can end the session and users see clear invalid-link behavior.

Included backlog stories:

- P0-015 End Session.
- P0-016 Handle Basic Invalid Links and Missing Sessions.

Demo:

```text
End the session and verify voting is disabled. Open a fake session URL and verify a clear not-found message appears.
```

## v0.1 Release Criteria

v0.1 is complete when:

- The full MVP flow works locally.
- The full MVP flow has been manually tested with at least two browser sessions.
- All P0 stories are complete or explicitly deferred with rationale.
- The app has a clean enough UI for a real planning session.
- The code is committed.
- The code is pushed to GitHub.
- The app is deployed when practical.
- `DEVLOG.md` is updated.

## v0.1 Manual Test Script

1. Open PokerPlanner home page.
2. Create a session named `Sprint 24 Planning`.
3. Use deck `1, 2, 3, 5, 8`.
4. Copy session link.
5. Open link in a second browser window.
6. Join as `Priya`, voter.
7. Open link in a third browser window.
8. Join as `Observer`, spectator.
9. Start round named `US-1234`.
10. Vote as Scrum Master if enabled, or leave Scrum Master as facilitator only if not enabled.
11. Vote as Priya.
12. Confirm vote values are hidden before reveal.
13. Reveal votes.
14. Confirm median displays.
15. Record final estimate.
16. Start a re-vote.
17. Confirm previous votes are cleared.
18. Start next round.
19. End the session.
20. Confirm voting and new rounds are disabled.

---

# 6. v0.2 - MVP Hardening

## Goal

Improve the MVP so it is more reliable, easier to use, and more comfortable on different devices.

## Scope

- Responsive web layout.
- Basic accessibility support.
- Basic browser refresh recovery.
- Simple ended-session summary.
- Better empty states and error messages.
- Improved visual hierarchy in the active room.
- Improved vote button spacing and readability.

## Out of Scope

- Authentication.
- Dashboard.
- Team management.
- Full historical session browsing.
- Native mobile app.

## Acceptance Criteria

```gherkin
Feature: MVP hardening

Scenario: Room works on narrow screen
  Given a user opens the room on a narrow browser width
  When they view the voting area
  Then vote buttons remain readable and tappable
  And the main workflow remains usable

Scenario: User refreshes browser
  Given a user is in an active session
  When the user refreshes the browser
  Then the app attempts to restore the user to the session
  And shows a clear recovery or rejoin path if restoration is not possible

Scenario: Ended session shows simple summary
  Given a session has ended
  When the Scrum Master views the ended state
  Then completed rounds and final estimates are visible
```

## Demo

Run the full v0.1 manual test script on desktop and narrow mobile browser width.

## Learning Focus

- Responsive UI.
- Accessibility basics.
- Browser refresh behavior.
- Error-state design.
- UX polish without scope expansion.

---

# 7. v0.3 - Public Beta Readiness

## Goal

Prepare the product for public demonstration and broader feedback.

## Scope

- Production deployment.
- Basic application telemetry.
- Basic automated tests.
- README local setup instructions.
- Contribution guidance.
- Issue templates or simple contribution notes.
- Basic privacy-conscious product metrics.
- Clear known limitations section.

## Out of Scope

- Full open-source governance.
- Authentication.
- Paid tier.
- Integrations.
- Native mobile app.

## Acceptance Criteria

```gherkin
Feature: Public beta readiness

Scenario: New developer runs app locally
  Given a developer has cloned the repository
  When they follow the README setup instructions
  Then they can run PokerPlanner locally

Scenario: Product owner views basic telemetry
  Given users create sessions and complete rounds
  When telemetry is reviewed
  Then session-created and round-completed events are visible
  And no unnecessary personal data is collected

Scenario: Automated tests run
  Given the repository has automated tests
  When tests are executed locally or in continuous integration
  Then the core MVP behavior is covered by passing tests
```

## Demo

Clone the repository, run the app locally from documentation, complete the MVP flow, and show the deployed version.

## Learning Focus

- Deployment.
- Telemetry.
- Testing.
- Documentation.
- Public portfolio readiness.

---

# 8. v1.0 - Public Web Release

## Goal

Release a stable, polished, production-quality first version of PokerPlanner as a public web application.

## Version 1 Scope

Version 1 includes:

- Complete v0.1 MVP workflow.
- v0.2 hardening improvements.
- v0.3 beta readiness improvements.
- Clean responsive web UI.
- Basic accessibility support.
- Basic telemetry.
- Basic automated tests.
- Deployed public web application.
- Public GitHub repository documentation.
- Clear product limitations.
- Open-source-friendly project structure.

## Version 1 Explicit Non-Goals

Version 1 does not include unless deliberately re-prioritized:

- User accounts.
- Authentication.
- Team dashboard.
- Team management.
- Team-level default decks.
- Delegated ownership.
- Long-term searchable history.
- Paid tier.
- Donation system.
- Jira integration.
- Azure DevOps integration.
- Slack integration.
- Microsoft Teams integration.
- Native mobile app.
- AI estimation suggestions.

## Version 1 Acceptance Criteria

```gherkin
Feature: Version 1 public release

Scenario: Scrum Master completes planning session
  Given the public web app is deployed
  When a Scrum Master creates a session and invites participants
  Then the team can join, vote, reveal, record final estimates, run multiple rounds, and end the session

Scenario: First-time participant joins without instructions
  Given a participant receives a session link
  When they open the link
  Then they can enter their name, join, and vote without reading documentation

Scenario: Product remains ad-free
  Given a user is using PokerPlanner
  When they create, join, vote, reveal, or end sessions
  Then no advertisements are displayed

Scenario: Repository is portfolio-ready
  Given a visitor opens the public GitHub repository
  When they review the README and docs folder
  Then they can understand the product vision, MVP scope, backlog, release plan, and local setup path
```

## Version 1 Release Criteria

Version 1 is ready when:

- The app is deployed publicly.
- The full Planning Poker workflow works in production.
- Manual test script passes.
- Core automated tests pass.
- Basic telemetry works.
- Documentation is current.
- Known limitations are documented.
- `DEVLOG.md` shows the project history and learning progress.
- The repository is presentable as a career portfolio project.

## Version 1 Demo Script

1. Open public PokerPlanner URL.
2. Create a session named `Sprint Planning Demo`.
3. Use deck `1, 2, 3, 5, 8, 13`.
4. Copy and share the session link.
5. Join as two voters in separate browser sessions.
6. Join as one spectator.
7. Start round named `US-1001`.
8. Cast hidden votes.
9. Reveal votes.
10. Show median.
11. Record final estimate.
12. Start a second round.
13. End the session.
14. Show session ended state or summary.
15. Open GitHub repo and show product docs.

---

# 9. Future Product Releases

Future releases should be driven by real use, not speculation.

## v1.1 Candidate - Lightweight Session Summary

Potential scope:

- Improved ended-session summary.
- Copy final estimates to clipboard.
- Optional export to CSV.
- Better read-only room view after session ends.

## v1.2 Candidate - Scrum Master Accounts

Potential scope:

- Scrum Master sign-in.
- Sessions associated with Scrum Master account.
- Participants still join without account.
- Basic account settings.

## v1.3 Candidate - Dashboard and History

Potential scope:

- Previous session dashboard.
- Completed session history.
- Read-only historical room view.
- Search or filter by session name.

## v1.4 Candidate - Teams

Potential scope:

- Create team.
- Select existing team when creating room.
- Organize rooms by team on dashboard.
- Team-level default deck.

## v1.5 Candidate - Delegated Ownership

Potential scope:

- Add one or more room co-owners.
- Allow delegated owners to start rounds, reveal votes, record final estimates, and end sessions.
- Clear owner role display.

## v2.0 Candidate - Integrations

Potential scope:

- Jira integration.
- Azure DevOps integration.
- Slack integration.
- Microsoft Teams integration.
- Import backlog items.
- Sync final estimates.

---

# 10. Future Ideas Parking Lot

These are not committed releases.

## Adds Value

- Authentication.
- Scrum Master account.
- Dashboard.
- Saved session history.
- Team management.
- Select existing team while creating room.
- Add new team while creating room.
- Organize rooms by team on dashboard.
- Team-level default decks.
- Delegated ownership.
- Read-only historical session view.
- Session summary page.
- Copy final estimates to clipboard.
- CSV export.
- PDF export.

## Nice to Have

- Paid tier.
- Donation link.
- About page.
- Public roadmap.
- Multiple deck presets.
- Advanced custom deck management.
- Jira integration.
- Azure DevOps integration.
- Slack integration.
- Microsoft Teams integration.
- AI-assisted estimation insights.
- Analytics dashboard.
- Native mobile app.
- Organization accounts.
- Role-based permissions.
- Public templates.

---

# 11. Release Governance

Before starting a release, answer:

1. What is the smallest valuable next step?
2. What visible demo will this release enable?
3. What is explicitly out of scope?
4. What will be committed at the end of the session?
5. What will be recorded in `DEVLOG.md`?

Before accepting a feature into a release, ask:

> Does this feature make the core Planning Poker workflow faster, clearer, or more reliable?

If the answer is no, park it.

---

# 12. Recommended Next Action

The next action after adding these product documents is to hand the documents to the Architect role for a technical review.

The Architect should answer:

1. What is the simplest architecture that supports v0.1?
2. What can be fake, in-memory, or deferred for the first vertical slice?
3. What technical choices would create unnecessary complexity?
4. What is the smallest buildable first slice?

After that, the DevOps role should define the simplest local-run, commit, push, and deployment path.
