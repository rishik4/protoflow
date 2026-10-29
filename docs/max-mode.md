# Max mode

Max mode is ProtoFlow's most capable AI mode. You describe a board in one message, and it picks real, orderable parts, draws the schematic, lays out and routes the PCB, and checks the result for errors. In the AI Copilot's mode menu it appears as **Max (Studio)**.

Max mode runs in one of two ways: on your own Claude Code or Codex, installed on your computer and signed in with your own subscription, or on ProtoFlow's hosted AI with nothing to install.

## Max mode or Standard mode

| | **Standard** | **Max (Studio)** |
|---|---|---|
| Best for | Quick edits, questions, focused changes | A whole board from a description |
| Parts | Searches and places parts you ask for | Chooses every part, with LCSC numbers, and imports its symbol, footprint and 3D model |
| Board | Edits the open schematic or PCB | Schematic, placement, routing and checks in one run |
| Memory | The current conversation | A design plan saved in the project, so a later session picks up where the last one stopped |
| Attachments | Images and PDFs | Any file |

See [AI assistant](ai-assistant.md) for Standard and Ask.

## What Max mode can do

- **Choose parts.** It searches the parts catalog, checks ratings, packages and stock, and brings each chosen part into the project with its symbol, footprint and 3D model. Standard resistors, capacitors, inductors and power symbols come from the built-in library.
- **Draw the schematic.** It builds and edits the schematic from the parts it chose, then runs the electrical rules check.
- **Lay out the board.** It sets the board outline, places parts, routes the copper, and runs the design rules check before it reports the board as done.
- **Read datasheets.** Give it a part number or attach a datasheet, and it reads the pages it needs.
- **Produce outputs when you ask.** Fabrication files (Gerbers, drill files, pick-and-place, an assembly BOM and a STEP model), a BOM or a netlist. It only exports fabrication files when you ask for them. It can also write firmware and assembly instructions as files in the same project.
- **Simulate when you ask.** It can run the built-in simulator and attach the waveform graph to its reply. It only simulates when you ask for a simulation.

The Studio introduction in the app estimates about 30 minutes for a board, depending on complexity.

### The design plan

While it works, Max mode keeps a live **Design plan** card pinned in the chat. It shows the functional blocks, the parts being weighed, chosen or ruled out, the decisions made so far and the next steps. Click the card to open the full plan.

The plan is saved in the project. When you start a new session on the same project, even with a different model, Max mode starts from the plan instead of researching the same parts again.

### Questions

When Max mode needs a decision that changes the hardware, such as a package size or the board size, it shows a question card with a few options and one marked as recommended. The run pauses until you answer.

To let it keep going without stopping, open the settings pill next to the send button, choose **Questions**, and pick **Use recommended**. Every choice it makes still appears in the chat. Pick **Ask me** to get the cards back.

## Who can use Max mode

