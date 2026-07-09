# PokerPlanner Initial Product Backlog

## Document Status

- **Product:** PokerPlanner
- **Document:** Initial Product Backlog
- **Version:** 0.1
- **Status:** Draft
- **Owner:** Product Manager
- **Primary Goal:** Define the initial prioritized backlog for the MVP and near-term releases.

---

## 1. Backlog Principles

This backlog is intentionally small and delivery-focused.

PokerPlanner should be built in vertical slices that result in visible working software. Each story should be small enough to build, manually test, commit, and document in a development session whenever practical.

The backlog prioritizes:

1. A usable Planning Poker workflow.
2. Minimal friction for Scrum Masters and participants.
3. Clean product behavior before visual polish.
4. Learning modern AI-assisted development through small increments.
5. Avoiding accounts, dashboards, teams, integrations, and paid features until after the MVP is working.

---

## 2. Priority Definitions

| Priority | Meaning |
|---|---|
| **P0 - MVP Must Have** | Required for the first usable MVP. Do not ship MVP without it. |
| **P1 - Version 1 Polish** | Needed for a reliable and pleasant public web release, but not required for the first internal MVP demo. |
| **P2 - Adds Value** | Useful after the core workflow is proven. Explicitly not part of MVP. |
| **P3 - Nice to Have** | Optional future improvements. Do not prioritize until the product has real usage. |

---

## 3. Epic Overview

| Epic | Priority | Description |
|---|---:|---|
| E1. Session Creation | P0 | Scrum Master creates a session without login. |
| E2. Joining | P0 | Participants join by link with a display name and role. |
| E3. Room Experience | P0 | Users see the active planning room, participants, and states. |
| E4. Voting | P0 | Voters select one hidden vote from the estimation deck. |
| E5. Reveal and Results | P0 | Scrum Master reveals votes and sees the median. |
| E6. Final Estimate and Rounds | P0 | Scrum Master records final estimate, re-votes, and runs multiple rounds. |
| E7. Session End | P0 | Scrum Master ends the session. |
| E8. UX, Reliability, and Accessibility | P1 | Improve quality after the core flow works. |
| E9. Deployment and Open Source Readiness | P1 | Make the app demonstrable, deployable, and portfolio-ready. |
| E10. Accounts, Teams, History, and Dashboard | P2 | Future value after the no-login MVP is validated. |
| E11. Integrations and Monetization | P3 | Optional future ideas. |

---

# 4. P0 - MVP Must-Have Stories

## P0-001 - Create a Session Without Login

**Epic:** E1. Session Creation  
**Priority:** P0 - MVP Must Have  
**Dependencies:** None

### User Story

As a Scrum Master, I want to create a Planning Poker session without signing in so that I can start estimating with my team quickly.

### Acceptance Criteria

```gherkin
Feature: Create session without login

Scenario: Scrum Master creates a session with no account
  Given I am on the PokerPlanner home page
  When I create a new session without signing in
  Then a new session is created
  And I become the Scrum Master for that session
  And I am taken to the active session room

Scenario: Scrum Master creates a session with an optional session name
  Given I am on the PokerPlanner home page
  When I enter "Sprint 24 Planning" in the session name field
  And I create a new session
  Then the active session room displays "Sprint 24 Planning" as the session name

Scenario: Scrum Master creates a session without a session name
  Given I am on the PokerPlanner home page
  When I leave the session name field blank
  And I create a new session
  Then a new session is created
  And the room displays a clear fallback title
```

### Notes

- There is only one optional free-text session name field.
- Placeholder examples may include sprint name, team name, or refinement name, but these are not separate fields.

### Learning Objective

Practice building the first thin vertical slice from home page to active room.

### Demo Scenario

Create a session named `Sprint 24 Planning` and land in the active room as Scrum Master.

---

## P0-002 - Configure Estimation Deck at Session Creation

**Epic:** E1. Session Creation  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-001

### User Story

As a Scrum Master, I want to configure the estimation deck when creating a session so that the voting options match my team's estimation style.

### Acceptance Criteria

```gherkin
Feature: Configure estimation deck

Scenario: Scrum Master uses the default deck
  Given I am creating a new session
  When I leave the default estimation deck unchanged
  And I create the session
  Then the session uses the default deck values
  And the deck values appear in the same order in the voting area

Scenario: Scrum Master edits the deck before creating the session
  Given I am creating a new session
  When I change the estimation deck to "1, 2, 3, 5, 8"
  And I create the session
  Then the session uses "1, 2, 3, 5, 8" as the deck
  And the voting area shows one button for each deck value

Scenario: Scrum Master attempts to create a session with an empty deck
  Given I am creating a new session
  When I remove all estimation deck values
  And I try to create the session
  Then the session is not created
  And I see a clear message that at least one deck value is required
```

