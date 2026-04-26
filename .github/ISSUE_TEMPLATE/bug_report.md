---
name: Bug Report
about: Report unexpected behavior in an agent mode
title: "fix(<mode-slug>): <brief description>"
labels: bug, triage
assignees: ''
---

## 🐛 Bug Description

A clear description of what the unexpected behavior is.

## 🤖 Affected Mode

Which mode(s) are affected? Check all that apply:

- [ ] Orchestrator (`orchestrator`)
- [ ] Ask (`ask`)
- [ ] Architect (`architect`)
- [ ] Subtask Orchestrator (`subtask-orchestrator`)
- [ ] Git (`git`)

## 📋 Steps to Reproduce

1. Import the affected mode YAML into Roo Code
2. Activate the mode and provide the following prompt: _'...'_
3. Observe the behavior at step...
4. ...

## ✅ Expected Behavior

What did you expect the mode to do according to the pipeline?

## ❌ Actual Behavior

What actually happened? Include any relevant output or observed behavior.

## 🔗 Pipeline Impact

Does this affect the orchestration pipeline? If so, how?

- [ ] Blocks downstream modes from functioning
- [ ] Produces incorrect output that propagates
- [ ] Causes mode to exit prematurely
- [ ] Violates the pipeline protocol (e.g., unauthorized mode switch)
- [ ] No pipeline impact — isolated issue

## 📎 Context

- **Roo Code version:**
- **VS Code version:**
- **Mode YAML file version/commit:** 
- **Other active modes during the session:**

## 📝 Additional Information

Any other context, logs, or screenshots that help explain the issue.
