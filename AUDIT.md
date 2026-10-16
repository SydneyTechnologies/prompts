# Personal instructions audit

Reviewed on 16 October 2026.

The full reusable prompt is [AGENTS.md](AGENTS.md). It contains the shared rules in one file, as requested.
This audit explains the evidence, proposed skill split, and tool setup.
No global configuration or other project file was changed. No skills were installed.

## Main finding

Keep short preferences in the main instruction file. Use skills for detailed, repeated workflows.
Keep project facts and commands in project instruction files. Put the current task's scope in its prompt.

An instruction file is persistent guidance. A skill is a task procedure loaded when needed.
A harness is the tool that runs the model, loads instructions, and controls tools and permissions.
The actual system prompt is a separate instruction layer controlled by the harness.
An `AGENTS.md` file does not become a system prompt because of its filename.

This split is a recommendation based on the documentation below. It is not a new user requirement.

## Evidence labels

| Label | Meaning |
| --- | --- |
| Confirmed | Stated in the current request, existing instructions, or direct user feedback. |
| Generalized | A confirmed project preference adapted for use across projects. |
| Proposed | A practical format or safeguard added to implement the stated goal. |
| Local | A project or task rule that should retain its original scope. |

Existing agent-written documents show useful patterns. They do not, by themselves, prove a personal preference.

## Placement table

| Topic | Evidence status | Keep in main instructions | Skill recommendation | Reason |
| --- | --- | --- | --- | --- |
| ASD-STE100 explanations | Confirmed: E1, E5 | Short sentences, simple terms, consistent names, term definitions | No separate skill for normal answers | This applies across most tasks. Formal language checks can be a separate workflow. |
| PR title and description | Confirmed: E2–E4 | Conventional title; required `What` and `Why`; concise wording | Optional `prepare-pr` | The format is short. A skill helps only when it also inspects changes and collects validation. |
| Commit messages | Confirmed: E2–E4 | Conventional Commits 1.0.0 | Combine with `prepare-pr` if useful | A second skill for a few format rules adds little value. |
| Branch names | Confirmed in three projects; generalized: E2–E4 | Prefer `<type>/<short-description>`; honor required host rules | No | Keep the exact project ban on `codex/` local where required. |
| Code comments | Confirmed: E2–E4 | Explain reasons, constraints, workarounds, and tradeoffs | No | A short rule applies whenever code changes. |
| Function documentation | Confirmed locally; generalized: E3–E4 | Document useful contracts with the language's format | No | Exact Dart and TypeScript requirements remain local. |
| Business decisions | Confirmed goal: current request and E4 | Explain user example, impact, options, and recommendation before an unresolved decision | Good candidate: `assess-business-impact` | Detailed evidence collection and comparison are repeatable work. |
| System explanations | Confirmed goal: current request; supporting pattern: E8 | Show relevant parts, data movement, ownership, and proposed change | Good candidate: `explain-system` | The inspection and diagram procedure can be detailed. |
| Interactive learning | Confirmed: E5 | Use interaction when it helps; connect equations to visible changes | Use an existing visualization skill first | A custom skill is useful only if a stable personal workflow is still missing. |
| Tables and diagram choice | Confirmed goal; exact routing is proposed | Short table of suitable formats | Include detailed rules in `explain-system` | Avoid putting renderer or plugin instructions in the global file. |
| Code reuse and separation of concerns | Confirmed in E3–E4; generalized | Reuse suitable code; keep responsibilities clear | No | These are broad engineering preferences. |
| Repeated requests and cost | Confirmed example: E6; generalized | Check reuse, accuracy, and refresh behavior | Include in business-impact work when relevant | Caching is one option. It is not a universal solution. |
| UI consistency and useful copy | Confirmed: E7, E9–E11; generalized | Reuse design rules; keep text short and useful | Use existing project design skills | Asset names, platform rules, and dimensions depend on the project. |
| Chart values and precision | Confirmed later feedback: E7; generalized | Preserve meaningful values and avoid misleading rounding | Keep formatter procedures local | Later feedback corrects an older blanket truncation rule. |
| Validation and completion report | Mixed: E3–E4 plus proposed safeguards | Report actual checks and limits; use project commands | No general skill needed | A global test ban or test command would be too broad. |
| Process protection | Confirmed in E4; generalized | Do not disrupt active user sessions without permission for that disruption | No | This protects work across tools. |
| Current branch, target, and approval | Task-specific: E7, E9 | Follow current scope and explicit review requests | Current task prompt | Past permission to push to `main` is not permission for a new task. |
| Framework, localization, sync, and product rules | Local: E2–E4 | A reminder to read project rules | Existing project skills and local instructions | These rules are not valid in every project. |

