---
name: cli-design
description: Design and implement CLI interfaces. Use when the user wants to build a command-line tool, add a CLI to a project, design command/subcommand structure, or follow CLI best practices.
---

# CLI Design Skill

Design and implement well-structured, user-friendly command-line interfaces following industry conventions.

## Workflow

Make a todo list for all tasks in this workflow and work through them one at a time.

### 1. Understand Requirements

Ask the user (or infer from context) what the CLI should do:
- What is the primary purpose of the tool?
- Who is the target user (developers, ops, end users)?
- What are the core operations/commands needed?
- Does it need subcommands, or is it a single-purpose tool?
- What language/framework is the project using?

### 2. Audit the Existing Codebase

- Read the project's README, package.json / pyproject.toml / Cargo.toml / go.mod, or equivalent
- Identify existing entry points (main files, bin scripts)
- Note the language, existing dependencies, and any existing CLI code
- Check for existing argument parsing libraries already in use

### 3. Choose a Parsing Library

Pick the idiomatic library for the project's language unless one is already in use:

| Language   | Recommended library        |
|------------|---------------------------|
| Node.js    | `commander` or `yargs`    |
| Python     | `click` or `argparse`     |
| Go         | `cobra` or `flag` (stdlib)|
| Rust       | `clap`                    |
| Ruby       | `thor` or `optparse`      |
| Java/Kotlin| `picocli`                 |
| C/C++      | `CLI11` or `getopt`       |

### 4. Design the Command Structure

Model the CLI as a tree:

```
<tool-name> [global-flags] <command> [command-flags] [arguments]
```

**Naming conventions:**
- Tool name: lowercase, hyphen-separated (`my-tool`)
- Commands/subcommands: lowercase verbs or noun-verb pairs (`init`, `add`, `list`, `delete`)
- Flags: `--long-form` and `-s` short form for common flags
- Arguments: positional, clearly described in help text

**Common global flags to include:**
- `--help` / `-h`: show help (always)
- `--version` / `-v` or `-V`: print version
- `--verbose`: increase output verbosity
- `--quiet` / `-q`: suppress non-error output
- `--config <path>`: specify config file, if applicable
- `--output` / `-o`: output format (`text`, `json`, `yaml`) for tools that emit structured data

**Exit codes:**
- `0`: success
- `1`: general error / usage error
- `2`: misuse of command (wrong args/flags)
- Other codes: document them in the help text or man page

### 5. Write Help Text

Every command must have clear, concise help text:

```
Usage: <tool> <command> [flags] <args>

<One-line description of what this command does.>

Arguments:
  <arg>    Description of the argument

Flags:
  --flag   Description. (default: value)
  -h, --help   Show this help message

Examples:
  <tool> <command> arg1
  <tool> <command> --flag value arg1
```

**Principles:**
- Lead with a verb in the one-liner ("Create a...", "List all...", "Delete the...")
- Show examples — they are the most useful part of help text
- Mention defaults for flags
- Keep descriptions to one line; use a longer description block only when necessary

### 6. Handle Errors Gracefully

- Print errors to **stderr**, not stdout
- Include actionable guidance: "Run `<tool> --help` for usage."
- Never print a stack trace to the user by default; use `--verbose` or `--debug` to expose it
- Validate arguments early and fail fast with clear messages

Example error pattern:
```
error: missing required argument <name>
Run '<tool> <command> --help' for usage.
```

### 7. Implement the CLI

Structure the code cleanly:

```
src/
  cli/
    index.ts        # entry point, wires up commands
    commands/
      init.ts       # one file per top-level command
      add.ts
      list.ts
    utils/
      output.ts     # formatters for text/json output
      errors.ts     # error helpers
```

- Keep command handler functions thin — delegate logic to the core library
- Use a consistent output helper so `--output json` is easy to implement
- Inject dependencies (config, API clients) rather than importing globals

### 8. Add Shell Completion (optional but recommended)

Most modern CLI libraries can generate shell completion scripts:

```bash
# cobra (Go)
my-tool completion bash > /etc/bash_completion.d/my-tool

# click (Python)
_MY_TOOL_COMPLETE=bash_source my-tool > ~/.my-tool-complete.bash

# commander (Node.js)
my-tool completion >> ~/.bashrc
```

Document how to install completions in the README.

### 9. Write Tests

- Unit-test each command handler with mocked I/O
- Integration-test the full CLI binary with subprocess calls
- Test error paths (missing args, bad flags, permission errors)
- Verify exit codes and stderr output

### 10. Update Documentation

Update or create:
- **README.md**: Installation, quickstart, and command reference
- **CHANGELOG.md**: Note the CLI addition
- Man page or `docs/` directory for detailed reference (optional)

### 11. Commit and Push

Commit with a clear message such as:

```
feat: add CLI with init, add, and list commands
```

## Wrap Up

In your final message to the user, provide:

* **Command structure summary** — a tree of all commands and their flags
* **Library chosen** and why
* **How to run** — the exact command to invoke the tool
* **How to install shell completion** (if implemented)
* **Test results** — ✅/‼️ for each test suite run
