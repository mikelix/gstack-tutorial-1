# Gstack Team Mode — Collaborator Guide

This guide walks you through participating in team-based project review using gstack.

## Your Role: What You'll Do

You'll collaborate with your project owner using specialized AI reviews:
- **Planning**: Break down tasks, timelines, dependencies
- **QA/Testing**: Find bugs, verify functionality, test coverage
- **Architecture Review**: Evaluate design decisions (if needed)

You work **asynchronously** — no real-time meetings required. Reviews happen in parallel, findings shared in Conductor.

## Prerequisites

✓ Git installed (`git --version`)
✓ Claude Code installed (`claude --version`)
✓ Access to this repository (GitHub clone link from owner)
✓ Conductor workspace invite from owner (for async chat)

## Step 1: Clone the Repository

```bash
# Get the repo URL from the owner
git clone https://github.com/OWNER/hello_world.py
cd hello_world.py

# Verify you have the files
ls -la
# You should see: hello_world.py, PLAN.md, README.md, COLLABORATOR_GUIDE.md
```

## Step 2: Understand the Project

Before running any reviews:

```bash
# 1. Read the project overview
cat README.md

# 2. Read the plan
cat PLAN.md

# 3. Run the code to understand what it does
python hello_world.py
# Output: hello world
```

**Key questions to answer for yourself:**
- What problem does this solve?
- What are the success criteria?
- What's the timeline?
- What risks exist?

## Step 3: Choose Your Review Role

### Option A: Project Manager / Planning Review

**Your task:** Break down the plan into actionable tasks, timeline, dependencies.

```bash
# Run the spec review
/spec PLAN.md

# This will:
# ✓ Ask clarifying questions about the plan
# ✓ Break down into concrete tasks
# ✓ Identify dependencies and risks
# ✓ Propose timeline
# ✓ Create tasks.md artifact
```

**Output to share:**
- Task breakdown (who does what, in what order)
- Timeline (Hour 1, Day 1, Week 1...)
- Critical path (what blocks what)
- Risk assessment (what could go wrong)

**Post in Conductor:** Share the task breakdown in `#planning` channel

---

### Option B: QA Engineer / Testing Review

**Your task:** Test the code, find bugs, verify quality.

```bash
# Run QA review (reporting mode — no fixing)
/qa-only

# This will:
# ✓ Run the code multiple ways
# ✓ Test edge cases
# ✓ Check for bugs
# ✓ Verify test coverage
# ✓ Create qa-results.md artifact
```