### Notes

- The deck can be implemented as a simple comma-separated field or an equivalent simple UI.
- Values are fixed after session creation for the MVP.
- Team-level decks and saved deck presets are not part of the MVP.

### Learning Objective

Practice simple product configuration without creating a complex settings experience.

### Demo Scenario

Create a session with deck `0, 1, 2, 3, 5, 8` and verify that those values become voting buttons.

---

## P0-003 - Generate and Copy Shareable Session Link

**Epic:** E1. Session Creation  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-001

### User Story

As a Scrum Master, I want a unique shareable session link so that I can invite my team through an existing communication tool.

### Acceptance Criteria

```gherkin
Feature: Share session link

Scenario: Session link is generated after session creation
  Given I have created a new session
  When I view the active session room
  Then I see a unique session link
  And the link can be shared with participants

Scenario: Scrum Master copies the session link
  Given I am in the active session room as Scrum Master
  When I click the copy link action
  Then the session link is copied or made easy to copy
  And I receive clear feedback that the link is ready to share

Scenario: Participant opens a valid session link
  Given a session exists
  When a participant opens the session link
  Then the participant is taken to the join session screen
```

### Notes

- The app does not need built-in email, Slack, or Microsoft Teams sharing for MVP.
- Users share the link manually through their normal communication tools.

### Learning Objective

Practice routing, unique identifiers, and basic copy-to-clipboard behavior.

### Demo Scenario

Create a session, copy the link, open it in another browser window, and reach the join screen.

---

## P0-004 - Join Session With Display Name

**Epic:** E2. Joining  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-003

### User Story

As a participant, I want to join a session by entering my display name so that the team can identify me during estimation.

### Acceptance Criteria

```gherkin
Feature: Join session with display name

Scenario: Participant joins with a valid display name
  Given I opened a valid session link
  When I enter "Priya" as my display name
  And I join the session
  Then I enter the active session room
  And the room shows me as "Priya"

Scenario: Participant attempts to join without a display name
  Given I opened a valid session link
  When I leave the display name blank
  And I try to join the session
  Then I remain on the join screen
  And I see a clear message that my name is required

Scenario: Participant joins a session that has already started
  Given a session exists
  And a round is already active
  When I join with a valid display name
  Then I enter the active session room
  And I can participate according to the current room state
```

### Notes

- Display name is the only required participant identity field.
- No email address, password, or profile is required.

### Learning Objective

Practice minimal anonymous participant onboarding.

### Demo Scenario

Open a shared session link, enter `Priya`, and see `Priya` appear in the room.

---

## P0-005 - Join as Voter or Spectator

**Epic:** E2. Joining  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-004

### User Story

As a participant, I want to choose whether I am a voter or spectator so that observers can watch without affecting estimation.

### Acceptance Criteria

```gherkin
Feature: Join mode

Scenario: Participant joins as voter by default
  Given I opened a valid session link
  When I enter my display name
  And I do not change the join mode
  And I join the session
  Then I enter as a voter
  And I can vote during active rounds

Scenario: Participant joins as spectator
  Given I opened a valid session link
  When I enter my display name
  And I choose spectator mode
  And I join the session
  Then I enter as a spectator
  And I can observe the room
  And I cannot vote

Scenario: Spectator is excluded from voting status
  Given a spectator has joined the session
  When a voting round starts
  Then the spectator is not counted as missing a vote
  And the spectator is visually distinguished from voters
```

### Notes

- Voter is the default join mode.
- Spectator support is useful enough for MVP but should stay simple.

### Learning Objective

Practice role-based UI behavior without authentication.

### Demo Scenario

Join one browser as voter and another as spectator; confirm only the voter sees voting controls.

---

## P0-006 - Display Active Room Participants and States

**Epic:** E3. Room Experience  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-004, P0-005

### User Story

As a Scrum Master, I want to see who has joined and what their current state is so that I can facilitate the session confidently.

### Acceptance Criteria

