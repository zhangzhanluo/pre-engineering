---
name: pre-engineering
description: "PRE Engineering — Set up a Plan-Review-Execute multi-agent collaborative framework for any project. Three AI agent roles (Planner, Executor, Reviewer) work together through a shared collaboration log to continuously deliver project goals. TRIGGER when: user wants multiple AI agents to collaborate on a project, mentions PRE system, PRE Engineering, Plan-Review-Execute, wants to divide AI work into planning/execution/review roles, wants agents to coordinate via a shared log, wants to set up Planner/Executor/Reviewer guide documents, wants to start a loop-driven multi-agent workflow, asks how to make AI roles work together, mentions collaborative agents or multi-agent workflow, says things like 'let AI help me divide work', 'I want different AI roles to collaborate', 'set up a collaborative project', or expresses any multi-agent or team-of-AIs intent — even without explicitly mentioning PRE."
---

# PRE Engineering

Set up a multi-agent collaborative framework where three AI roles — Planner, Executor, Reviewer — coordinate through a shared collaboration log to continuously deliver project goals.

PRE is not a standalone project — it's a framework you add to an existing project to enable multi-agent collaboration. Think of it as giving your project a "team of AI workers" with clear role divisions and a shared communication channel.

## Installation & Updating

**Install**: `npx skills add zhangzhanluo/pre-engineering` (recommended) or manually place `skills/pre-engineering/` into your AI tool's skills directory.

**Update**: Re-run the install command to get the latest version. Existing `.pre/{project_name}/` collaboration documents in your projects are unaffected — they're separate from the skill templates.

## Step 0: Language Detection & Confirmation

Before collecting requirements, detect the user's language and confirm:

1. **Detection rule**: If user's input contains Chinese characters → default to `zh`; otherwise → default to `en`
2. **Confirm with user** — present an interactive prompt offering language options.

Set `lang` variable: `zh` or `en`. This determines template path and document file names:

| Document | `lang=zh` | `lang=en` |
|----------|-----------|-----------|
| Project goals | 项目目标.md | project-goals.md |
| Collaboration log | 协作日志.md | collaboration-log.md |
| Planner guide | 规划者指导.md | planner-guide.md |
| Executor guide | 执行者指导.md | executor-guide.md |
| Reviewer guide | 审核者指导.md | reviewer-guide.md |
| Template dir | references/zh/ | references/en/ |

## Step 1: Collect Project Name + All Requirements

First collect a project name (used as subdirectory under `.pre/{project_name}/` for multi-project support), then collect all requirements.

Collect project information via an interactive prompt: project name, overview, features, technical constraints, special notes.

Set `project_name` variable from user input. All documents will be placed in `.pre/{project_name}/`.

**Information Inference Rules**:
- Auto-scan README.md, design docs, package.json, requirements.txt, etc. to extract overview and tech stack — this saves the user from repeating what's already in their project
- If project directory has structured requirements, extract feature list directly
- Present inferred results to user for confirmation or modification

After collection, refine requirements: remove duplicates, normalize descriptions, supplement missing dimensions.

## Step 2: Confirm Draft & Generate Documents

Synthesize collected information into a project goals document draft, present to user for final confirmation. Upon confirmation, generate all 5 core documents.

The user must be satisfied with the project goals document before proceeding — this document drives all subsequent agent work, so getting it right matters.

## Project Goals Document

Write to `.pre/{project_name}/{goals_file}` upon confirmation.

For English projects:
```markdown
# Project Goals

## Overview
{Project overview provided by the user}

## Feature Requirements
- {Feature requirements provided by the user, one per line}

## Technical Constraints
- {Technical constraints provided by the user, one per line}

## Notes
- {Special notes provided by the user, one per line}
```

For Chinese projects, adapt the section titles and content to Chinese while maintaining the same structure.

**Important**: This document is the driving core of the entire project. Agents can only read it — they must not modify it. Only the human user can change project direction by editing this file.

## Collaboration Log Initial Entry

Create the initial entry by appending to `.pre/{project_name}/{log_file}` via shell append (`cat >> .pre/{project_name}/{log_file} <<'EOF'` ... `EOF`) with proper language (Chinese for lang=zh, English for lang=en). Do not use Write/Edit tools.

Time format: `[YYYY-MM-DD HH:MM]`, must execute `date +"%Y-%m-%d %H:%M"`. **Timezone**: Confirm with user during initialization, record in project goals Notes.

The initial entry declares `PLN_WAIT` status, which triggers the Planner to start the first planning cycle — this is how the project begins.

## Agent Guide Document Generation

Generate three agent guide documents from templates in `references/{lang}/`:

| Guide | Template (`lang=zh`) | Template (`lang=en`) |
|-------|---------------------|---------------------|
| Planner | references/zh/规划者指导模板.md | references/en/planner-guide-template.md |
| Executor | references/zh/执行者指导模板.md | references/en/executor-guide-template.md |
| Reviewer | references/zh/审核者指导模板.md | references/en/reviewer-guide-template.md |

