# PokerPlanner MVP UX Flow

## Document Status

- **Product:** PokerPlanner
- **Document:** MVP UX Flow
- **Version:** 0.1
- **Status:** Draft
- **Owner:** Product Manager / UX
- **Primary Goal:** Define the simplest screen flow for the MVP so implementation stays focused.

---

## 1. UX Goal

PokerPlanner should feel simple enough that a first-time user can join and vote without instructions.

The MVP UX should optimize for:

- Fast session creation.
- Clear participant onboarding.
- Obvious voting actions.
- Clear voting status.
- Simple Scrum Master controls.
- Minimal screens.
- Minimal configuration.

---

## 2. MVP Screens

The MVP needs four primary screens:

1. Home / Create Session.
2. Join Session.
3. Active Session Room.
4. Ended Session State.

The ended session state may be part of the Active Session Room screen rather than a separate route.

---

## 3. Screen 1: Home / Create Session

### Purpose

Allow the Scrum Master to create a new Planning Poker session quickly.

### Primary User

Scrum Master.

### Main Elements

- App name: `PokerPlanner`
- Short value statement.
- Session name input.
- Estimation deck input.
- Create Session button.

### Session Name Field

Label:

```text
Session name
```

Placeholder:

```text
Example: Sprint 24 Planning, Platform Team, July Refinement
```

Behavior:

- Optional.
- Single free-text field.
- No separate room name, sprint name, team name, or session label fields.

### Estimation Deck Field

Label:

```text
Estimation deck
```

Default value:

```text
0, 1/2, 1, 2, 3, 5, 8, 13, 20, 40, 100, ?, coffee
```

Helper text:

```text
Separate values with commas. These become the voting buttons for this session.
```

Behavior:

- Required.
- Must contain at least one value.
- Preserves entered order.
- Values become vote buttons inside the session.

### Primary Action

```text
Create session
```

### Success Result

User lands in the Active Session Room as Scrum Master.

---

## 4. Screen 2: Join Session

### Purpose

Allow a participant or spectator to join using a shared link.

### Primary User

Participant or spectator.

### Main Elements

- Session name, if available.
- Display name input.
- Join mode choice.
- Join button.

### Display Name Field

Label:

```text
Your name
```

Placeholder:

```text
Example: Priya
```

Behavior:

- Required.
- Used only for display in the session.

### Join Mode

Default:

```text
Voter
```

Options:

```text
Voter
Spectator
```

Behavior:

- Voter can vote.
- Spectator can watch but cannot vote.

### Primary Action

```text
Join session
```

### Success Result

User lands in Active Session Room.

---

## 5. Screen 3: Active Session Room

### Purpose

Support the live Planning Poker session.

### Primary Users

- Scrum Master.
- Voter.
- Spectator.

### Main Regions

1. Header.
2. Share link area.
3. Current round area.
4. Participant/table area.
5. Voting button area.
6. Scrum Master controls.
7. Round results area.

---

## 6. Active Session Header

### Elements

- Session name, if provided.
- Fallback title if no session name exists.
- Session status.

### Example

```text
Sprint 24 Planning
Status: Waiting for round
```

### Fallback

```text
Untitled planning session
```

---

## 7. Share Link Area

### Purpose

Allow Scrum Master to share the session link.

### Elements

- Read-only session link.
- Copy link button.

### Primary Action

```text
Copy link
```

### Notes

This area is primarily for the Scrum Master.

Participants do not need this to be prominent after joining.

---

## 8. Current Round Area

### Before Round Starts

Display:

```text
No round started yet.
```

Scrum Master sees:

- Round name input.
- Start Round button.

### Round Name Field

Label:

```text
Round name
```

Placeholder:

```text
Example: US-1234, Login flow, Payment retry story
```

Behavior:

- Optional.
- Single free-text field.
- No separate user story number, feature name, or short story label fields.

### During Voting

Display:

- Round name, if provided.
- Round status: `Voting in progress`.
- Count of voters who have voted.

Example:

```text
US-1234
Voting in progress: 3 of 5 voters have voted
```

### After Reveal

Display:

- Round name, if provided.
- Round status: `Votes revealed`.
- Median, if available.
- Final estimate field/control for Scrum Master.

---

## 9. Participant / Table Area

### Purpose

Show who is in the session and their voting status.

### MVP Layout

The MVP may use a simple list or card layout.

The final product may evolve toward a table-style visual layout where participants are seated around a table.

### Before Reveal

For each voter, show:

- Display name.
- Status: `Not voted` or `Voted`.
- Hidden card face or equivalent visual indicator.

For spectators, show:

- Display name.
- Status: `Spectator`.

### After Reveal

For each voter, show:

- Display name.
- Vote value, if submitted.
- Missing indicator if no vote was submitted.

For spectators, show:

- Display name.
- Status: `Spectator`.

### Important UX Rule

Before reveal, never show another voter's selected value.

---

## 10. Voting Button Area

### Purpose

Allow voters to submit exactly one vote per round.

### Display

The estimation deck appears as buttons.

Example:

```text
[0] [1/2] [1] [2] [3] [5] [8] [13] [20] [40] [100] [?] [coffee]
```

