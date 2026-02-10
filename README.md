# DoToDos README

Go to [Quick Guide](#quick-guide) if you don't want to read my life's story...

After trying multiple VS Code TODO extensions, I've decided to make my own so I can finally have a simple tool to track my tasks without any crazy features.
No graphs, no complicated lists, no time tracking...
Just create a file with `.dotodos` extension and add new tasks!
I didn't use `.todo` to prevent interfering with other extensions if you want to still use them!

## Quick Guide

Create a file with `.dotodos` extension.

- `ctrl + enter` - Marks line of text as task.
- `ctrl + d` - Toggle task state (check/uncheck).
- `ctrl + shift + a` - Archives done tasks.
- `enter` - Creates new task automatically when pressed at the end of a task line.
- `tab` - Indents task line(s). Works on single line or multiple selected lines containing tasks.

You can divide tasks into blocks by adding titles like `Some Task Group:` - just add text with `:` at the end.

![DoToDos Screenshot](https://raw.githubusercontent.com/zakladwebdeweloperski/dotodos-release/main/img/tasks-screen-1.png)

## Features

### Tasks

Tasks are text lines with specific characters at the start of the line (first non-whitespace character).

- `☐` - for tasks to do
- `☑` - for completed tasks

When you mark a parent task as done (☑), all its subtasks (more indented tasks below it) will automatically be marked as done too. Similarly, when you mark a parent task as undone (☐), all its subtasks will be marked as undone.

### Sections

A section divides tasks into smaller blocks. It could be a module name, a feature, or anything you like.
Sections will have counters with done/all tasks.

### Auto-Task Creation

When you press `Enter` at the end of a task line, a new task will be automatically created on the next line with the same indentation level.

### Task Indentation

Press `Tab` anywhere within a task line to indent the entire line, making it easy to organize tasks hierarchically. You can also select multiple lines and press `Tab` to indent all task lines in the selection at once.

### Archiving

Users can archive tasks marked as done. This will remove them from the list and put them in an `Archived:` section below. If this section doesn't exist yet, archiving will create it.

## Version History

### 1.0.8

- **Visual Fix**: Fixed strikethrough glitch on done tasks where the line appeared in a different color than text, especially noticeable with many archived tasks - replaced opacity-based styling with theme-aware color

### 1.0.7

- **Task Prefixes**: Task types like `bug`, `feat`, `test` are now highlighted without requiring a colon (e.g. `bug` works same as `bug:`)
- **Archived Counter**: Added task counter to the Archived section (shows total count)
- **Visual Fix**: Fixed issue where strikethrough color didn't match text color on done tasks; now uses opacity for better compatibility with syntax highlighting

### 1.0.6

- **Task Type Prefixes**: Color-coded task categories (bug:🔴, feat:🟢, pending:🟣, refactor:🔵, test:🟡, docs:🔷, chore:⚪)
- **Inline Code Highlighting**: Backtick-wrapped text `like this` is highlighted in orange
- **Bug Fix**: Tasks ending with `:` no longer colored as sections
- **Customizable**: Configure your own colors for task prefixes via settings

### 1.0.5

- **Section Folding**: Sections can now be collapsed/expanded like code blocks for better organization
- **Syntax Highlighting**: Enhanced visual appearance with proper highlighting for sections, tasks, and timestamps
- **Performance**: Improved performance with task hierarchy caching for large documents
- **Error Handling**: Better error messages when operations fail
- **Tests**: Comprehensive test coverage including timestamp, double-enter, backspace, and content strikethrough behavior

### 1.0.4

- **Bug Fix**: Removed ESC keybinding that was interfering with normal VS Code ESC functionality (multi-cursor removal, suggestion closing, etc.)
- **Change**: Task cancellation now only works with Backspace key - ESC behaves normally in all contexts

### 1.0.3

- **Bug Fix**: Fixed issue where pressing ESC inserted the literal string "Escape" into task text
- **Test Coverage**: Added automated test for ESC key behavior to ensure it cancels newly-created tasks correctly

### 1.0.2

- **Task Content Support**: Text between task lines now belongs to the task above; content is struck through when the task is done and preserved during archive
- **Timestamp on Completion**: Done tasks get a timestamp appended like `@YYYY-MM-DD HH:mm:ss` (applies to parent and cascading subtasks)
- **Double-Enter Cancel**: Press `Enter` twice on an empty new task to cancel automatic task creation and insert a regular blank line instead
- **Backspace Cancel**: While on a newly created empty task, press `Backspace` to remove the checkbox and convert the line to content (keeps indentation)
- **All features from 1.0.1**: Auto-task creation, multi-line indentation, cascading completion, CSS-based counters, and UX fixes

### 1.0.1

- **Auto-Task Creation**: Press `Enter` at the end of a task line to automatically create a new task on the next line with the same indentation
- **Task Indentation**: Press `Tab` anywhere within a task line to indent the entire line for hierarchical organization
- **Multi-Line Task Indentation**: Select multiple lines and press `Tab` to indent all task lines in the selection at once
- **Cascading Task Completion**: When a parent task is marked as done, all its subtasks are automatically marked as done too
- **CSS-Based Counters**: Migrated from text-based to CSS decoration-based counters to prevent undo issues and unwanted file modifications
- **Improved User Experience**: Fixed cursor positioning and eliminated file save state issues
- **Bug Fixes**: Fixed issue where pressing Enter in the middle of a task line would create malformed tasks

### 1.0.0

Initial release of DoToDos
