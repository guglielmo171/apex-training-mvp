# APEX Training — Changelog

## [1.3.0] — 2026-04-19

### Added
- **Multi-day workout plans** — plans now contain multiple configurable days, each with its own exercise sequence.
- **Per-day exercise parameters** — every exercise inside a plan day can define its own sets, reps, and rest time.
- **Athlete plan assignment state** — athletes now track `planId`, `currentDayIndex`, `completedExerciseIds`, and completed day history.
- **Sequential day progression** — completing all exercises in the current day advances the athlete to the next plan day.
- **Automatic cycle reset** — completing the final day of a plan resets the athlete back to Day 1 for the next cycle.
- **Completed day history** — coach athlete detail now surfaces previously completed days.

### Changed
- Workout screen now renders only the exercises for the athlete's current plan day instead of the global exercise catalog.
- Athlete home now reflects the assigned plan, current day, day progress, estimated duration, and plan day tracker.
- Coach home and athlete detail now calculate progress from the assigned plan day instead of flat `progress` / `total` counters.
- Plan assignment now replaces the previous plan, resets the athlete to Day 1, and clears current-day exercise completion.
- Plan editor now works day-by-day: add/remove days, rename each day, add/remove exercises per day, and edit sets/reps per exercise.
- Coach chat pinned session note now uses the athlete's current structured plan/day label.

### Removed
- Flat workout template model based on one `exerciseIds` array reused for every workout day.
- Athlete plan strings and flat progress counters as the source of truth for assigned workout state.

---

## [1.2.0] — 2026-04-19

### Added
- **Exercise set/rest tracker** — sticky bottom bar in Exercise Detail screen with 4 states:
  - `IDLE` — "Start Set N of N · X reps" CTA button + set progress segments
  - `ACTIVE` — elapsed timer counting up (MM:SS), reps reminder, "Set N Done" button
  - `RESTING` — SVG ring countdown, rest seconds remaining (turns red ≤ 5s), elapsed label, Skip button; auto-advances to next set when done
  - `COMPLETE` — confirmation card + "Back to Workout" button; auto-marks exercise as done in workout progress
- Timer state resets whenever a new exercise is opened
- Completing all sets from the detail screen marks the exercise as done on the workout list (no double-tap needed)

### Changed
- Exercise Detail screen is now a proper flex-column layout (video → scrollable detail → sticky timer bar)
- Removed excess bottom padding from exercise detail content area

---

## [1.1.0] — 2026-04-19

### Added
- **Workout timer** — chip in workout header (top-right). Tap START to begin session; shows elapsed time MM:SS. Tap again to pause/resume. Chip turns grey when paused.
- **"Begin Session" banner** — shown at top of exercise list before session starts. Replaced by live status pill ("Session in progress" / "Session paused") once started.
- **Rest timer bottom sheet** — slides up automatically after each exercise is checked (only when session is active, not on last exercise).
  - SVG ring countdown draining in real time
  - Ring turns red when ≤ 5 seconds remain
  - Displays: exercise name, total rest seconds, elapsed, next exercise preview
  - "Skip →" button to dismiss early
  - Auto-dismisses after 0.9s with "✓" flash on completion

---

## [1.0.0] — 2026-04-19

### Added
- Initial MVP prototype — single HTML file, no backend
- iPhone-style frame (393×852px) with Dynamic Island, status bar, side buttons, home indicator
- Hash-based routing — `#home`, `#workout`, `#exercise`, `#feedback`
- Slide transitions between screens (CSS transform + opacity)

**Home screen**
- Athlete greeting with avatar and online indicator
- Today's workout hero card (gradient, difficulty badge, CTA)
- Weekly progress ring (SVG, animated on load) + streak + volume stats
- Day tracker (M–F dots with completion state)
- Coach message preview card (taps to Chat)
- Bottom tab bar with notification dot on Chat

**Workout screen**
- Sticky header with workout name, duration, difficulty, progress text
- Animated progress bar (updates on exercise completion)
- Exercise list: name, muscle badge (color-coded by group), sets×reps, rest time, video play button
- Animated lime checkboxes (spring animation on check/uncheck, line-through on done)
- Workout complete modal with kcal + duration stats

**Exercise Detail screen**
- Simulated video player with scrubber, play/pause, seek, skip controls
- Animated play-ring pulse
- Numbered step-by-step instructions
- Muscle tags + sets×reps + rest badges
- Per-exercise Coach Marco note (pinned card)

**Chat screen**
- Coach header with online status indicator
- Pinned session note (lime accent card)
- Message thread (coach + athlete bubbles)
- Functional message input — send on Enter or button tap
- Typing indicator (animated dots) + randomised coach auto-reply
- Input border glows lime on focus
