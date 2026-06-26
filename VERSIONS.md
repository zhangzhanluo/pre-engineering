# Version History

Curated English mirror of the canonical project version history (root `VERSIONS.md`), scoped to skill-relevant entries. Pre-article LaTeX-paper commits (V0.3.8–V0.3.19) are omitted.

V20260512-0440 V0.1.0
- Project initialization; PRE mechanism design completed

V20260512-1457 V0.1.1
- 核心设计.md: add 3 design principles (think-before-act, surgical modification, goal-driven execution), timezone standard, unify directory naming to .pre/
- Chinese templates completed: planner (90→166 lines), executor (87→187), reviewer (110→338); add behavior-principles, timezone, loop-blocking, process-management sections
- English templates: add behavior-principles section, role-personality emphasis, unify version format to V{date}-{time} V{semantic-version}
- SKILL.md: remove external dependencies (inline 核心设计.md references), unify .pre/ naming, timezone to user-local
- Create CLAUDE.md (navigation pointer) and VERSIONS.md (version record)

V20260512-1530 V0.1.2
- Timezone: change from fixed Shanghai UTC+8 to user-local timezone (confirmed at init)
- Project background story merged into 4 docs: README.md, CLAUDE.md, two skill READMEs (three-smith proverb, PRE dual meaning)
- Create README.md under both skill folders

V20260512-1646 V0.1.3
- Template path placeholders changed to real defaults (协作日志.md, 项目目标.md, ../src), removing path ambiguity
- SKILL.md positioning: "initialize PRE project" → "configure PRE collaboration mechanism for user projects"
- Fix typo "荣誉代码" → "冗余代码" (4 files)
- Add .pre/ to .gitignore to prevent stash from touching collaboration docs
- Project code dir: hardcoded src/ → flexible (default src/)
- Collaboration-log format rules: blank line between entries; status declarations cannot stand alone
- All three agents auto-cancel loop task after DONE (added to all 6 templates)

V20260513-1015 V0.1.5
- "死代码" → "冗余代码" (5 files: README, 核心设计, CLAUDE, reviewer templates ×2)
- CLAUDE.md: add project-modification norms (three-file linkage check; collaboration docs append-only)
- 核心设计.md principle #8 extended: collaboration docs append-only, no deleting existing content
- Time-fetch policy: all templates/docs add rule — must run `date +"%Y-%m-%d %H:%M"` before writing log time, no filling from memory (10 files)

V20260513-1100 V0.1.6
- 6 agent templates: core rule adds "collaboration docs append-only, no deleting existing content"
- Collaboration-log format reference rule #1 strengthened: "log append-only" → "collaboration docs append-only, no deleting/modifying existing entries"
- Two skill READMEs: remove "self-contained" section (design-process artifact, not for release)
- Confirm zh/en structure match (78 sections, 100% corresponding)

V20260513-1442 V0.2.0
- Push to GitHub repository

V20260513-1442 V0.2.1
- Improve skill documentation

V20260513-1442 V0.2.2
- Exclude the claude directory from version recording

V20260514-1118 V0.3.0
- Merge zh/en skill into a single version, eliminating version split
- SKILL.md: auto-detect zh/en language with user confirmation; reference templates via subdirectories
- README.md: bilingual switching; 核心设计.md syncs file structure
- Remove redundant skills/pre-engineering-cn directory

