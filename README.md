# Homework: Fixing a Conda Environment

In this assignment you will clone a repository, build a conda environment, fix a **package version conflict** in it, run a script, and submit proof that it worked by pushing to this repo.

> **Heads up:** The environment is broken on purpose. The `conda env create` step in Part 2 will fail. Figuring out why and fixing it is the assignment.

---

## What you'll turn in

A folder named `[your group]/<your-github-username>/` pushed to this repository, containing:

1. `screenshot.png`: a screenshot of your terminal showing `python run_example.py` succeeding (see Part 4)
---
## Part 0: Set up
 - If you don't have email access set up a github account using your personal email. 
- Open a terminal and navigate to your Desktop. If you are in windows use WSL (you might have to install it). If you are using a mac run git --version and follow the instructions.
- You will need to login to github from your terminal. First you need to install brew. /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
- I recommend using github CLI. Run `brew install gh`. 
- run ```bash 
gh auth login```
- Select Github.com as the type to authenticate and choose HTTPS
- Authenticate with y using git in the terminal
- Login to the Web and use the one time code from your terminal to login.


## Part 1: Download the repository

```bash
git clone <REPO-URL>
cd <REPO-NAME>
git update-index --skip-worktree environment.yml
git checkout -b [FirstName_LastName]
```

This tells git to ignore any changes you make to `environment.yml`, so your fix stays on your computer and the file stays broken for everyone else. (You'll still submit a copy of your fix in your own folder in Part 5.)

Hint: If you scroll up to the code button

---

## Part 2: Try to create the environment

The file `environment.yml` lists the Python version and packages this project needs. Ask conda to build an environment from it:

```bash
conda env create -f environment.yml
```

---

## Part 3: Fix the environment

Open `environment.yml` in a text editor. Your job is to change it so conda can install everything together.
In particular, we want the latest version of numpy.
---

## Part 4: Run the code

Activate the hw-env to make sure if builds correctly after your changes.
```bash
conda env create -f environment.yml
conda activate hw-env
```


```bash
python run_example.py
```

Expected output (your exact version numbers may differ):

```
hi
numpy (version) | pandas version
```

**Take a screenshot** of your terminal showing the command and both output lines. Save it as `screenshot.png`.

---

## Part 5: Submit by pushing to the repo

1. **Get the latest changes** so your push isn't rejected:
   ```bash
   git pull origin main
   ```

2. **Make your submission folder** using your GitHub username:
   ```bash
   mkdir [your group]/<your-github-username>
   ```

3. **Put your files in it:**
   - Move `screenshot.png` into the folder.

4. **Commit and push:**
   ```bash
   git add [your group]/<your-github-username>
   git commit -m "Submission: <your-github-username>"
   git push -u origin FirstName_LastName
   ```
   There will be a link: https://github.com/Tonnar/HW_Python_Class/pull/new/FirstName_LastName. Follow the link and  create the the pull request. 

> **Only add files inside your own folder.** Don't change anyone else's files.