## Proposed skills

These are designs for possible skills. They are not installed skills or available commands.
Each skill should retain the short personal rules in `AGENTS.md` as a fallback.

| Candidate | Trigger | Procedure and output | Boundaries |
| --- | --- | --- | --- |
| `assess-business-impact` | A recommendation affects users, cost, data accuracy, access, or reliability | Inspect evidence; give a concrete example; compare options; state assumptions; recommend an option; identify any unresolved decision | Do not invent financial gains. Do not ask again about settled decisions. |
| `explain-system` | The user needs to understand architecture, data flow, or a proposed system change | Inspect relevant sources; map parts and ownership; show current flow; mark proposed changes; explain affected callers and failure paths | Do not invent architecture. Keep diagrams small and tied to evidence. |
| `prepare-pr` | The user asks to draft or prepare a PR or commit message | Inspect the diff and target; summarize final behavior; apply title and message formats; include actual validation results | Drafting text does not grant permission to push, merge, or deploy. |

Start with instruction-only skills. Add scripts only when a repeated tool step needs them.
Keep `name` and `description` metadata clear. State positive triggers and important exclusions.
Test each skill on a matching task and a task that should not trigger it.
Check the output against the user's known examples, not just the presence of headings.

Do not create separate skills for short sentences, comment wording, and commit syntax at this stage.
Their rules are small and often needed. Keep them easy to load consistently.

## What the master file adds

The master file is a synthesis, not a word-for-word record of past commands.

| AGENTS.md section | Basis | Added interpretation |
| --- | --- | --- |
| 1. Language | E1 and E5 | Active voice, purpose per sentence, and a formal-compliance caveat help apply the request. |
| 2. Task understanding | Current request, E4, E7, E9 | Scope control and facts/assumptions separation are proposed safeguards. |
| 3. Decisions | Current request and E4 | The five-part decision format is proposed. The need for business impact is confirmed. |
| 4. Systems | Current request and E8 | Ownership, evidence labels, and failure paths are proposed details. |
| 5. Visual learning | Current request and E5 | The format table and fallback to static steps are proposed. |
| 6–8. PRs, commits, comments | E2–E4 | Validation wording is supported by E3. Examples are newly written illustrations. |
| 9. Code and reuse | E3–E4 and E6 | Cache refresh and accuracy checks are proposed safeguards. |
| 10. Design and content | E4, E7, E9–E11 | Broad design principles are generalized. Exact screen behavior stays local. |
| 11. Verification | E3–E4 | Reporting local versus published state is a proposed safeguard. |
| 12. Skills and instructions | Documentation research | This is a maintenance recommendation, not a recovered historical preference. |

## Conflicts and scope decisions

| Source issue | Resolution in the master file |
| --- | --- |
| BudgetGo's older chart rule favors ellipsis. Later feedback rejects cutting digits and excessive rounding. | Preserve meaningful numbers. Keep layout and tap behavior tied to the current product decision. |
| BudgetGo says not to add tests unless asked. | Keep that ban in BudgetGo. The shared file follows each project's verification rules. |
| BudgetGo favors native iOS patterns, named assets, and specific model tools. | Keep platform and asset rules local. Share the preference to reuse an existing design. |
| The backend defaults to latest `main` for new branches and PR targets. | Keep that default local. Follow the user's current branch and target elsewhere. |
| Three repos ban `codex/`; some hosts require their own branch prefix. | The portable file expresses the preferred format and honors required host rules. |
| One insight view must not scroll. | Keep this as a view rule. Other pages still need usable scrolling. |
| Some chats authorize a direct push; another requires review first. | Honor each current request. Do not turn one task's authorization into a permanent rule. |
| “ASD SC100” in the spoken request differs from existing instructions. | Use the confirmed name: ASD-STE100 Simplified Technical English. |

## Source register

### Local instruction sources

