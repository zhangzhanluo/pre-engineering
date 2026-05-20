# Version History

V20260513-1437 V0.1.0
- Initial commit: SKILL.md, README.md, 6 reference templates (planner/executor/reviewer guides, collaboration log format, state system reference)

V20260513-1452 V0.1.1
- README.md: add project background story (three-smith proverb, PRE dual meaning)

V20260518-1129 V0.2.0
- Add bilingual (en/zh) support and reorganize reference templates by language
- Move English templates to references/en/ subdirectory
- Add full Chinese template set (planner/executor/reviewer guides, collaboration log format, state system reference)
- README.md bilingual restructuring, SKILL.md updated for language detection

V20260519-1104 V0.3.0
- Skill optimization: template total lines from 1472→913 (38% reduction), core content fully preserved
- Reviewer template 360→219 lines: merge code conciseness into review dimensions, streamline three-dimension standards, compress version recording and loop blocking
- Planner template 180→141 lines: refine behavioral principles, compress loop task management and blocking explanation
- Executor template 203→151 lines: merge quality self-check into 8-item concise version, streamline loop management
- SKILL.md trigger description: from enumerated trigger words to natural-expression coverage
- SKILL.md structure: merge install & update sections, add why explanations, streamline redundant format specs
- README.md add Updating section (both en/zh): re-run install command to update, existing collaboration docs unaffected

V20260520-1053 V0.4.0
- Log operation hard rules: all 6 templates add 3 mandatory rules (read every cycle, append only, verify status before action) to prevent log corruption
- Multi-perspective review mechanism: reviewer templates (en/zh) add 4-step scan (rebuttal-first → perspective-switch → assumption-challenge → cross-dimension conflicts), flowchart updated accordingly
- Reviewer behavioral principles: add "Rebuttal First" as top principle, deliverable review requires multi-perspective scan before checklist
- Git pre-check: SKILL.md and reviewer templates add mandatory `.pre/` in `.gitignore` verification before any git operation