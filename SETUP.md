# Setup Guide: Imaging with Nilearn (2026)

Welcome! This guide will get the course notebooks running on your own computer, in your web browser. It assumes **no prior coding experience**.

This guide has two parts:

- **Part 1: Pre-session setup** - do this on your own, before the session. It takes around 20–30 minutes.
- **Part 2: On the day** - a much shorter set of steps to reopen everything when the session begins.

If you get stuck at any point, email `samuel.beaton@psych.ox.ac.uk` with a screenshot of what you're seeing.

Throughout this guide, "Terminal" refers to: **Terminal** (Mac), **Command Prompt or PowerShell** (Windows), or your terminal application (Linux).

---

## Which instructions should I follow?

The steps below are split into three self-contained sections, one per operating system. Find yours and follow it all the way through, you shouldn't need to look at the other sections at all.

**Before jumping to your section, complete the two steps just below first, they're the same for everyone.**

- **Using a Mac?** → Go to Section A: Mac
- **Using Windows?** → Go to Section B: Windows
- **Using Linux?** → Go to Section C: Linux

---

## Step 1: Choose where the course materials will live (all systems)

Pick or create a folder on your computer where you'll keep course materials - for example `Documents/CourseMaterials`. You don't need to create the specific project folder yet; that happens automatically in the next step.

## Step 2: Download the course repository (all systems)

Choose **one** of the three methods below.

### Option A - Download as a ZIP (simplest, no extra software needed)

1. Go to the repository page in your browser: `https://github.com/sam-beaton/Nilearn2026`
2. Click the green **Code** button, then **Download ZIP**.
3. Find the downloaded ZIP file (usually in your Downloads folder) and unzip it (double-click, or right-click → Extract, depending on your system).
4. Move the unzipped folder into the location you chose in Step 1.

### Option B - Clone with Git (if you're comfortable with the Terminal)

1. Open a Terminal and navigate to the folder from Step 1, e.g.:
   ```
   cd Documents/CourseMaterials
   ```
