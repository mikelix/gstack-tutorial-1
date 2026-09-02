# Setup Instructions: Team Mode Collaboration

This guide walks you through setting up GitHub and Conductor for team collaboration.

## Quick Summary of What You Have

✅ **Local project ready:**
- hello_world.py (the code)
- PLAN.md (project plan with tasks)
- README.md (project overview)
- COLLABORATOR_GUIDE.md (instructions for team member)
- .git/ (version control)

**Next:** Push to GitHub + invite collaborator + set up Conductor

---

## Phase 1: Set Up GitHub Repository

### Option A: Create New Repository on GitHub

1. **Go to github.com** → Sign in → Click **"New"** (top left, next to avatar)

2. **Create repository:**
   - Name: `hello_world.py`
   - Description: "Gstack team mode collaboration tutorial"
   - Visibility: **Public** (for tutorial visibility) or **Private** (for control)
   - Do NOT initialize with README (you have one already)
   - Click **"Create repository"**

3. **You'll see setup instructions. Follow them:**

```bash
# In your local directory (D:\temp\ai\claude):
git remote add origin https://github.com/YOUR_USERNAME/hello_world.py.git
git branch -M main
git push -u origin main
```

4. **Verify on GitHub:**
   - Go to your repo on github.com
   - You should see: README.md, PLAN.md, hello_world.py, etc.
   - Green "Code" button visible

### Option B: Use Existing Repository

If you already have a GitHub repo:

```bash
# Replace OWNER/REPO with your GitHub path:
cd D:\temp\ai\claude
git remote set-url origin https://github.com/YOUR_USERNAME/hello_world.py.git
git push -u origin main
```

---

## Phase 2: Invite Your Collaborator to GitHub

### If Repository is Public:
```
Just send them the GitHub URL:
https://github.com/YOUR_USERNAME/hello_world.py

They can clone and work immediately.
```

### If Repository is Private:

1. **Go to your GitHub repo** → **"Settings"** → **"Collaborators"**
2. **Click "Add people"**
3. **Enter collaborator's GitHub username** (e.g., `john_dev`)
4. **Select permission:** "Maintain" or "Push access"
5. **Click "Invite"**
6. **Send collaborator the repo URL**

Collaborator will get an invite email and can accept access.

---

## Phase 3: Set Up Conductor Workspace

Conductor is where your team shares reviews, chats, and decisions.

### Create Conductor Workspace

1. **Open Claude Code** or go to **claude.ai/code**
2. **Look for "Conductor"** or **"Team"** in the left sidebar
3. **Click "Create Workspace"** or **"New Team Project"**
4. **Fill in details:**
   - Name: `hello_world.py Tutorial`
   - Description: "Gstack team mode collaboration demo"
   - Visibility: Invite-only or public (your choice)
   - Link: Paste your GitHub repo URL (optional but recommended)

### Invite Collaborator to Conductor

1. **In Conductor workspace** → Click **"Invite"** or **"Team Members"**
2. **Enter collaborator's email** (same as their Claude account)
3. **Set role:** "Editor" (can run reviews and post findings)
4. **Send invite**
5. **Share workspace link with collaborator**

### Create Channels (optional but helpful)

Conductor channels organize findings by type:

1. **#ceo-review** — Strategic findings (you post here)
2. **#planning** — Task breakdown, timeline (collaborator posts here if doing PM role)
3. **#qa-report** — Bug reports, test results (collaborator posts here if doing QA)
4. **#engineering** — Architecture, code quality (collaborator posts here if doing eng review)
5. **#decisions** — Decision log (track what was decided)
6. **#general** — Questions, clarifications

---

## Phase 4: Start the Team Workflow

### You (Project Owner): Run CEO Review

```bash
cd D:\temp\ai\claude

# Run the CEO review
/plan-ceo-review PLAN.md

# Answer the questions honestly
# Review generated artifacts (ceo-findings.md, etc.)
```

**Then post in Conductor:**
```
📋 CEO Review Complete

I've reviewed the project strategy. Key findings:
- Scope is appropriate for tutorial
- 3 premises confirmed, 1 assumption flagged
- Risk: Need GitHub collaboration setup (ongoing)
- Timeline: 1 week realistic

See attached: ceo-findings.md
Ready for collaborator's planning review.
```

### Collaborator: Run Their Role

**Collaborator receives Conductor invite:**

1. **Clones repo:**
```bash
git clone https://github.com/YOUR_USERNAME/hello_world.py
cd hello_world.py
cat COLLABORATOR_GUIDE.md  # Read their instructions
```

2. **Runs their chosen review** (pick one):
   - **Planning:** `/spec PLAN.md`
   - **QA:** `/qa-only`
   - **Architecture:** `/plan-eng-review PLAN.md`

