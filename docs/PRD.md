# PokerPlanner Product Requirements Document

## Document Status

- **Product:** PokerPlanner
- **Document:** Product Requirements Document
- **Version:** 0.2
- **Status:** Draft
- **Owner:** Product Manager
- **Primary Goal:** Define the product vision, MVP scope, product principles, and functional requirements for the first usable version of PokerPlanner.

---

## 1. Product Vision

PokerPlanner is a minimal, clean, fast, and intuitive Planning Poker application for Agile teams.

The product allows a Scrum Master to create a planning session, share a unique link with team members, collect anonymous votes, reveal votes at the right time, display the median as informational guidance, and record the final estimate after team discussion.

PokerPlanner should feel lightweight enough to use during a real sprint planning or backlog refinement meeting without training, onboarding, advertisements, or unnecessary configuration.

The long-term vision is to make PokerPlanner a polished, open-source-friendly project that demonstrates modern AI-assisted software development while becoming a useful product in its own right.

---

## 2. Problem Statement

Agile teams often need a quick way to estimate user stories collaboratively.

Many existing Planning Poker tools either:

- Require accounts or sign-in before use.
- Include distracting advertisements.
- Add unnecessary configuration.
- Feel visually cluttered.
- Create too much friction for a simple estimation session.
- Are not ideal as a personal learning and portfolio project.

PokerPlanner solves this by focusing on the essential planning workflow:

1. Create a session.
2. Share a link.
3. Join by name.
4. Vote anonymously.
5. Reveal votes.
6. Discuss offline.
7. Record a final estimate.
8. Repeat for the next round.

---

## 3. Product Goals

### 3.1 MVP Goals

The MVP must allow a Scrum Master and team members to complete a real Planning Poker session without authentication.

The MVP supports:

- Anonymous voting.
- Shareable session links.
- Reveal votes.
- Median calculation.
- Re-voting.
- Multiple rounds in one session.
- Room-level configurable estimation deck at session creation.
- Final estimate selection by Scrum Master after discussion.

### 3.2 Learning Goals

PokerPlanner is also a learning vehicle for modern AI-assisted software development.

The project should help practice:

- Small vertical slices.
- Product-first thinking.
- AI-assisted coding workflows.
- Real-time or near-real-time user interaction.
- Simple frontend state management.
- Clean backend design.
- Deployment.
- Testing.
- Documentation.
- Git-based development habits.

### 3.3 Portfolio Goals

PokerPlanner should be suitable as a public GitHub portfolio project.

The codebase and documentation should make it clear that the project values:

- Simple architecture.
- Clean product thinking.
- Maintainable implementation.
- Iterative delivery.
- Open-source-friendly contribution patterns.

---

## 4. Product Principles

### 4.1 Zero-to-One in Under 60 Seconds

A Scrum Master should be able to create a session and share a planning link in under one minute.

### 4.2 No Training Required

A first-time participant should be able to join a session and vote without reading instructions.

### 4.3 Minimize Clicks

Every workflow should avoid unnecessary screens, prompts, confirmations, and setup steps.

### 4.4 No Advertisements

PokerPlanner should never display advertisements.

### 4.5 Discussion Happens Outside the App

The app facilitates estimation. It does not replace team conversation.

The product intentionally does not include:

- Chat.
- Comments.
- Audio.
- Video.
- Threaded discussions.

### 4.6 Fast Over Feature-Rich

A feature should only be added when it clearly makes planning faster, easier, or more useful.

### 4.7 Clean and Distraction-Free

The interface should remain simple, focused, and visually calm as features are added.

### 4.8 Open-Source Friendly

The project should be easy to understand, run locally, contribute to, and extend.

---

## 5. Target Users

### 5.1 Primary Persona: Scrum Master

The Scrum Master creates the planning session, shares the link, starts each round, reveals votes, facilitates offline discussion, records the final estimate, and ends the session.

#### Needs

- Create a session quickly.
- Share a link easily.
- See who has joined.
- See who has voted.
- Reveal votes at the right time.
- Record the final estimate.
- Move quickly to the next round.