**Output to share:**
- Bug list (if any)
- Test scenarios you ran
- Coverage assessment (what's tested vs untested)
- Edge cases to handle
- Deployment readiness (green light or blockers?)

**Post in Conductor:** Share the QA report in `#qa-report` channel

---

### Option C: Architecture / Code Review

**Your task:** Evaluate the design and code quality.

```bash
# Run engineering review
/plan-eng-review PLAN.md

# This will:
# ✓ Review architecture
# ✓ Check code quality
# ✓ Propose test plan
# ✓ Identify technical debt
# ✓ Create architecture.md artifact
```

**Output to share:**
- Design evaluation
- Code quality assessment
- Test strategy recommendations
- Technical debt or shortcuts identified
- Deployment considerations

**Post in Conductor:** Share findings in `#engineering` channel

---

## Step 4: During Your Review

### What the Skill Does

When you run `/spec`, `/qa-only`, or `/plan-eng-review`, Claude Code will:

1. **Ask you questions** — Answer them honestly. These drive the analysis.
2. **Generate artifacts** — Documents, diagrams, tables, checklists
3. **Create audit trail** — Every decision is logged and timestamped
4. **Produce findings** — Summary of issues, recommendations, risks

### If You Get Stuck

**Q: The skill is asking confusing questions?**
- Answer as best you can. There are no wrong answers.
- If genuinely unsure, skip the question or reply "not sure yet"

**Q: The skill generated something I disagree with?**
- You can edit the outputs manually
- Make notes in Conductor for discussion with the owner

**Q: I want to see what the owner found in their review?**
- Check Conductor workspace
- The owner should have posted their findings there

## Step 5: Share Your Findings

### Where to Post (Conductor Workspace)

Your project owner created a Conductor workspace for team chat. Post your findings there:

**Channels:**
- `#planning` — Task breakdown, timeline, dependencies
- `#qa-report` — Bugs, test results, coverage
- `#engineering` — Architecture, code quality, tech debt
- `#decisions` — Major decisions made during reviews
- `#general` — Questions, clarifications, coordination

**Format for posting findings:**

```
🔍 QA Review Complete

Status: ✅ All tests passed

Key Findings:
- 0 bugs found
- 100% of happy paths tested
- Edge case: large input (>1000 chars) — untested
- Ready for deployment

See attached: qa-results.md

Questions for owner:
- Should we test with very large inputs?
- Do we need monitoring in prod?
```

## Step 6: Wait for Owner's Review

After you post your findings:

1. **Owner reviews** your findings in Conductor
2. **Owner decides** whether to address your recommendations
3. **Owner posts** their own reviews (CEO, Engineering, Deployment)
4. **You discuss** any disagreements in Conductor

**This is async** — don't wait for real-time responses. Check in daily.

## Step 7: Track Decisions

Every review generates decisions. These are logged automatically:

**Decision Log** (in Conductor, updated continuously):
- Decision 1: [topic] → [choice] (by whom, when)
- Decision 2: [topic] → [choice] (by whom, when)
- Decision 3: [topic] → [choice] (by whom, when)

**Why it matters:** If something goes wrong later, the decision log shows why we chose this path.

## Example: Your First QA Review

```bash
# 1. Get the repo
git clone https://github.com/OWNER/hello_world.py
cd hello_world.py

# 2. Understand what you're testing
cat PLAN.md
python hello_world.py

# 3. Run the QA review
/qa-only

# The skill will ask:
# ❓ "What are the critical features to test?"
#    → Reply: "The print statement works, handles different inputs"
# 
# ❓ "What edge cases concern you?"
#    → Reply: "Empty input, very long strings, special characters"
#
# ❓ "What's the test environment?"
#    → Reply: "Python 3.9+, Linux/Mac/Windows"

# 4. Review the generated qa-results.md

# 5. Post findings to Conductor
#    Channel: #qa-report
#    Message: "QA review complete — 0 bugs, edge cases documented"
```

## Common Tasks During Reviews

### "Update a finding"
```bash
# If you want to amend your review findings:
vim qa-results.md       # Edit the file
git add qa-results.md
git commit -m "QA: updated findings after further testing"
git push
```

### "Comment on owner's findings"
```bash
# Post in Conductor — don't edit the original review
```

### "Ask the owner a question"
```bash
# Post in Conductor #general channel
# Wait for async response
```

### "Disagree with a decision"
```bash
# Post your alternative view in Conductor
# Reference the Decision Log: "Decision #3 should have been..."
# Owner will discuss or update the log
```

## Checklist: Before Declaring Review Complete

- [ ] Ran the appropriate skill (`/spec`, `/qa-only`, or `/plan-eng-review`)
- [ ] Answered all questions honestly
- [ ] Reviewed generated artifacts (task list, QA report, architecture)
- [ ] Posted findings to Conductor in the right channel
- [ ] Included a summary (status, key findings, questions for owner)
- [ ] Committed any manual edits to git (`git push`)
- [ ] Waited for owner to respond (24-48 hours typical)

## After All Reviews Are Done

Once all team members have posted findings:

1. **Owner reviews everything** in Conductor
2. **Team discusses** any disagreements (async in Conductor)
3. **Owner makes final decisions** and updates PLAN.md
4. **Owner runs** `/ship` to deploy
5. **Everyone celebrates** ✨

## Questions?

| Q | A |
|---|---|
| **Can I edit the generated artifacts?** | Yes, edit them and commit to git. Note changes in Conductor. |
| **What if I find a critical bug?** | Post immediately in Conductor. Owner may ask you to run `/qa-only` again to confirm. |
| **Do I need Claude Code Pro?** | No, basic Claude Code works. Some skills have Pro features (optional). |
| **Can I see the owner's reviews before they're done?** | Only if they share them in Conductor. Async reviews mean checking in 1-2x per day. |
| **What if I disagree with a decision?** | Post in Conductor with your reasoning. The team discusses and decides together. |
| **Do I need to push my findings to GitHub?** | Share the findings in Conductor. Push to GitHub if you made code changes. |

---

**You're ready!** Start with Step 1 (clone repo), then pick your review role (A, B, or C) and run the corresponding skill.

Any questions? Post in Conductor `#general` channel.