```gherkin
Feature: Active room participant display

Scenario: Voter appears in the active room
  Given a voter has joined the session
  When the active room is displayed
  Then the voter's display name is visible
  And the voter is shown as eligible to vote

Scenario: Spectator appears in the active room
  Given a spectator has joined the session
  When the active room is displayed
  Then the spectator's display name is visible
  And the spectator is clearly marked as spectator

Scenario: Scrum Master appears in the active room
  Given I created the session
  When I view the active room
  Then I am shown as the Scrum Master
  And Scrum Master controls are visible to me
```

### Notes

- MVP may use a simple participant list or card layout.
- Final table-style seating can be improved later.

### Learning Objective

Practice presenting live shared state in a simple, understandable way.

### Demo Scenario

Create a session, join as two voters and one spectator, and verify that all users appear with correct states.

---

## P0-007 - Start a Voting Round With Optional Round Name

**Epic:** E6. Final Estimate and Rounds  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-006

### User Story

As a Scrum Master, I want to start a voting round with an optional round name so that the team knows what item is being estimated.

### Acceptance Criteria

```gherkin
Feature: Start voting round

Scenario: Scrum Master starts a round with a round name
  Given I am in the active room as Scrum Master
  When I enter "US-1234" in the round name field
  And I start the round
  Then a new voting round starts
  And the active round displays "US-1234"

Scenario: Scrum Master starts a round without a round name
  Given I am in the active room as Scrum Master
  When I leave the round name field blank
  And I start the round
  Then a new voting round starts
  And the room shows a clear fallback current-round label

Scenario: Non-owner cannot start a round
  Given I am a participant who did not create the session
  When I view the active room
  Then I do not see Scrum Master start-round controls
```

### Notes

- There is only one optional free-text round name field.
- Placeholder examples may include user story number, feature name, or story label, but these are not separate fields.

### Learning Objective

Practice owner-only actions and simple round state transitions.

### Demo Scenario

Start a round named `Login flow` and verify all participants see it as the active round.

---

## P0-008 - Render Deck Values as Vote Buttons

**Epic:** E4. Voting  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-002, P0-007

### User Story

As a voter, I want to see the estimation deck as buttons so that I can quickly select my vote.

### Acceptance Criteria

```gherkin
Feature: Vote buttons

Scenario: Deck values appear as buttons during active round
  Given a session was created with deck "1, 2, 3, 5, 8"
  And a round has started
  When I view the voting area as a voter
  Then I see vote buttons for "1", "2", "3", "5", and "8"
  And the buttons appear in the deck order

Scenario: Voter selects one vote button
  Given a round has started
  When I click the "5" vote button
  Then my selected vote is recorded as "5"
  And the "5" button appears selected to me

Scenario: Voter changes vote before reveal
  Given I selected "5" in an active round
  When I click the "8" vote button before votes are revealed
  Then my selected vote is changed to "8"
  And only "8" remains selected for me
```

### Notes

- Each voter can have only one selected vote per round.
- Button selection replaces the previous vote before reveal.

### Learning Objective

Practice simple input state with clear user feedback.

### Demo Scenario

Select `5`, then select `8`, and verify only `8` remains selected.

---

## P0-009 - Keep Votes Anonymous Before Reveal

**Epic:** E4. Voting  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-008

### User Story

As a voter, I want my vote hidden until reveal so that I am not influenced by other team members' estimates.

### Acceptance Criteria

```gherkin
Feature: Anonymous voting before reveal

Scenario: Voter's selected value is hidden from others
  Given a round has started
  And I selected a vote value
  When another participant views my status before reveal
  Then they can see that I have voted
  But they cannot see my selected value

Scenario: Voter sees their own selected value
  Given a round has started
  When I select a vote value
  Then I can see which value I selected
  But the value remains hidden from other users

Scenario: Voter has not voted yet
  Given a round has started
  And I have not selected a vote value
  When participants view the room before reveal
  Then I am shown as not voted
  And no vote value is shown for me
```

### Notes

- The room should distinguish "voted" from "not voted" before reveal.
- Vote values are only shown after Scrum Master reveal.

### Learning Objective

Practice conditional display of shared data based on room state.

### Demo Scenario

Submit a vote in one browser and confirm another browser only sees `voted`, not the value.

---

## P0-010 - Reveal Votes

**Epic:** E5. Reveal and Results  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-009

### User Story

As a Scrum Master, I want to reveal all votes at the same time so that the team can compare estimates after everyone has voted.

### Acceptance Criteria