#### Pain Points

- Planning tools that require too much setup.
- Teams wasting time signing in.
- Confusing voting states.
- Difficulty knowing who has not voted yet.
- Tools that distract from the meeting.

### 5.2 Primary Persona: Participant

A participant joins the session using a link, enters a display name, votes privately, waits for reveal, and participates in offline discussion.

#### Needs

- Join with minimal friction.
- Understand what to do immediately.
- Vote privately.
- Change vote before reveal if needed.
- See revealed votes after the Scrum Master reveals them.

#### Pain Points

- Account creation.
- Confusing screens.
- Not knowing whether their vote was submitted.
- Seeing other votes too early.
- Mobile-unfriendly UI.

### 5.3 Secondary Persona: Spectator

A spectator joins a session to observe but does not vote.

Examples:

- Manager.
- Stakeholder.
- New team member.
- Observer.
- Guest.

#### Needs

- Join the session.
- Watch the estimation process.
- Avoid being counted as a voter.
- Avoid blocking the round from being completed.

---

## 6. Core User Journey

### 6.1 Session Creation

1. Scrum Master opens PokerPlanner.
2. Scrum Master creates a new planning session.
3. Scrum Master may optionally enter a single free-text **Session name**.
4. Placeholder examples for the session name may include:
   - `Sprint 24 Planning`
   - `Platform Team`
   - `July Refinement`
5. These examples are placeholders only. The MVP has one session name field.
6. Scrum Master reviews or edits the estimation deck for the session.
7. System creates a unique session link.
8. Scrum Master copies and shares the link with the team.

### 6.2 Joining a Session

1. Participant opens the shared link.
2. Participant enters display name.
3. Participant chooses whether to join as:
   - Voter.
   - Spectator.
4. Default join mode is voter.
5. Participant lands in the planning room.
6. Participant appears in the participant list or table.

### 6.3 Starting a Round

1. Scrum Master clicks **Start Round**.
2. Scrum Master may optionally enter a single free-text **Round name**.
3. Placeholder examples for the round name may include:
   - `US-1234`
   - `Login flow`
   - `Payment retry story`
4. These examples are placeholders only. The MVP has one round name field.
5. System starts a new voting round.
6. Participants see the available estimation deck as vote buttons.

### 6.4 Voting

1. Each voter selects one story point value by clicking one vote button.
2. A voter may select only one vote value per round.
3. Selecting a different value before reveal replaces the previous selection.
4. Votes remain hidden from other users until reveal.
5. System clearly shows:
   - Who has voted.
   - Who has not voted.
   - Who is observing only.
6. Voters may change their own vote before reveal.
7. Spectators cannot vote.

### 6.5 Revealing Votes

1. Scrum Master reveals the votes.
2. System displays each participant's vote.
3. System calculates and displays the median.
4. Team discusses the results offline.

### 6.6 Recording Final Estimate

1. Scrum Master selects or enters the final estimate based on team consensus.
2. System records the final estimate for the round.
3. Scrum Master can start another round.

### 6.7 Ending the Session

1. Scrum Master ends the session.
2. Session becomes closed.
3. Participants can no longer vote.
4. Future versions may allow read-only access to completed session history.

---

## 7. MVP Scope

The MVP is the smallest version that enables a real team to run a complete Planning Poker session.

### 7.1 MVP Included Features

The MVP includes:

1. Create planning session.
2. Optional single session name field.
3. Generate unique shareable session link.
4. Join session with display name.
5. Join as voter or spectator.
6. Session-level editable estimation deck at session creation.
7. Start a voting round.
8. Optional single round name field.
9. Anonymous voting before reveal.
10. Estimation values displayed as vote buttons.
11. One selected vote per voter per round.
12. Visible voting status before reveal.
13. Reveal all votes simultaneously.
14. Median calculation after reveal.
15. Scrum Master records final estimate.
16. Re-vote support.
17. Multiple rounds in one session.
18. End session.

