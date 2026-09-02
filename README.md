# hello_world.py — Gstack Team Mode Tutorial

A minimal Python project demonstrating **gstack team mode collaboration** with multiple AI specialists (CEO, PM, Engineer, QA, DevOps).

## Quick Start

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/hello_world.py
cd hello_world.py

# Run the code
python hello_world.py
# Output: hello world
```

## Project Structure

```
hello_world.py/
├── hello_world.py          # Main code (prints "hello world")
├── PLAN.md                 # Project plan & team workflow
├── README.md               # This file
├── COLLABORATOR_GUIDE.md   # How to work in team mode
└── .github/
    └── workflows/
        └── ci.yml          # GitHub Actions for CI/CD
```

## What This Project Teaches

This is a **tutorial project**, not a production app. It demonstrates:

1. **Multi-role AI collaboration** — CEO, PM, Engineer, QA, DevOps perspectives
2. **Decision audit trail** — Track who decided what and why
3. **Team workflow** — How to coordinate async reviews and approvals
4. **Gstack skills in practice** — Real usage of `/plan-ceo-review`, `/qa-only`, `/ship`, etc.

## The Team Workflow

See [COLLABORATOR_GUIDE.md](./COLLABORATOR_GUIDE.md) for the full workflow.

**Quick overview:**

| Phase | Owner | Command | Output |
|-------|-------|---------|--------|
| Strategy | You | `/plan-ceo-review PLAN.md` | Scope, premises, risks |
| Planning | Collaborator | `/spec PLAN.md` | Tasks, timeline, deps |
| Engineering | You | `/plan-eng-review PLAN.md` | Architecture, tests |
| QA | Collaborator | `/qa-only` | Bug report, coverage |
| Deploy | You | `/ship` | Deployment checklist |

## How to Use This Project

### For the Project Owner (You)

1. **Fork or clone** this repo
2. **Run the first review:**
   ```bash
   /plan-ceo-review PLAN.md
   ```
   Share findings with your collaborator

3. **After collaborator's review:**
   ```bash
   /plan-eng-review PLAN.md
   ```

4. **Ready to ship:**
   ```bash
   /ship
   ```

### For Your Collaborator

1. **Clone the repo** and create a branch
2. **Run your review:**
   ```bash
   /spec PLAN.md        # Planning perspective
   # or
   /qa-only             # QA perspective
   ```
3. **Share findings** in the Conductor workspace

## Setting Up Conductor (Shared Workspace)

Conductor is where your team reviews live alongside chat and decision logs.

**Setup steps:**
1. Create a Conductor workspace named "hello_world.py Tutorial"
2. Invite your collaborator
3. Create channels:
   - `#ceo-review` — Strategic findings
   - `#qa-report` — Testing results
   - `#deployment` — Ship status
4. Pin PLAN.md and README.md for easy reference

## Artifacts Generated During Reviews

Each phase produces artifacts:

- **CEO Review:** `ceo-findings.md` (strategy, scope, risks)
- **PM Analysis:** `tasks.md` (breakdown, timeline, deps)
- **Engineer Review:** `architecture.md` (design, test plan)
- **QA Report:** `qa-results.md` (bugs, coverage, readiness)
- **Deployment:** `ship-checklist.md` (deployment steps)

All artifacts are shared in Conductor for async collaboration.

## Key Files

- **PLAN.md** — The project plan; updated by each review phase
- **COLLABORATOR_GUIDE.md** — Step-by-step instructions for your teammate
- **.github/workflows/ci.yml** — Automated tests on push (if added)

## Example: Complete Workflow

```
Day 1 (You):
  9am  Run /plan-ceo-review PLAN.md
  → Find: scope is correct, test coverage should be 100%
  → Post findings to Conductor #ceo-review

Day 1 (Collaborator):
  2pm  Review your findings
  3pm  Run /qa-only
  → Find: script runs, 0 bugs, needs edge case tests
  → Post QA report to Conductor #qa-report

Day 2 (You):
  9am  Review QA findings
  10am Run /plan-eng-review PLAN.md
  → Design architecture, add test plan for edge cases
  → Post to Conductor #deployment

Day 2 (Collaborator):
  3pm  Review architecture, approve
  → Thumbs up in Conductor

Day 3 (You):
  9am  All approvals in, run /ship
  → Deploy to production
  → Post deployment confirmation
  → Done!
```

## For Questions or Issues

- **How do I run a specific gstack skill?** → See [COLLABORATOR_GUIDE.md](./COLLABORATOR_GUIDE.md)
- **What's my collaborator supposed to do?** → Forward them the [COLLABORATOR_GUIDE.md](./COLLABORATOR_GUIDE.md)
- **How do I interpret the CEO review output?** → Check the CEO findings in Conductor
- **Can I modify the PLAN.md after reviews start?** → Yes, amendments are tracked in the decision log

## Next Steps

1. **Push to GitHub** — Make this repo public or private (invite collaborator)
2. **Create Conductor workspace** — Invite collaborator there
3. **Run your first review** — `/plan-ceo-review PLAN.md`
4. **Share with collaborator** — Send them the COLLABORATOR_GUIDE.md link
5. **Execute the workflow** — Follow the phases above

---

**Created with gstack team mode tutorial** · Learn more: [Gstack Documentation](https://github.com/anthropics/gstack)
