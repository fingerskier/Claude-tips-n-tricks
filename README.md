# Claude-tips-n-tricks
Helpful info and scripts for Claude

## External

`dude-claude-plugin` is my local sqlite-backed vectorized-RAG memory for Claude to automatically track projects issues and specs.

`xlii` is my app that does stores and restore stuff outside of your repos (prompt-files, skills, settings, etc) in a central place so you can track them with Git.
* `npx xlii` to start, then `npx xlii harvest`

## Local

* Always use **planning** mode
* Always use **thinking** mode
* Use the **top model**

### ...you may use more tokens, and more expensive tokens, up front but saves in the long run with better results and fewer iterations.

* Keep your CLAUDE.md files up to date- especially after tough sessions
* Have Claude write skills for you when it needs to perform repeatable tasks

### ...all this ancillary data times the model prompts for the project and task at hand.

* Run multiple Claude's in separate worktrees or clones for major features/tasks
* Run multiple, deep specification planning sessions
* Do regular, targeted, code reviews
  * performance
  * duplication
  * security
* Install the official Claude Code GitHub App ~ it'll respond to mentions

* Give Claude full error stack-traces and/or logs
* Ask Claude to run your app or test-suite and evaluate the results

### ...don't waste your time doing what LLMs are naturally much better at

* Have Claude do a Q&A with you to learn about your project (especially fruitful with `dude` or `claude-mem`)
* Append `use subagents` to a prompt to spawn other agents for tasks ~ keeps the main context clean

* Use Learning or Explanatory mode for conceptualizing
* Have Claude generate visualizations for a project

---

## Agent Teams & Multi-Agent

* **Agent Teams**: coordinate multiple Claude instances with one as team lead
  * Enable via `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS` in settings.json
  * Great for: research/review, parallel module development, debugging with competing hypotheses, cross-layer coordination
* **Background agents**: fire off tasks that run in the background while you keep working
  * Use `run_in_background` or keyboard shortcuts to launch
  * Each gets a unique ID for monitoring and control
* Orchestration patterns are emerging fast — check [claude-flow](https://github.com/ruvnet/claude-flow) and [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code) for inspiration

## Hooks

* Pre/post tool-use hooks for automation, guardrails, and monitoring
  * `type: "command"` — run shell commands on events
  * `type: "prompt"` — use LLM evaluation to gate actions
* Key events: `PreToolUse`, `PostToolUse`, `UserPromptSubmit`, `Stop`, `SubagentStop`, `TaskCompleted`
* Use cases: enforce coding standards, block dangerous operations, multi-agent observability
* See [hooks reference](https://code.claude.com/docs/en/hooks) and [claude-code-hooks-mastery](https://github.com/disler/claude-code-hooks-mastery)

## Plugins & Custom Commands

* **Plugins** bundle slash commands, subagents, MCP servers, and hooks into installable packages
* **Custom slash commands**:
  * `.claude/commands/` — project-specific, shareable via git
  * `~/.claude/commands/` — personal, available across all projects
  * Connected MCP servers also expose prompts as slash commands
* Create a slash command for every "inner loop" workflow you do repeatedly
* Community repos:
  * [awesome-claude-code](https://github.com/hesreallyhim/awesome-claude-code)
  * [awesome-claude-code-plugins](https://github.com/ccplugins/awesome-claude-code-plugins)
  * [awesome-claude-skills](https://github.com/ComposioHQ/awesome-claude-skills)

## Cost & Context Management

* `/clear` when switching to unrelated work — avoids resending full conversation history
* `/cost` to check token usage; configure the status line to show it continuously
* `/compact` with custom instructions: `/compact Focus on code samples and API usage`
  * Tells Claude what to preserve when summarizing context
* Plans and todo items persist across compaction events — use them for long sessions
* Start with Sonnet for routine tasks, escalate to Opus for hard problems
* Most developers reduce costs **40-70%** with these strategies

## Session & IDE Tips

* `/teleport` moves sessions seamlessly between terminal and web interface
* **VS Code**:
  * @-mention files with specific line ranges from selection
  * Open multiple conversations in separate tabs/windows
  * Auto-accept edits as they're made
* **JetBrains**: official Claude Code [Beta] plugin — runs CLI in IDE terminal, opens changes in diff viewer
* **Keyboard**:
  * Escape twice — shows all previous messages to jump back to
  * Ctrl+V for pasting images (not Cmd+V on Mac for clipboard images)
  * Shift+Tab twice or Alt+M — enter Plan Mode
* **Status line**: customize to show model, git branch, uncommitted files, token usage progress bar
