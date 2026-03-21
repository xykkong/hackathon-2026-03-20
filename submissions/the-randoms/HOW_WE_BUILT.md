# How We Built This

## Project Goal

Build an AI speaking coach (LexiCoach) where learners practice target vocabulary in real-time conversation with an avatar, receive corrections, and retry naturally.

## Model Choices

### Development-time AI (coding and docs)

- Primary assistant: Codex (GPT-5 family) in agent mode
- Why: fast repository refactoring, command execution, and iterative doc/code updates in one loop
- Used for: code organization, README updates, setup cleanup, and implementation guidance

### Runtime AI (inside the product)

- Conversational LLM: OpenAI-compatible provider configured by environment variables (`VIDEO_*` in backend env)
- Why: provider-agnostic setup from Agora sample architecture, easy switching without code rewrite
- Used for: dialogue generation, corrective feedback, and vocabulary coaching behavior

## Prompting Strategy

We used short, task-specific prompts and iterated from broad to precise instructions.

### Prompt examples (development)

1. "Reorganize this submission so all runnable code is under `submissions/the-randoms/src` and update all docs to match."
2. "Rewrite README with exact startup commands and remove machine-specific absolute paths."
3. "Create a `CODE_ORGANIZATION.md` that explains where frontend/backend/custom LLM code lives."
4. "Update HOW_WE_BUILT with concrete model choices, prompt examples, and iteration notes."

### Prompt examples (product behavior)

1. "You are a supportive English speaking coach. Prioritize target vocabulary usage in natural conversation."
2. "If learner usage is incorrect, give a short correction and ask for one retry in-context."
3. "Adapt difficulty to learner level and avoid long explanations during live speaking flow."

## Iteration Timeline

### Iteration 1: Baseline integration

- Started from Agora Conversational AI sample components
- Wired frontend avatar client + Python backend for local run
- Outcome: end-to-end call flow worked

### Iteration 2: Coaching behavior tuning

- Adjusted system prompt to focus on active vocabulary usage
- Tightened correction style (short feedback + retry)
- Outcome: conversations became more goal-oriented and less generic

### Iteration 3: Submission structure cleanup

- Moved runnable code into `src/`
- Updated README commands and paths
- Added dedicated docs for organization
- Outcome: cleaner handoff and hackathon-compliant folder layout

### Iteration 4: Documentation hardening

- Added explicit model-choice rationale
- Added prompt samples and iteration log
- Outcome: clearer evidence of AI craftsmanship and workflow

## Testing and Verification

- Manual E2E checks: start backend, start frontend, place a live call, verify avatar response and retry behavior.
- Config checks: validated that required `VIDEO_*` variables are present before runtime testing.
- Regression checks after refactors: revalidated startup commands and paths after moving code into `src/`.
- Documentation checks: confirmed README instructions and folder tree match the current repository layout.

## What AI Helped Most With

- Fast restructuring and path-safe refactors
- Prompt wording alternatives for coaching behavior
- Converting working notes into submission-ready documentation

## Human Decisions

- Defined product scope and success criteria
- Chose tradeoff: reliable demo over broader feature set
- Reviewed all AI-generated outputs before keeping them

## Challenges and Fixes

- Challenge: path drift after moving folders
  - Fix: updated docs and run commands immediately after each move
- Challenge: inconsistent coaching tone
  - Fix: constrained prompt style to short corrections + retry loop
- Challenge: multi-service setup complexity
  - Fix: documented required env variables and startup order

## What We Would Do Next

- Add automated evaluation for vocabulary-target hit rate
- Add session analytics dashboard for learner progress
- Add reusable prompt test cases for regression checks