V20260514-1136 V0.3.1
- Complete skill-merge leftovers: SKILL.md Step 0 language detection + npx skills add install; README.md bilingual anchors + acknowledgments
- Migrate templates to references/en/ and references/zh/; delete pre-engineering-cn/
- 6 guide templates: add log norms (no line numbers, record only on status change) and loop-task-ID + model-name recording rules
- 核心设计.md syncs file structure and log rules (#7 no line numbers, #8 record only on status change)

V20260514-1210 V0.3.2
- Version-recording mechanism refactor: drop git stash save; switch to confirm git-enabled at init + commit directly after review passes
- SKILL.md: add git-confirmation flow (enabled/disabled paths) and auto-inferred version-info logic
- Reviewer guide templates (en/zh): remove planner-review stash step; add skip rule when git disabled
- 核心设计.md syncs version-recording mechanism

V20260514-1223 V0.3.3
- Multi-project parallel collaboration: SKILL.md Step 1 collects project name; docs generated under .pre/{project-name}/
- 6 guide templates: code path update ../src → ../../src (adapt to new directory level)
- 核心设计.md: file-structure section adds multi-project subdirectory note

V20260514-1637 V0.3.4
- Skill generalization: SKILL.md → pure English; drop Claude-Code-specific concepts; switch to generic AI-agent-tool description
- Template directory rename: references/zh/ → references/cn/ (international language-code convention)
- 6 guide templates: code path → default root dir: ../../src → ./
- 核心设计.md: update file structure (zh→cn) and file-role notes (code dir defaults to root ./)

V20260514-1933 V0.3.5
- Template directory correction: references/cn/ → references/zh/ (align with project goal #12)
- SKILL.md: update all cn path references to zh (Step 0 language detection, doc dictionary, launch commands)
- 核心设计.md: update file-structure description (cn/→zh/)

V20260514-1950 V0.3.6
- Fix template code-path bug: 6 guide templates (zh/en ×3) code path ./ → ../../ (agent working dir is .pre/{project-name}/)
- SKILL.md template-gen step 2: default path → ../../, with relative-position note
- 核心设计.md file-role notes: clarify code dir defaults to root, relative path ../../

V20260515-0939 V0.3.7
- Agent guide files add project identity — all 6 templates (3 zh + 3 en) add ## 项目标识 / ## Project Identity section with {PROJECT_NAME} and {PROJECT_ROOT} placeholders
- Paths relative → absolute — collaboration log, project-goal doc, project-code paths change from bare filenames/../../ to {PROJECT_ROOT}/.pre/{PROJECT_NAME}/... absolute format
- Launch commands use absolute paths — /loop commands reference files via absolute paths; agents need no cd
- Job ID auto-recorded by agent — no longer user-manual; agent writes it to the collaboration log on first loop
- Git flow fix — remove old git stash save references; commit directly after review passes; reviewer git commands prefixed with cd {PROJECT_ROOT}

V20260519-1004 V0.3.20
- SKILL.md, skill README.md, project README.md: add Skill Updating section — re-run npx skills add to update; existing collaboration docs unaffected

V20260519-1100 V0.4.0
- Skill optimization & refactor: template total lines 1472→913 (38% reduction); core content fully preserved
- Reviewer template 360→219: merge code-conciseness into review dimensions; streamline three-dimension standards; compress version-recording and loop-blocking
- Planner template 180→141: refine behavior principles; compress loop-task management and blocking explanation
- Executor template 203→151: merge quality self-check into 8-item concise version; streamline loop management
- SKILL.md trigger description: enumerated trigger words → natural-expression "push" description
- SKILL.md structure: merge install & update sections; add why explanations; streamline redundant format specs

V20260519-1400 V0.4.1
- Add internal version file (VERSIONS.md) for the skill project

V20260520-1019 V0.4.2
- Git pre-check: reviewer template, 核心设计.md, SKILL.md all add mandatory rule — verify .pre/ is in .gitignore before any git operation (non-skippable)
- Multi-perspective review: reviewer template adds 4-step scan (rebuttal-first → perspective-switch → assumption-challenge → cross-dimension conflicts); must run before deliverable review
- Reviewer behavior principles: add "Rebuttal First" as top principle (find rejection reasons before approval reasons)
- Mermaid flowchart: add MultiScan node (insert multi-perspective scan step in deliverable-review path)
- CLAUDE.md, 核心设计.md sync reviewer-strictness and git-check rules
- Log integrity: all 6 agent templates add "Log operation hard rules" section (read actual file every cycle, append-only no modifying existing, verify status before action)
- Collaboration-log format reference (zh/en): add "Log operation hard rules" section to prevent log corruption
- 核心设计.md collaboration-log rules: add "Log integrity" subsection
- CLAUDE.md project-modification norms: add log-integrity rule
- Root cause: in practice agents inferred status from memory instead of reading the actual file, and modified existing log entries instead of appending

V20260520-1122 V0.4.4
- Log conciseness strengthened: all 6 agent templates' output specs changed to role-specific format (planner: need/plan/deliverable; executor: output/changes; reviewer: conclusion/reasons); clarify "log entries are direction pointers, not full spec docs"
- Collaboration-log format reference (zh/en): entry template generic → role-specific; rule #5 extended — "acceptance criteria, subtask lists, etc. do not belong in the log"
- 核心设计.md: example log switched to role-specific format; status-declaration recording format updated; template output specs updated
- Root cause: in practice the planner wrote 30+ line log entries (need detail, current-state analysis, 6-step plan, 8 acceptance items, 3 subtasks), seriously violating the 5-line limit

V20260624-0950 V0.4.5
- Shell-append hard rule: collaboration-log writes must use shell append (`cat >> file <<'EOF'`); Write/Edit tools forbidden — shell append can only write to end, cannot modify existing content
- Time must come from command: log-entry time must be taken directly from `date +"%Y-%m-%d %H:%M"` output; no filling from memory or context
- Log-operation hard-rules update scope: 6 role templates 4 rules (read every cycle / shell-append / status verify / time from command); 核心设计.md and collaboration-log format reference (zh/en) 3 rules (time rule placed in timezone-standard / format-reference rule #7, no duplicate #4); CLAUDE.md one-line summary
- Root cause: in practice agents still used Edit/Write to modify existing log entries, and times showed 10:XX (from memory, not command output)
- Time-rule de-dup: 核心设计.md and collaboration-log format reference (zh/en) delete redundant hard-rule #4 (time from command); keep each doc's existing time-rule location (核心设计.md timezone-standard time-fetch, format-reference rule #7) and strengthen "no context time" — eliminates drift of two time rules in one file
- Heredoc hang prevention: 核心设计.md and 8 reference files' shell-append rule adds "EOF end-marker must be flush-left" note, preventing shell from not recognizing the marker and hanging
- SKILL.md consistency: init collaboration-log first entry changed to shell append (old "Write to" literally conflicted with hard rule); safety checklist adds shell-append requirement
- README.md consistency: design principle #8 and collaboration-log note add shell-append requirement, aligning with CLAUDE.md
- Shell-append hard rule and Write/Edit ban retained (intentionally hardened, not reverted); V0.4.2→V0.4.4 missing V0.4.3 is historical legacy (V0.1.3→V0.1.5 same gap, suspected intentional skip), not backfilled

V20260626-1445 V0.4.6
- Job-ID registration rule reconciliation: 6 role templates (zh/en) + SKILL.md add a defined "Job-ID registration entry" — first cycle, one-time only, the sole entry permitted during a non-action cycle; its status line re-states the log's current status code (no status change, not a role declaration, no parenthetical notes)
- Root cause: in real use (vrp-rl project, Session c36a787f) the Executor's first cycle was PLN_WAIT (must skip); the "record job ID on first cycle" rule collided with hard rule #3 "do not write when status doesn't match" and the core rule "no skip-noise entries", forcing the agent to improvise a "loop started" entry that declared PLN_WAIT (not an Executor-allowed status) and appended parenthetical notes to the status line — violating hard rule #3, core rule, status-declaration spec, and format rule #4

V20260626-1508 V0.4.7
- Reviewer output-spec parity: reviewer template (zh/en) output spec adds the "three-dimension review and multi-perspective scan are the review process — their results do NOT go in the log; log only conclusion + 1-2 lines of core reason" note, matching the planner ("现状分析不在日志") and executor ("代码详解不在日志") specs
- Root cause: in real use (vrp-rl project) the Reviewer's output-approval log entry laid out the full three-dimension analysis (功能/规范/对齐) plus the multi-perspective scan as entry content, bloating to 6 content lines (exceeding the 5-line limit); unlike the planner/executor specs, the reviewer spec lacked the explicit "process doesn't go in log" note, so the reviewer logged its process

V20260626-1548 V0.4.8
- Reviewer output-spec: close the non-blocking-suggestion loophole in V0.4.7. V0.4.7 said multi-perspective-scan findings do not go in the log, but in real use (vrp-rl project) the Reviewer evaded it by relabeling maintainer-lens findings as a separate "改进建议（非阻塞）/improvement suggestions (non-blocking)" slot on approval entries — recurred across 2 deliverable reviews (15:14, 15:29), each with genuine tech-debt content (e.g. _obs() tensor reconstruction, _dist_mat type inconsistency), bloating entries further. Fix: reviewer output spec (zh/en) now explicitly states non-blocking suggestions (under any label) are process findings and do NOT go in the log; if important, elevate to a blocking rejection modification point, otherwise drop — forward-looking concerns are rediscovered by the Planner when it re-reads code; the Reviewer does not pre-direct future planning. Template unchanged (still Conclusion/Reason/Status — no new slot).
- Root cause: V0.4.7's "process doesn't go in log" note named "多视角发现/multi-perspective findings" literally; the agent evaded by parking the same findings under a different label ("改进建议"), so a strict reader could treat the relabeled slot as outside V0.4.7's scope. The fix closes that evasion by stating the rule applies regardless of label.

V20260626-1635 V0.4.9
- Agent anti-bloat compliance (B+A): glm agents sometimes ignore "don't-log-X" notes — observed planner 14:42 dumped 现状 diagnostics into the Approach line despite the guide's "现状分析不在日志" note being present (note-ignoring, vs V0.4.7/V0.4.8's note-ABSENCE gaps). Fix: (B) pre-write self-check gate added to all 6 role templates (zh/en) 质量自检 — "before writing: ≤5 lines? slot contains only its positive contract (planner: implementation path+key choices; executor: file paths+change summary; reviewer: conclusion+1-2 lines core reason) with no prohibited content (status diagnostics / subtasks / acceptance criteria / code details / three-dim analysis / multi-perspective findings / non-blocking suggestions)? trim to direction-only" — action-time gate (strong lever) vs read-time prose. (A) planner Approach bracket sharpened "方向要点"→"实现路径+关键技术选择"; format-reference rule #5 (zh/en) adds "5-line limit is a ceiling, not a pass — packing prohibited content into a single dense line is still a violation; line-count compliance ≠ content compliance" (closes the 14:42 misread: 4 lines, under limit, Approach packed with 现状).
- 8 files: 6 role templates (B) + 2 format references (A2) + planner bracket (A1, within the 6). No change to 核心设计.md/CLAUDE.md (they carry no per-slot contracts). Live vrp-rl on old guides — governs future projects/re-init. Residual model over-write may persist (necessary, maybe not sufficient) — observe post-restart.

V20260626-1646 V0.4.10
- standard project structure

V20260626-1710 V0.5.0
- Remove loop-id (job ID) output machinery: delete the "循环任务进程管理 / Loop Task Process Management" section from all 6 role templates (zh/en), the "Record Loop Task IDs" paragraph from SKILL.md, and the "Job IDs" bullets from README.md (zh/en)
- Agents no longer record their /loop job ID to the collaboration log and no longer self-CronDelete on DONE; DONE → agents skip each cycle (already covered by the state-driven-behavior tables), user stops the three /loop commands manually when done. Pause/restart become user-managed via the job ID /loop prints at launch
- Reverts the V0.4.6 Job-ID registration rule and its rule-collision reconciliation (registration entry as the sole non-action-cycle exception, status-line-restates-current-code workaround) — eliminates the carve-out that contradicted hard rule #3 (no write on skip) and the no-skip-noise core rule
- Root cause: the V0.4.6 registration mechanism added significant complexity (exception carve-out, status-line restatement, rule reconciliation) for marginal value (user "verifying job IDs via the log"); user requested removal of the loop-id output setting

V20260626-1759 V0.5.1
- Restore DONE loop self-exit as a follow-up to V0.5.0: add "循环退出（DONE）/ Loop Exit (DONE)" section to all 6 role templates (zh/en) — on DONE, the agent calls CronList to find its session's /loop job (prompt contains its guide filename; session-only crons mean each agent session has exactly one) and CronDelete it; no job-ID registration in the collaboration log (V0.5.0's removal stands)
- SKILL.md DONE condition + README Key Mechanisms (zh/en) note the runtime self-exit (CronList + CronDelete, no registration)
- Root cause: V0.5.0 removed DONE auto-exit together with the job-ID registration it depended on (agent had read its own id from the log); user wanted DONE self-cancel back WITHOUT restoring the log-polluting registration — runtime CronList discovery decouples self-exit from any job-ID recording. Verified CronList returns id + prompt text; CronCreate default is session-only, so each agent's /loop is the sole cron in its session