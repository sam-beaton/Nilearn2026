# Setup Guide: Imaging with Nilearn (2026)

Welcome! This guide will get the course notebooks running on your own computer, in your web browser. It assumes **no prior coding experience**.

This guide has two parts:

- **Part 1: Pre-session setup**: do this on your own, before the session. It takes around 20 to 30 minutes, most of which is waiting for downloads.
- **Part 2: On the day**: a much shorter set of steps to reopen everything when the session begins.

If you get stuck at any point, email `samuel.beaton@psych.ox.ac.uk` with a screenshot of what you're seeing.

Throughout this guide, "Terminal" refers to: **Terminal** (Mac), **PowerShell or Command Prompt** (Windows), or your terminal application (Linux).

A few tips that apply to everything below:

- **Copy and paste commands exactly**, one at a time. If an error shows two commands stuck together on one line, press **Esc** (Windows) or **Ctrl + C** (Mac/Linux) to clear the line, then paste the command again on its own.
- **If a folder name contains spaces, put it in double quotes**, e.g. `cd "My Course Files"`.
- **After you install anything** (Python or Git), close your Terminal window and open a new one. A Terminal only notices newly installed programs when it starts.
- **Use a normal Terminal window**, not one opened with "Run as administrator".

---

## Which instructions should I follow?

The steps below are split into three self-contained sections, one per operating system. Find yours and follow it all the way through, you shouldn't need to look at the other sections at all.

**Before jumping to your section, complete the two steps just below first, they're the same for everyone.**

- **Using a Mac?** → Go to Section A: Mac
- **Using Windows?** → Go to Section B: Windows
- **Using Linux?** → Go to Section C: Linux

---

## Step 1: Choose where the course materials will live (all systems)

Pick or create a folder on your computer where you'll keep course materials, for example a folder called `CourseMaterials` inside your `Documents` folder.

A folder that is *not* synced by OneDrive, iCloud or Dropbox is best, because the setup creates thousands of small files that these services try to sync, which can slow things down. This is only a recommendation: on many university computers `Documents` is synced by OneDrive, and the setup still works there, just a little more slowly.

If you'd like to create the folder from the Terminal instead of your file explorer, the same command works on every system:

```
mkdir CourseMaterials
```

## Step 2: Download the course repository (all systems)

Choose **one** of the three methods below. If you have never used Git, **Option A is the simplest**.

### Option A - Download as a ZIP (simplest, no extra software needed)

1. Go to the repository page in your browser: `https://github.com/sam-beaton/Nilearn2026`
2. Click the green **Code** button, then **Download ZIP**.
3. Find the downloaded ZIP file (usually in your Downloads folder) and unzip it (double-click, or right-click → Extract All, depending on your system).
4. Move the unzipped folder into the location you chose in Step 1.

> **Note on the folder name:** the unzipped folder will be called `Nilearn2026-master`, not `Nilearn2026`. On Windows, "Extract All" sometimes creates a folder *inside* a folder of the same name. The folder you want is the one that **contains the file `nb_00_introduction.ipynb`**. Wherever the instructions below say "the course folder", this is the folder they mean.

### Option B - Clone with Git (if you're comfortable with the Terminal)

1. Open a Terminal and go to the folder from Step 1. In Terminal (Mac), PowerShell (Windows) or your terminal (Linux), type `cd` followed by the folder's path, for example:
   - Mac or Linux:
     ```
     cd Documents/CourseMaterials
     ```
   - Windows:
     ```
     cd Documents\CourseMaterials
     ```
2. Run:
   ```
   git clone https://github.com/sam-beaton/Nilearn2026
   ```
   This creates a new folder called `Nilearn2026` containing all the course files.

   If you get an error saying `git` is "command not found" (Mac and Linux) or "The term 'git' is not recognized" (Windows), Git isn't installed. Either use Option A or C instead, or install Git from [git-scm.com](https://git-scm.com/downloads), **close your Terminal, open a new one**, go back to the folder from Step 1 and run the clone command again.

### Option C - GitHub Desktop (a visual alternative to Git)

