# Collaborator Guide — How to Use This Repo

This guide gets your collaborator from "I have a GitHub username" to "I'm running the gstack tutorial on my own machine." Follow it top to bottom, in order.

**Repo:** https://github.com/mikelix/gstack-tutorial-1 (private)

---

## Step 0 — Get Invited (the repo owner does this)

This repo is **private**. Nobody can clone or even view it until the owner (`mikelix`) adds them as a collaborator.

**Owner: send the invite one of two ways**

**Option A — GitHub website:**
1. Go to https://github.com/mikelix/gstack-tutorial-1/settings/access
2. Click **Add people**
3. Type the collaborator's GitHub username or email, select them, click **Add [name] to this repository**

**Option B — GitHub CLI (faster if you're already using `gh`):**
```bash
gh repo add-collaborator mikelix/gstack-tutorial-1 <their-github-username>
```

Either way, GitHub sends the collaborator an email + a notification. Nothing works for them until this step is done.

---

## Step 1 — Accept the Invitation (collaborator does this)

1. Check email for a message from GitHub: *"[mikelix] invited you to collaborate on gstack-tutorial-1"*
2. Click **View invitation** in the email (or check https://github.com/notifications on GitHub directly)
3. Click **Accept invitation**

You should now see the repo at https://github.com/mikelix/gstack-tutorial-1 when logged into your own GitHub account.

---

## Step 2 — Install Prerequisites

Check what you already have:

```bash
git --version    # need Git installed
gh --version     # optional but recommended — GitHub CLI
```

**No Git?** Install from https://git-scm.com/downloads

**No GitHub CLI?** Install from https://cli.github.com — makes Step 3 easier (handles auth automatically)

---

## Step 3 — Authenticate (collaborator does this)

A private repo requires you to prove it's really you before you can clone it.

**Easiest path — GitHub CLI:**
```bash
gh auth login
```
Pick **GitHub.com** → **HTTPS** → **Login with a web browser**, then follow the on-screen code + browser steps.

**Alternative — plain Git:** if you clone without `gh`, Git will prompt for your GitHub username and a **Personal Access Token** (not your password — GitHub no longer accepts passwords for Git operations). Generate one at https://github.com/settings/tokens if you don't have one.

---

## Step 4 — Clone the Repo

```bash
gh repo clone mikelix/gstack-tutorial-1
cd gstack-tutorial-1
```

(Or, without `gh`: `git clone https://github.com/mikelix/gstack-tutorial-1.git`)

You should now have all 20 files on your local machine.

---

## Step 5 — Orient Yourself: What's In Here

| File | What It Is | Start Here? |
|---|---|---|
| `START_HERE.md` | Entry point — choose solo (Path A) or collaborative (Path B) learning | ✅ **Read this first** |
| `GSTACK_TEAM_MODE_TUTORIAL.docx` | Full English tutorial, McKinsey-style Word doc | Main teaching material |
| `GSTACK_TEAM_MODE_TUTORIAL_CN.docx` | Same, Simplified Chinese | If you prefer Chinese |
| `GSTACK_TEAM_MODE_TUTORIAL_DECK.pptx` / `_CN.pptx` | Slide-deck summary, EN/CN | Quick executive overview |
| `SETUP_INSTRUCTIONS.md` | GitHub + Conductor workspace setup detail | Reference during Step 6 below |
| `COLLABORATOR_GUIDE.md` | Your role-specific instructions if doing Path B | Read once you've picked a role |
| `PLAN.md` | The actual project plan the 5 AI reviews ran against | Input to the reviews |
| `CEO_REVIEW.md` → `DEVOPS_REVIEW.md` | The 5 completed review documents (already run, for reference) | See what a finished review looks like |
| `hello_world.py` | The trivial demo project the tutorial is built around | The "codebase" being reviewed |
| `GSTACK_TUTORIAL_1_WORKFLOW_PLAYBOOK.docx` / `_DECK.pptx` | Meta-document: how this whole tutorial package was built | Only if you're curious about the process itself |
| `MCKINSEY_DOCX_PLAYBOOK.docx` | Technical reference for building McKinsey-style docx/pptx | Only if you're producing Tutorial #2 |

---

## Step 6 — Follow the Tutorial

1. Open `START_HERE.md` and pick **Path A (solo)** or **Path B (collaborative, with you as a specific review role)**
2. Open `GSTACK_TEAM_MODE_TUTORIAL.docx` (or the `_CN.docx` edition) and read Sections 1–3 for the concept overview
3. Follow the **Installation Guide** section for whichever platform you'll use — Claude Code, OpenAI Codex, or Tencent Workbuddy
4. Work through the **Five Perspectives** — note the callout box after the Engineer perspective: none of the 5 reviews write code. After Engineer review approves, you tell Claude Code directly *"Implement this plan"* before QA review runs on the result
5. If doing **Path B**, `COLLABORATOR_GUIDE.md` tells you which of the 5 roles (CEO / PM / Engineer / QA / DevOps) to run and how to share findings with your teammate

---

## Step 7 — If You'll Push Changes Back

Only if the repo owner gave you **write** access (not just read):

```bash
git checkout -b your-name/tutorial-notes    # work on a branch, not master
git add <files-you-changed>
git commit -m "notes: what you found running the tutorial"
git push origin your-name/tutorial-notes
```

Then open a Pull Request on GitHub so the owner can review before merging into `master`.

If you only have **read** access, fork the repo instead (top-right **Fork** button on GitHub) and push to your own fork.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `git clone` fails with "Repository not found" | You haven't accepted the invite yet (Step 1), or you're not authenticated (Step 3) |
| `gh: command not found` | GitHub CLI isn't installed — either install it or use plain `git clone` with a Personal Access Token |
| Password rejected during clone | GitHub removed password auth for Git in 2021 — use a Personal Access Token or `gh auth login` instead |
| Can't open the `.docx`/`.pptx` files | Any modern Word/PowerPoint (2016+) or free alternatives (LibreOffice, Google Docs/Slides import) will open them |
| Not sure which review role to pick (Path B) | Read `COLLABORATOR_GUIDE.md` — it walks through each of the 5 roles and what they need from you |

---

**Once cloned and oriented, you're ready to start at Section 1 of the tutorial. Questions go back to whoever set up this repo for you.**