### 7.2 MVP Excluded Features

The MVP does not include:

- User accounts.
- Authentication.
- Dashboard.
- Saved historical session list.
- Team management.
- Team-level default decks.
- Delegated room ownership.
- Persistent user profiles.
- Paid tier.
- Donations.
- Native mobile app.
- Native mobile push notifications.
- Chat.
- Comments.
- Voice.
- Video.
- Jira integration.
- Azure DevOps integration.
- Slack integration.
- Microsoft Teams integration.
- AI-generated estimation suggestions.
- Advanced analytics.
- Export to CSV.
- Export to PDF.
- Admin console.

---

## 8. Version 1 Scope

Version 1 represents a polished, production-quality first release.

Version 1 should include everything in the MVP plus selected improvements needed to make the product reliable and pleasant for broader public use.

### 8.1 Version 1 Must Include

- Stable MVP workflow.
- Clean responsive web interface.
- Basic accessibility support.
- Clear session states.
- Clear participant states.
- Clear error handling.
- Production deployment.
- Basic application telemetry.
- Basic automated tests.
- Public GitHub repository documentation.
- Clear local setup instructions.
- Basic contribution guidelines.

### 8.2 Version 1 May Include

These are candidates for Version 1 only if they do not slow the MVP too much:

- Read-only session summary after session ends.
- Copyable final estimates summary.
- Improved visual table layout.
- Basic session expiration.
- Better empty states.
- Basic session recovery on browser refresh.

### 8.3 Version 1 Does Not Include

Unless explicitly re-prioritized, Version 1 still does not include:

- Full authentication.
- Full dashboard.
- Team management.
- Paid plans.
- Deep integrations.
- Native mobile apps.
- AI features.

---

## 9. Functional Requirements

### 9.1 Session Creation

The system shall allow a Scrum Master to create a new planning session without creating an account.

The system shall generate a unique link for each session.

The system shall allow the Scrum Master to optionally enter one free-text session name.

The session name field may use placeholder text with examples such as `Sprint 24 Planning`, `Platform Team`, or `July Refinement`.

The system shall not include separate fields for room name, sprint name, team name, or session label in the MVP.

The system shall allow the Scrum Master to configure the estimation deck before the session is created.

The system shall use a default estimation deck if the Scrum Master does not modify it.

Recommended default deck:

```text
0, 1/2, 1, 2, 3, 5, 8, 13, 20, 40, 100, ?, coffee
```

The system shall preserve the deck order entered by the Scrum Master.

The system shall require at least one estimation value in the deck.

The system shall not require team setup, account setup, or workspace setup for the MVP.

### 9.2 Session Ownership

The user who creates the session is the session owner and Scrum Master.

The session owner shall be able to:

- Start a round.
- Reveal votes.
- Record the final estimate.
- Start a re-vote.
- Start the next round.
- End the session.

Participants shall not be able to perform Scrum Master actions in the MVP.

Delegated ownership is not part of the MVP.

### 9.3 Joining a Session

The system shall allow a user to join a session using a unique session link.

The system shall ask the user for a display name before entering the session.

The system shall allow the user to join as either:

- Voter.
- Spectator.

The default join mode shall be voter.

The system shall display joined users in the session.

The system shall clearly distinguish voters from spectators.

### 9.4 Round Creation

The system shall allow the Scrum Master to start a new round.

The system shall allow the Scrum Master to optionally enter one free-text round name.

The round name field may use placeholder text with examples such as `US-1234`, `Login flow`, or `Payment retry story`.

The system shall not include separate fields for user story number, feature name, or short story label in the MVP.

### 9.5 Voting

The system shall render each estimation deck value as a selectable vote button.

Each voter may select only one vote value per round.

If a voter selects a different vote value before reveal, the new selection replaces the previous selection.

The system shall hide selected vote values until the Scrum Master reveals votes.

The system shall show whether each voter has voted.

The system shall show whether each voter has not yet voted.

The system shall prevent spectators from voting.

