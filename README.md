# JARVIS-Releases

# JARVIS

A voice assistant for Windows. Say "Jarvis" and then what you want — open apps,
find and read your files, take notes, set reminders, check the news, markets and
weather, control your screen, and more. It runs on your own PC with a heads-up
display in the corner of the screen, and uses the AI provider of your choice
with your own API key.

## Requirements

- Windows 10 or 11 (64-bit)
- A microphone
- An API key for at least one AI provider (see step 3)

## Install

1. Download **JARVIS-Setup.exe** from the latest release under
   [Releases](../../releases/latest).
2. Run it. The installer isn't code-signed yet, so Windows may show
   "Windows protected your PC". Click **More info**, then **Run anyway**.
3. JARVIS installs to `%LOCALAPPDATA%\Programs\JARVIS` and adds a Start menu
   shortcut. No administrator rights are needed.

## Set up your keys (required)

JARVIS ships without any keys. You supply your own, and they never leave your PC
except to call the provider they belong to.

1. Open the install folder: press **Win + R**, type
   `%LOCALAPPDATA%\Programs\JARVIS` and press Enter.
2. Copy **.env.example** and rename the copy to **.env**. If you can't see file
   extensions, turn on **View > Show > File name extensions** in File Explorer
   first, so the file isn't saved as `.env.txt`.
3. Open `.env` in Notepad and fill in **at least one** AI provider:

   | Provider | Key to set | Set `LLM_PROVIDER` to |
   |---|---|---|
   | Groq (has a free tier) | `GROQ_API_KEY` | `groq` |
   | Google Gemini | `GEMINI_API_KEY` | `gemini` |
   | Claude via Microsoft Foundry | `ANTHROPIC_FOUNDRY_API_KEY`, `ANTHROPIC_FOUNDRY_BASE_URL` | `claude` |

   Keys for more than one provider are fine: JARVIS uses `LLM_PROVIDER` first
   and falls back to the others if it fails.

4. Speech recognition: for the most accurate listening, set `STT_ENGINE=groq`
   (needs `GROQ_API_KEY`). `STT_ENGINE=whisper` runs entirely on your PC instead.
5. Optional extras:
   - `TAVILY_API_KEY`: better web research
   - `TRIPO_API_KEY`: 3D models from pictures
6. Save the file and start (or restart) JARVIS.

Never share your `.env` or post it anywhere. It holds your keys.

## Using it

- Start JARVIS from the Start menu. The HUD appears in the bottom-right corner.
- Say **"Jarvis"** followed by a command, e.g. "Jarvis, what time is it?" or
  "Jarvis, take a note: buy milk".
- Drag the HUD to move it. The square button stops him mid-sentence.
- Your notes, memory, calendar and files live in `C:\Users\<you>\JARVIS`,
  created on first run. They stay on your PC.

If Windows blocks the microphone, go to **Settings > Privacy & security >
Microphone** and allow desktop apps to use it.

## Updates

JARVIS checks this page for new releases every few hours. When one is available
it asks before installing. Your `.env` and your JARVIS folder are kept.

## Uninstall

**Settings > Apps > Installed apps > JARVIS > Uninstall.** Your
`C:\Users\<you>\JARVIS` folder is left in place. Delete it yourself if you want
your data gone too.
