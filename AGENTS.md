# ProtoFlow: instructions for AI agents

You're helping someone install and start using **ProtoFlow**, a desktop app for designing circuit boards with AI. It covers schematics, parts, PCB layout, autorouting, ERC/DRC and manufacturing files. ProtoFlow is a graphical app. You install it and help the person get going; they sign in and design inside the app.

Follow these steps in order. Keep your messages to the person short and plain.

## Ground rules

- **Ask first.** Before you download or install anything, tell the person what you'll install, where it goes, and roughly how big it is (60 to 250 MB). Wait for a yes.
- **Use official files only.** Download installers only from this repository's GitHub Releases (the URLs in `latest.json`). Always check the SHA-256 before you install.
- **Don't handle their account.** Never create an account, type a password, or sign in for them. The person does that part in the app.
- **Don't use admin rights you don't need.** No ProtoFlow install needs `sudo` or an administrator prompt.
- If a step fails, show the person the error and stop. Don't work around security prompts.

## 1. Find the right installer

Fetch the manifest:

```
https://raw.githubusercontent.com/rishik4/protoflow/main/latest.json
```

Its shape:

```json
{
  "platforms": {
    "macos":       { "version": "3.3.1", "files": [{ "name": "...macOS.dmg", "kind": "dmg", "url": "...", "sha256": "...", "size": 0 }] },
    "windows":     { "version": "3.3.1", "files": [{ "kind": "exe", "...": "..." }] },
    "linux-x64":   { "version": "3.3.1", "files": [{ "kind": "AppImage" }, { "kind": "tar.gz" }] },
    "linux-arm64": { "version": "3.0.5", "files": [{ "kind": "AppImage" }, { "kind": "tar.gz" }] }
  }
}
```

Pick the platform key:

| System | Key | Requirements |
|---|---|---|
| macOS, Apple silicon or Intel | `macos` | macOS 11 or later. One universal app. On macOS 12 or 13, tell the person the AI features may not connect; macOS 14 or later is recommended. |
| Windows | `windows` | Windows 10 or 11, x64. |
| Linux x86_64 | `linux-x64` | Ubuntu 22.04 or newer, or a similar distro (glibc 2.35+). |
| Linux arm64 | `linux-arm64` | Same as above. Its arm64 build may be older than the x86_64 one. |

Platforms can be on different versions. That's expected, because each platform ships separately. ProtoFlow updates itself after install.

## 2. Install

### macOS

```bash
curl -fsSL https://raw.githubusercontent.com/rishik4/protoflow/main/latest.json -o /tmp/protoflow-latest.json
url=$(plutil -extract platforms.macos.files.0.url raw -o - /tmp/protoflow-latest.json)
sha=$(plutil -extract platforms.macos.files.0.sha256 raw -o - /tmp/protoflow-latest.json)
curl -fL "$url" -o /tmp/ProtoFlow.dmg
echo "$sha  /tmp/ProtoFlow.dmg" | shasum -a 256 -c -
hdiutil attach -nobrowse -quiet -mountpoint /tmp/protoflow-dmg /tmp/ProtoFlow.dmg
ditto /tmp/protoflow-dmg/Protoflow.app /Applications/Protoflow.app
hdiutil detach -quiet /tmp/protoflow-dmg
open /Applications/Protoflow.app
```

- `plutil ... raw` needs macOS 12 or later. On macOS 11, read the JSON another way, for example with `python3 -c`.
- If `/Applications/Protoflow.app` already exists, ProtoFlow is installed. Ask before replacing it. It updates itself anyway.
- The app is signed and notarized, so it should open without a Gatekeeper warning.

### Windows (PowerShell)

```powershell
$ProgressPreference = 'SilentlyContinue'
$latest = Invoke-RestMethod https://raw.githubusercontent.com/rishik4/protoflow/main/latest.json
$file = $latest.platforms.windows.files[0]
$out = Join-Path $env:TEMP $file.name
Invoke-WebRequest $file.url -OutFile $out
if ((Get-FileHash $out -Algorithm SHA256).Hash.ToLower() -ne $file.sha256) { throw "Checksum mismatch: do not install" }
Start-Process $out -ArgumentList '/VERYSILENT','/SUPPRESSMSGBOXES','/NORESTART' -Wait
Start-Process "$env:LOCALAPPDATA\Programs\Protoflow\Protoflow.exe"
```

- The installer is per-user (no administrator prompt). It installs to `%LOCALAPPDATA%\Programs\Protoflow`.
- If the person would rather click through the installer, run `Start-Process $out` without the arguments.
- If Windows SmartScreen shows "Windows protected your PC", tell the person. They can choose **More info**, then **Run anyway**. Don't try to bypass it yourself.

### Linux

AppImage (simplest):

```bash
curl -fsSL https://raw.githubusercontent.com/rishik4/protoflow/main/latest.json -o /tmp/protoflow-latest.json
key=linux-x64   # or linux-arm64
read -r url sha < <(python3 -c "import json,sys; f=[f for f in json.load(open('/tmp/protoflow-latest.json'))['platforms']['$key']['files'] if f['kind']=='AppImage'][0]; print(f['url'], f['sha256'])")
mkdir -p ~/Applications
curl -fL "$url" -o ~/Applications/ProtoFlow.AppImage
echo "$sha  $HOME/Applications/ProtoFlow.AppImage" | sha256sum -c -
chmod +x ~/Applications/ProtoFlow.AppImage
~/Applications/ProtoFlow.AppImage &
```

