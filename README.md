# ⚡ LeetCode Auto Sync & Organizer

Automate your entire LeetCode workflow — from syncing solved problems to organizing them by topic and updating your README automatically.

Stop manually copying solutions. Let automation handle it.

---

## 🚀 What This Does

This project creates a fully automated pipeline that:

* 🔄 Syncs solved problems from LeetCode
* 🗂 Organizes them into DSA topic folders
* 📊 Generates and updates README statistics
* 🤖 Commits changes automatically using GitHub Actions

---

## 🧠 Why This Exists

Manually maintaining a LeetCode repository looks like this:

* Copy solution
* Create folder
* Paste code
* Update README
* Repeat forever

This project eliminates that entire workflow.

---

## ⚙️ How It Works

```text
LeetCode
   ↓
GitHub Action Trigger
   ↓
Fetch Accepted Submissions
   ↓
Organize by DSA Topics (Python Script)
   ↓
Update README Statistics
   ↓
Auto Commit to Repository
```

Runs automatically on schedule or manually.

---

## 📂 Project Structure

```text
leetcode-auto-sync
│
├── .github
│   └── workflows
│       └── leetcode-sync.yml
│   └── scripts
|        ├── organize.py
|        └── update_readme.py
│
└── README.md
```

---

## 🛠 Tech Stack

* Python (automation scripts)
* GitHub Actions (CI/CD automation)
* LeetCode session authentication

---

## 🔧 Setup Guide

### 1. Create Your Own Repo

Create a new GitHub repository (empty).

---

### 2. Copy Files

Copy these into your repo:

* `.github/workflows/leetcode-sync.yml`
* `.github/scripts/organize.py`
* `.github/scripts/update_readme.py`

---

### 3. Get LeetCode Session Cookie

1. Open LeetCode in browser
2. Open DevTools → Application → Cookies
3. Copy value of:

```text
LEETCODE_SESSION
```

---

### 4. Add GitHub Secret

Go to:

**Settings → Secrets → Actions**

Add:

```text
LEETCODE_SESSION = your_cookie_value
```

---

### 5. Run Workflow

Go to:

**Actions → LeetCode Sync → Run Workflow**

That’s it. The system will:

* fetch your solved problems
* organize them
* generate README
* push updates automatically

---

## ⚠️ Common Issues & Fixes

During setup, you may encounter some common errors. Here are the fixes for the most frequent ones:

---

### 1. ❌ Script Not Found

**Error:**

```text
python: can't open file 'scripts/update_readme.py'
```

**Fix:**

* Ensure your scripts are inside the correct folder:

```text
scripts/
```

* Verify workflow path:

```yaml
run: python scripts/update_readme.py
```

---

### 2. ❌ Push Rejected (Fetch First)

**Error:**

```text
failed to push some refs
```

**Fix:**
Update your commit step in workflow:

```bash
git add .
git commit -m "Auto update" || echo "No changes"
git pull --rebase origin main
git push
```

---

### 3. ❌ Cannot Pull with Rebase

**Error:**

```text
cannot pull with rebase: You have unstaged changes
```

**Fix:**
Commit changes before pulling:

```bash
git add .
git commit -m "update"
git pull --rebase origin main
```

---

### 4. ❌ Scripts Not Running After Sync

**Cause:**
LeetCode sync action may overwrite repository contents.

**Fix:**
Store scripts safely inside:

```text
.github/scripts/
```

Update workflow:

```yaml
run: python .github/scripts/organize.py
run: python .github/scripts/update_readme.py
```

---

### 5. ❌ Problems Going to `misc` Folder

**Cause:**
Topic keyword not detected.

**Fix:**
Add more keywords in `organize.py`:

```python
"integer": "13-math",
"roman": "13-math",
"sum": "02-two-pointers",
"parentheses": "04-stack"
```

---

### 6. ❌ README Shows 0 Problems

**Cause:**
Script is checking for files, but problems are stored as folders.

**Fix:**
Replace:

```python
os.path.isfile(...)
```

with:

```python
os.path.isdir(...)
```

---

### 7. ❌ Workflow Runs but No Changes Appear

**Possible Reasons:**

* No new problems solved
* No changes detected in repo

This is expected behavior.

---

### 8. ❌ Workflow Not Triggering

**Fix:**

* Ensure workflow file is inside:

```text
.github/workflows/
```

* Trigger manually:

```text
Actions → LeetCode Sync → Run Workflow
```

---

## 💡 Tip

If something doesn’t work:

* Check GitHub Actions logs
* Verify file paths carefully
* Ensure secrets are correctly added

Most issues are caused by small misconfigurations.

---


## 📊 Sample Output

### 📁 Folder Structure

```text
01-arrays
02-two-pointers
03-sliding-window
04-stack
07-trees
10-dynamic-programming
13-math
15-strings
16-misc
```

---

### 📄 README Statistics (Auto Generated)

```text
Total Problems Solved: 50

| Topic | Problems |
|------|------|
01-arrays | 6  
02-two-pointers | 5  
04-stack | 4  
10-dynamic-programming | 7  
13-math | 5  
15-strings | 6  
16-misc | 17  
```

---

### 📦 Problem Structure

```text
07-trees/
   0104-maximum-depth-of-binary-tree/
       README.md
       solution.py
```

---

## 🔍 Live Example

Check a working implementation here:

👉 https://github.com/TheCreator8055/LeetCode-Programs

---

## 📈 What You Learn From This

* CI/CD automation using GitHub Actions
* Python scripting for real-world workflows
* Repository design & structure
* Eliminating repetitive developer tasks

---

## 💡 Future Improvements

* Smarter topic classification
* Multi-language support
* Difficulty-based grouping
* Visualization dashboard

---

## 📜 License

MIT License

---

## ⭐ Support

If this saved you time, consider starring the repo.