1. Install [GitHub Desktop](https://desktop.github.com/) if you don't already have it.
2. Open GitHub Desktop → **File → Clone Repository**.
3. Paste in the repository link: `https://github.com/sam-beaton/Nilearn2026`
4. Choose the folder from Step 1 as the **Local Path**, then click **Clone**.

---

Now go to the section for your operating system below.

---

## Section A: Mac

### PART 1 - Pre-session setup

**A1. Check you have a suitable version of Python**

You need **Python 3.12 or later**. Python 3.13 is the version this course was tested on, and is the one we recommend.

1. Open Terminal.
2. Type `python3 --version` and press Enter.
3. You should see something like `Python 3.13.3`.

If you get an error, or the version is older than 3.12 (Macs often come with an old Python, such as 3.9), download and install Python 3.13 from [python.org/downloads](https://www.python.org/downloads/) (on that page, scroll to the list of releases and choose the latest 3.13). Then **close Terminal, open a new one**, and repeat the check.

**A2. Open Terminal in the course folder**

The easiest way:

1. In Terminal, type `cd` followed by **a space** (don't press Enter yet).
2. In Finder, drag the course folder (the one containing `nb_00_introduction.ipynb`) into the Terminal window. Its path is filled in for you.
3. Press Enter.

Alternatively, type the path yourself, e.g. `cd Documents/CourseMaterials/Nilearn2026`. Put the path in double quotes if any folder name has spaces.

To check you're in the right place, type `ls` and press Enter. You should see `nb_00_introduction.ipynb` in the list.

**A3. Create a virtual environment**

A "virtual environment" (or "venv") is an isolated space for this course's Python packages, so they don't interfere with anything else on your computer.
```
python3 -m venv venv
```

**A4. Activate the virtual environment**

```
source venv/bin/activate
```
Your Terminal prompt should now show `(venv)` at the start of the line.

**A5. Install the required packages**

```
./venv/bin/python -m pip install -r requirements.txt
```

> **Why this exact command?** On some computers, other Python tools you may have installed (like `pyenv` or `conda`) can quietly intercept the plain `pip` command, even when a venv is active, and install packages in the wrong place. Calling Python by its full path inside the `venv` folder, as shown above, avoids this problem entirely. Please use this exact form.

**This takes several minutes (usually 3 to 10), and the screen may look frozen** at a line saying "Installing collected packages". It hasn't crashed. Wait until you get your prompt back (the line starting with `(venv)`) and the last line starts with "Successfully installed". Don't close the window or press anything before then.

**A6. You're done with pre-session setup!**

You can close everything down now and pick back up at the start of the session. To close down cleanly:

```
deactivate
```
This deactivates the virtual environment (your prompt will lose the `(venv)` prefix). You can then simply close the Terminal window.

> **Everything from here onward (Part 2) is only needed once the session itself begins**: there's no need to do this in advance.

---

### PART 2 - On the day (during the session)

**A7. Reactivate the virtual environment**

Open a Terminal, go back into the course folder (same as A2), then:
```
source venv/bin/activate
```

**A8. Launch Jupyter in your browser**

```
./venv/bin/jupyter-notebook
```
A new browser tab should open automatically, showing a file list. If it doesn't, look in the Terminal for a web address starting with `http://localhost:8888/...` (copy the whole address, including the part after `?token=`) and paste it into the address bar of any browser.

If that command doesn't work, use this one instead:
```
./venv/bin/python -m notebook
```

**A9. Open and run a notebook**

1. Click **`nb_00_introduction.ipynb`** to open it.
2. Click into a grey code cell and press **Shift + Enter** to run it.
3. You shouldn't be asked to choose a kernel. If you are, choose **Python 3**.
4. Work through `nb_00`, then `nb_01`, then `nb_02`, in order.

**A10. When you're finished**

Go back to the Terminal and press **Ctrl + C** (confirm with `y` if asked) to stop Jupyter. Then run:
```
deactivate
```
to close the virtual environment, and close the Terminal window.

---

## Section B: Windows

### PART 1 - Pre-session setup

**B1. Check you have a suitable version of Python**

You need **Python 3.12 or later**. Python 3.13 is the version this course was tested on, and is the one we recommend.

1. Open PowerShell (search for "PowerShell" in the Start menu).
2. Type `python --version` and press Enter.
3. You should see something like `Python 3.13.3`.

If you see an error such as "The term 'python' is not recognized", or the Microsoft Store opens, or the version is older than 3.12, then Python isn't installed (or Windows can't find it). Download and install Python 3.13 from [python.org/downloads](https://www.python.org/downloads/) (on that page, scroll to the list of releases and choose the latest 3.13). **On the first page of the installer, tick the box "Add python.exe to PATH"** before clicking Install. This is easy to miss and causes problems later if skipped. Then **close PowerShell, open a new window**, and repeat the check.

**B2. Open PowerShell in the course folder**

The easiest way:

1. Open File Explorer and go to the course folder (the one containing `nb_00_introduction.ipynb`).
2. Click once in the **address bar** at the top, where the folder's path is shown, so the text highlights.
3. Type `powershell` and press Enter.

A PowerShell window opens already inside that folder.

Alternatively, open PowerShell from the Start menu and type `cd` followed by the folder's path, e.g. `cd Documents\CourseMaterials\Nilearn2026`. **If any folder name contains spaces, put the whole path in double quotes**, e.g. `cd "OneDrive - Nexus365\Documents\Nilearn2026"`.

To check you're in the right place, type `dir` and press Enter. You should see `nb_00_introduction.ipynb` in the list.

**B3. Create a virtual environment**

A "virtual environment" (or "venv") is an isolated space for this course's Python packages, so they don't interfere with anything else on your computer.
```
python -m venv venv
```

**B4. Activate the virtual environment**

```
venv\Scripts\Activate.ps1
```
Your Terminal prompt should now show `(venv)` at the start of the line.

If PowerShell blocks this with a red error about running scripts being "disabled on this system", run this once, then try activating again:
```
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```
If that command is refused too (some university or work computers don't allow it), open **Command Prompt** in the course folder instead (the same address bar trick, but type `cmd`) and activate with:
```
venv\Scripts\activate.bat
```
Activation is a convenience: the install and launch commands in the following steps use the full path to the `venv` folder, so they work either way.

**B5. Install the required packages**

```
.\venv\Scripts\python.exe -m pip install -r requirements.txt
```

> **Why this exact command?** On some computers, other Python tools you may have installed can quietly intercept the plain `pip` command, even when a venv is active, and install packages in the wrong place. Calling Python by its full path inside the `venv` folder, as shown above, avoids this problem entirely. Please use this exact form.

**This takes several minutes (usually 3 to 10), and the screen may look frozen** at a line saying "Installing collected packages". It hasn't crashed. Wait until you get your prompt back (the line starting with `(venv)` or `PS`) and the last line starts with "Successfully installed". Don't close the window or press anything before then.

**B6. You're done with pre-session setup!**

You can close everything down now and pick back up at the start of the session. To close down cleanly:

```
deactivate
```
This deactivates the virtual environment (your prompt will lose the `(venv)` prefix). You can then simply close the Terminal window.

> **Everything from here onward (Part 2) is only needed once the session itself begins**: there's no need to do this in advance.

---

### PART 2 - On the day (during the session)

**B7. Reactivate the virtual environment**

Open PowerShell in the course folder (same as B2), then use the same command as B4 (`venv\Scripts\Activate.ps1`, or `venv\Scripts\activate.bat` in Command Prompt).

**B8. Launch Jupyter in your browser**

```
.\venv\Scripts\jupyter-notebook.exe
```
A new browser tab should open automatically, showing a file list. A few things can happen here:

- **Windows may ask which app to use to open the link.** Choose any web browser (Chrome, Edge or Firefox) and, if offered, tick the option to always use it. This happens on computers that haven't had a default browser chosen yet.
- **If no browser tab opens**, look in the Terminal for a web address starting with `http://localhost:8888/...`. Copy the whole address, including the part after `?token=`, and paste it into the address bar of any browser.

If the command above doesn't work, use this one instead:
```
.\venv\Scripts\python.exe -m notebook
```

**B9. Open and run a notebook**

1. Click **`nb_00_introduction.ipynb`** to open it.
2. Click into a grey code cell and press **Shift + Enter** to run it.
3. You shouldn't be asked to choose a kernel. If you are, choose **Python 3**.
4. Work through `nb_00`, then `nb_01`, then `nb_02`, in order.

**B10. When you're finished**

Go back to the Terminal and press **Ctrl + C** (confirm with `y` if asked) to stop Jupyter. Then run:
```
deactivate
```
to close the virtual environment, and close the Terminal window.

---

## Section C: Linux

### PART 1 - Pre-session setup

**C1. Check you have a suitable version of Python**

You need **Python 3.12 or later**. Python 3.13 is the version this course was tested on, and is the one we recommend.

1. Open your terminal application.
2. Type `python3 --version` and press Enter.
3. You should see something like `Python 3.13.3`.

If you get an error, or the version is older than 3.12 (some Linux versions come with an older Python), install a newer one using your distribution's package manager (e.g. `sudo apt install python3.13 python3.13-venv` on Ubuntu or Debian, if your version offers it), or download it from [python.org/downloads](https://www.python.org/downloads/). If you installed a specific version such as 3.13, use `python3.13` in place of `python3` in the commands below.

On Ubuntu and Debian you may also need `sudo apt install python3-venv` (or `python3.13-venv`) so that virtual environments can be created.

**C2. Open a terminal in the course folder**

Most file managers let you right-click inside the course folder (the one containing `nb_00_introduction.ipynb`) and choose **Open in Terminal**; the exact wording depends on your desktop.

Alternatively, open your terminal and type `cd` followed by the folder's path, e.g. `cd Documents/CourseMaterials/Nilearn2026`. Put the path in double quotes if any folder name has spaces.

To check you're in the right place, type `ls` and press Enter. You should see `nb_00_introduction.ipynb` in the list.

**C3. Create a virtual environment**

A "virtual environment" (or "venv") is an isolated space for this course's Python packages, so they don't interfere with anything else on your computer.
```
python3 -m venv venv
```

**C4. Activate the virtual environment**

```
source venv/bin/activate
```
Your Terminal prompt should now show `(venv)` at the start of the line.

**C5. Install the required packages**

```
./venv/bin/python -m pip install -r requirements.txt
```

> **Why this exact command?** On some computers, other Python tools you may have installed (like `pyenv` or `conda`) can quietly intercept the plain `pip` command, even when a venv is active, and install packages in the wrong place. Calling Python by its full path inside the `venv` folder, as shown above, avoids this problem entirely. Please use this exact form.

**This takes several minutes (usually 3 to 10), and the screen may look frozen** at a line saying "Installing collected packages". It hasn't crashed. Wait until you get your prompt back (the line starting with `(venv)`) and the last line starts with "Successfully installed". Don't close the window or press anything before then.

**C6. You're done with pre-session setup!**

You can close everything down now and pick back up at the start of the session. To close down cleanly:

```
deactivate
```
This deactivates the virtual environment (your prompt will lose the `(venv)` prefix). You can then simply close the terminal window.

> **Everything from here onward (Part 2) is only needed once the session itself begins**: there's no need to do this in advance.

---

### PART 2 - On the day (during the session)

**C7. Reactivate the virtual environment**

Open a terminal, go back into the course folder (same as C2), then:
```
source venv/bin/activate
```

**C8. Launch Jupyter in your browser**

```
./venv/bin/jupyter-notebook
```
A new browser tab should open automatically, showing a file list. If it doesn't, look in the terminal for a web address starting with `http://localhost:8888/...` (copy the whole address, including the part after `?token=`) and paste it into the address bar of any browser.

If that command doesn't work, use this one instead:
```
./venv/bin/python -m notebook
```

**C9. Open and run a notebook**

1. Click **`nb_00_introduction.ipynb`** to open it.
2. Click into a grey code cell and press **Shift + Enter** to run it.
3. You shouldn't be asked to choose a kernel. If you are, choose **Python 3**.
4. Work through `nb_00`, then `nb_01`, then `nb_02`, in order.

**C10. When you're finished**

Go back to the terminal and press **Ctrl + C** (confirm with `y` if asked) to stop Jupyter. Then run:
```
deactivate
```
to close the virtual environment, and close the terminal window.

---

## Troubleshooting

**An error shows two commands stuck together on one line**

You pasted a command while the previous one was still on the line. Press **Esc** (Windows PowerShell) or **Ctrl + C** (Mac/Linux) to clear the line, then paste the command again on its own.

**"command not found" or "is not recognized" for `python`, `git`, `jupyter` or similar**

If you have just installed the program, close your Terminal and open a new one. If you are running a `jupyter` or `pip` command, use the full-path versions shown above (`./venv/bin/...` on Mac/Linux, `.\venv\Scripts\...` on Windows) rather than the short command name. This sidesteps a common conflict with other Python tools that may be installed on your computer.

**(Windows) PowerShell won't let me activate the venv**

Run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` once, then try again. If that is refused, activate from Command Prompt using `venv\Scripts\activate.bat` instead (see Step B4).

**The install says "No matching distribution found", or a package fails to install**

Check your Python version with `python3 --version` (Mac/Linux) or `python --version` (Windows). The course needs Python 3.12 or later, and has been tested on 3.13. Very new Python releases may not be supported by every package yet, so if yours is newer than 3.13, install 3.13 instead.

**The install seems frozen**

Package installation is slow and prints nothing for several minutes at "Installing collected packages". Wait for the prompt to come back. If the course folder is in a OneDrive, iCloud or Dropbox folder, it can take longer; pausing syncing for a while may help.

**I already use `uv`, `conda` or `pyenv`, and `python` isn't found or is the wrong one**

Create the venv with whichever Python you prefer (for example, the full path to a Python 3.13), then follow the other steps unchanged. The full-path commands (`./venv/bin/...` or `.\venv\Scripts\...`) work whatever else is installed.

**A notebook shows `ModuleNotFoundError: No module named 'nilearn'` (or similar)**

This means the notebook isn't using the right Python environment. Stop Jupyter (Ctrl + C), then launch it again using the full-path command from your section's "Launch Jupyter" step, from a Terminal in the course folder. Check that the install step finished with "Successfully installed".

**A cell that downloads data seems to hang, or shows a `429` or "Too Many Requests" error**

This shouldn't happen: the datasets needed for this course are already included in the `nilearn_data` folder in this repository. If you see this, please get in touch rather than trying to force a re-download.

**Something else isn't working**

Email `samuel.beaton@psych.ox.ac.uk` with a screenshot of the error and which step you were on.
