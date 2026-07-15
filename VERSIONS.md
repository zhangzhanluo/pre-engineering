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
V20260630-1844 V1.0.0
- 监督者驱动架构重设计（破坏性 major）：新增第 4 角色「监督者」（zh/en 监督者指导模板）；启动从「/loop 三终端」改为「主智能体建 6 文档后 CronCreate 起监督者 cron，每轮 headless claude -p --resume 拉起该动角色并监控」；三角色不再 /loop 自驱，「循环退出（DONE）」节改写为 DONE 跳过本轮、监督者停摆
- state.json（.pre/{project}/.supervisor/）管角色 session-id/模型/失败计数/cron job-id；故障模型 consecutive_failures(3→升级修复/可硬重启换 session-id)/fix_attempts(3→熔断 blocked)/成功归零；DONE 时监督者 CronDelete 自身停摆
- 角色轮询 prompt 强化（headless 自治：自主读目标/日志/代码、不得提问）+ 拉起限时（~4min 超时视同非零退出计入 consecutive_failures）；SKILL.md 启动节重写 Phase1(6文档)+Phase2(state.json+CronCreate)；状态体系/日志格式参考增 DONE-by-supervisor 与监督者控制条目（修复/熔断/停摆，均以状态码结尾）
- e2e toy 实测：happy path（PLN_WAIT→规划者自主读目标写 PLN_ING+REV_WAIT、监督者判成功轮不写控制条目、更新 state.json）+ DONE 自动停摆两路径全链路通过；故障检测逻辑经审阅正确（退出码非0/无新条目/*_ING 滞留→consecutive_failures++），hang 拉起缝隙已加限时条款堵住
- 破坏性：旧「/loop 三终端 + 角色 DONE 自取消」工作流不再支持，升级后改用监督者单点 cron 启动

V20260713-1439 V1.0.1
- 日志格式合规强化（根因：ros-ai 项目第8轮执行者日志格式漂移——状态码塞标题、末尾无独立状态行、单条30-40行，暴露监督者无格式校验 + 5行规范对"诚实失败+根因"场景不足）：
- 监督者指导模板（zh/en）监控判定增"严重格式违规"判失败条件（状态码塞标题 / 末尾无独立 `状态：<码>` 行 / 单条>10行 → consecutive_failures++ 软重启重写，连续3次升级修复追加 `监督者—修复：<角色>格式校正` 控制条目重申当前真实状态码、不改历史）
- 执行者指导模板（zh/en）增"未达成场景"5行精炼模板（未达成验收点 + 1句根因 + 1句下轮方向压一行，详细推导放代码注释/本地备忘不进日志）
- 协作日志格式参考（zh/en）第4条强化（状态码不可出现在标题行、不得用"状态推进/下一步→"等叙述性措辞替代标准状态声明行）
- 非破坏性：仅强化既有格式约束 + 补监督者校验职责，不改状态机/状态码/角色边界

V20260713-1656 V1.0.2
- 状态判断职责收归监督者：4角色模板删"状态驱动行为"节(三角色)→"调度约定"节；mermaid删状态自判分支→末尾错位兜底(角色读日志末尾严重错位则本轮不写直接退出，防监督者误判拉错角色)；项目目标节改"每次被拉起读最新版本"(用户改目标控方向，不得用上下文缓存旧版)；日志硬规则第1/3条改措辞(获取状态码→了解上下文/状态验证→末尾错位兜底)；循环退出节简化(监督者停摆，角色不自取消)；循环阻断角色应对简化(阻断经状态码自然传导，角色无需主动扫描)
- 完善监督者3断点：每轮执行逻辑加"检测项目目标变更"步(md5哈希对比state.json.goals_hash，变更记控制条目不改状态)；SKILL.md启动加续跑检测三分支(state.json存在→CronList查旧job-id在运行则提示已运行/不在运行则续跑复用session-id/无则首次)；异常处理细化续跑；state.json加goals_hash字段
- 状态体系参考zh/en文首加"监督者专属权威"说明；协作日志格式参考zh/en硬规则同步+修zh格式参考第45行孤立代码块标记瑕疵；拉起角色prompt重写(读日志上下文+读最新目标+干活+写条目)
- 根因:V1.0.0监督者驱动重设计后角色模板未瘦身(保留完整状态自判表与监督者调度职责重叠冗余)+监督者3断点(不读目标/角色非每轮读目标/续跑不完善)

V20260714-1742 V1.0.3
- Merge-implement two specs: 2026-07-14 supervisor auto-recommend skill + 2026-07-10 long-task cross-cycle resume & remote/SSH
- Supervisor → "status + skill dual dispatcher": on-demand skill discovery (scan ~/.claude/skills/ + plugins cache + {PROJECT_ROOT}/.claude/skills/, time-interval OR task-complexity triggered — not every cycle; WebSearch online when local has no fit, whitelist sources trusted_skill_sources installed to project-level .claude/skills/ with .gitignore) + recommend best-fit skill in spawn prompt tail (restraint: less is better, no log control entry); role guides hardcode no skill name
- Long-task cross-cycle resume: *_ING reframed from "anomaly/failure" → "cross-cycle in progress → --resume resume spawn" (normal behavior, not failure — ros-ai 16-round empirical misjudgment motivated this); executor long commands must nohup background + write EXE_ING checkpoint (progress+PID+next step)+exit 0 pause, next cycle --resume continues; consecutive_ing_rounds(5) audits checkpoint truth (local: file/process, remote: ssh {REMOTE_HOST}); hard-restart preferred at clean checkpoint
- Remote code support: {CODE_LOCATION} placeholder (local={PROJECT_ROOT}, remote=ssh {REMOTE_HOST} access {REMOTE_PATH}, headless bash -lic or source env script, never source ~/.bashrc); .pre/ collaboration docs stay local; planner+executor templates' Project Code Path uses {CODE_LOCATION}; SKILL.md Step 1 collects code location + remote REMOTE_HOST/REMOTE_PATH/env script, Step 2 replaces {CODE_LOCATION}
- Git-disabled branch: reviewer template + SKILL.md — when git disabled, still append version entry to VERSIONS.md/CHANGELOG.md (skip git ops only)
- state.json +13 fields: code_location/remote_host/remote_path/skills_hash/skills_inventory/last_explore_round/explore_interval_rounds/current_round/trusted_skill_sources/searched_queries + per-role consecutive_ing_rounds/spawn_timeout_sec; SKILL.md startup adds first skill-inventory scan step
- Files: zh+en supervisor template (skill discovery section + long-task resume + state fields) / executor (CanDone mermaid branch + long-task rules + {CODE_LOCATION}) / planner ({CODE_LOCATION} + skill convention) / reviewer (git-disabled branch + skill convention) / SKILL.md
- Root cause: headless claude -p skill auto-trigger recall 0% (known limit) — design is fully explicit (Bash scan + WebSearch + prompt names skill), not relying on auto-trigger

V20260715-1121 V1.0.4
- Fix V1.0.3 implementation-vs-spec gap (07-10 long-task spec B3): reviewer template "Project Code Path" section was not migrated to {CODE_LOCATION} — spec B3 main text explicitly lists 3 role templates (planner/executor/reviewer), but the spec's own change-list table omitted reviewer for B3 (only marked C); V1.0.3 impl followed the table → reviewer missed B3. Found via post-impl consistency check. Now reviewer zh+en line 22 {PROJECT_ROOT}→{CODE_LOCATION} + line 23 remote SSH note added (bash -lic/env script, never source ~/.bashrc), aligned with planner/executor format; all 3 role templates now consistent ({CODE_LOCATION} 6 occurrences across zh+en verified)
- root=skill+2: root → V1.0.6; corresponding skill repo (github: zhangzhanluo/pre-engineering) V1.0.4
