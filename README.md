# Rename.sys — Bulk File Renamer

A single-file, browser-based tool for renaming large batches of files at once, styled like a retro green-on-black terminal.

## Tech Stack

- **HTML5** — single self-contained `.html` file, no build step, no install
- **CSS3** — custom properties (CSS variables) for the CRT/terminal theme, no external stylesheet or framework
- **Vanilla JavaScript (ES6+)** — no libraries, no frameworks, no dependencies (no React, no jQuery, nothing to `npm install`)
- **File System Access API** — the browser API (`window.showDirectoryPicker`, `FileSystemFileHandle.move()`) that lets the page read a folder on your computer and rename files directly on disk
- **Runs entirely client-side** — nothing is uploaded anywhere; all renaming happens locally in your browser

**Browser support:** Requires a Chromium-based browser (Chrome, Edge, Brave, Opera). The File System Access API is not supported in Firefox or Safari at the time of writing.

## Who It's For and What problem does it solve?

This tool is built for anyone who regularly has to rename large batches of files by hand — most notably:

- **Creative Directors / Design & Photo teams** — cleaning up a folder of exported assets (e.g. renaming `IMG_2931.jpg`, `IMG_2932.jpg`… into a proper naming convention like `Falcat_Hero_01.jpg`, `Falcat_Hero_02.jpg`)
- **Photographers & videographers** organizing shoot exports
- **Marketing/content teams** standardizing file names before upload to a DAM or CMS
- **Anyone** who's ever had to manually rename 50+ files one at a time in File Explorer/Finder

If you find yourself selecting files, hitting F2, and typing similar names over and over — this replaces that entire workflow with one pass.

## How to Use It

1. **Open the file.** Double-click `Rename.sys.html` (or open it via your browser's File > Open). It runs locally — no server needed.
2. **Choose a folder.** Click **"Choose folder…"** and select the folder containing the files you want to rename. Your browser will ask for permission to read/write that folder — allow it.
3. **Review the file list.** All files in that folder load into the panel, sorted naturally by name. Every file is selected by default.
4. **Narrow your selection (optional).**
   - Use **"Select files by number in name"** (From/To) plus **Select range** to only grab files containing a number in that range (e.g. only `photo_010.jpg` through `photo_050.jpg`).
   - Or use **Select all** / **Select none**, and click individual checkboxes next to each file.
5. **Set up your rename rule:**
   - **Find / Replace** — type text (or a regex pattern, if "Treat find as regex" is checked) to find in filenames, and what to replace it with. Leave "Replace with" blank to delete the matched text.
   - **Case sensitive** — toggle whether the Find match respects letter case.
   - **Case transform** — force the result to lowercase, UPPERCASE, Title Case, or Sentence case.
   - **Filename template** — build the final name using tokens:
     - `{name}` — the (possibly find/replace-edited) original filename
     - `{ext}` — the file extension
     - `{n}` — a sequence number
     - Click the token chips to insert them into the template, or just type your own text around them, e.g. `Falcat_Hero_{n}.{ext}`
   - **Numbering** — set the starting number (**Start at**) and how many digits to pad it to (**Digits**, e.g. `3` → `001`, `002`…).
6. **Check the live preview.** As you adjust settings, the file list updates in real time showing the current name → new name for every selected file, so you can confirm it looks right before committing.
7. **Apply the renames.** Click **"Apply renames"**. The tool renames each selected file directly in the folder and reports how many succeeded (and flags any that failed).

**Tip:** Nothing is renamed until you click "Apply renames" — feel free to experiment with Find/Replace, case transforms, and templates freely; the preview is non-destructive.