**Generation steps**:
1. Read the corresponding template file from `references/{lang}/`
2. Replace all placeholders with project-specific values:
   - `{PROJECT_NAME}` → project name collected in Step 1
   - `{PROJECT_ROOT}` → absolute path to the project root directory (e.g., `/home/user/my-project`)
   - If user specified a non-default code directory (e.g., `src/`), additionally replace `{PROJECT_ROOT}` in the **Project Code Path** section only with `{PROJECT_ROOT}/{custom_dir}` (e.g., `{PROJECT_ROOT}/src`)
3. Write to the corresponding guide document in `.pre/{project_name}/`
4. Check for existing files before overwriting

## Startup Instructions

After all documents are generated, present startup instructions in the selected language (Chinese for lang=zh, English for lang=en).

### For English Projects (lang=en):

**PRE Engineering initialization complete!** Files generated:

- `.pre/{project_name}/{goals_file}` — Project requirements (only humans can modify)
- `.pre/{project_name}/{log_file}` — Initial PLN_WAIT entry
- `.pre/{project_name}/{planner_guide}` — Planner guide
- `.pre/{project_name}/{executor_guide}` — Executor guide
- `.pre/{project_name}/{reviewer_guide}` — Reviewer guide

**IMPORTANT: Git baseline setup**

`.pre/` is excluded via `.gitignore` by default. This ensures agents can always access collaboration documents on disk. Two options:

- **Default**: `.pre/` excluded from git — collaboration documents are local-only, agents access them directly on disk. No baseline commit needed.
- **Track in git**: If user wants to version the collaboration documents, remove `.pre/` from `.gitignore` and commit baseline:
```bash
cd {project_directory_path}
git add .pre/{project_name}/
git commit -m "PRE initialization: collaboration documents baseline"
```

**Launch agents** (3 separate terminals/sessions):

1. **Planner** (strong reasoning model):
   `/loop 3m "Read {PROJECT_ROOT}/.pre/{project_name}/{planner_guide} and follow its instructions as the Planner role. Each cycle starts by reading {PROJECT_ROOT}/.pre/{project_name}/{log_file} to check the latest status."`

2. **Executor** (fast coding model):
   `/loop 3m "Read {PROJECT_ROOT}/.pre/{project_name}/{executor_guide} and follow its instructions as the Executor role. Each cycle starts by reading {PROJECT_ROOT}/.pre/{project_name}/{log_file} to check the latest status."`

3. **Reviewer** (thorough review model):
   `/loop 3m "Read {PROJECT_ROOT}/.pre/{project_name}/{reviewer_guide} and follow its instructions as the Reviewer role. Each cycle starts by reading {PROJECT_ROOT}/.pre/{project_name}/{log_file} to check the latest status."`

### For Chinese Projects (lang=zh):

Present equivalent instructions in Chinese, with file names and paths adapted accordingly. Refer to references/zh/ template files for localized content.

---

**Project control**:

| Control | Operation | Agent response |
|----------|-----------|----------------|
| Adjust direction | Modify `.pre/{project_name}/{goals_file}` | Planner adjusts plan next cycle |
| Reduce scope | Delete features in `.pre/{project_name}/{goals_file}` | Planner submits "no new requirements" |
| Add requirements | Add items to `.pre/{project_name}/{goals_file}` | Planner identifies and proposes |
| Pause project | Write "currently paused" in Notes | Planner recognizes and skips |

**DONE condition**: Planner declares no new requirements → Reviewer confirms → DONE.

---

## Loop Prevention

- **Blocking rule**: 3 consecutive rejections on same requirement → loop blockage, revert to `PLN_WAIT`
- **Planner**: Re-split or adjust requirement
- **Executor**: Stop retrying, wait for new requirements

## Version Recording Mechanism

**Git confirmation at initialization**:

After Step 2 confirmation, before generating documents, ask user whether to enable git version recording.

**If disabled**: Skip ALL git operations throughout the entire workflow.

**If enabled**:
1. Verify `.pre/` is in `.gitignore`. If NOT present, add `.pre/` to `.gitignore` first (unless user wants to track `.pre/{project_name}/`). This check is mandatory — collaboration documents must not be accidentally committed.
2. Before starting agents, commit current project state as baseline.
3. After each execution review passes:
   - Auto-infer version info from project (check existing VERSIONS.md, CHANGELOG.md, or similar). If none found, create `VERSIONS.md`.
   - Commit directly with version information in commit message.
4. **Version format**: `V{date}-{time} V{semantic-version}` (e.g., V20260514-1637 V0.3.4)

---

## Safety and Integrity Checks

1. **Collaboration log is append-only via shell append** — log entries must be written using shell append (`cat >> file <<'EOF'`), never Write/Edit tools; this guarantees new content is only added at the end
2. **Project goals document protected**
3. **Code directory creation**: Create default code directory if not exists