```gherkin
Feature: Reveal votes

Scenario: Scrum Master reveals votes
  Given a round is active
  And at least one voter has submitted a vote
  When the Scrum Master reveals votes
  Then submitted vote values are shown to all users
  And all revealed votes appear at the same time

Scenario: Missing votes remain visible after reveal
  Given a round is active
  And one voter has not submitted a vote
  When the Scrum Master reveals votes
  Then the missing voter is shown as not voted
  And no vote value is shown for that voter

Scenario: Participant cannot reveal votes
  Given I am a voter who is not the Scrum Master
  When I view the active round
  Then I do not see the reveal control
```

### Notes

- Auto-reveal is not part of MVP.
- Reveal is controlled by the Scrum Master.

### Learning Objective

Practice owner-only state changes that affect all room participants.

### Demo Scenario

Submit votes from two browsers, reveal as Scrum Master, and verify both vote values appear to everyone.

---

## P0-011 - Display Median After Reveal

**Epic:** E5. Reveal and Results  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-010

### User Story

As a Scrum Master, I want to see the median after votes are revealed so that I have an informational starting point for team discussion.

### Acceptance Criteria

```gherkin
Feature: Median calculation

Scenario: Median is shown for odd number of numeric votes
  Given revealed numeric votes are "2", "3", and "8"
  When the results are displayed
  Then the median is shown as "3"

Scenario: Median is shown for even number of numeric votes
  Given revealed numeric votes are "2", "3", "5", and "8"
  When the results are displayed
  Then the median is calculated from the two middle numeric values
  And the median is shown clearly

Scenario: Non-numeric votes are excluded from median
  Given revealed votes are "3", "5", "?", and "coffee"
  When the results are displayed
  Then the median is calculated using only "3" and "5"
  And the non-numeric values are not included in the median calculation

Scenario: Median is unavailable when no numeric votes exist
  Given revealed votes are "?" and "coffee"
  When the results are displayed
  Then the median is shown as unavailable
```

### Notes

- Median is informational only.
- The final estimate is still recorded manually by the Scrum Master.
- Calculation logic should be easy to replace later.

### Learning Objective

Practice isolating product logic so calculation behavior can evolve later.

### Demo Scenario

Reveal votes `2`, `3`, and `8`; verify median displays as `3`.

---

## P0-012 - Record Final Estimate

**Epic:** E6. Final Estimate and Rounds  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-010, P0-011

### User Story

As a Scrum Master, I want to record the final estimate after team discussion so that the agreed estimate is captured for the round.

### Acceptance Criteria

```gherkin
Feature: Record final estimate

Scenario: Scrum Master records final estimate after reveal
  Given votes have been revealed for the current round
  When the Scrum Master records "5" as the final estimate
  Then the current round shows final estimate "5"
  And the round is marked as estimated

Scenario: Scrum Master records final estimate different from median
  Given votes have been revealed
  And the median is "3"
  When the Scrum Master records "5" as the final estimate
  Then the final estimate is shown as "5"
  And the median remains informational only

Scenario: Participant cannot record final estimate
  Given votes have been revealed
  When a voter who is not the Scrum Master views the room
  Then the voter cannot record the final estimate
```

### Notes

- Recommendation for first implementation: choose final estimate from deck values.
- Manual final estimate entry can be added if needed.

### Learning Objective

Practice capturing outcome state separately from calculated guidance.

### Demo Scenario

Reveal votes, record final estimate `5`, and verify the round shows final estimate `5`.

---

## P0-013 - Start Re-Vote for Current Round

**Epic:** E6. Final Estimate and Rounds  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-010

### User Story

As a Scrum Master, I want to start a re-vote for the current round so that the team can vote again after discussion.

### Acceptance Criteria

```gherkin
Feature: Re-vote

Scenario: Scrum Master starts a re-vote after reveal
  Given votes have been revealed for the current round
  When the Scrum Master starts a re-vote
  Then previous submitted votes are cleared
  And the same round name is preserved
  And voters can submit new votes

Scenario: Re-vote uses the same deck
  Given a session uses deck "1, 2, 3, 5, 8"
  And the Scrum Master starts a re-vote
  When voters view the voting area
  Then they see the same deck values as vote buttons

Scenario: Participant cannot start a re-vote
  Given votes have been revealed
  When a voter who is not the Scrum Master views the room
  Then the voter cannot start a re-vote
```

### Notes

- Re-vote is part of MVP because disagreement is common in Planning Poker.
- Re-vote should keep the UX simple and not require creating a separate story.

### Learning Objective

Practice resetting state safely without losing the current round context.

### Demo Scenario

