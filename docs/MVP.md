# PokerPlanner MVP Definition

## Document Status

- **Product:** PokerPlanner
- **Document:** MVP Definition
- **Version:** 0.1
- **Status:** Draft
- **Owner:** Product Manager
- **Primary Goal:** Define the smallest useful version of PokerPlanner that supports a real Planning Poker session.

---

## 1. MVP Goal

The MVP goal is to allow a Scrum Master to run a complete Planning Poker session with a team using only a shareable link.

The MVP must support this core flow:

1. Scrum Master creates a session.
2. Scrum Master shares a unique link.
3. Participants join with display names.
4. Participants vote anonymously using estimation buttons.
5. Scrum Master reveals votes.
6. System displays the median.
7. Team discusses offline.
8. Scrum Master records the final estimate.
9. Scrum Master repeats the process for additional rounds.
10. Scrum Master ends the session.

The MVP should prove that the product is useful before adding accounts, dashboards, teams, session history, integrations, or paid features.

---

## 2. MVP Product Principles

The MVP must follow these principles:

- No login required.
- No advertisements.
- No unnecessary configuration.
- Minimal clicks.
- First-time users should understand what to do without instructions.
- Discussion happens outside the app.
- Working software matters more than perfect visual polish.
- Each feature should be small enough to build, test, commit, and review incrementally.

---

## 3. MVP Included Features

### 3.1 Create Session

The Scrum Master can create a new Planning Poker session.

Included:

- One optional free-text session name field.
- Placeholder examples such as `Sprint 24 Planning`, `Platform Team`, or `July Refinement`.
- Editable estimation deck at session creation.
- Unique shareable session link.
- Scrum Master becomes session owner.

Not included:

- Separate room name, sprint name, team name, or session label fields.
- Team selection.
- Authentication.
- Dashboard.

---

### 3.2 Configure Session Deck

The Scrum Master can edit the estimation deck before creating the session.

Included:

- Default deck.
- Simple editable comma-separated list or equivalent simple UI.
- Ordered deck values.
- At least one required value.
- Deck fixed after session creation.

Recommended default deck:

```text
0, 1/2, 1, 2, 3, 5, 8, 13, 20, 40, 100, ?, coffee
```

Not included:

- Deck presets.
- Team-level decks.
- Saved decks.
- Drag-and-drop deck editing.
- Advanced validation.

---

### 3.3 Join Session

Participants can join a session from the shared link.

Included:

- Enter display name.
- Join as voter or spectator.
- Voter is the default mode.
- Spectators can observe but cannot vote.

Not included:

- Email invite.
- User profile.
- Password.
- Account creation.

---

### 3.4 Start Round

The Scrum Master can start a voting round.

Included:

- One optional free-text round name field.
- Placeholder examples such as `US-1234`, `Login flow`, or `Payment retry story`.
- Clear voting state after round starts.

Not included:

- Separate user story number field.
- Separate feature name field.
- Separate short story label field.
- Backlog import.
- Jira or Azure DevOps integration.

---

### 3.5 Vote Anonymously

Voters can select one vote value per round.

Included:

- Estimation deck values displayed as buttons.
- One selected vote button per voter per round.
- Voter can change vote before reveal.
- Vote value hidden from others before reveal.
- System shows whether each voter has voted.
- System shows whether each voter has not voted.

Not included:

- Free-text vote entry during voting.
- Multiple votes per person.
- Weighted votes.
- Comments on votes.

---

### 3.6 Reveal Votes

The Scrum Master can reveal votes.

Included:

- Only Scrum Master can reveal.
- All votes reveal simultaneously.
- Revealed vote value shown next to each voter.
- Missing votes remain visible as missing.
- Spectators excluded from voting count.

Not included:

- Participant-triggered reveal.
- Auto-reveal when everyone has voted.
- Reveal animations required for MVP.

---

### 3.7 Display Median

The system displays the median after reveal.

