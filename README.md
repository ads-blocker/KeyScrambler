# ⌨️ KeyScrambler

> **You see only what you type. Keyloggers see garbage.**

A lightweight anti-keylogger tool that runs a low-level keyboard hook and injects random fake keystrokes around your real ones. What you type appears normally on screen; keyloggers and screen scrapers capture mostly noise.

---

## ✨ What it does

| You see | Keyloggers see |
|--------|-----------------|
| Your real typing, exactly as entered | Random A–Z characters mixed with your keys |
| Normal app behavior | Unusable, scrambled output |

- **Invisible mode** — runs in the background with no console window (when using the built `.exe`).
- **Layout-agnostic** — works with any keyboard layout; only injects around A–Z.
- **Modifier-safe** — does not scramble when Shift/Ctrl/Alt are held (shortcuts and capital letters stay clean).

---

## 🛠️ Requirements

- **Windows** (uses `user32` low-level hooks and `SendInput`).
- **.NET Framework 4.x** (for the C# build) or **PowerShell 5+** (for the script).

No admin rights needed for normal use. Run as admin only if you need the scrambler to affect apps that are themselves elevated.

---

## 📥 Usage

### Option 1: Run the executable (recommended)

1. Download or build **`KeyScrambler.exe`** (see [Building](#-building) below).
2. Double-click or run from a terminal. No window will appear.
3. Use your PC as usual; scrambling is active until you stop the process.

**To stop:** Task Manager → find **KeyScrambler.exe** → End task.

### Option 2: Run the PowerShell script

```powershell
powershell -ExecutionPolicy Bypass -File KeyScrambler.ps1
```

A console window will show status. Close the window or press **Ctrl+C** to stop.

---

## 🔨 Building

To produce a windowless `.exe` with your own icon:

1. **C# compiler**  
   Use the .NET Framework C# compiler, e.g.:
   - `C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe`

2. **Compile** (replace `YourIcon.ico` with your icon path):

   ```bat
   csc /target:winexe /out:KeyScrambler.exe /win32icon:YourIcon.ico KeyScrambler.cs
   ```

   - **`/target:winexe`** — no console window (runs in background).
   - **`/target:exe`** — keeps a console window if you prefer.

3. **Run**  
   Run **KeyScrambler.exe**; no installation needed.

---

## 📁 Repo contents

| File | Description |
|------|-------------|
| `KeyScrambler.ps1` | Original PowerShell script (inline C# + hook). |
| `KeyScrambler.cs`   | Standalone C# source for building the `.exe`. |

---

## ⚠️ Disclaimer

This tool is for **personal use and education**. Use it in environments where you are allowed to install and run keyboard hooks. The author is not responsible for misuse or compatibility issues with specific software or security policies.

---

## 📄 License

Use and modify as you like. Attribution appreciated but not required.