Reveal votes, start a re-vote, confirm votes are cleared and the same round name remains.

---

## P0-014 - Start Next Round

**Epic:** E6. Final Estimate and Rounds  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-012

### User Story

As a Scrum Master, I want to start another round after recording a final estimate so that the team can estimate multiple stories in one session.

### Acceptance Criteria

```gherkin
Feature: Multiple rounds

Scenario: Scrum Master starts next round after final estimate
  Given the current round has a final estimate
  When the Scrum Master starts the next round
  Then a new round is created
  And previous round results remain separate from the new round
  And voters can vote again for the new round

Scenario: Next round can have a different round name
  Given the current round is complete
  When the Scrum Master starts a new round named "Payment retry story"
  Then the active round displays "Payment retry story"

Scenario: New round starts with no submitted votes
  Given a previous round has revealed votes
  When the Scrum Master starts the next round
  Then all voters are shown as not voted for the new round
  And no previous votes are selected for the new round
```

### Notes

- Multiple rounds are a must-have because a planning session usually estimates more than one item.

### Learning Objective

Practice modeling repeated workflow cycles inside a single session.

### Demo Scenario

Complete one round, start a second round, and verify the second round begins with clean voting state.

---

## P0-015 - End Session

**Epic:** E7. Session End  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-014

### User Story

As a Scrum Master, I want to end the session so that the planning room is clearly closed when estimation is finished.

### Acceptance Criteria

```gherkin
Feature: End session

Scenario: Scrum Master ends active session
  Given I am in an active session as Scrum Master
  When I end the session
  Then the session status changes to ended
  And users see that the session has ended

Scenario: Ended session does not allow new voting
  Given a session has ended
  When a voter views the room
  Then the voter cannot submit votes
  And the voter cannot change previous votes

Scenario: Ended session does not allow new rounds
  Given a session has ended
  When the Scrum Master views the room
  Then the Scrum Master cannot start a new round
```

### Notes

- Read-only historical dashboard is not part of MVP.
- The active room may simply show an ended state.

### Learning Objective

Practice terminal workflow states and disabling invalid actions.

### Demo Scenario

End a session and verify voting and new-round actions are disabled.

---

## P0-016 - Handle Basic Invalid Links and Missing Sessions

**Epic:** E2. Joining  
**Priority:** P0 - MVP Must Have  
**Dependencies:** P0-003

### User Story

As a user, I want a clear message when I open an invalid or unavailable session link so that I understand what happened.

### Acceptance Criteria

```gherkin
Feature: Invalid session link

Scenario: User opens invalid session link
  Given I have a session link that does not match an existing session
  When I open the link
  Then I see a clear message that the session was not found
  And I am given a way to return to the home page

Scenario: User opens link for ended session
  Given a session has ended
  When I open the session link
  Then I see that the session has ended
  And I cannot join as a new voter
```

### Notes

- This is included in MVP because broken links are a common first-use failure mode.

### Learning Objective

Practice simple error and empty state handling.

### Demo Scenario

Open a fake session URL and verify the app shows a clear not-found state.

---

# 5. P1 - Version 1 Polish Stories

## P1-001 - Responsive Web Layout

**Epic:** E8. UX, Reliability, and Accessibility  
**Priority:** P1 - Version 1 Polish  
**Dependencies:** P0 MVP flow

### User Story

As a participant, I want the room to work on common desktop and mobile browser sizes so that I can vote from the device I have available.

### Acceptance Criteria

```gherkin
Feature: Responsive web layout

Scenario: Participant votes on desktop browser
  Given I am in an active round on a desktop browser
  When I view the voting area
  Then all vote buttons are visible and usable

Scenario: Participant votes on narrow mobile browser
  Given I am in an active round on a narrow mobile browser
  When I view the voting area
  Then vote buttons remain readable and tappable
  And the main voting workflow remains usable without horizontal scrolling
```

### Learning Objective

Practice responsive frontend implementation without building a native mobile app.

### Demo Scenario

Use browser dev tools to verify the active room works at desktop and mobile widths.

---

## P1-002 - Basic Accessibility Support

**Epic:** E8. UX, Reliability, and Accessibility  
**Priority:** P1 - Version 1 Polish  
**Dependencies:** P0 MVP flow

### User Story

As a user, I want the app to support basic accessibility needs so that the voting workflow is usable with keyboard navigation and clear visual labels.

### Acceptance Criteria

