---
name: pre-engineering
description: "PRE Engineering — Set up a Plan-Review-Execute multi-agent collaborative framework for any project. A Supervisor (the main agent) dispatches three AI role loops (Planner, Executor, Reviewer) through a shared collaboration log to continuously deliver project goals; the Supervisor monitors role health and repairs/restarts failed roles. TRIGGER when: user wants multiple AI agents to collaborate on a project, mentions PRE system, PRE Engineering, Plan-Review-Execute, wants to divide AI work into planning/execution/review roles, wants agents to coordinate via a shared log, wants to set up Planner/Executor/Reviewer guide documents, wants to start a supervisor-driven multi-agent workflow, asks how to make AI roles work together, mentions collaborative agents or multi-agent workflow, says things like 'let AI help me divide work', 'I want different AI roles to collaborate', 'set up a collaborative project', or expresses any multi-agent or team-of-AIs intent — even without explicitly mentioning PRE."
---

# PRE Engineering

Set up a multi-agent collaborative framework where a Supervisor (the main agent) dispatches three AI roles — Planner, Executor, Reviewer — through a shared collaboration log to continuously deliver project goals. The Supervisor monitors role health, repairs runtime failures, and restarts roles.

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
| Current task card | 当前方案.md | current-task-card.md |
| Planner guide | 规划者指导.md | planner-guide.md |
| Executor guide | 执行者指导.md | executor-guide.md |
| Reviewer guide | 审核者指导.md | reviewer-guide.md |
| Supervisor guide | 监督者指导.md | supervisor-guide.md |
| Template dir | references/zh/ | references/en/ |

## Step 1: Collect Project Name + All Requirements

First collect a project name (used as subdirectory under `.pre/{project_name}/` for multi-project support), then collect all requirements.

Collect project information via an interactive prompt: project name, overview, features, technical constraints, special notes.

Set `project_name` variable from user input. All documents will be placed in `.pre/{project_name}/`.

