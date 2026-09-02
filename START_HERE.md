# START HERE: Gstack Team Mode Tutorial

Welcome! You're about to learn **gstack team mode** — collaborative AI-powered project reviews.

## What This Project Does

This is a **minimal tutorial project** (just prints "hello world") that demonstrates:
- ✅ Multiple AI team members reviewing the same project
- ✅ Async collaboration (no meetings needed)
- ✅ Decision audit trail (track who decided what)
- ✅ Parallel reviews with Conductor shared workspace

**Real project?** No. **Useful for learning?** Absolutely.

---

## Your Mission (Choose One)

### 🎯 Path A: Solo Tutorial (Learn How It Works)
**Time: 30 minutes**

1. Read `README.md` — Understand the project
2. Read `SETUP_INSTRUCTIONS.md` — Understand the workflow
3. Run: `/plan-ceo-review PLAN.md` — See CEO perspective
4. Done! You've learned the workflow.

**Outcome:** You understand how gstack team mode works.

---

### 🎯 Path B: With a Collaborator (Full Demo)
**Time: 2-3 days (async)**

1. **Today:**
   - Follow SETUP_INSTRUCTIONS.md phases 1-3
   - Create GitHub repo and push this code
   - Set up Conductor workspace
   - Invite collaborator

2. **Your collaborator:**
   - Clones repo
   - Reads COLLABORATOR_GUIDE.md
   - Runs `/qa-only` or `/spec PLAN.md`
   - Posts findings to Conductor

3. **You:**
   - Run `/plan-ceo-review PLAN.md`
   - Run `/plan-eng-review PLAN.md`
   - Review collaborator's findings
   - Run `/ship` to complete the workflow

4. **Done!** Full team mode workflow demonstrated.

**Outcome:** You've lived through the complete gstack team workflow with a real collaborator.

---

## File Guide

| File | Purpose | Read If... |
|------|---------|-----------|
| **START_HERE.md** | This file | You just cloned the repo |
| **README.md** | Project overview | You want quick context |
| **PLAN.md** | Project plan & goals | You want specifics on what to build |
| **SETUP_INSTRUCTIONS.md** | GitHub + Conductor setup | You're ready to collaborate |
| **COLLABORATOR_GUIDE.md** | Instructions for your teammate | You want to share with collaborator |
| **hello_world.py** | The actual code | You want to see what runs |

---

## 5-Minute Quickstart

```bash
# 1. Understand the code
python hello_world.py
# Output: hello world

# 2. Read the plan
cat PLAN.md

# 3. Run a quick CEO review
/plan-ceo-review PLAN.md

# 4. See what got generated
ls -la  # Look for new .md files

# 5. Read the summary in PLAN.md
# (It will be updated with CEO findings)
```

---

## Common Questions

**Q: Is this a real project?**
No. It's a teaching project. The code is intentionally minimal.

**Q: Do I need to modify the code?**
No. You'll review the existing code using gstack. Modifications are optional.

**Q: Do I need a collaborator?**
No. Path A (solo) works fine. But Path B (with collaborator) shows the real magic of team mode.

**Q: How long does this take?**
- Solo tutorial: **30 minutes**
- Full team workflow: **2-3 days** (async, no meetings)

**Q: Can I adapt this for my real project?**
100%. Once you finish this tutorial, you can:
```bash
# In your real project:
git clone https://github.com/YOUR_USERNAME/my_real_project
cd my_real_project
/plan-ceo-review .  # Review your real project
/qa-only             # QA your real project
/ship                # Ship your real project
```

**Q: What's the difference between this and running reviews one-at-a-time?**
Team mode = async parallel reviews + shared Conductor workspace + decision audit trail.
Instead of "I reviewed it, then you review it," it's "we all review it simultaneously in one workspace, then decide together."

---

## Next Steps

### If You're Learning Solo (Path A)

```bash
# 1. Read the overview
cat README.md

# 2. Understand the plan
cat PLAN.md

# 3. Run CEO review
/plan-ceo-review PLAN.md

# 4. See the generated findings
cat ceo-findings.md  # (if generated)

# 5. Explore what gstack skills do
# - /plan-ceo-review — Strategic review
# - /plan-eng-review — Architecture review
# - /qa-only — Quality assurance
# - /spec — Project breakdown
# - /ship — Deployment
```

### If You're Collaborating with Someone (Path B)

```bash
# 1. Follow SETUP_INSTRUCTIONS.md (phases 1-3)
cat SETUP_INSTRUCTIONS.md

# 2. Create GitHub repo
# (Instructions in SETUP_INSTRUCTIONS.md)

# 3. Set up Conductor workspace
# (Instructions in SETUP_INSTRUCTIONS.md)

# 4. Invite collaborator
# - GitHub repo URL
# - Conductor workspace link
# - Forward them: COLLABORATOR_GUIDE.md

# 5. Run your reviews
/plan-ceo-review PLAN.md
/plan-eng-review PLAN.md

# 6. Post findings to Conductor
# (Share the generated .md files)

# 7. When ready, deploy
/ship
```

---

## What You'll Learn

By the end of this tutorial, you'll understand:

✅ **What gstack team mode is** — Multiple AI specialists, async collaboration, shared decisions

✅ **How different roles contribute** — CEO (strategy), PM (tasks), Engineer (architecture), QA (quality), DevOps (deployment)

✅ **How to use Conductor** — Shared workspace for chat, artifacts, decision tracking

✅ **How to audit decisions** — Every decision is logged with who made it and why

✅ **How to scale this pattern** — Apply the same workflow to your real projects

---

## Support

**If you get stuck:**

1. **Check README.md** — Overall project context
2. **Check SETUP_INSTRUCTIONS.md** — GitHub/Conductor setup
3. **Check COLLABORATOR_GUIDE.md** — How to run a skill
4. **Run the skill again** — Sometimes a skill needs a retry

**If a gstack skill fails:**
```bash
# Get help with Claude Code
/help

# Get help with a specific skill
# (In your terminal, while running the skill)
# Most skills will explain what they're doing
```

---

## Let's Go!

**Choose your path:**
- **Learning solo?** Start with `cat README.md`
- **Collaborating?** Start with `cat SETUP_INSTRUCTIONS.md`

You've got this! 🚀

---

*Created with gstack* | Tutorial for team mode collaboration | [gstack docs](https://github.com/anthropics/gstack)