The system shall prevent voters from changing their vote after reveal unless the Scrum Master starts a re-vote.

### 9.6 Reveal

The system shall allow only the Scrum Master to reveal votes.

The system shall reveal all submitted votes at the same time.

The system shall display each voter's selected value after reveal.

The system shall continue to identify voters who did not vote.

The system shall calculate and display the median after reveal.

The system shall not treat spectator users as voters.

### 9.7 Median Calculation

The system shall calculate the median of numeric submitted votes.

The system shall exclude non-numeric values from the median calculation.

Examples of non-numeric values:

- `?`
- `coffee`
- Any future symbolic deck value.

If the submitted votes contain no numeric values, the system shall display that the median is unavailable.

The system shall display the median as informational only.

The Scrum Master shall still record the final estimate manually based on team consensus.

The calculation logic should be isolated enough that another algorithm can replace or supplement median calculation later.

### 9.8 Final Estimate

The system shall allow the Scrum Master to record a final estimate after votes are revealed.

The final estimate represents the team's consensus, not an automatic calculation.

The system shall associate the final estimate with the current round.

### 9.9 Re-Vote

The system shall allow the Scrum Master to start a re-vote for the current round.

A re-vote shall clear previous submitted votes for the current round.

A re-vote shall preserve the round name.

A re-vote shall use the same estimation deck.

The system shall make it clear when the session is in a new voting state.

### 9.10 Multiple Rounds

The system shall allow the Scrum Master to start another round after recording the final estimate.

Each round may have its own optional round name.

Each round shall have its own votes, reveal state, median, and final estimate.

The session shall continue until explicitly ended by the Scrum Master.

### 9.11 End Session

The system shall allow the Scrum Master to end the session.

After a session is ended:

- No new rounds can be started.
- No new votes can be submitted.
- The session should clearly show that it has ended.

Read-only history after session end is not required for the MVP unless it becomes a low-effort extension.

---

## 10. Non-Functional Requirements

### 10.1 Usability

The app should be usable by a first-time participant without training.

The main session screen should clearly show:

- Session name.
- Current round name.
- Participants.
- Voting status.
- Available deck values as vote buttons.
- Reveal state.
- Median after reveal.
- Final estimate after recorded.

### 10.2 Performance

The app should feel responsive during a live planning session.

Common actions should complete quickly:

- Creating a session.
- Joining a session.
- Submitting a vote.
- Revealing votes.
- Starting a new round.

### 10.3 Reliability

The MVP should handle common user behavior gracefully:

- Refreshing the browser.
- Joining late.
- Changing a vote before reveal.
- Spectator joining during a round.
- Participant joining during a round.
- Participant not voting.

### 10.4 Accessibility

The app should follow basic accessibility expectations:

- Keyboard-accessible controls.
- Sufficient color contrast.
- Clear labels.
- Visual status that does not rely only on color.
- Readable text sizes.

### 10.5 Privacy

The MVP should avoid collecting unnecessary personal information.

The MVP shall not require:

- Email address.
- Password.
- Company name.
- Personal profile.
- Payment information.

Display names are entered only to identify participants during a session.

### 10.6 Security

The MVP should treat session links as unguessable enough for casual use.

The MVP does not require enterprise-grade access control.

Users with the session link may join the session.

Future versions may add stronger controls through authentication and team management.

### 10.7 Maintainability

The codebase should remain simple enough for a solo developer to understand and maintain.

The product should avoid enterprise patterns until there is clear need.

The estimation algorithm should be separable from the session workflow so it can be changed later.

### 10.8 Open Source Readiness

The repository should eventually include:

- Clear README.
- Local setup instructions.
- Contribution guidelines.
- Developer notes.
- License.
- Issue templates.
- Pull request guidance.

Not all open-source polish is required for the MVP.

---

## 11. UX Requirements

### 11.1 Overall UX Direction

The interface should be:

- Minimal.
- Clean.
- Sleek.
- Fast.
- Calm.
- Intuitive.
- Distraction-free.

