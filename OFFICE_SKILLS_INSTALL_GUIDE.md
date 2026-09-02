# Installing Anthropic's Office Skills in Claude Code

This guide walks your collaborator through installing the 4 official document-generation skills — the same ones used to build every `.docx` and `.pptx` file in this tutorial repo. Takes about 5 minutes.

---

## Currently Installed (this machine)

| Skill | Purpose | License |
|---|---|---|
| **docx** | Create, read, edit Word documents (.docx/.dotx) | Proprietary — see LICENSE.txt |
| **pptx** | Create, read, edit PowerPoint presentations (.pptx/.potx) | Proprietary — see LICENSE.txt |
| **xlsx** | Create, read, edit Excel spreadsheets (.xlsx/.xlsm/.csv/.tsv) | Proprietary — see LICENSE.txt |
| **pdf** | Read, merge, split, fill forms, OCR PDF files | Proprietary — see LICENSE.txt |

Source: [github.com/anthropics/skills](https://github.com/anthropics/skills) — Anthropic's official skills repo.

---

## Step-by-Step Installation

### Step 1: Clone the skills repo to a temp location

```bash
git clone --depth 1 https://github.com/anthropics/skills.git ~/anthropic-skills-src
```

### Step 2: Confirm the exact folder paths

Don't assume — check first. The 4 document skills live directly under `skills/` in this repo (not nested under a `document-skills/` subfolder):

```bash
ls ~/anthropic-skills-src/skills/
```

You should see `docx`, `pptx`, `xlsx`, `pdf` alongside other skills like `pdf`, `frontend-design`, `mcp-builder`, etc.

### Step 3: Create the Claude Code skills directory (if it doesn't exist)

```bash
mkdir -p ~/.claude/skills
```

### Step 4: Copy the 4 skill folders over

```bash
cp -r ~/anthropic-skills-src/skills/{docx,pptx,xlsx,pdf} ~/.claude/skills/
```

### Step 5: Verify installation

```bash
ls ~/.claude/skills/ | grep -E "docx|pptx|xlsx|pdf"
```

You should see all 4 folders listed.

### Step 6: Confirm each skill loaded correctly

```bash
head -5 ~/.claude/skills/docx/SKILL.md
head -5 ~/.claude/skills/pptx/SKILL.md
head -5 ~/.claude/skills/xlsx/SKILL.md
head -5 ~/.claude/skills/pdf/SKILL.md
```

Each should show a `name:` field matching the skill (docx, pptx, xlsx, pdf) and a `description:` explaining when to use it.

---

## Dependencies (install only if a `require`/`import` fails)

The skills assume these are preinstalled. If they're missing, install once:

```bash
# For docx and pptx (Node.js libraries)
npm install docx pptxgenjs

# For icons in slide decks (optional, only if building pptx with custom icons)
npm install react react-dom react-icons sharp

# For xlsx and pdf (Python libraries)
pip install openpyxl pandas pypdf

# For inspecting file contents quickly
pip install "markitdown[pptx]"
```

**Also needed on the system (not via npm/pip):**
- **LibreOffice** (`soffice`) — used for PDF-export-based visual QA of generated documents. If it's not installed, document generation still works, but you'll need to skip the visual-render QA step and rely on structural checks instead (schema validation, XML tree inspection).
- **Poppler** (`pdftoppm`) — converts PDF pages to images for visual inspection, only needed alongside LibreOffice.

---

## Quick Test — Confirm It Actually Works

```bash
node -e "require('docx'); require('pptxgenjs'); console.log('docx + pptx libraries OK')"
python -c "import openpyxl, pypdf; print('xlsx + pdf libraries OK')"
```

If either line errors with `Cannot find module` or `ModuleNotFoundError`, go back to the Dependencies section above and install the missing piece.

---

## Using the Skills in Claude Code

Once installed, just ask Claude Code naturally — it recognizes when to use each skill:

- *"Create a Word document summarizing this..."* → uses `/docx`
- *"Make a slide deck about..."* → uses `/pptx`
- *"Build a spreadsheet tracking..."* → uses `/xlsx`
- *"Merge these PDFs..."* / *"Extract text from this PDF..."* → uses `/pdf`

No need to type the skill name explicitly — mentioning the file type or intent (Word doc, slides, spreadsheet, PDF) is enough for Claude Code to route to the right one.

---

## Where This Repo's Documents Came From

Every `.docx` and `.pptx` in this repo (`GSTACK_TEAM_MODE_TUTORIAL.docx`, the slide decks, both playbooks) was built using exactly this installation, following the patterns documented in `MCKINSEY_DOCX_PLAYBOOK.docx`. If you install these 4 skills, you have everything needed to produce the same quality of output for Tutorial #2.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `git clone` fails | Check internet connection; confirm `git` is installed (`git --version`) |
| Copied folders but Claude Code doesn't seem to recognize them | Restart Claude Code — skills are loaded at session start |
| `require('docx')` fails after copying skill | Run `npm install docx` in your working directory — libraries aren't bundled with the skill folder itself |
| Skill folder structure looks different from this guide | The anthropics/skills repo layout can change over time — re-run Step 2 (`ls`) to check the current actual paths rather than assuming this guide is still accurate |