Max mode is part of ProtoFlow's paid plans. Depending on your plan, you run it with your own Claude Code or Codex, or on ProtoFlow's hosted AI. See [pricing](https://www.protoflow.ai/pricing) for what each plan includes.

While the free trial is on, new accounts can try Max mode on their own board idea before choosing a plan. The trial is a small number of time-limited runs, and the mode menu shows how many are left. During a free run ProtoFlow picks the model. If a request fails before Max mode produces a response, the run is given back.

## Two ways to run Max mode

### With your own Claude Code or Codex

Claude Code (from Anthropic) and Codex (from OpenAI) are coding agents that run on your computer. When you link one, ProtoFlow starts it in the background for each Max mode run, inside your project folder, and connects it to ProtoFlow's design tools for that run. The work uses your own Claude or ChatGPT subscription and its usage limits.

What you need:

- ProtoFlow, signed in, on a plan that includes Max mode.
- Claude Code with a Claude account, or Codex with a ChatGPT account.
- A ProtoFlow project. Max mode works on saved project files. If nothing is open when you send your first message, the chat offers to create a project (see [Start a run](#start-a-run)).

Max mode runs with Claude Code or Codex. Gemini CLI is not one of the Max mode choices in this release, even with the **Enable Gemini CLI** setting under **Settings** > **Beta** turned on.

### On ProtoFlow's hosted AI

Pick **ProtoFlow AI** to run Max mode on ProtoFlow's servers. There is nothing to install. Choose a level in the **Model** menu:

| Level | Use it for |
|---|---|
| **Basic** | Quick boards and simple changes |
| **Fast** | The quickest full builds; good for most boards |
| **Pro** | Balanced; the default for most boards |
| **Advanced** | Dense, complex boards; reasons hardest |

Hosted runs use your plan's Max mode allowance. The chat shows how much of the month's allowance is used.

## Set up Max mode

1. Open the **AI Copilot** panel.
2. Click the mode menu at the bottom of the panel (tooltip **Conversation mode**) and choose **Max (Studio)**.
3. The first time, ProtoFlow shows the Studio introduction. Click **Open Studio**. If your plan doesn't include Max mode, the introduction offers an upgrade instead.
4. The **Max (Studio) runs with…** dialog opens. It checks your computer for Claude Code and Codex and shows a card for each, plus **ProtoFlow AI**.
5. Pick the agent you want to use.
   - If a card says **Not installed on this computer yet.**, click **Install Claude Code** or **Install Codex** on that card. ProtoFlow downloads the maker's official installer, verifies it, and sets it up in your user folder. You don't need a terminal, npm or an admin password.
   - If a card says the agent is **Signed out**, click **Sign in**. Your browser opens; approve the sign-in there and ProtoFlow picks it up. If the browser shows a code instead, paste it into the box in ProtoFlow and click **Submit**.
6. Click **Link Claude** or **Link Codex**. For hosted runs, click **Use ProtoFlow AI**.

On a free trial run there is nothing to set up: ProtoFlow runs it on its hosted AI and skips this dialog.

To change this later, open the settings pill and choose **Model**. The menu, **Choose who runs Max (Studio)**, lists **Claude**, **Codex** and **ProtoFlow AI**, each with its own models.

### Install or sign in from a terminal instead

If you prefer a terminal, these are the makers' own commands. ProtoFlow shows the same command under **Or in a terminal:** with a copy button.

| | macOS and Linux | Windows (PowerShell) |
|---|---|---|
| Install Claude Code | `curl -fsSL https://claude.ai/install.sh \| bash` | `irm https://claude.ai/install.ps1 \| iex` |
| Install Codex | `curl -fsSL https://chatgpt.com/codex/install.sh \| sh` | `powershell -ExecutionPolicy ByPass -c "irm https://chatgpt.com/codex/install.ps1 \| iex"` |
| Sign in to Claude Code | `claude auth login` | `claude auth login` |
| Sign in to Codex | `codex login` | `codex login` |

Then click **Re-check installed agents** in the dialog.

ProtoFlow finds `claude` and `codex` on your PATH, including paths set only in your shell's startup files. On macOS it can also use the agent that comes with the Claude desktop app, the Codex app or the ChatGPT app when no separate command is installed.

### If the agent is missing, signed out or out of date

You don't have to go back to the dialog. If you send a Max mode message and the agent is missing, signed out, or too old for the chosen model, the chat shows a card with a button to fix it, such as **Install Claude Code**, **Sign in to Codex** or **Update Codex**. Once it is fixed, ProtoFlow retries your message.

## Start a run

1. Open the project you want Max mode to work in. If no project is open, the chat shows a **Creating project** card when you send. Enter a **Project name**, pick a **Save location**, add a **Description**, and click **Accept**.
2. Describe the board. Say what it does, how it is powered, the connectors and interfaces, size limits, and any parts you already chose.
3. Attach anything that helps: datasheets, requirement documents, sketches or photos. Max mode accepts any file type. Attaching files needs a paid plan.
4. Press <kbd>Enter</kbd> or click the send button.

As Max mode saves its work, ProtoFlow reloads the open schematic and board tabs and opens new design files it creates. A status line in the chat says what it is doing.

Example prompts:

- "USB-C powered ESP32-S3 board with a 3.3 V regulator, two buttons and a status LED. Keep it under 40 x 30 mm, two layers."
- "Add a CAN transceiver to this board and route it to the connector on the left edge."
- "Export Gerbers and a BOM for this board."

### Settings for a run

Open the settings pill next to the send button (tooltip **Model & effort settings**):

| Row | What it sets |
|---|---|
| **Model** | Who runs Max mode, and which model. |
| **Effort** | How hard the model thinks. **Automatic** keeps whatever your Claude Code or Codex setup uses. |
| **Permissions** | **Allow all edits** or **Ask before edits** (see below). |
| **Questions** | **Ask me** or **Use recommended**. |
| **Usage limit** | When a Claude Code or Codex run should wrap up (see below). |

### Permissions

The **Permissions** setting decides how much your linked agent may do on its own:

- **Allow all edits** (the default): the agent runs commands and edits files in the project folder without approval prompts.
- **Ask before edits**: the agent falls back to its provider's automatic review for commands.

### Usage limits

Claude and ChatGPT subscriptions have 5-hour and weekly usage limits. Under **Usage limit**, choose **Wrap up at** a percentage. When your usage reaches it, Max mode finishes the current step, saves handoff notes in the project, and closes the task, so the project is free for you to edit.

The chat then shows a card with the time the limit resets. Click **Continue from notes** after the reset (or **Continue now** to use what is left), or **Open notes** to read them. Choose **Keep going** instead if you want runs to continue into the limit and pause until it resets.

## Stop and go back

- **Stop a run:** click the red stop button next to the send button. Work that Max mode already saved stays in your project.
- **Send while it works:** press <kbd>Enter</kbd> to queue a message so it sends when the run finishes, or <kbd>Shift</kbd>+<kbd>Enter</kbd> to steer (interrupt and send it now). See [AI assistant](ai-assistant.md#while-the-ai-works).
- **Go back:** Max mode saves its changes straight into the project files, so they are not separate undo steps in the editor. Before a large run, save a version of the project (see [Version control](version-control.md)) so you can return to it.
- **Protect parts:** right-click a part and choose **Lock in Place**. If Max mode tries to move, turn, flip or delete a locked part, ProtoFlow asks you first. If you keep it locked, the part goes back to where it was.

## Files Max mode adds to your project

Max mode works inside your project folder:

- It edits the project's schematic (`.kicad_sch`) and board (`.kicad_pcb`) files, and adds files you ask for, such as fabrication outputs.
- `.protoflow/studio/design-plan.json` and `.protoflow/studio/knowledge.md` hold the design plan and what earlier sessions settled. ProtoFlow writes them; you don't need to edit them.
- `Studio Handoff.md` holds the handoff notes when a run wraps up before a usage limit. You can read and edit it.

ProtoFlow keeps the design skills and instructions it gives your agent, and copies of your chat attachments, in its own app data folder. It does not add `AGENTS.md`, `CLAUDE.md` or skill folders to your project, and it passes its tools to Claude Code or Codex for each run instead of editing their configuration.

## Related

- [AI assistant](ai-assistant.md)
- [What the AI can do](ai-tools.md)
- [PCB editor](pcb-editor.md)
- [Version control](version-control.md)
