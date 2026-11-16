# Homework: Fixing a Conda Environment

In this assignment you will clone a repository, build a conda environment, fix a **package version conflict** in it, run a script, and submit proof that it worked by pushing to this repo.

> **Heads up:** The environment is broken on purpose. The `conda env create` step in Part 2 will fail. Figuring out why and fixing it is the assignment.

---

## What you'll turn in

A folder named `submissions/<your-github-username>/` pushed to this repository, containing:

1. `screenshot.png`: a screenshot of your terminal showing `python run_example.py` succeeding (see Part 4)
2. `environment.yml`: your fixed copy of the environment file

---

## Part 1: Download the repository

```bash
git clone <REPO-URL>
cd <REPO-NAME>
git update-index --skip-worktree environment.yml
```

This tells git to ignore any changes you make to `environment.yml`, so your fix stays on your computer and the file stays broken for everyone else. (You'll still submit a copy of your fix in your own folder in Part 5.)

---

## Part 2: Try to create the environment

The file `environment.yml` lists the Python version and packages this project needs. Ask conda to build an environment from it:

```bash
conda env create -f environment.yml
```

---

## Part 3: Fix the environment

Open `environment.yml` in a text editor. Your job is to change it so conda can install everything together.
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

4. **Commit and push:**
   ```bash
   git add submissions/<your-github-username>
   git commit -m "Submission: <your-github-username>"
   git push
   ```

> **Only add files inside your own folder.** Don't change anyone else's files.

---
