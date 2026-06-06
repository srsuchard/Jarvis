# Jarvis
This is where I will be posting updates on my remake of Tony Starks Jarvis Ai


# Jarvis — your PC assistant

A lightweight Windows assistant that opens apps, finds files, opens folders and
websites, and answers to either typed or spoken commands.

## 1. Install Python
If you don't have it: https://www.python.org/downloads/ — **check "Add Python to PATH"** during install.

## 2. (Optional) Install voice support
Text mode works with zero dependencies. For voice:

```
pip install -r requirements.txt
```

If `pyaudio` fails to install (common on Windows), try:

```
pip install pipwin
pipwin install pyaudio
```

`pyttsx3` (the speaking voice) works offline. The listening side uses Google's
free recognizer, so voice input needs an internet connection.

## 3. Run it

```
python jarvis.py
```

## What to say / type
| Command | Does |
|---|---|
| `open chrome` | launches any installed app (matched from your Start Menu) |
| `open downloads` | opens a folder |
| `find budget.xlsx` | searches your files — then type the result number to open |
| `search for resume` | same as find |
| `open youtube` | opens a saved website |
| `google mechanical keyboards` | web search |
| `what time is it` / `what's the date` | clock |
| `list apps` | shows apps Jarvis discovered |
| `rescan files` | rebuilds the file index (after adding new files) |
| `voice` / `text` | switch input mode |
| `help` / `quit` | self-explanatory |

## Make it yours
Open `jarvis.py` and edit the section near the top marked **CUSTOMIZE ME**:

- `CUSTOM_APPS` — nicknames → an .exe path or app name (e.g. `"ide": r"C:\...\Code.exe"`)
- `CUSTOM_FOLDERS` — nicknames → folder paths you want to jump to (`"pi": r"C:\...\RaspberryPi"`)
- `CUSTOM_SITES` — words → URLs
- `SEARCH_ROOTS` — which folders get indexed when you search for files

## Notes
- First file search builds an index (cached in `.jarvis_cache.json`); later searches are instant.
- Folder matching beats app matching, so `open downloads` opens the folder, `open chrome` opens the app.
