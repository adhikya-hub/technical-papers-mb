# Git

## Git Basics

### 1. Initialize Git repository

```bash
git init
```

### 2. Add a file `a.txt`

```bash
touch a.txt
git add a.txt
```

### 3. Make a commit

```bash
git commit -m "Initial commit"
```

### 4. Create a branch called `leaf`

```bash
git branch leaf
git checkout leaf
```

Alternative:

```bash
git checkout -b leaf
```

Alternative (modern Git):

```bash
git switch -c leaf
```

### 5. Add a file `b.txt`

```bash
touch b.txt
git add b.txt
```

### 6. Create a second commit

```bash
git commit -m "Add b.txt"
```

### 7. Merge `leaf` into `master`

```bash
git checkout master
git merge leaf
```

Alternative (modern Git):

```bash
git switch master
git merge leaf
```

## Checking Understanding

### What is the staging area?

* The staging area is an intermediate space where changes are prepared before committing.
* `git add` moves changes to the staging area.

### Where is the HEAD right now?

```bash
git status
git log --oneline --decorate
```

Alternative:

```bash
git branch
```

Alternative:

```bash
cat .git/HEAD
```

* `HEAD` points to the current branch and latest commit.
* After merging, `HEAD` usually points to the latest commit on `master`.