### Behavior for Voters

- Buttons are enabled during active voting.
- Clicking a button submits that value.
- Clicking another button before reveal replaces the vote.
- Selected button is visually highlighted to the current voter.
- Only one button can be selected at a time.
- Buttons become disabled after reveal.

### Behavior for Spectators

- Spectators cannot vote.
- Spectators may see the deck as disabled or may see a message:

```text
You are observing this round.
```

### Behavior Before Round Starts

Participants see:

```text
Waiting for the Scrum Master to start a round.
```

### Behavior After Reveal

Participants see revealed results, not active vote buttons.

---

## 11. Scrum Master Controls

### Waiting for Round

Controls:

- Round name input.
- Start Round button.
- End Session button.

### Voting In Progress

Controls:

- Reveal Votes button.
- End Session button.

Optional future enhancement:

- Disable Reveal Votes until at least one voter has voted.

### Votes Revealed

Controls:

- Final estimate control.
- Record Final Estimate button.
- Re-Vote button.
- End Session button.

### Final Estimate Recorded

Controls:

- Start Next Round button.
- End Session button.

---

## 12. Round Results Area

### After Reveal

Show:

- Revealed votes.
- Median.
- Missing votes, if any.
- Spectators excluded from vote count.

### Median Display

If median is available:

```text
Median: 5
```

If no numeric votes exist:

```text
Median unavailable
```

### Final Estimate Display

Before final estimate:

```text
Final estimate not recorded yet.
```

After final estimate:

```text
Final estimate: 5
```

---

## 13. Screen 4: Ended Session State

### Purpose

Show that the session is closed.

### Display

```text
This session has ended.
```

### Behavior

- No new rounds can be started.
- No new votes can be submitted.
- Existing visible results may remain visible if technically simple.

### Not MVP

- Full historical dashboard.
- Read-only session archive.
- Export results.

---

## 14. State Model for UX

The session should visually communicate one of these states:

1. Waiting for participants.
2. Waiting for round.
3. Voting in progress.
4. Votes revealed.
5. Final estimate recorded.
6. Session ended.

The current state should be obvious from the screen.

---

## 15. Button Labels

Use direct labels:

- `Create session`
- `Copy link`
- `Join session`
- `Start round`
- `Reveal votes`
- `Record final estimate`
- `Re-vote`
- `Start next round`
- `End session`

Avoid vague labels:

- `Submit`
- `Continue`
- `Next`
- `Proceed`

---

## 16. Empty States

### No Participants Yet

```text
Share the link to invite your team.
```

### No Round Started

```text
Start a round when your team is ready to vote.
```

### Participant Waiting

```text
Waiting for the Scrum Master to start a round.
```

### Voter Has Not Voted

```text
Choose one estimate.
```

### Spectator

```text
You are observing this session.
```

---

## 17. Error and Validation Messages

### Missing Display Name

```text
Enter your name to join the session.
```

### Empty Deck

```text
Enter at least one estimation value.
```

### Session Not Found

```text
This session link is invalid or no longer available.
```

### Session Ended

```text
This session has ended and no longer accepts votes.
```

---

## 18. Accessibility Notes

The MVP should support:

- Keyboard navigation for buttons and form fields.
- Visible focus states.
- Labels for all inputs.
- Status text in addition to visual indicators.
- Sufficient contrast.
- Clear disabled states.

Voting status should not depend on color alone.

---

## 19. UX Acceptance Criteria

```gherkin
Feature: Create session screen

Scenario: Scrum Master sees a simple session creation form
  Given the Scrum Master opens PokerPlanner
  When the home page loads
  Then the Scrum Master sees a session name field
  And the Scrum Master sees an estimation deck field
  And the Scrum Master sees a Create session button
```

```gherkin
Feature: Join session screen

Scenario: Participant joins from link
  Given a participant opens a valid session link
  When the join screen loads
  Then the participant sees a display name field
  And the participant can choose voter or spectator mode
  And voter mode is selected by default
```

```gherkin
Feature: Vote buttons

Scenario: Voter selects exactly one vote button
  Given a voting round is active
  And the voter sees the estimation deck buttons
  When the voter clicks one estimation button
  Then that button becomes selected for the voter
  And no other estimation button is selected for that voter
```

```gherkin
Feature: Hidden votes

Scenario: Votes remain hidden before reveal
  Given a voting round is active
  And multiple voters have submitted votes
  When votes have not been revealed
  Then each voter can see their own selected state
  And no voter can see another voter's selected value
```

```gherkin
Feature: Scrum Master controls

Scenario: Scrum Master sees controls for current session state
  Given the Scrum Master owns the session
  When the session state changes
  Then the Scrum Master sees only the controls relevant to the current state
```

---

## 20. UX Decision Summary

The MVP should use the fewest screens practical.

There is one session name field.

There is one round name field.

Deck values become voting buttons.

A voter can select exactly one button per round.

The selected vote can be changed before reveal.

Votes remain hidden until the Scrum Master reveals them.

The MVP may use a simple participant list or card layout before investing in a polished table visualization.