```gherkin
Feature: Basic accessibility

Scenario: User navigates voting buttons with keyboard
  Given a round is active
  When I use keyboard navigation
  Then I can reach the vote buttons
  And I can select a vote without using a mouse

Scenario: Voting status does not rely only on color
  Given a round is active
  When I view participant voting status
  Then status is communicated with text or icons in addition to color

Scenario: Form fields have clear labels
  Given I am creating or joining a session
  When I view the form fields
  Then each input has a visible or accessible label
```

### Learning Objective

Practice accessibility as part of normal feature quality rather than a late add-on.

### Demo Scenario

Navigate create, join, and vote flows using only the keyboard.

---

## P1-003 - Basic Browser Refresh Recovery

**Epic:** E8. UX, Reliability, and Accessibility  
**Priority:** P1 - Version 1 Polish  
**Dependencies:** P0 MVP flow

### User Story

As a user, I want the room to recover gracefully after browser refresh so that an accidental refresh does not completely break the session.

### Acceptance Criteria

```gherkin
Feature: Browser refresh recovery

Scenario: Participant refreshes active room
  Given I have joined an active session
  When I refresh the browser
  Then I return to the same session if possible
  And I can continue participating according to my role

Scenario: Scrum Master refreshes active room
  Given I created a session as Scrum Master
  When I refresh the browser
  Then I return to the session if possible
  And Scrum Master controls remain available if ownership can be verified
```

### Learning Objective

Practice client/server state boundaries and lightweight session continuity.

### Demo Scenario

Refresh the room as Scrum Master and as participant; verify the experience does not collapse.

---

## P1-004 - Session Summary After End

**Epic:** E8. UX, Reliability, and Accessibility  
**Priority:** P1 - Version 1 Polish  
**Dependencies:** P0-015

### User Story

As a Scrum Master, I want to see a simple session summary after ending the session so that I can copy the final estimates into another system.

### Acceptance Criteria

```gherkin
Feature: Ended session summary

Scenario: Scrum Master views ended session summary
  Given a session has ended
  And at least one round has a final estimate
  When I view the ended session state
  Then I see each round name
  And I see each final estimate

Scenario: Session summary excludes unfinished rounds
  Given a session has ended
  And a round does not have a final estimate
  When I view the ended session summary
  Then the unfinished round is clearly marked or excluded
```

### Learning Objective

Practice displaying compact outcome data without building full session history.

### Demo Scenario

Complete two rounds, end the session, and verify both final estimates appear in a simple summary.

---

## P1-005 - Basic Telemetry for Product Learning

**Epic:** E9. Deployment and Open Source Readiness  
**Priority:** P1 - Version 1 Polish  
**Dependencies:** Deployed MVP

### User Story

As the product owner, I want basic usage telemetry so that I can understand whether users complete the core workflow.

### Acceptance Criteria

```gherkin
Feature: Basic product telemetry

Scenario: Session creation is tracked
  Given a Scrum Master creates a session
  When the session is created successfully
  Then a session-created event is recorded

Scenario: Round completion is tracked
  Given a Scrum Master records a final estimate
  When the final estimate is saved
  Then a round-completed event is recorded

Scenario: No unnecessary personal data is collected
  Given telemetry is enabled
  When events are recorded
  Then email addresses and passwords are not collected
  And display names are not required for product metrics
```

### Learning Objective

Practice privacy-aware telemetry and basic product analytics.

### Demo Scenario

Create a session and complete a round, then verify telemetry records the expected events.

---

## P1-006 - Public Repository Documentation

**Epic:** E9. Deployment and Open Source Readiness  
**Priority:** P1 - Version 1 Polish  
**Dependencies:** Project structure exists

### User Story

As a developer visiting the repository, I want clear setup and contribution documentation so that I can understand and run the project locally.

### Acceptance Criteria

```gherkin
Feature: Repository documentation

Scenario: Developer reads local setup instructions
  Given I open the repository README
  When I follow the local setup instructions
  Then I can run the application locally

Scenario: Developer reads contribution guidance
  Given I open the repository documentation
  When I review contribution guidance
  Then I understand how to propose a change
  And I understand the expected development workflow
```

### Learning Objective

Practice maintaining project documentation as part of the build process.

### Demo Scenario

Follow the README from a clean checkout and verify the app starts locally.

---

# 6. P2 - Adds Value Stories

These stories are explicitly not part of the MVP.

## P2-001 - Scrum Master Authentication

**Epic:** E10. Accounts, Teams, History, and Dashboard  
**Priority:** P2 - Adds Value

