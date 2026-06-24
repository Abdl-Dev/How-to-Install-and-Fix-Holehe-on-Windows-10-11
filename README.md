# How to Install and Fix Holehe on Windows 10/11

A simple, step-by-step guide to installing the **holehe** OSINT tool on Windows, including how to fix common Python path errors and network crash issues.

---

## 🛠️ Step 1: Install Python Correctly

Before installing the tool, you must have Python installed on your computer.

1. Go to the official website: **[python.org/downloads](https://www.python.org/downloads/)**
2. Download the latest stable version for Windows
3. Open the downloaded installer file
4. **CRUCIAL STEP:** At the very bottom of the installer window, check the box that says **"Add python.exe to PATH"**
5. Click **Install Now**

---

## ⚙️ Step 2: Fix Windows "Not Found" or "Truncated" Errors

Windows sometimes gets confused about where Python is installed. We need to tell your computer exactly where to find your tools permanently.

1. Click your Windows **Start** button
2. Type **PowerShell**, right-click it, and choose **Run as Administrator**
3. Copy and paste this exact command into the blue window and press **Enter**:

```powershell
[Environment]::SetEnvironmentVariable('Path', [Environment]::GetEnvironmentVariable('Path', 'User') + ';C:\Users\Administrator\AppData\Local\Programs\Python\Python312\Scripts', 'User')
```

4. Close the PowerShell window completely

---

## 🚀 Step 3: Install Holehe

Now that your system knows where Python is, you can install the tool cleanly.

1. Open a brand new **PowerShell** or **Command Prompt (CMD)** window
2. Type this command to install the tool using Python 3.12:

```cmd
py -3.12 -m pip install holehe
```

3. Upgrade your package manager to the latest version by running:

```cmd
python.exe -m pip install --upgrade pip
```

---

## 🔧 Step 4: Fix the "ConnectTimeout" Crash

If you try to run the tool now, it might crash with a long error message ending in `httpx.ConnectTimeout`. This happens because the tool tries to check for updates online, and your internet network or firewall blocks it.

Here's how to turn off the update check permanently:

1. In your PowerShell window, type this command to open the tool's core code file in Notepad:

```powershell
notepad "C:\Users\Administrator\AppData\Local\Programs\Python\Python312\Lib\site-packages\holehe\core.py"
```

2. Inside Notepad, press **Ctrl + F** on your keyboard to open the search box
3. Search for the word: `check_update()`
4. Look for the line where it is called (around line 190) inside maincore
5. Put a hashtag (`#`) at the very beginning of that line to turn it off. It should look like this:

```python
#check_update()
```

6. Press **Ctrl + S** to save the file, then close Notepad

---

## 🎉 Step 5: Run the Tool!

Your tool is now perfectly fixed and ready to go. You can open a standard command prompt anytime and run a scan from anywhere.

To scan an email, just type:

```cmd
holehe youremail@gmail.com
```

---

## Understanding Your Results

| Symbol | Meaning | Action |
|--------|---------|--------|
| **[+] Green / Plus** | The email is used on this website | — |
| **[-] Minus** | The email is not registered here | — |
| **[x] Yellow / X** | Rate Limit - Website blocked the tool | Turn on a VPN or use Mobile Hotspot to change your IP address, then try again |

---

## Troubleshooting

If you encounter any issues during the installation process, make sure to:

- Verify that Python is correctly added to your PATH environment variable
- Run PowerShell as Administrator when executing environment variable commands
- Ensure you have an active internet connection for the initial pip install
- Check that your firewall or antivirus software isn't blocking Python or the holehe tool

---

## Resources

- **Holehe GitHub:** [GitHub Repository](https://github.com/megadose/holehe)
- **Python Official Website:** [python.org](https://www.python.org/)
- **OSINT Tools:** Learn more about OSINT techniques and tools

---

**Last Updated:** June 2026
