# MySkills

Personal Codex skills collection.

## Skills

### handoff

Save the current task state to `handoff.md` so a later Codex session can continue without rereading the conversation.

**How to use:** In any Codex conversation, say `handoff`. The skill overwrites the workspace-root `handoff.md` with the current goal, completed work, decisions, changed files, verification results, and next steps.

---

### neura-ticket

Create Jira Service Management tickets for the Neura Robotics Customer Service & Support Portal.

**Supported product groups:**

| Group | Request Types |
|-------|--------------|
| Robot Arms | Service Request, General Inquiry, Submit Feature |
| Mobile Manipulation MAV/MAV+ | Service Request, General Inquiry, Submit Feature |
| MiPA | Technical Feedback, Service Request |
| Academy & Training | Book Customer Training, Sales Training |

**How to use:** In any Codex conversation, say "write a ticket" or "create a ticket" with your request details. Codex will generate the ticket content including all required fields and the portal link for manual submission.

---

### preserving-layout-document-translation

Translate layout-sensitive PDFs, DOCX files, brochures, technical specifications, engineering drawings, scans, and image-heavy documents while preserving page geometry and visual fidelity.

**How to use:** Ask Codex to translate a document while preserving its original layout. The skill inventories visible image text, protects technical tokens, tracks page assets, requires page-by-page visual QA, and appends a post-task review record.

---

## Installation

Skills are auto-discovered from `~/.codex/skills/`. To install:

```bash
cp -r handoff neura-ticket preserving-layout-document-translation ~/.codex/skills/
```

Or clone the repo and symlink:

```bash
git clone https://github.com/Ross98/MySkills.git
ln -s "$(pwd)/MySkills/neura-ticket" ~/.codex/skills/neura-ticket
```