### User Story

As a Scrum Master, I want to sign in so that I can access previous rooms and manage my planning activity over time.

### Acceptance Criteria

```gherkin
Feature: Scrum Master authentication

Scenario: Scrum Master signs in
  Given authentication is enabled
  When I sign in successfully
  Then I can create sessions associated with my account

Scenario: Participant still joins without account
  Given authentication is enabled for Scrum Masters
  When a participant opens a shared session link
  Then the participant can still join without creating an account
```

### Learning Objective

Practice adding authentication only after the anonymous MVP is proven.

### Demo Scenario

Sign in as Scrum Master, create a room, and invite a participant who joins without signing in.

---

## P2-002 - Dashboard for Previous Sessions

**Epic:** E10. Accounts, Teams, History, and Dashboard  
**Priority:** P2 - Adds Value

### User Story

As a Scrum Master, I want a dashboard of previous sessions so that I can revisit estimation results later.

### Acceptance Criteria

```gherkin
Feature: Session dashboard

Scenario: Scrum Master views previous sessions
  Given I am signed in
  And I have created previous sessions
  When I open the dashboard
  Then I see a list of my previous sessions

Scenario: Scrum Master opens previous session read-only
  Given I am viewing the dashboard
  When I select a completed session
  Then I can view the session history in read-only mode
```

### Learning Objective

Practice authenticated data ownership and read-only historical views.

### Demo Scenario

Complete a session, open the dashboard, and view the completed session summary.

---

## P2-003 - Team Management

**Epic:** E10. Accounts, Teams, History, and Dashboard  
**Priority:** P2 - Adds Value

### User Story

As a Scrum Master, I want to create or select a team when creating a room so that sessions can be organized by team.

### Acceptance Criteria

```gherkin
Feature: Team management

Scenario: Scrum Master creates a new team while creating a session
  Given I am signed in
  When I create a session
  And I enter a new team name
  Then the session is associated with that team

Scenario: Scrum Master selects an existing team
  Given I am signed in
  And I have an existing team
  When I create a session
  And I select that team
  Then the session is associated with the selected team

Scenario: Dashboard groups sessions by team
  Given I have sessions associated with multiple teams
  When I view the dashboard
  Then sessions are organized by team
```

### Learning Objective

Practice data modeling around accounts, teams, and owned resources.

### Demo Scenario

Create two teams and verify dashboard groups sessions under the correct team.

---

## P2-004 - Team-Level Default Deck

**Epic:** E10. Accounts, Teams, History, and Dashboard  
**Priority:** P2 - Adds Value

### User Story

As a Scrum Master, I want each team to have a default estimation deck so that I do not need to configure the deck every time.

### Acceptance Criteria

```gherkin
Feature: Team default deck

Scenario: Team has a default deck
  Given I have a team with default deck "1, 2, 3, 5, 8"
  When I create a new session for that team
  Then the session deck defaults to "1, 2, 3, 5, 8"

Scenario: Scrum Master customizes deck for one room
  Given I am creating a session for a team
  When I customize the deck before creating the session
  Then the session uses the customized deck
  And the team's default deck is not changed
```

### Learning Objective

Practice defaults and overrides without overcomplicating MVP setup.

### Demo Scenario

Set a team default deck, create a room, and verify the room inherits that deck.

---

## P2-005 - Delegate Room Ownership

**Epic:** E10. Accounts, Teams, History, and Dashboard  
**Priority:** P2 - Adds Value

### User Story

As a Scrum Master, I want to delegate room ownership to one or more people so that another facilitator can manage the session if needed.

### Acceptance Criteria

```gherkin
Feature: Delegate room ownership

Scenario: Scrum Master adds another owner
  Given I own a session
  When I add another participant as owner
  Then that participant can use Scrum Master controls

Scenario: Delegated owner reveals votes
  Given I am a delegated owner
  And a round is active
  When I reveal votes
  Then votes are revealed to all users

Scenario: Non-owner still cannot use owner controls
  Given I am a regular voter
  When I view the active room
  Then I cannot start rounds, reveal votes, or end the session
```

### Learning Objective

Practice authorization rules after the app has authentication or durable room identity.

### Demo Scenario

Delegate ownership to another user and verify both owners can reveal votes.

---

# 7. P3 - Nice-to-Have Stories

These stories should stay parked until the product has real usage.

## P3-001 - Integrations With Work Tracking Tools

**Epic:** E11. Integrations and Monetization  
**Priority:** P3 - Nice to Have

