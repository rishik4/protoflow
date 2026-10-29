# Version Control

ProtoFlow tracks your design history in two ways. **Version History** keeps a snapshot every time you save, with a visual preview of what changed. The **Git** panel lets you commit, branch, and push a project with Git without leaving the editor.

## Version History

Version History works on schematics, boards, symbols, and footprints. It starts once a document has been saved to a file or project.

Open it with the **Version History** button (the clock icon) in the schematic toolbar, or with **View > Version History**.

### What gets recorded

- Each save adds a version to the list. A version lists the changes made since the previous save, each marked **You** or **AI**.
- Changes you have not saved yet appear at the top under **Unsaved changes**.
- ProtoFlow keeps the most recent 50 versions for each project. They are stored in a hidden folder inside the project folder.

### Preview a version

Hover over a version in the list. The canvas shows what differs between that version and your current design: on a schematic, parts, wires, and labels that were added show in green and ones that were removed show in red. Move the pointer away to hide the preview. Symbols and footprints have no canvas preview, but you can still restore them.

### Restore a version

1. Click **Restore** on the version you want.
2. Confirm in the **Restore version?** dialog.

Your current state is saved first as a **Before restore** entry, so nothing is lost. Restoring clears the undo and redo history for that tab.

## Git

The **Git** panel is a full Git client for your project folder. It needs Git installed on your computer. If it is missing, the panel shows **Git is not available on this system**.

Open the panel from its icon in the activity bar on the left edge, or with **View > Git**. Click **Full Screen** in the panel header for a larger view with branches, commit history, and commit details side by side.

### Set up a repository

When no repository is open, the panel offers:

- **Open Folder**: open a folder that is already a Git repository.
- **Initialize Repository**: turn the current project folder into a repository.
- **Clone Repository**: clone from GitHub or any Git URL into a folder you choose.
- **Create Repository**: create a new project folder and initialize it.
- **Open Recent Repository**: reopen a repository you used before.

### Commit changes

1. The panel lists changed files as **Added**, **Modified**, **Deleted**, or **Renamed**.
2. Stage the files you want with **Stage All**, or stage and unstage files one at a time.
3. Type a **Commit message**.
4. Click **Commit to** *branch name*.

Right-click a file for more options, such as **Discard Changes** or revealing it in your file manager. Discarding cannot be undone.

### Sync with a remote

Use **Fetch**, **Pull**, and **Push** at the top of the commit graph. They use the remotes and credentials already set up for Git on your computer. To publish a new repository to GitHub, create the repository on GitHub, add it as a remote with Git, then push from ProtoFlow. Cloning works with any Git URL.

### Branches and merges

- **New Branch** creates a branch. You can also right-click a commit and choose **New Branch from Here**.
- **Checkout** switches to another branch.
- **Delete Branch** removes a branch. If it has work that is not merged, ProtoFlow warns you and offers **Force Delete**.
- **Merge Branch** merges another branch into the current one.

If a merge has conflicts, each conflicted file offers **Ours** (keep the current branch's version), **Theirs** (keep the incoming version), and **View** (show the differences). For schematics, **View** draws the conflict on the canvas. When every conflict is resolved, click **Complete Merge**, or click **Abort Merge** to cancel.

### Commit history and diffs

The **GRAPH** section shows the commit history.

- Hover over a commit to preview, on the open schematic, how it differs from your current design. Click the commit to pin the preview, and press <kbd>Esc</kbd> to exit.
- Right-click a commit for **Copy Commit Hash**, **Checkout This Commit**, and commit details.
- Open a file's text diff and use **Copy Diff** to copy it.

ProtoFlow saves designs as KiCad text files, so Git diffs and merges work on them the same way they do for KiCad projects. Commit the `.protoflow.json` files and the `.protoflow` launcher along with your KiCad files. See [Files, import and export](files-and-import-export.md).

## Related

- [Files, import and export](files-and-import-export.md)
- [Collaboration](collaboration.md)
- [Comments and reviews](comments-and-reviews.md)
- [AI assistant](ai-assistant.md)