Included:

- Numeric votes included in median calculation.
- Non-numeric votes excluded from median calculation.
- Median shown as informational only.
- Median unavailable if there are no numeric votes.

Not included:

- Average calculation.
- Vote distribution chart.
- Configurable estimation algorithm.
- AI estimate recommendation.

---

### 3.8 Record Final Estimate

The Scrum Master records the final estimate after team discussion.

Included:

- Final estimate associated with the current round.
- Final estimate shown after recorded.
- Final estimate represents team consensus.

Open implementation choice:

- Final estimate may be selected from the deck only, or may allow manual text entry.

Recommendation for first vertical slice:

- Start with selecting from the deck.
- Add manual entry only if needed.

---

### 3.9 Re-Vote

The Scrum Master can restart voting for the current round.

Included:

- Previous votes cleared.
- Same round name preserved.
- Same deck used.
- Participants vote again.
- Votes remain hidden until next reveal.

Not included:

- Full re-vote history.
- Comparison between voting attempts.

---

### 3.10 Multiple Rounds

The Scrum Master can estimate more than one item during a session.

Included:

- Start next round after final estimate is recorded.
- Each round has independent votes, reveal state, median, and final estimate.
- Session continues until ended.

Not included:

- Full historical dashboard.
- Cross-session history.
- Team-level reporting.

---

### 3.11 End Session

The Scrum Master can end the session.

Included:

- Session clearly marked as ended.
- No new rounds after end.
- No new votes after end.

Not included:

- Permanent historical read-only dashboard.
- Export.
- Email summary.

---

## 4. MVP Excluded Features

The following are explicitly outside MVP scope:

- User accounts.
- Authentication.
- Dashboard.
- Saved session history.
- Team management.
- Team-level default decks.
- Delegated ownership.
- Paid tier.
- Donation flow.
- About page polish.
- Native mobile app.
- Chat.
- Comments.
- Voice.
- Video.
- Jira integration.
- Azure DevOps integration.
- Slack integration.
- Microsoft Teams integration.
- AI-assisted estimation.
- Export to CSV.
- Export to PDF.
- Advanced analytics.

---

## 5. MVP User Flows

### 5.1 Scrum Master Creates Session

1. Open app.
2. Click **Create Session**.
3. Optionally enter session name.
4. Review or edit estimation deck.
5. Click **Create**.
6. See session page.
7. Copy session link.
8. Share link outside app.

### 5.2 Participant Joins Session

1. Open shared link.
2. Enter display name.
3. Choose voter or spectator.
4. Click **Join**.
5. Arrive in session.
6. Wait for round to start.

### 5.3 Scrum Master Runs Round

1. Click **Start Round**.
2. Optionally enter round name.
3. Ask team to vote offline.
4. Watch voting status.
5. Click **Reveal Votes**.
6. Review revealed votes and median.
7. Facilitate offline discussion.
8. Record final estimate.
9. Start next round or end session.

### 5.4 Participant Votes

1. Wait for round to start.
2. View deck buttons.
3. Click one vote button.
4. See confirmation that vote is submitted.
5. Optionally click a different button before reveal to change vote.
6. Wait for reveal.
7. Participate in offline discussion.

### 5.5 Scrum Master Re-Votes

1. Review revealed votes.
2. Decide the team needs another vote.
3. Click **Re-Vote**.
4. Votes clear.
5. Participants vote again.
6. Scrum Master reveals again.
7. Scrum Master records final estimate.

---

## 6. MVP Acceptance Criteria

### 6.1 Create Session

```gherkin
Feature: Create planning session

Scenario: Scrum Master creates a session with default settings
  Given the Scrum Master is on the PokerPlanner home page
  When the Scrum Master creates a new session without changing optional fields
  Then the system creates a new session
  And the system assigns the Scrum Master as the session owner
  And the system generates a unique shareable session link
  And the session uses the default estimation deck
```