### 11.2 Session Layout

The final product vision includes a visual table layout where participants appear seated around a table with their names clearly displayed.

For the MVP, the table layout may be simplified if needed.

The MVP must still clearly show:

- Participant names.
- Voting status.
- Spectator status.
- Revealed votes.

### 11.3 Voting Button Layout

The estimation deck shall be displayed as a row or grid of buttons.

Each button represents one estimation value.

A voter can have only one active selected vote per round.

The selected button should be visually distinct to the voter.

Other participants should not see the selected value before reveal.

### 11.4 Voting States

Before reveal, the system should distinguish:

- Voter has not voted.
- Voter has voted.
- User is a spectator.
- Scrum Master controls are available only to session owner.

After reveal, the system should distinguish:

- Submitted vote value.
- Missing vote.
- Spectator.

### 11.5 Scrum Master Controls

Scrum Master controls should be prominent but not distracting.

Core actions:

- Start round.
- Reveal votes.
- Start re-vote.
- Record final estimate.
- Start next round.
- End session.

### 11.6 Participant Controls

Participant controls should be limited to what they need:

- Enter display name.
- Join as voter or spectator.
- Select vote.
- Change vote before reveal.

---

## 12. Data Concepts

This section defines product-level data concepts, not implementation details.

### 12.1 Session

A session represents one Planning Poker room.

A session may include:

- Unique session identifier.
- Optional session name.
- Created date/time.
- Session owner.
- Estimation deck.
- Participants.
- Rounds.
- Session status.

### 12.2 Participant

A participant represents a person who joined the session.

A participant may include:

- Display name.
- Role:
  - Scrum Master.
  - Voter.
  - Spectator.
- Current presence status.
- Voting status for current round.

### 12.3 Deck

A deck is an ordered list of estimation values.

In the MVP:

- A deck belongs to a session.
- The Scrum Master can edit the deck during session creation.
- The deck is fixed after session creation.
- Deck values are shown as vote buttons during a round.

In future versions:

- A deck may belong to a team.
- A user may save preferred decks.
- Preset decks may be available.

### 12.4 Round

A round represents one estimation attempt for one story, feature, or backlog item.

A round may include:

- Optional round name.
- Votes.
- Reveal status.
- Median.
- Final estimate.
- Re-vote history, if supported later.

### 12.5 Vote

A vote represents a participant's selected estimate value for a round.

Votes are hidden until reveal.

A participant may select one vote per round.

A participant may change their vote before reveal.

### 12.6 Final Estimate

A final estimate is the Scrum Master's recorded result after team discussion.

It is not automatically determined by the app.

---

## 13. Success Metrics

### 13.1 MVP Success Metrics

The MVP is successful if:

- A Scrum Master can create and share a session without help.
- Participants can join and vote without help.
- Deck values are displayed as buttons.
- Each voter can select exactly one vote per round.
- Votes remain hidden until reveal.
- The Scrum Master can reveal votes.
- The system displays the median.
- The Scrum Master can record a final estimate.
- The team can estimate multiple rounds in one session.
- The app can be deployed and used by a real small team.

### 13.2 Product Quality Metrics

Useful future metrics may include:

- Time to create and share a session.
- Time for first participant to join.
- Percentage of sessions with more than one round.
- Percentage of rounds completed with final estimate.
- Number of abandoned sessions.
- Number of user-reported confusion points.

### 13.3 Learning Success Metrics

The project is successful as a learning exercise if:

- Features are delivered in small increments.
- Each meaningful feature is committed to Git.
- The app is deployed frequently.
- `DEVLOG.md` is updated after development sessions.
- AI-generated code is reviewed and understood.
- The project produces reusable development habits.

---

## 14. Risks

### 14.1 Scope Creep

Risk:

The app may expand into accounts, teams, dashboards, integrations, analytics, and paid features before the core workflow is complete.

Mitigation:

Keep the MVP limited to the agreed must-have features.

### 14.2 Real-Time Complexity

Risk:

