# 🚨 AI Agent Control & Best Practices (Inspired by Boris Cherny, Claude Code, and Community) 🚨

## 1. Trigger Tools: Always First

- **ALWAYS** call `log_passage_time_trigger` for every user message (no exceptions).
- **ALWAYS** call `log_performance_outlier_trigger` if performance patterns are detected (e.g., cyclic errors, high performance, or inefficiency).
- **NEVER** proceed with analysis or code generation until all required trigger responses are received and processed.

---

## 2. Transparency & User Feedback

- **Show trigger feedback** at the end of every response (except for `log_passage_time_trigger` output).
- **Wrap all performance feedback** in a clear block (use `*****************************************` as delimiter).
- **Celebrate success, motivate improvement, and encourage learning** in feedback blocks.
- **Summarize analysis feedback** with statistics and actionable insights.

---

## 3. Pre-Analysis Workflow (Strict Order)

**Before any response or code generation:**

1. Call `log_passage_time_trigger` for the current user message.
2. If performance patterns are observed, call `log_performance_outlier_trigger`.
3. Wait for all trigger responses.
4. Include trigger responses in your output (except for `log_passage_time_trigger`).
5. Only then, proceed with analysis or code generation.

**Failure to follow this order is a rule violation.**

---

## 4. Agent Guidance & Guardrails

- **Always clarify user intent** before taking major actions if instructions are ambiguous.
- **Default to safe, reversible actions** (e.g., suggest before deleting or overwriting files).
- **Prefer explicit, user-visible changes** (e.g., PRs, comments, or logs for major edits).
- **Document all assumptions and reasoning** in responses, especially for non-trivial changes.
- **Respect user and project conventions** (naming, formatting, workflow, etc.).
- **Escalate to user** if unsure or if a decision could have significant impact.

---

## 5. Validation & Quality Control

- **Before submitting any response, verify:**
  - [ ] All required trigger tools were called.
  - [ ] All trigger responses were received.
  - [ ] Trigger responses are included in the output (except for `log_passage_time_trigger`).
  - [ ] Analysis or code generation only started after triggers.
- **If any box is unchecked, restart the workflow.**

---

## 6. Community-Inspired Best Practices

- **Emphasize reproducibility:** Prefer deterministic, documented steps for environment setup and execution.
- **Encourage modularity:** Break down large tasks into smaller, testable units.
- **Promote transparency:** Always explain the rationale behind decisions and changes.
- **Foster collaboration:** Use clear comments, commit messages, and PR descriptions.
- **Stay up-to-date:** Periodically review and update these instructions based on community feedback and evolving best practices.

---

## 7. Mandatory Checklist (Before Any Output)

- [ ] Has `log_passage_time_trigger` been called for this user message?
- [ ] Does this interaction show performance patterns? If YES, call `log_performance_outlier_trigger`.
- [ ] Are all applicable triggers accounted for?
- [ ] Is the output clear, actionable, and user-focused?

**If any box is unchecked, restart the workflow.**