```gherkin
Scenario: Scrum Master creates a session with a custom session name
  Given the Scrum Master is creating a session
  When the Scrum Master enters a session name
  And creates the session
  Then the session displays the entered session name
```

```gherkin
Scenario: Scrum Master edits the estimation deck before creating session
  Given the Scrum Master is creating a session
  When the Scrum Master edits the estimation deck
  And creates the session
  Then the session uses the edited estimation deck
  And the deck values appear in the same order entered by the Scrum Master
```

---

### 6.2 Join Session

```gherkin
Feature: Join planning session

Scenario: Participant joins as voter
  Given a planning session exists
  When a participant opens the session link
  And enters a display name
  And joins with the default role
  Then the participant enters the session as a voter
  And the participant appears in the participant list
```

```gherkin
Scenario: Participant joins as spectator
  Given a planning session exists
  When a participant opens the session link
  And enters a display name
  And selects spectator mode
  Then the participant enters the session as a spectator
  And the participant cannot vote
```

---

### 6.3 Start Round

```gherkin
Feature: Start voting round

Scenario: Scrum Master starts a round without a round name
  Given the Scrum Master owns the session
  And the session is waiting for a round
  When the Scrum Master starts a round without entering a round name
  Then the system starts a voting round
  And voters can see the estimation deck buttons
```

```gherkin
Scenario: Scrum Master starts a round with a round name
  Given the Scrum Master owns the session
  And the session is waiting for a round
  When the Scrum Master enters a round name
  And starts the round
  Then the system starts a voting round
  And the round displays the entered round name
```

---

### 6.4 Vote

```gherkin
Feature: Submit vote

Scenario: Voter selects one estimation value
  Given a voting round is active
  And a participant is a voter
  When the voter clicks one estimation button
  Then the system records that value as the voter's vote
  And the system shows that the voter has voted
  And the vote value remains hidden from other users
```

```gherkin
Scenario: Voter changes vote before reveal
  Given a voting round is active
  And a voter has already selected a vote value
  When the voter clicks a different estimation button before reveal
  Then the system replaces the previous vote with the new vote
  And the voter still has only one recorded vote for the round
```

```gherkin
Scenario: Spectator cannot vote
  Given a voting round is active
  And a participant is a spectator
  When the spectator views the estimation deck
  Then the spectator cannot submit a vote
```

---

### 6.5 Reveal Votes

```gherkin
Feature: Reveal votes

Scenario: Scrum Master reveals submitted votes
  Given a voting round is active
  And one or more voters have submitted votes
  When the Scrum Master reveals votes
  Then all submitted vote values are displayed
  And voters who did not vote are shown as missing votes
  And spectators are not counted as voters
```

```gherkin
Scenario: Participant cannot reveal votes
  Given a voting round is active
  And a participant is not the Scrum Master
  When the participant views the session controls
  Then the participant cannot reveal votes
```

---

### 6.6 Median

```gherkin
Feature: Display median

Scenario: System calculates median from numeric votes
  Given votes have been revealed
  And the submitted votes include numeric values
  When the system displays round results
  Then the system displays the median of numeric votes
```

```gherkin
Scenario: System excludes non-numeric votes from median
  Given votes have been revealed
  And the submitted votes include numeric and non-numeric values
  When the system calculates the median
  Then the system excludes non-numeric values from the median calculation
```

```gherkin
Scenario: Median unavailable when no numeric votes exist
  Given votes have been revealed
  And no submitted votes are numeric
  When the system displays round results
  Then the system displays that the median is unavailable
```

---

### 6.7 Record Final Estimate

```gherkin
Feature: Record final estimate

Scenario: Scrum Master records final estimate after reveal
  Given votes have been revealed
  And the Scrum Master has facilitated team discussion outside the app
  When the Scrum Master records a final estimate
  Then the final estimate is saved for the current round
  And the final estimate is displayed in the round results
```