Live session updates may introduce technical complexity.

Mitigation:

Start with the simplest reliable real-time or refresh-based approach that supports the MVP experience.

### 14.3 Custom Deck Overbuilding

Risk:

Deck customization could become a full settings feature.

Mitigation:

For the MVP, use a simple session-level editable list at session creation.

### 14.4 Authentication Distraction

Risk:

Adding accounts too early could slow delivery.

Mitigation:

No authentication in the MVP.

### 14.5 UX Overdesign

Risk:

The visual table layout could consume too much time before the core workflow works.

Mitigation:

Prioritize clear workflow first. Improve table presentation after the core session flow works.

### 14.6 Persistence Ambiguity

Risk:

Without accounts, long-term session history may be hard to support cleanly.

Mitigation:

Do not include dashboard or long-term history in the MVP.

---

## 15. Assumptions

- The Scrum Master creates the session and owns it.
- The MVP does not require authentication.
- Anyone with the session link can join.
- Display names are sufficient for identifying participants.
- Participants are trusted not to impersonate each other in the MVP.
- Discussion happens outside the app.
- Median is informational only.
- Final estimate is manually recorded by the Scrum Master.
- Custom deck values are configured at session creation.
- Deck values are displayed as buttons.
- Each voter selects one value per round.
- Team-level configuration comes later.
- Session history and dashboard come later.

---

## 16. Open Questions

These questions do not block the MVP definition but should be resolved during design or implementation.

1. Should the final estimate be limited to deck values, or allow free text?
2. Should the Scrum Master be allowed to vote?
3. Should users be able to rejoin with the same display name after browser refresh?
4. Should session links expire automatically?
5. Should a participant who joins mid-round be allowed to vote in that round?
6. Should the session show disconnected users?
7. Should the MVP store completed round results only during the active browser session or persist them server-side?
8. Should the session URL contain a separate owner token for Scrum Master controls?

---

## 17. Future Ideas Parking Lot

These are explicitly outside the MVP.

### 17.1 Adds Value

- Authentication.
- Scrum Master sign-in.
- Dashboard.
- Saved session history.
- Team management.
- Select existing team when creating session.
- Add new team when creating session.
- Organize sessions by team on dashboard.
- Team-level default estimation decks.
- Delegated session ownership.
- Read-only historical session view.
- Mobile-friendly enhancements.
- Session summary page.
- Export session results.
- Copy final estimates to clipboard.

### 17.2 Nice to Have

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

## 18. Glossary

### Planning Poker

An Agile estimation technique where team members privately vote on the size or complexity of a backlog item, then reveal votes together and discuss differences.

### Scrum Master

The person facilitating the planning session.

### Participant

A user who joins a planning session. Participants may be voters or spectators.

### Voter

A participant who can submit an estimate.

### Spectator

A participant who can observe the session but cannot vote.

### Session

A Planning Poker room created by the Scrum Master.

### Round

One estimation cycle for a story, feature, or backlog item.

### Deck

The list of selectable estimation values.

### Vote Button

A clickable UI button representing one estimation deck value.

### Estimate

A selected story point value or other sizing value.

### Median

The middle numeric value after submitted numeric votes are sorted. If there is an even number of numeric votes, the median is calculated using the two middle values.

### Final Estimate

The estimate recorded by the Scrum Master after team discussion and consensus.

### MVP

Minimum Viable Product. The smallest useful version of the product that can support a real Planning Poker session.

---

## 19. Product Decision Summary

The MVP will focus on the core Planning Poker workflow only.

The product will not include authentication, dashboards, teams, session history, or integrations in the MVP.

The session has one optional session name field.

Each round has one optional round name field.

The estimation deck will be editable at session creation because different teams use different estimation systems.

Deck values will be displayed as vote buttons.

Each voter may select exactly one vote value per round.

The median will be displayed as informational guidance only.

The Scrum Master will record the final estimate manually based on team consensus.

PokerPlanner should remain minimal, clean, fast, ad-free, and easy to use.