2. Run:
   ```
   git clone https://github.com/sam-beaton/Nilearn2026
   ```
   This creates a new folder containing all the course files.

   (If you get a "command not found" error for `git`, you don't have Git installed - use Option A or C instead, or install Git from [git-scm.com](https://git-scm.com/downloads).)

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

**A1. Check you have Python installed**

1. Open Terminal.
2. Type `python3 --version` and press Enter.
3. You should see something like `Python 3.11.4`. You need **Python 3.10 or later**.

If you get an error, or your version is older than 3.10, download and install Python from [python.org/downloads](https://www.python.org/downloads/), then close and reopen Terminal and repeat the check.

**A2. Check pip is available**

```
pip3 --version
```
If this shows a version number, you're fine. If you get an error:
```
python3 -m ensurepip --upgrade
```

**A3. Navigate to the course folder in Terminal**

```
cd path/to/Nilearn2026
```
(Replace with wherever you put it - e.g. `cd Documents/CourseMaterials/Nilearn2026`.)

**A4. Create a virtual environment**

A "virtual environment" (or "venv") is an isolated space for this course's Python packages, so they don't interfere with anything else on your computer.
```
python3 -m venv venv
```

**A5. Activate the virtual environment**

```
source venv/bin/activate
```
Your Terminal prompt should now show `(venv)` at the start of the line.

**A6. Install the required packages**

```
./venv/bin/pip install -r requirements.txt
```

> **Why not just `pip install -r requirements.txt`?** On some computers, other Python tools you may have installed (like `pyenv` or `conda`) can quietly intercept the plain `pip` command, even when a venv is active, and install packages in the wrong place. Calling `pip` by its full path inside the `venv` folder, as shown above, avoids this problem entirely - please use this exact form.

This may take a minute or two.

**A7. You're done with pre-session setup!**

You can close everything down now and pick back up at the start of the session. To close down cleanly:

```
deactivate
```
This deactivates the virtual environment (your prompt will lose the `(venv)` prefix). You can then simply close the Terminal window.

> **Everything from here onward (Part 2) is only needed once the session itself begins** - there's no need to do this in advance.

---

### PART 2 - On the day (during the session)

**A8. Reactivate the virtual environment**

Open a Terminal, navigate back into the course folder (same as A3), then:
```
source venv/bin/activate
```

**A9. Launch Jupyter in your browser**

```
./venv/bin/jupyter-notebook
```
A new browser tab should open automatically, showing a file list. If it doesn't, look in the Terminal for a web address starting with `http://localhost:8888/...` and paste that into any browser.

**A10. Open and run a notebook**

1. Click **`nb_00_introduction.ipynb`** to open it.
2. Click into a grey code cell and press **Shift + Enter** to run it.
3. If you're asked to select a kernel, choose the option that mentions your project's `venv` folder (it may just be listed as "Python 3").
4. Work through `nb_00`, then `nb_01`, then `nb_02`, in order.

**A11. When you're finished**

Go back to the Terminal and press **Ctrl + C** (confirm with `y` if asked) to stop Jupyter. Then run:
```
deactivate
```
to close the virtual environment, and close the Terminal window.

---

## Section B: Windows

### PART 1 - Pre-session setup

**B1. Check you have Python installed**

1. Open Command Prompt (or PowerShell).
2. Type `python --version` and press Enter.
3. You should see something like `Python 3.11.4`. You need **Python 3.10 or later**.

If you get an error, or your version is older than 3.10, download and install Python from [python.org/downloads](https://www.python.org/downloads/). **On the first page of the installer, tick the box "Add python.exe to PATH"** before clicking Install - this step is easy to miss and causes problems later if skipped. Then close and reopen your Terminal and repeat the check.

**B2. Check pip is available**

```
pip --version
```
If this shows a version number, you're fine. If you get an error:
```
python -m ensurepip --upgrade
```

**B3. Navigate to the course folder in Terminal**

```
cd path\to\Nilearn2026
```
(Replace with wherever you put it - e.g. `cd Documents\CourseMaterials\Nilearn2026`.)

**B4. Create a virtual environment**

A "virtual environment" (or "venv") is an isolated space for this course's Python packages, so they don't interfere with anything else on your computer.
```
python -m venv venv
```

**B5. Activate the virtual environment**

Command Prompt:
```
venv\Scripts\activate.bat
```
PowerShell:
```
venv\Scripts\Activate.ps1
```
If PowerShell blocks this with an error about "execution policies," run this once first, then try activating again:
```
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
```
Your Terminal prompt should now show `(venv)` at the start of the line.

**B6. Install the required packages**

```
.\venv\Scripts\pip.exe install -r requirements.txt
```

> **Why not just `pip install -r requirements.txt`?** On some computers, other Python tools you may have installed can quietly intercept the plain `pip` command, even when a venv is active, and install packages in the wrong place. Calling `pip` by its full path inside the `venv` folder, as shown above, avoids this problem entirely - please use this exact form.

This may take a minute or two.

**B7. You're done with pre-session setup!**

You can close everything down now and pick back up at the start of the session. To close down cleanly:

```
deactivate
```
This deactivates the virtual environment (your prompt will lose the `(venv)` prefix). You can then simply close the Terminal window.

> **Everything from here onward (Part 2) is only needed once the session itself begins** - there's no need to do this in advance.

---

### PART 2 - On the day (during the session)

**B8. Reactivate the virtual environment**

Open a Terminal, navigate back into the course folder (same as B3), then use the same command as B5 (`venv\Scripts\activate.bat` or `venv\Scripts\Activate.ps1`).

**B9. Launch Jupyter in your browser**

```
.\venv\Scripts\jupyter-notebook.exe
```
A new browser tab should open automatically, showing a file list. If it doesn't, look in the Terminal for a web address starting with `http://localhost:8888/...` and paste that into any browser.

**B10. Open and run a notebook**

1. Click **`nb_00_introduction.ipynb`** to open it.
2. Click into a grey code cell and press **Shift + Enter** to run it.
3. If you're asked to select a kernel, choose the option that mentions your project's `venv` folder (it may just be listed as "Python 3").
4. Work through `nb_00`, then `nb_01`, then `nb_02`, in order.

**B11. When you're finished**

Go back to the Terminal and press **Ctrl + C** (confirm with `y` if asked) to stop Jupyter. Then run:
```
deactivate
```
to close the virtual environment, and close the Terminal window.

---

## Section C: Linux

### PART 1 - Pre-session setup

**C1. Check you have Python installed**

1. Open your terminal application.
2. Type `python3 --version` and press Enter.
3. You should see something like `Python 3.11.4`. You need **Python 3.10 or later**.

If you get an error, or your version is older than 3.10, install Python using your distribution's package manager (e.g. `sudo apt install python3` on Ubuntu/Debian), or from [python.org/downloads](https://www.python.org/downloads/).

**C2. Check pip is available**

```
pip3 --version
```
If this shows a version number, you're fine. If you get an error:
```
python3 -m ensurepip --upgrade
```
(On some distributions you may instead need `sudo apt install python3-pip` or your distribution's equivalent.)

**C3. Navigate to the course folder in Terminal**

```
cd path/to/Nilearn2026
```
(Replace with wherever you put it - e.g. `cd Documents/CourseMaterials/Nilearn2026`.)

**C4. Create a virtual environment**

A "virtual environment" (or "venv") is an isolated space for this course's Python packages, so they don't interfere with anything else on your computer.
```
python3 -m venv venv
```

**C5. Activate the virtual environment**

```
source venv/bin/activate
```
Your Terminal prompt should now show `(venv)` at the start of the line.

**C6. Install the required packages**

```
./venv/bin/pip install -r requirements.txt
```

> **Why not just `pip install -r requirements.txt`?** On some computers, other Python tools you may have installed (like `pyenv` or `conda`) can quietly intercept the plain `pip` command, even when a venv is active, and install packages in the wrong place. Calling `pip` by its full path inside the `venv` folder, as shown above, avoids this problem entirely - please use this exact form.

This may take a minute or two.

**C7. You're done with pre-session setup!**

You can close everything down now and pick back up at the start of the session. To close down cleanly:

```
deactivate
```
This deactivates the virtual environment (your prompt will lose the `(venv)` prefix). You can then simply close the terminal window.

> **Everything from here onward (Part 2) is only needed once the session itself begins** - there's no need to do this in advance.

---

### PART 2 - On the day (during the session)

**C8. Reactivate the virtual environment**

Open a terminal, navigate back into the course folder (same as C3), then:
```
source venv/bin/activate
```

**C9. Launch Jupyter in your browser**

```
./venv/bin/jupyter-notebook
```
A new browser tab should open automatically, showing a file list. If it doesn't, look in the terminal for a web address starting with `http://localhost:8888/...` and paste that into any browser.

**C10. Open and run a notebook**

1. Click **`nb_00_introduction.ipynb`** to open it.
2. Click into a grey code cell and press **Shift + Enter** to run it.
3. If you're asked to select a kernel, choose the option that mentions your project's `venv` folder (it may just be listed as "Python 3").
4. Work through `nb_00`, then `nb_01`, then `nb_02`, in order.

**C11. When you're finished**

Go back to the terminal and press **Ctrl + C** (confirm with `y` if asked) to stop Jupyter. Then run:
```
deactivate
```
to close the virtual environment, and close the terminal window.

---

## Troubleshooting

**"command not found" for `pip`, `jupyter`, or similar, even though the venv looks active**
Use the full-path versions shown above (`./venv/bin/...` on Mac/Linux, `.\venv\Scripts\...` on Windows) rather than the short command name. This sidesteps a common conflict with other Python tools that may be installed on your computer.

**(Windows) PowerShell won't let me activate the venv**
Run `Set-ExecutionPolicy -Scope CurrentUser RemoteSigned` once, then try again (see Step B5).

**`pip` isn't recognised at all**
Run `python3 -m ensurepip --upgrade` (Mac/Linux) or `python -m ensurepip --upgrade` (Windows), then retry.

**A notebook shows `ModuleNotFoundError: No module named 'nilearn'` (or similar)**
This means the notebook isn't using the right Python environment. Make sure you launched Jupyter using the full-path command (Step 9 in your section), from a Terminal where the venv was active, and check the selected kernel as described in Step 10.

**A cell that downloads data seems to hang, or shows a `429` or "Too Many Requests" error**
This shouldn't happen - the datasets needed for this course are already included in the `nilearn_data` folder in this repository. If you see this, please get in touch rather than trying to force a re-download.

**Something else isn't working**
Email `samuel.beaton@psych.ox.ac.uk` with a screenshot of the error and which step you were on.