---

### 6.8 Re-Vote

```gherkin
Feature: Re-vote current round

Scenario: Scrum Master starts a re-vote
  Given votes have been revealed for the current round
  When the Scrum Master starts a re-vote
  Then previous votes for the current round are cleared
  And the round name is preserved
  And voters can submit new votes
```

---

### 6.9 Multiple Rounds

```gherkin
Feature: Multiple rounds

Scenario: Scrum Master starts another round after recording final estimate
  Given the Scrum Master has recorded a final estimate for the current round
  When the Scrum Master starts the next round
  Then the system creates a new round
  And previous round results remain separate from the new round
```

---

### 6.10 End Session

```gherkin
Feature: End session

Scenario: Scrum Master ends session
  Given a session is active
  When the Scrum Master ends the session
  Then the session is marked as ended
  And no new rounds can be started
  And no new votes can be submitted
```

---

## 7. MVP Definition of Done

The MVP is done when:

- Session creation works locally.
- Unique shareable session link works locally.
- Participants can join with display names.
- Participants can join as voters or spectators.
- Scrum Master can start a round.
- Participants can vote using deck buttons.
- Each voter can select exactly one vote value per round.
- Votes remain hidden before reveal.
- Scrum Master can reveal votes.
- Median displays after reveal.
- Scrum Master can record final estimate.
- Scrum Master can start a re-vote.
- Scrum Master can run multiple rounds in one session.
- Scrum Master can end the session.
- MVP has been manually tested.
- MVP has basic automated test coverage for critical logic.
- MVP has been committed to Git.
- MVP has been pushed to GitHub.
- MVP has been deployed when practical.
- `DEVLOG.md` has been updated.

---

## 8. MVP Exit Criteria

The MVP can be considered complete when a real or simulated team can successfully run this demo:

1. Scrum Master creates a session named `Sprint Planning`.
2. Scrum Master uses a custom or default estimation deck.
3. Scrum Master shares the session link.
4. Three voters join the session.
5. One spectator joins the session.
6. Scrum Master starts a round named `US-1234`.
7. Each voter selects one vote button.
8. Votes remain hidden before reveal.
9. Scrum Master reveals votes.
10. System displays all submitted votes.
11. System displays median.
12. Scrum Master records final estimate.
13. Scrum Master starts a second round.
14. Scrum Master runs a re-vote.
15. Scrum Master ends the session.

---

## 9. Recommended First Build Sequence

This is not a technical architecture. It is a product slicing recommendation.

### Slice 1: Static Session Creation UI

Visible accomplishment:

- Home page with create session form.
- Session name field.
- Deck field.
- Create button.

### Slice 2: Create Session and Show Session Page

Visible accomplishment:

- Create session works.
- Session page displays session name, deck, and share link.

### Slice 3: Join Session

Visible accomplishment:

- Participant can open link, enter name, and join.

### Slice 4: Start Round

Visible accomplishment:

- Scrum Master can start a named or unnamed round.

### Slice 5: Vote Buttons

Visible accomplishment:

- Voters can click one deck button.
- Vote status updates.

### Slice 6: Reveal and Median

Visible accomplishment:

- Scrum Master reveals votes.
- Median displays.

### Slice 7: Final Estimate and Next Round

Visible accomplishment:

- Scrum Master records final estimate.
- Scrum Master starts next round.

### Slice 8: Re-Vote and End Session

Visible accomplishment:

- Scrum Master can re-vote.
- Scrum Master can end session.

---

## 10. Product Decision Summary

The MVP is intentionally small.

It includes only the workflow needed to run a live Planning Poker session.

It does not include accounts, teams, dashboards, session history, integrations, or paid features.

The MVP includes session-level deck customization because teams often use different estimation systems.

The deck appears as vote buttons.

Each voter selects exactly one value per round.

Median is informational only.

The Scrum Master records the final estimate after offline discussion.
