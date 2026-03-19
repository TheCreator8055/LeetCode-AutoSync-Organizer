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
│
├── scripts
│   ├── organize.py
│   └── update_readme.py
│
├── sample-output
│   └── README-preview.md
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
* `scripts/organize.py`
* `scripts/update_readme.py`

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

👉 https://github.com/yourusername/leetcode-solutions

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
