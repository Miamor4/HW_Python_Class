# Homework: Fixing a Conda Environment

In this assignment you will clone a repository, build a conda environment, fix a **package version conflict** in it, run a script, and submit proof that it worked by pushing to this repo.

> **Heads up:** The environment is broken on purpose. The `conda env create` step in Part 2 will fail. Figuring out why and fixing it is the assignment.

---

## What you'll turn in

A folder named `submissions/<your-github-username>/` pushed to this repository, containing:

1. `screenshot.png`: a screenshot of your terminal showing `python run_example.py` succeeding (see Part 4)
2. `environment.yml`: your fixed copy of the environment file
3. `notes.md`: 2–4 sentences on what the conflict was and how you fixed it

---

## Prerequisites

- **Conda.** Any of these works: [Miniforge](https://github.com/conda-forge/miniforge) (recommended), Miniconda, or Anaconda. Check with `conda --version`.
  - Windows: use the **Miniforge Prompt** (or Anaconda Prompt) instead of the regular Command Prompt.
- **Git.** Check with `git --version`.
- A GitHub account with access to this repository.

---

## Part 1: Download the repository

```bash
git clone <REPO-URL>
cd <REPO-NAME>
```

Replace `<REPO-URL>` with the URL from the green **Code** button on this repo's GitHub page.

Then run this **once**, right after cloning:

```bash
git update-index --skip-worktree environment.yml
```

This tells git to ignore any changes you make to `environment.yml`, so your fix stays on your computer and the file stays broken for everyone else. (You'll still submit a copy of your fix in your own folder in Part 5.)

---

## Part 2: Try to create the environment

The file `environment.yml` lists the Python version and packages this project needs. Ask conda to build an environment from it:

```bash
conda env create -f environment.yml
```

**This will fail.** Read the error message carefully.

---

## Part 3: Fix the environment

Open `environment.yml` in a text editor. Your job is to change it so conda can install everything together.

Some hints:
- Read the error. Which package does conda say can't be installed, and what does it need?
- Look at the version numbers in `environment.yml`. Do they agree with what the error says?
- Change as little as possible.

After editing `environment.yml`, try again:

```bash
conda env create -f environment.yml
```

If conda says the environment **already exists**, remove it and try again:

```bash
conda env remove -n hw-env
conda env create -f environment.yml
```

When it works, activate the environment:

```bash
conda activate hw-env
```

Your prompt should now start with `(hw-env)`.

---

## Part 4: Run the code

With `hw-env` active:

```bash
python run_example.py
```

Expected output (your exact version numbers may differ):

```
hi
numpy 1.26.4 | pandas 2.2.3
```

**Take a screenshot** of your terminal showing the command and both output lines. Save it as `screenshot.png`.

---

## Part 5: Submit by pushing to the repo

1. **Get the latest changes** so your push isn't rejected:
   ```bash
   git pull
   ```

2. **Make your submission folder** using your GitHub username:
   ```bash
   mkdir submissions/<your-github-username>
   ```

3. **Put your files in it:**
   - Move `screenshot.png` into the folder.
   - Copy your fixed `environment.yml` into the folder.
   - Create `notes.md` in the folder with your 2–4 sentence explanation.

4. **Check what git sees:**
   ```bash
   git status
   ```
   Only your `submissions/<your-github-username>/` folder should be listed. If `environment.yml` (the one at the top level) shows up, you skipped the `git update-index` command in Part 1. Run it now.

5. **Commit and push:**
   ```bash
   git add submissions/<your-github-username>
   git commit -m "Submission: <your-github-username>"
   git push
   ```

6. Refresh the repo on GitHub and make sure your folder shows up.

### If `git push` is rejected

Someone else pushed after you pulled. Run this, then push again:

```bash
git pull --rebase
git push
```

> **Only add files inside your own folder.** Don't change anyone else's files.

---

## Troubleshooting

| Problem | Try this |
|---|---|
| `conda: command not found` | Open a new terminal after installing conda. On Windows, use the Miniforge/Anaconda Prompt. |
| `conda activate` says to run `conda init` | Run `conda init`, close the terminal, and open a new one. |
| `ModuleNotFoundError: No module named 'pandas'` | The environment isn't active. Run `conda activate hw-env` and check for `(hw-env)` in your prompt. |
| "prefix already exists" / environment already exists | `conda env remove -n hw-env`, then create it again. |
| Lost track of what you changed | Easiest fix: delete your clone, clone again, and redo Part 1. |
| `Permission denied` on `git push` | Make sure you've been added as a collaborator and are signed in to GitHub. |
