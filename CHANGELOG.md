# Change Log

All notable changes to the "dotodos" extension will be documented in this file.

## [1.1.1] - 2026-02-20

### Fixed
- **Section Detection**: Lines with `:` that are indented (e.g., task content like `Note:` or `Steps:`) are no longer misidentified as sections — sections must start at column 0 with no indentation, fixing incorrect task counters in sections

## [1.1.0] - 2026-02-12

### Fixed
- **Strikethrough Scope**: Checkbox character (☑) and completion timestamp are no longer struck through on done tasks — only the task text itself gets strikethrough
- **Strikethrough on Whitespace**: Spaces between words in done tasks are no longer struck through (improved range calculation with start/end column bounds)
- **Task Prefix Colon Coloring**: Task prefix keywords (Bug:, Feat:, etc.) now include the trailing colon in the colored highlight

## [1.0.9] - 2026-02-10

### Fixed
- **First-Word-Only Coloring**: Task prefix keywords (bug, feat, test, etc.) now only highlight the first word of a task, not every occurrence throughout the text
- **Strikethrough on Whitespace**: Strikethrough decoration on completed tasks no longer bleeds through tabs and spaces — only visible characters are struck through

## [1.0.8] - 2025-12-11

### Fixed
- **Strikethrough Visual Glitch**: Replaced opacity-based styling with theme color for done tasks to fix visual inconsistencies where strikethrough appeared in different color than text, especially visible with many archived tasks

### Note
- Task prefix keywords (bug, feat, test, docs, etc.) already highlight without requiring a colon suffix (implemented in 1.0.6)
- Archived section already displays count like "Archived: (99)" (implemented in 1.0.5)

## [1.0.6] - 2025-10-23

### Added
- **Task Type Prefixes**: Tasks starting with keywords like `bug:`, `feat:`, `pending:` are now color-coded (case-insensitive)
  - 🔴 **bug/error/issue/fix:** - Red (bold)
  - 🟢 **feat/feature/new/add:** - Green (bold)
  - 🟣 **pending/waiting/blocked/wip:** - Purple (bold)
  - 🔵 **refactor/cleanup/improve/optimize:** - Blue (bold)
  - 🟡 **test/testing/tests:** - Yellow (bold)
  - 🔷 **docs/doc/documentation:** - Light Blue (bold)
  - ⚪ **chore/misc/other:** - Gray (bold)
- **Inline Code Highlighting**: Text wrapped in backticks like \`this\` is now highlighted in orange (markdown-style)
- **Customizable Colors**: Users can customize task prefix colors via VS Code's `editor.tokenColorCustomizations`

### Fixed
- **Section Detection Bug**: Tasks ending with `:` (like "Bug: something") are no longer incorrectly colored as sections
  - Section pattern now uses negative lookahead to exclude lines starting with task checkboxes

### Changed
- Updated `.vscodeignore` to include CHANGELOG.md in the package and exclude development files

## [1.0.5] - 2025-10-10

### Added
- **Section Folding**: Sections can now be collapsed/expanded for better document organization
- **Syntax Highlighting**: Added TextMate grammar for better visual distinction between sections, tasks, and timestamps
- **Performance Caching**: Task hierarchy is now cached to avoid recalculation on every decoration update
- **Error Handling**: All commands now have try-catch blocks with user-friendly error messages
- **Comprehensive Tests**: Added tests for timestamp behavior, double-enter cancellation, backspace cancellation, and task content strikethrough

### Changed
- Improved decoration update performance by caching task content lines
- Better error reporting with console logging for debugging

### Fixed
- Performance improvements for large documents with many tasks

## [1.0.4] - 2025-10-08

### Fixed
- **ESC Key Interference**: Removed ESC keybinding that was preventing normal VS Code ESC functionality (closing suggestions, removing multi-cursors, etc.)

### Changed
- **Task Cancellation**: Empty task cancellation now only works with Backspace key - ESC key behaves normally in all contexts

### Removed
- ESC keybinding from package.json

## [1.0.3] - 2025-10-06

### Fixed
- **ESC Key Behavior**: Fixed bug where pressing ESC on a task line inserted the literal string "Escape" into the document

### Added
- **Test Coverage**: Added automated test to verify ESC correctly cancels newly-created empty tasks without inserting text

## [1.0.2] - 2025-10-05

### Added
- **Task Content Support**: Text between task lines now belongs to the task above
  - Content is any text between a task and the next task/section
  - Content is automatically struck through when parent task is marked as done
  - Content is included when archiving done tasks
  - Empty lines within content are preserved
- **Timestamp on Task Completion**: When marking a task as done, timestamp "@YYYY-MM-DD HH:mm:ss" is automatically added at the end
  - Timestamp is added to parent task and all cascading subtasks
  - Timestamp is removed when marking task as undone
- **Double-Enter to Cancel Task**: Press Enter twice on an empty new task to cancel task creation and proceed with normal line break
- **ESC/Backspace to Convert Task to Content**: Press ESC or Backspace on an empty new task to remove checkbox and convert line to regular content
  - Preserves indentation while removing checkbox
  - User can seamlessly create content for tasks

### Changed
- Enter key behavior enhanced with double-press detection
- ESC and Backspace keys now handle task cancellation

## [1.0.1] - 2025-10-01

### Added
- Bidirectional cascading task completion (parent done/undone affects all subtasks)
- Multi-line tab indentation for selected task lines
- Auto-task creation when pressing Enter at end of task line
- Comprehensive test suite with 21 tests

### Changed
- CSS-based decorations to prevent undo issues
- Theme-integrated colors for better compatibility

### Fixed
- Whitespace decoration issues
- Cursor positioning in various edge cases
## [1.0.1] - 2025-10-01

### Added
- Bidirectional cascading task completion (parent done/undone affects all subtasks)
- Multi-line tab indentation for selected task lines
- Auto-task creation when pressing Enter at end of task line
- Comprehensive test suite with 21 tests

### Changed
- CSS-based decorations to prevent undo issues
- Theme-integrated colors for better compatibility

### Fixed
- Whitespace decoration issues
- Cursor positioning in various edge cases

## [1.0.0] - 2025-09-30

### Added
- Initial release
- Basic task management with ☐ (todo) and ☑ (done) markers
- Section support with automatic task counters
- Archive functionality for completed tasks
- Keyboard shortcuts (Ctrl+Enter, Ctrl+D, Ctrl+Shift+A, Tab, Enter)
- Hierarchical task support with indentation
- Automatic counter updates for sections