### User Story

As a Scrum Master, I want to connect PokerPlanner to a work tracking tool so that story names and final estimates can be synced automatically.

### Acceptance Criteria

```gherkin
Feature: Work tracking integration

Scenario: Scrum Master imports backlog item
  Given an integration is configured
  When I select a backlog item
  Then the round name is populated from that item

Scenario: Scrum Master exports final estimate
  Given a round has a final estimate
  When I choose to sync the estimate
  Then the final estimate is sent to the connected work tracking tool
```

### Learning Objective

Practice external API integration after the standalone product is valuable.

### Demo Scenario

Import one backlog item and sync one final estimate to an external tool.

---

## P3-002 - Donation or Paid Tier

**Epic:** E11. Integrations and Monetization  
**Priority:** P3 - Nice to Have

### User Story

As the product owner, I want a donation or paid option so that the product can offset hosting and maintenance costs without showing ads.

### Acceptance Criteria

```gherkin
Feature: Donation or paid tier

Scenario: User sees optional support option
  Given monetization is enabled
  When a user visits the product
  Then the user may choose to support the project
  And the core free experience remains usable

Scenario: Product remains ad-free
  Given monetization is enabled
  When users use PokerPlanner
  Then no advertisements are displayed
```

### Learning Objective

Practice lightweight monetization without compromising product principles.

### Demo Scenario

Verify the support option is visible but does not block creating and joining sessions.

---

## P3-003 - AI-Assisted Estimation Insights

**Epic:** E11. Integrations and Monetization  
**Priority:** P3 - Nice to Have

### User Story

As a Scrum Master, I want optional AI-assisted estimation insights so that the team can compare its estimate against historical or contextual guidance.

### Acceptance Criteria

```gherkin
Feature: AI-assisted estimation insights

Scenario: Scrum Master requests AI insight
  Given AI insights are enabled
  And a round has a name or description
  When the Scrum Master requests insight
  Then the system provides optional estimation guidance
  And the team can ignore the guidance

Scenario: AI does not replace team consensus
  Given AI insight is displayed
  When the Scrum Master records final estimate
  Then the final estimate is still manually selected by the Scrum Master
```

### Learning Objective

Practice adding AI in a product-responsible way only after the core workflow is stable.

### Demo Scenario

Request AI insight for a round and confirm the Scrum Master still records the final estimate manually.

---

# 8. Recommended MVP Build Order

The recommended build order is optimized for small vertical slices.

1. **P0-001** Create a session without login.
2. **P0-002** Configure estimation deck at session creation.
3. **P0-003** Generate and copy shareable session link.
4. **P0-004** Join session with display name.
5. **P0-005** Join as voter or spectator.
6. **P0-006** Display active room participants and states.
7. **P0-007** Start voting round with optional round name.
8. **P0-008** Render deck values as vote buttons.
9. **P0-009** Keep votes anonymous before reveal.
10. **P0-010** Reveal votes.
11. **P0-011** Display median after reveal.
12. **P0-012** Record final estimate.
13. **P0-013** Start re-vote.
14. **P0-014** Start next round.
15. **P0-015** End session.
16. **P0-016** Handle invalid links and missing sessions.

---

# 9. MVP Definition of Done

The MVP is complete when:

- A Scrum Master can create a session without login.
- The Scrum Master can configure the session deck at creation.
- A unique link can be shared.
- Participants can join with display names.
- Participants can join as voters or spectators.
- Voters can select one vote button per round.
- Votes remain hidden before reveal.
- Scrum Master can reveal votes.
- Median is displayed after reveal.
- Scrum Master can record the final estimate.
- Scrum Master can start a re-vote.
- Scrum Master can run multiple rounds.
- Scrum Master can end the session.
- Basic invalid-link behavior exists.
- The app works locally.
- The MVP has been manually tested.
- The code has been committed to Git.
- The code has been pushed to GitHub.
- The app has been deployed when practical.
- `DEVLOG.md` has been updated.

---

# 10. Backlog Maintenance Notes

This backlog should be updated after each sprint or meaningful development session.

When adding a new story, include:

- Epic.
- Priority.
- User story.
- Gherkin acceptance criteria.
- Dependencies.
- Learning objective.
- Demo scenario.

When a story becomes too large, split it into smaller vertical slices.

When tempted to add a feature, ask:

> Does this help a real team complete the planning poker workflow faster or with less confusion?

If not, park it outside the MVP.
