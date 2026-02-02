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