3. **Posts findings to Conductor** in the appropriate channel

### You: Review Collaborator's Findings

1. **Check Conductor** for their posted findings
2. **Discuss any disagreements** in Conductor chat
3. **Update PLAN.md** with decisions made

### You: Deploy (When Ready)

```bash
# Run the ship command
/ship

# This will:
# - Verify all reviews done
# - Create deployment checklist
# - Ask for final approval
# - Handle deployment (if applicable)
```

---

## Example: Complete Workflow Timeline

```
Day 1, 10am (You):
  • Run /plan-ceo-review PLAN.md
  • Post findings to Conductor #ceo-review
  • Send collaborator the Conductor invite + GitHub link

Day 1, 3pm (Collaborator):
  • Clones repo from GitHub
  • Joins Conductor workspace
  • Runs /qa-only
  • Posts QA findings to Conductor #qa-report

Day 2, 9am (You):
  • Review collaborator's QA findings
  • Discuss in Conductor #general
  • Agree on actions

Day 2, 2pm (Collaborator):
  • Implements any changes based on findings
  • Pushes to GitHub

Day 3, 9am (You):
  • Final review of code changes
  • Run /ship to deploy
  • Post deployment confirmation to Conductor

Day 3, 5pm (Collaborator):
  • Confirms deployment works on their end
  • Team celebrates! 🎉
```

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| **Collaborator can't clone the repo** | Make sure repo is public OR they were added as collaborator (private repos) |
| **Collaborator not seeing Conductor invite** | Check their email spam, or resend invite from Conductor settings |
| **Can't find my GitHub repo on Conductor** | Paste the GitHub URL when creating workspace, or add it to workspace settings |
| **Collaborator run `/spec` but it didn't work** | Make sure they're in the project directory and have `claude` CLI installed |
| **Reviews look incomplete** | Review artifacts might not have been generated. Run the skill again. |
| **Disagree on a finding** | Post in Conductor — the team discusses async and decides together |

---

## What Happens in Each Review

### Your CEO Review (`/plan-ceo-review PLAN.md`)
**You answer questions like:**
- Is this the right problem to solve?
- Are the premises valid?
- What could go wrong in 6 months?

**You get:**
- Strategic assessment
- Scope validation
- Risk identification
- Dream state diagram

**Post to:** `#ceo-review`

---

### Collaborator's PM Review (`/spec PLAN.md`)
**They answer:**
- What are the concrete tasks?
- What's the timeline?
- What are dependencies?

**They get:**
- Task breakdown
- Timeline
- Dependency graph
- Risk assessment

**Post to:** `#planning`

---

### Collaborator's QA Review (`/qa-only`)
**They:**
- Run the code
- Test edge cases
- Look for bugs
- Check coverage

**They get:**
- Bug list (if any)
- Test scenarios
- Coverage report
- Readiness assessment

**Post to:** `#qa-report`

---

### Your Engineering Review (`/plan-eng-review PLAN.md`)
**You evaluate:**
- Architecture design
- Code quality
- Test strategy
- Technical debt

**You get:**
- Design audit
- Quality assessment
- Test plan
- Implementation guide

**Post to:** `#engineering`

---

### Your Deployment (`/ship`)
**You:**
- Review all findings
- Create deployment checklist
- Handle deployment (if applicable)
- Verify everything works

**You get:**
- Deployment checklist
- Green light (or blockers)
- Deployment confirmation
- Post-deployment verification

**Post to:** `#deployment`

---

## Ready to Go!

✅ All setup files created
✅ Git initialized and ready to push
✅ Documentation complete

**Your next 5 actions:**

1. Create repository on GitHub
2. Push your local code: `git push -u origin main`
3. Invite collaborator to GitHub (share repo URL)
4. Create Conductor workspace
5. Invite collaborator to Conductor
6. Post this message in Conductor:

```
🚀 Team Mode Tutorial Starting!

Hi! Welcome to the hello_world.py team mode collaboration.

Here's how this works:
1. You'll run a gstack review skill (your choice: PM, QA, or architecture)
2. I'll run my reviews (CEO, engineering, deployment)
3. We discuss findings in this Conductor workspace
4. Async collaboration — no meetings required!

Your options:
- **PM Review:** /spec PLAN.md → Create task breakdown
- **QA Review:** /qa-only → Find bugs, test everything
- **Arch Review:** /plan-eng-review PLAN.md → Evaluate design

Start with whichever role interests you most!

See COLLABORATOR_GUIDE.md for step-by-step instructions.
```

---

**You're set up!** Push to GitHub, invite your collaborator, and start collaborating.