**Code location** (ask the user): whether code is local or remote.
- Local → set `code_location=local`, code path = `{PROJECT_ROOT}`.
- Remote → set `code_location=remote`, collect `{REMOTE_HOST}` + `{REMOTE_PATH}` (remote code path) + optional env script path (e.g. `~/env.sh`). Note: `.pre/` collaboration documents stay local at `{PROJECT_ROOT}`; only the code may be remote. **Code sovereignty is local** (#7): product code must live in the local repo (versioned via `git`/local VERSIONS); the remote is only an execution environment — the Executor must `rsync` remote outputs back to the local repo and commit locally (see Executor guide).

**PRE fit-gate** (advisory, #1): before initializing PRE, run a 4-question self-check on the project — (a) can needs be tackled in independent granules? (b) how deep is the domain (hidden conventions)? (c) are there long-running tasks (training/deploy)? (d) is it exploratory (needs shift as you build)? If the total score is below threshold, suggest the user use a lighter flow instead of forcing the four-role PRE. Do not hard-block — just advise; the user decides.

**Requirement grading & flow routing** (#3): not every need needs the full four-role cycle. Grade by the task card's granularity — **small** needs (≤1 file / ≤1 hour): single role, one pass, one log entry; **medium** needs: planning→execution→output-review (three steps); **large** needs: full four-role cycle. The Supervisor picks the flow from the granularity field in `.pre/{project_name}/{task_card_file}`. This lowers the protocol tax on small/medium needs.

**Information Inference Rules**:
- Auto-scan README.md, design docs, package.json, requirements.txt, etc. to extract overview and tech stack — this saves the user from repeating what's already in their project
- If project directory has structured requirements, extract feature list directly
- Present inferred results to user for confirmation or modification

After collection, refine requirements: remove duplicates, normalize descriptions, supplement missing dimensions.

## Step 2: Confirm Draft & Generate Documents

Synthesize collected information into a project goals document draft, present to user for final confirmation. Upon confirmation, generate all 7 core documents (goals, log, current task card, planner/executor/reviewer/supervisor guides).

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

The initial entry declares `PLN_WAIT` status, which triggers the first planning cycle — this is how the project begins.

## Agent Guide Document Generation

Generate four agent guide documents from templates in `references/{lang}/` (Planner, Executor, Reviewer, Supervisor):

| Guide | Template (`lang=zh`) | Template (`lang=en`) |
|-------|---------------------|---------------------|
| Planner | references/zh/规划者指导模板.md | references/en/planner-guide-template.md |
| Executor | references/zh/执行者指导模板.md | references/en/executor-guide-template.md |
| Reviewer | references/zh/审核者指导模板.md | references/en/reviewer-guide-template.md |
| Supervisor | references/zh/监督者指导模板.md | references/en/supervisor-guide-template.md |

**Generation steps**:
1. Read the corresponding template file from `references/{lang}/`
2. Replace all placeholders with project-specific values:
   - `{PROJECT_NAME}` → project name collected in Step 1
   - `{PROJECT_ROOT}` → absolute path to the project root directory (e.g., `/home/user/my-project`)
   - `{CODE_LOCATION}` (in the three role templates' "Project Code Path" section only):
     - Local → replace with `{PROJECT_ROOT}`
     - Remote → replace with a multi-line SSH block: `Remote server {REMOTE_HOST} / remote code path {REMOTE_PATH} / access via ssh {REMOTE_HOST} '<cmd>' / headless must use bash -lic '<cmd>' or source env script first (e.g. source ~/env.sh); never source ~/.bashrc (contains [ -z "$PS1" ] && return non-interactive guard, NPU/conda env vars won't load)`
   - If user specified a non-default code directory (e.g., `src/`), additionally replace `{PROJECT_ROOT}` in the **Project Code Path** section only with `{PROJECT_ROOT}/{custom_dir}` (e.g., `{PROJECT_ROOT}/src`)
3. Write to the corresponding guide document in `.pre/{project_name}/`
4. Check for existing files before overwriting

Note: `.pre/` collaboration document paths in templates stay `{PROJECT_ROOT}` (collaboration docs are local even when code is remote) — only the role templates' "Project Code Path" section uses `{CODE_LOCATION}`. The supervisor template's "Project root" stays `{PROJECT_ROOT}` (`.pre/` lives there); the supervisor senses code location via `state.json.code_location` and audits via SSH.

## Startup Instructions

After all documents are generated, the main agent (this session) becomes the Supervisor and starts the loop itself — no need to open 3 terminals.

**Phase 1 — generate 7 documents** (Steps 0-2 above, now including the supervisor guide and the current task card):
- `.pre/{project_name}/{goals_file}`
- `.pre/{project_name}/{log_file}` — initial `PLN_WAIT` entry
- `.pre/{project_name}/{task_card_file}` — **NEW**, created as a stub (`# 当前方案` / `# Current Task Card` + a 变更记录 init line); the Planner fills it per-need before `REV_WAIT` (structure reference: `references/{lang}/当前方案模板.md` / `current-task-card-template.md`)
- `.pre/{project_name}/{planner_guide}` / `{executor_guide}` / `{reviewer_guide}`
- `.pre/{project_name}/{supervisor_guide}` — **NEW** (from `references/{lang}/监督者指导模板.md` / `supervisor-guide-template.md`)

**Phase 2 — initialize supervisor state**

**Resume detection first**: If `.pre/{project_name}/.supervisor/state.json` already exists, read its `supervisor_cron_job_id` and `CronList` to check whether that job is still running:
- If running → tell the user "Supervisor already running" and stop (do not re-initialize).
- If not running → **resume**: `CronCreate` a new cron, write the new job-id back into state.json, reuse the three role session-ids already in state.json (do not re-allocate), and append to the log `## [<time>] 监督者 — 续跑恢复` (zh) / `## [<time>] Supervisor — resume after cron loss` (en), ending with the current status code. Then stop — the supervisor cron takes over from here.
- (state.json missing → first initialization, continue below.)

For first initialization:

1. Allocate one stable session-id per role (UUID). Write `.pre/{project_name}/.supervisor/state.json`:
```json
{
  "supervisor_cron_job_id": "",
  "goals_hash": "",
  "code_location": "local",
  "remote_host": "",
  "remote_path": "",
  "skills_hash": "",
  "skills_inventory": [],
  "last_explore_round": 0,
  "explore_interval_rounds": 5,
  "current_round": 0,
  "trusted_skill_sources": ["<superpowers marketplace url>"],
  "searched_queries": [],
  "roles": {
    "Planner": {"session_id":"<uuid>","model":"<planner-model>","last_exit_code":0,"last_run_time":"","consecutive_failures":0,"fix_attempts":0,"consecutive_ing_rounds":0,"spawn_timeout_sec":240,"status":"active"},
    "Executor": {"session_id":"<uuid>","model":"<executor-model>","last_exit_code":0,"last_run_time":"","consecutive_failures":0,"fix_attempts":0,"consecutive_ing_rounds":0,"spawn_timeout_sec":240,"status":"active"},
    "Reviewer": {"session_id":"<uuid>","model":"<reviewer-model>","last_exit_code":0,"last_run_time":"","consecutive_failures":0,"fix_attempts":0,"consecutive_ing_rounds":0,"spawn_timeout_sec":240,"status":"active"}
  }
}
```
   Role keys: `Planner`/`Executor`/`Reviewer` for `lang=en`; `规划者`/`执行者`/`审核者` for `lang=zh` (match the supervisor guide). Default models: Planner=aliyun/Kimi-K2.5, Executor=aliyun/qwen3.7-max, Reviewer=aliyun/kimi-k2.7-code (override in project goals Notes). `goals_hash` holds the md5 of the project-goals file content; the supervisor computes it each cycle to detect user edits to project goals — initialize empty. `code_location`/`remote_host`/`remote_path` set per Step 1 (local by default). `skills_inventory`/`skills_hash`/`last_explore_round`/`explore_interval_rounds`/`current_round`/`trusted_skill_sources`/`searched_queries` enable on-demand skill discovery (the supervisor scans local skill dirs + searches online when triggered; see supervisor guide "Skill Discovery & Recommendation"). Per-role `consecutive_ing_rounds`/`spawn_timeout_sec` support long-task cross-cycle resume (set `spawn_timeout_sec` larger for deployment/install roles).

1b. **First skill inventory scan** (new): scan `~/.claude/skills/`, `~/.claude/plugins/cache/*/skills/`, `{PROJECT_ROOT}/.claude/skills/`; read each `SKILL.md` frontmatter (`name`+`description`); write the inventory into `state.json.skills_inventory`, compute `skills_hash`, set `last_explore_round=0`/`current_round=0`. Also ensure `{PROJECT_ROOT}/.claude/skills/` is in `.gitignore` (auto-installed skills are runtime tools, not project git).

2. `CronCreate` a durable recurring job (every 3 min) with prompt:
   `Read {PROJECT_ROOT}/.pre/{project_name}/{supervisor_guide} and run one supervisor cycle.`
   Note: the supervisor cron fires only while the REPL is idle; recurring jobs auto-expire after 7 days; long-cycle (cross-day) projects must keep the session open or switch to manual wrap-up. If the prompt contains backticks/special chars, wrap the whole prompt in single quotes to avoid command substitution; prefer baking discipline into role `.md` (roles read it directly) over stuffing the spawn prompt.
3. Write the returned job-id into `state.json.supervisor_cron_job_id`.
4. Append to the collaboration log (time via `date +"%Y-%m-%d %H:%M"`):
   - `lang=zh`: `## [<time>] 人工 — 监督者已启动，三角色循环由监督者调度`
   - `lang=en`: `## [<time>] Human — Supervisor started; three role loops are dispatched by the Supervisor`
   End with `状态：PLN_WAIT` / `Status: PLN_WAIT`.

**Keep this session open and idle.** The supervisor cron fires while idle; each cycle it spawns the active role via `claude -p --resume <session-id> --model X` (first run uses `--session-id`), monitors, repairs runtime issues, restarts, and circuit-breaks per the supervisor guide. On `DONE`, the supervisor CronDeletes itself and shuts down — no manual cancel needed.

### Git baseline setup

`.pre/` is excluded via `.gitignore` by default. This ensures agents can always access collaboration documents on disk. Two options:

- **Default**: `.pre/` excluded from git — collaboration documents are local-only, agents access them directly on disk. No baseline commit needed.
- **Track in git**: If user wants to version the collaboration documents, remove `.pre/` from `.gitignore` and commit baseline:
```bash
cd {project_directory_path}
git add .pre/{project_name}/
git commit -m "PRE initialization: collaboration documents baseline"
```

---

**Project control**:

| Control | Operation | Agent response |
|----------|-----------|----------------|
| Adjust direction | Modify `.pre/{project_name}/{goals_file}` | Planner adjusts plan next cycle |
| Reduce scope | Delete features in `.pre/{project_name}/{goals_file}` | Planner submits "no new requirements" |
| Add requirements | Add items to `.pre/{project_name}/{goals_file}` | Planner identifies and proposes |
| Pause project | Write "currently paused" in Notes | Planner recognizes and skips |

**DONE condition**: Planner declares no new requirements → Reviewer confirms → DONE. On DONE, the Supervisor detects it next cycle, stops spawning all roles, CronDeletes its own cron, and logs shutdown. Role agents no longer self-cancel loops (see each role guide's Loop Exit section).

---

## Loop Prevention

- **Blocking rule**: 3 consecutive rejections on same requirement → loop blockage, revert to `PLN_WAIT`
- **Planner**: Re-split or adjust requirement
- **Executor**: Stop retrying, wait for new requirements

> Note: the 3-consecutive-rejection blockage is a role-level protocol mechanism, separate from the Supervisor's own failure circuit-break (`fix_attempts=3` → role blocked). Both coexist.

## Version Recording Mechanism

**Git confirmation at initialization**:

After Step 2 confirmation, before generating documents, ask user whether to enable git version recording.

**If disabled**: Skip ALL git operations throughout the entire workflow. When the Reviewer's execution review passes, still append a version entry to VERSIONS.md/CHANGELOG.md (check existing, create VERSIONS.md if none; format `V{YYYYMMDD}-{HHMM} V{Major.Minor.Patch}`) — version recording continues, only git operations are skipped.

**If enabled**:
1. Verify `.pre/` is in `.gitignore`. If NOT present, add `.pre/` to `.gitignore` first (unless user wants to track `.pre/{project_name}/`). This check is mandatory — collaboration documents must not be accidentally committed.
2. Before starting the supervisor, commit current project state as baseline.
3. After each execution review passes:
   - Auto-infer version info from project (check existing VERSIONS.md, CHANGELOG.md, or similar). If none found, create `VERSIONS.md`.
   - Commit directly with version information in commit message.
4. **Version format**: `V{date}-{time} V{semantic-version}` (e.g., V20260514-1637 V0.3.4)

---

## Safety and Integrity Checks

1. **Collaboration log is append-only via shell append** — log entries must be written using shell append (`cat >> file <<'EOF'`), never Write/Edit tools; this guarantees new content is only added at the end
2. **Project goals document protected**
3. **Code directory creation**: Create default code directory if not exists
4. **Supervisor state file** `.pre/{project_name}/.supervisor/state.json` holds runtime state (role session-ids, failure counters, cron job-id) — it is read/written by the Supervisor only, lives under gitignored `.pre/`, and is the recovery basis if the supervisor cron is lost