Or the tarball, which also adds a menu entry and a `protoflow` launcher in `~/.local/bin`:

```bash
# url and sha for the file whose kind is "tar.gz"
curl -fL "$url" -o /tmp/ProtoFlow.tar.gz
echo "$sha  /tmp/ProtoFlow.tar.gz" | sha256sum -c -
tar -xzf /tmp/ProtoFlow.tar.gz -C /tmp
/tmp/Protoflow/install-local.sh
~/.local/bin/protoflow &
```

- If `jq` is installed you can use it instead of `python3`.
- Runtime libraries ProtoFlow needs on Ubuntu 22.04: `libnss3 libasound2 libgbm1 libpulse0`, plus GTK and a secret-service keyring (GNOME Keyring or KWallet). If one is missing, tell the person the `apt install` command and let them run it. It needs `sudo`.
- If the AppImage fails with a FUSE error, run it with `--appimage-extract-and-run`, or use the tarball.
- Run ProtoFlow as a normal user, not root.

## 3. First launch and sign-in

1. ProtoFlow opens to a sign-in screen. The person signs in or creates a free account, with email or with Google (which opens their browser). Wait for them to tell you it's done.
2. If they're new to PCB design, the app offers a short tutorial. Suggest taking it.

## 4. Help with the first project

Suggest something small and real, for example:

> "Make a USB-C powered board with an ESP32-S3, a 3.3 V regulator, a status LED, and a reset button."

Tell the person to:

1. Type the idea into the AI box on the start screen, or create a new project and describe it in the AI panel.
2. Watch the AI place parts and wire the schematic. Every change can be undone or rolled back to a checkpoint.
3. Run the checks (ERC), then move to the PCB: auto-place, autoroute, run DRC and look at the 3D view.
4. Export Gerbers or order boards when they're happy.

The [Getting started guide](docs/getting-started.md) walks through the same steps with GIFs. For any "how do I..." question, look it up in the [docs index](docs/README.md) before you answer. Don't guess menu names.

## 5. Working alongside ProtoFlow

### Max mode can run on the agent they already have

If the person uses Claude Code or Codex (you may be one of them), ProtoFlow's [Max mode](docs/max-mode.md) can run whole-board design work through it, using their own Claude or ChatGPT subscription. ProtoFlow starts the agent itself for each run, inside the project folder, and passes it ProtoFlow's design tools for that run only. It doesn't change the agent's own settings, and you don't need to configure anything. Gemini CLI is not a Max mode option.

The setup happens in the app:

1. Open the **AI Copilot** panel. In the mode menu at the bottom, choose **Max (Studio)**. The first time, click **Open Studio** on the introduction.
2. The **Max (Studio) runs with…** dialog lists Claude Code, Codex and **ProtoFlow AI** (hosted, nothing to install).
3. If the agent shows **Not installed on this computer yet.**, the person clicks **Install Claude Code** or **Install Codex**. If it shows **Signed out**, they click **Sign in** and finish in the browser. If you're helping in a terminal, the makers' own commands work too: `claude auth login` or `codex login` to sign in. Then they click **Re-check installed agents**.
4. They click **Link Claude** or **Link Codex**, then describe the board in the chat.

Before the first run, tell the person two things:

- By default (**Allow all edits** under the settings pill's **Permissions** row), the linked agent runs commands and edits files in the project folder without asking. **Ask before edits** is the stricter option.
- Max mode saves straight into the project files, so its changes aren't undo steps in the editor. Suggest saving a version of the project first ([Version control](docs/version-control.md)).

Max mode needs a plan that includes it. While the free trial is on, new accounts get a few trial runs on ProtoFlow's hosted AI, and the mode menu shows how many are left. Point the person to https://www.protoflow.ai/pricing for plans, and don't guess at what their plan includes.

### Project files

- Projects are folders of ordinary files. The schematic is a KiCad `.kicad_sch` file and the board is a KiCad `.kicad_pcb` file, so KiCad opens them too.
- Max mode adds `.protoflow/studio/design-plan.json` and `.protoflow/studio/knowledge.md` (its design plan and notes), and `Studio Handoff.md` when a run stops at a usage limit. It doesn't add AGENTS.md, CLAUDE.md or skill folders to the project.
- You can read these files to answer questions about the design.
- Make design changes inside ProtoFlow (its AI panel or Max mode) rather than by editing the files. If you have to edit a file directly, ask the person to save and close the project in ProtoFlow first, then reopen it afterwards.
- Don't edit a project while a Max mode run is working on it.

## 6. Uninstall

- macOS: quit ProtoFlow, then delete `/Applications/Protoflow.app`.
- Windows: **Settings > Apps > Installed apps > Protoflow > Uninstall**.
- Linux: delete the AppImage, or for the tarball install remove `~/.local/share/protoflow`, `~/.local/bin/protoflow`, `~/.local/bin/.protoflow-bin` and the `.desktop` file in `~/.local/share/applications`.

Projects are ordinary files in the folder the person chose, and uninstalling doesn't touch them.

## Links

- Docs: https://github.com/rishik4/protoflow/tree/main/docs
- Releases: https://github.com/rishik4/protoflow/releases
- Website: https://www.protoflow.ai
- Pricing and plans: https://www.protoflow.ai/pricing