| ID | Source | What it establishes |
| --- | --- | --- |
| E1 | [Global instructions](/Users/sydneyidundun/.codex/AGENTS.md:1) | Brief explanations and ASD-STE100. |
| E2 | [AI engine instructions](/Users/sydneyidundun/Desktop/GraphLeaf/budgetgo-ai-engine/AGENTS.md:17) | Commits, PRs, branches, comments; Mastra rules remain local. |
| E3 | [Backend instructions](/Users/sydneyidundun/Desktop/GraphLeaf/budget-go-backend/AGENTS.md:6) | Same Git and comment formats; code boundaries; validation; local `main` default. |
| E4 | [App instructions](/Users/sydneyidundun/Desktop/GraphLeaf/BudgetGo/AGENTS.md:31) | Shared Git formats; business decisions during review; reuse, design, docs, test and process rules. |
| E8 | [Docs introduction](/Users/sydneyidundun/Documents/ChatGPT/budgetgo-docs/docs/intro.mdx:23), [sync overview](/Users/sydneyidundun/Documents/ChatGPT/budgetgo-docs/docs/mobile-sync/overview.mdx:9) | Short explanations and real examples; existing system flow and ownership table. The diagram is supporting evidence, not a global instruction. |
| E10 | [Website copy notes](/Users/sydneyidundun/Desktop/GraphLeaf/BudgetGoSite/design/copy-relevance.txt:4) | Recorded request to remove repeated copy and decorative labels. Later agent proposals are not treated as user rules. |

### Chat sources

The chat titles below are copied from the app. Only direct user text was used to establish preferences.

| ID | Chat and ID | Relevant user evidence |
| --- | --- | --- |
| E5 | Build a perceptron curve playground — `01a13ac2-14a6-78a0-863e-667ed6702a58` | Asked for an interactive playground, all the math, ASD-STE100, and visible changes as each ReLU is added. ReLU is the activation function used in that example. |
| E6 | Cache transaction categories — `01a14361-78d4-7ab2-8387-d910c43e0de6` | Identified repeated categorization as wasted requests and cost; asked to check effects on other uses of the shared logic. |
| E7 | Fix graph value truncation — `01a14198-31c9-76b2-afbb-eb281ab71df2` | Rejected cut digits, excess rounding, changed bar widths, and changed tap actions; requested smaller text before hiding values. |
| E9 | Review wordy screenshot layout — `01a14366-fdff-7960-aa22-0e892faacce0` | Rejected wordy overflow; set a view-specific no-scroll rule; asked to see a prompt edit before pushing. |
| E11 | Improve first-time onboarding — `01a13717-9ec8-76a2-94a1-47e03ffe2822` | Asked for existing icon styles, canonical sizes, useful steps, and a smaller, clearer layout. Supports the design synthesis with E9 and E10. |
| E12 | Update Mastra and check breaks — `01a141e4-4631-79e2-b2ab-1bad375a4f1d` | Asked to check breaking changes during an update. A task example, not a global framework rule. |
| E13 | Find HTML rendering progress — `01a14190-7094-7a61-ae03-9137eb38f010` | Recent feedback on rendering delay, tap behavior, translations, and branch scope. These remain task or product rules. |

### Coverage

The review used the 50 most recent non-pinned chat entries and seven selected project chats in detail.
The graph and learning chats were paged back to their first turns. The onboarding and HTML chats were sampled.
This is a recent-project review. It is not a complete export of all past chats or archived work.

All nine registered local source projects were checked. This new `prompts` project is the output destination.

| Project | Material checked | Result |
| --- | --- | --- |
| BudgetGo | Root instructions and selected recent chats | Main source for coding, review, design, and scope preferences. |
| budgetgo-ai-engine | Root instructions and selected recent chats | Shared writing rules; framework and prompt behavior remain local. |
| budgetgo-backend | Root instructions | Shared writing rules and code structure. Directory name is `budget-go-backend`. |
| budgetgo-docs | Instruction search, README, and selected documentation | Supporting examples of plain language, system flows, and ownership tables. |
| BudgetGoSite | Instruction search and design notes | Recorded copy request; most design details remain local. |
| budgetgo-document-redaction | Instruction search and README | Service facts; no personal instruction file or PR template found. |
| budgetgo-supabase | Instruction search, README, and `.github` inventory | Deployment facts; no personal instruction file or PR template found. |
| Personal | Instruction search and redesign prompt set | BudgetGo-specific design requests. |
| machine-learning | Local file inventory and learning chat | Local folder contains only `.git`; the chat provides the learning preference. |

