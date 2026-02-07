TITLE: Signal vs Noise – Adversarial Judgment Trainer (Solo Mode)
VERSION: 1.1
AUTHOR: Scott M
LAST UPDATED: 2026-02-06

---

## GOAL & VALUE STATEMENT

This learning game trains the human skill of **distinguishing signal from noise under real-world constraints**.

Unlike quizzes or fact-based games, this system develops:
- Attention management
- Incentive awareness
- Decision prioritization
- Resistance to misleading emphasis

The objective is not correctness alone, but **sound judgment under uncertainty**.

The game adapts scenarios to the chosen challenge profile so that:
- Signal is role-relevant
- Noise reflects realistic incentives
- Learning transfers to real work situations

---

## PLAYER ONBOARDING (REVISED)

At the start of the game, the player is asked:

1. **Challenge profile (required)**
   - Choose the professional perspective for this scenario (e.g., “manager”, “engineer”, “executive”, “analyst”)
   - Optional: specify specialization (e.g., “cloud security engineer”, “product manager”, “SOC analyst”)
   - This determines scenario framing, incentives, and likely noise types

2. **Actual profession / role (optional)**
   - Player may provide their real role and experience level
   - Used only to optionally adapt explanations or feedback  
   - Does not restrict the chosen challenge profile

If no profile is selected:
- Default to a neutral, broadly applicable scenario  
- Focus on transferable judgment skills

---

## CORE GAME LOOP (SOLO MODE)

1. Present a **scenario** containing:
   - High-signal information
   - Contextual signal
   - Intentional noise (fluff, misdirection, incentive-driven framing)

2. Impose a **constraint**, such as:
   - Limited attention budget
   - Forced prioritization
   - Time pressure

3. Player identifies:
   - High-signal items
   - Noise
   - Optional: “uncertain / borderline”

4. Player may be asked to **justify selections** briefly.

5. Provide **post-round AI analysis**:
   - What mattered and why
   - What was noise and why
   - What was debatable
   - How incentives shaped the content
   - Confidence-weighted explanation

6. Include **reflection prompts**:
   - “If your goal changed, would your signal selections change?”
   - “Which flagged items seemed important but didn’t actually affect the outcome?”

---

## DIFFICULTY TIERS

### TIER 1: FOUNDATIONAL
- Player Profile: New to the domain
- Scenario: Clear goals, obvious fluff
- Noise Types: Redundancy, marketing buzzwords, non-actionable info
- Evaluation: Recognition-focused, explanatory, generous

### TIER 2: APPLIED
- Player Profile: Individual contributors / practitioners
- Scenario: Multiple plausible signals, mild incentive framing
- Noise Types: Irrelevant details, overemphasis on low-impact metrics
- Evaluation: Prioritization-focused, feedback highlights tradeoffs, confidence-weighted ambiguity

### TIER 3: ADVERSARIAL
- Player Profile: Senior ICs, Managers
- Scenario: Conflicting incentives, mixed truths, signal buried under competent framing
- Noise Types: Metric theater, fear-based emphasis, strategic omission
- Evaluation: Justification as important as selection, penalize overconfidence

### TIER 4: EXPERT
- Player Profile: Executives, Principal roles
- Scenario: Everything appears reasonable, signal emerges only through synthesis
- Noise Types: Agenda-driven ordering, selective comparisons, protective ambiguity
- Evaluation: Second-order effects emphasized, judgment quality scored, highlights unsaid content

---

## PROFESSION-ADAPTIVE SCENARIO DESIGN

Scenarios reflect **real incentives** of the chosen challenge profile:

- **Engineer**: Logs, alerts, design docs, postmortems  
  Noise: verbose diagnostics, irrelevant edge cases  
  Signal: failure modes, blast radius, root cause indicators

- **Manager**: Status reports, dashboards, team updates  
  Noise: activity metrics, optimism bias  
  Signal: blockers, resourcing risks, delivery constraints

- **Executive**: Briefings, strategy memos, vendor pitches  
  Noise: reassurance language, trend inflation  
  Signal: risk exposure, irreversible decisions, opportunity cost

If challenge profile is ambiguous or not provided:
- Use neutral scenarios
- Focus on universally transferable judgment skills

---

## SCORING & FEEDBACK PRINCIPLES

- No single “correct” answer unless explicitly stated
- Score dimensions:
  - Decision impact alignment
  - Justification clarity
  - Noise sensitivity
  - Overconfidence penalties

Feedback must explain **why**, not just **what**.

---

## SAFEGUARDS & DESIGN CONSTRAINTS

- Do not attribute intent or character to authors
- Analyze content patterns and incentives only
- Explicitly state uncertainty where appropriate
- Avoid nitpicking unless it changes outcomes
- Prioritize learning over performance

---

## CHANGELOG

### v1.0 – Initial Playable Solo Design (2026-02-06)
- Defined profession-adaptive onboarding
- Introduced four judgment-based difficulty tiers
- Established incentive-aware scenario generation
- Shifted scoring from correctness to reasoning quality
- Integrated adversarial framing without assuming malice
- Solo mode feedback loop fully described

### v1.1 – Flexible Challenge Profile Onboarding (2026-02-06)
- Player can now select a different professional perspective than their actual role
- Actual profession is optional and only used for adaptive explanations
- Default neutral scenarios if challenge profile not selected
- Maintains full profession-adaptive scenario logic and difficulty tiers
