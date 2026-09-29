# Simple Commentor — a fork of Commentator

A patched build of [Commentator](https://github.com/Fevol/obsidian-criticmarkup) 0.2.7, tuned for a
comment-first workflow. The changes were applied to the released bundle, so this branch contains
only the ready-to-install plugin files.

## Install

Copy `main.js`, `styles.css` and `manifest.json` from this branch into `<vault>/.obsidian/plugins/simple-commentor/`,
reload Obsidian, and enable **Simple Commentor** in Community Plugins. It has its own plugin id
(`simple-commentor`), so upstream updates won't overwrite it. Disable the official Commentator plugin
if you have it, so the two don't both render the same markup.

## Changes

**Commenting**
- `Cmd/Ctrl + /` (command "Comment on selection") wraps the selection as `{==target==}{>>…<<}` and puts
  the cursor where the comment text starts. There's no author/time metadata by default.
- Empty comments are removed automatically once the cursor leaves them. An empty comment's orphan highlight is unwrapped too.
- The inline bubble icon is shown for comments attached to a highlight or revision. Hover shows the popup, and click
  opens an editable chip.
- Replies to a comment render in one gutter card, separated by a faint line.

**Revisions**
- Hovering an addition, deletion or substitution shows a small capsule chip with accept (✓) and reject (✕).
- Gutter: an uncommented revision is shown as a coloured line and triangle, and clicking it adds a comment to that revision.
- Commented revisions use a transparent tint that keeps the text colour. The bubble and card border are
  red (deletion), green (addition) or `#a67c00` (substitution).
- Typing inside a comment in Suggestion mode stays plain text; it isn't turned into `{++…++}`.
- "Toggle suggestion mode" returns to the default mode instead of Corrected.

**Rendering**
- Only the markup under the cursor reveals its syntax. A selection spanning markup no longer shows raw syntax.
- Decorations rebuild on every edit, which avoids markup occasionally not rendering.
- Syntax is revealed on focus in every edit mode.
- Under the Minimal theme, the gutter sits next to the paragraph instead of at the left or far right edge.

**Annotation view (sidebar)**
- It shows the current note only, with a Comment / Revise segmented switch.
- Cards have no file header. The commented source text is a small, faded quote with a left rule.
- Revisions are colour-coded. The hover actions are reduced to ✓ / ✕ in the lower-left corner.
- Double-clicking a card fills the matching inline icon.

**Appearance**
- New setting "Annotation color scheme": Light / Dark / Follow Obsidian theme.
- All custom styles live in `styles.css`, so the plugin folder is self-contained.