The six projects without root agent rules were also checked for inherited instruction files and PR templates.
No new global preference was inferred from their absence.

## Documentation research

These are current documentation findings. The placement table applies them to this user's needs.

| Source | Finding | Effect on this draft |
| --- | --- | --- |
| [OpenAI: AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md) | Codex loads personal and project instructions in an ordered chain. Project instructions have a combined size limit, normally 32 KiB. | Keep shared guidance bounded. Leave local setup with the project. |
| [OpenAI: Build skills](https://learn.chatgpt.com/docs/build-skills) | Skills have metadata and task instructions. Full instructions load when selected. References and scripts are optional. | Move long task procedures into skills when they are stable. |
| [OpenAI: Rethinking skills and prompts](https://developers.openai.com/blog/rethinking-skills-and-prompts-for-gpt-6-astra) | Review accumulated instructions for excess context and obsolete guidance. | Preserve confirmed preferences; remove duplication and broad rules copied from one task. |
| [Claude Code: Memory](https://code.claude.com/docs/en/memory) | Personal and project instructions have specific paths and loading rules. Current versions also support repository `AGENTS.md`, with conditions. | Use the tool's documented entry point. Test that it loads. |
| [Claude Code: Skills](https://code.claude.com/docs/en/skills) | Skills provide task procedures and optional resources. Some metadata and execution features are Claude-specific. | Share plain instructions. Audit host-specific features before reuse. |
| [GitHub Copilot: Repository instructions](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/add-custom-instructions/add-repository-instructions) | Supported instruction types vary by Copilot surface. | Do not assume every Copilot feature loads `AGENTS.md`. |
| [GitHub Copilot: Skills](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) | Skills are supported through documented project and personal locations. | Check discovery paths and tool access in the chosen surface. |
| [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/) | Defines typed messages, optional scopes, bodies, and breaking-change notation. | Retain the format already required by three projects. |
| [ASD-STE100 official FAQ](https://www.asd-ste100.org/STE_faq.html) | STE includes writing rules and a controlled dictionary. | A short style checklist must not be presented as proof of full compliance. |

The ASD site returned HTTP 403 on direct retrieval. Its official indexed FAQ was available through search.
The draft does not reproduce the standard or claim a formal language check.

## Use across tools

Maintain one source file. Copy or adapt it to each tool's supported entry point.
Check which file was loaded after installation. A link in a file does not guarantee automatic loading.

| Tool | Suggested use | Limit to check |
| --- | --- | --- |
| Codex | Use the shared file as personal `~/.codex/AGENTS.md`, after reviewing the existing file. Keep project additions in each repository. | `AGENTS.override.md` can replace the file at that level. Local project rules may change defaults. |
| Claude Code | Use personal `~/.claude/CLAUDE.md` for cross-project preferences. For a repository, use supported `AGENTS.md` or an explicit `@AGENTS.md` import in `CLAUDE.md`. | Direct repository `AGENTS.md` support starts at v2.1.277. A project or ancestor `CLAUDE.md` or `CLAUDE.local.md` suppresses that direct route. Personal `~/.claude/CLAUDE.md` does not. |
| GitHub Copilot | Adapt shared rules into `.github/copilot-instructions.md` for the target repository. Use `AGENTS.md` where the selected agent feature supports it. | Support differs across features. Do not treat this as a universal personal installation path. |
| Custom harness | Load shared defaults through its explicit instruction loader. Load project instructions and task scope through defined layers. | Document precedence, size limits, permissions, and skill discovery. Do not assume a filename creates system-level authority. |

For a future skill split, Codex documents repository `.agents/skills` and personal `~/.agents/skills` locations.
Claude documents repository `.claude/skills` and personal `~/.claude/skills` locations.
Copilot documents several supported locations, including `.agents/skills`; check the selected surface.
The shared `SKILL.md` format does not guarantee that commands, connectors, scripts, or permissions are portable.

## Maintenance plan

Use the full file first as a reviewable master prompt.
If it becomes too large, retain sections 1, 6–8, and the short decision and visual rules as shared defaults.
Move detailed procedures into the proposed skills. Keep only their triggers and essential fallback rules in the main file.

When a new preference appears, record its source and scope before adding it.
If later feedback conflicts with an old rule, update the rule instead of adding a second conflicting instruction.
Keep installation changes separate from this draft review.
