# 🔐 Python Keylogger — Educational Project

> **Disclaimer:** This project is built strictly for educational purposes to understand how keyloggers work and how to defend against them. Never deploy this on any device you do not own. Unauthorized keylogging is illegal.

---

## 📋 Overview

A fully functional keylogger built in Python that captures keyboard input, mouse clicks, and active window titles — then saves the session as a `.txt` and `.docx` report, and optionally emails them when the session ends.

---

## ✨ Features

- **Keystroke logging** — captures all keyprintable characters word by word (not letter by letter)
- **Timestamped entries** — every word logged with the time it was typed
- **Active window tracking** — logs which app was in focus when keys were typed
- **Mouse click logging** — records click position and button used
- **Buffered file writing** — writes in batches of 10 for efficiency
- **Auto-rotating log files** — new file per session with start and end time in filename
- **Word-based logging** — flushes on space/enter, backspace removes last character
- **DOCX report generation** — formatted Word document with session info and captured log
- **Email reporting** — sends `.txt` and `.docx` as attachments via Gmail
- **Organized output** — all files saved into a dedicated `keylogger_info_files/` folder

---

## 📁 Project Structure

```
keylogger_project/
│
├── keylogger.py              # Main keylogger script
├── requirements.txt          # Python dependencies
├── README.md                 # This file
│
└── keylogger_info_files/     # Auto-created output folder (not uploaded)
    ├── 2026-04-26_09-34-22_to_09-45-10_keylog.txt
    └── 2026-04-26_09-34-22_to_09-45-10_keylog.docx
```

---

## 🛠️ Requirements

- Python 3.7+
- Windows OS (uses `pygetwindow` for active window detection)

### Dependencies

Install all dependencies with:

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install pynput pygetwindow python-docx
```

---

## ⚙️ Configuration

Before running, open `keylogger.py` and update Section 1:

```python
FLUSH_AFTER  = 10                       # Buffer size before writing to file
EMAIL_FROM   = "your_email@gmail.com"   # Sender Gmail address
EMAIL_TO     = "recipient@gmail.com"    # Recipient email address
EMAIL_PASS   = "your_app_password"      # Gmail App Password (not your main password)
OUTPUT_FOLDER = "keylogger_info_files"  # Output folder name
```

### Setting up Gmail App Password

1. Go to your Google Account → Security
2. Enable 2-Step Verification
3. Go to App Passwords → Generate a new password
4. Use that 16-character password as `EMAIL_PASS`

---

## 🚀 How to Run

**Step 1 — Clone the repo**
```bash
git clone https://github.com/your-username/keylogger-project.git
cd keylogger-project
```

**Step 2 — Create and activate virtual environment**
```bash
python -m venv venv

# Windows:
venv\Scripts\activate

# macOS/Linux:
source venv/bin/activate
```

**Step 3 — Install dependencies**
```bash
pip install -r requirements.txt
```

**Step 4 — Run the keylogger**
```bash
python keylogger.py
```

**Step 5 — Stop the keylogger**
```
Press ESC
```

When stopped, the script will:
1. Flush all buffered keystrokes to the `.txt` file
2. Rename the file with the final end time
3. Generate a `.docx` report
4. Email both files as attachments

---

## 📄 Output Example

**File names:**
```
2026-04-26_09-34-22_to_09-45-10_keylog.txt
2026-04-26_09-34-22_to_09-45-10_keylog.docx
```

**Log content:**
```
--- Session started: 2026-04-26 09:34:22 ---

[Window: Notepad]
[09:34:25] I'm [09:34:27] Chenitha [09:34:29] Gurusinghe
[09:34:31] I'm [09:34:32] 20 [09:34:34] years [09:34:35] old
[09:34:37] [CLICK Button.left at (540, 320)]

[Window: Chrome]
[09:34:42] hello [09:34:43] world
```

---

## 🔑 Key Behavior Reference

| Key | Behavior |
|---|---|
| Any letter / number | Collected silently into word buffer |
| `Space` | Flushes current word to log, stays on same line |
| `Enter` | Flushes current word and starts new line |
| `Backspace` | Removes last character from buffer |
| `Tab` | Flushes current word with tab spacing |
| `Shift / Ctrl / Alt` | Completely silent — not logged |
| `ESC` | Stops the keylogger and finalizes output |

---

## 🛡️ How to Defend Against Keyloggers

Understanding how keyloggers work helps you defend against them:

- Use a **password manager** — auto-fill bypasses keyboard input
- Enable **2FA** — passwords alone are not enough
- Keep **antivirus** up to date — behavioral detection catches hooks
- Monitor **running processes** for unknown scripts
- Use **virtual keyboards** for sensitive input
- Check **startup programs** regularly for suspicious entries

---

## 📚 What I Learned

- How `pynput` uses OS-level keyboard hooks (`SetWindowsHookEx` on Windows)
- Buffered file I/O for performance
- Active window detection with `pygetwindow`
- MIME email construction with attachments
- Word document generation with `python-docx`
- How antivirus tools detect keyloggers via behavioral heuristics

---

## ⚖️ Legal & Ethical Notice

This project is intended **only** for:
- Learning about cybersecurity concepts
- Running on your own machine in a controlled environment
- Understanding how to detect and defend against keyloggers

**It is illegal to use this on any device without explicit permission from the owner.**

---

## 👤 Author

**Chenitha Gurusinghe**
- GitHub: [@chenithz-gh](https://github.com/chenithz-gh)

---

## 📜 License

This project is licensed under the MIT License — for educational use only.
