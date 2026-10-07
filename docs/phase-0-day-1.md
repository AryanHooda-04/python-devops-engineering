# Phase 0 — Day 1 Notes

## DevOps Environment Setup + Linux + Git Fundamentals

These notes capture what was completed on **Day 1**, along with the concepts worth remembering for revision.

The Phase 0 goal is to establish a repeatable engineering environment with Python, Git, Linux access, secure credential handling, terminal basics, and Git workflow.

---

## 1. Current DevOps Environment

### Windows Office Laptop

```text
Python     : 3.14.2
Git        : 2.50.0.windows.2
Terraform  : Available
Git Bash   : Available
```

Restricted or unavailable:

```text
Docker Desktop : Cannot install
VS Code        : Cannot install
WSL            : Cannot install / not needed
```

### Red Hat Linux Environment

```text
OS      : Red Hat Enterprise Linux 10.0
Python  : 3.12.9
Git     : 2.47.1
User    : student
Home    : /home/student
```

### Environment Persistence Note

The Red Hat training VM is **ephemeral**. It has a limited lab lifetime and lab-hour allocation, and it may be reset or deleted later.

Therefore:

```text
Red Hat VM = Practice environment
GitHub / approved persistent storage = Source of truth
```

Important scripts, notes, configuration files, and project work should not exist only inside the VM.

Future workflow:

```text
Work in Red Hat VM
        ↓
Create or update files
        ↓
git add
git commit
        ↓
git push
        ↓
Persistent remote repository
```

If the VM is recreated later:

```bash
git clone <repository-url>
cd <repository>
```

This makes the learning environment rebuildable.

### Important Lesson

A DevOps learning environment does **not** require every tool to be installed on one computer.

The adapted setup is:

```text
Windows Office Laptop
│
├── Python
├── Git
├── Git Bash
├── Terraform
│
└── Browser
     │
     └── Red Hat Linux VM
          ├── Linux
          ├── Bash
          ├── Python
          └── Git
```

The Red Hat VM serves as the primary Linux lab environment.

---

## 2. Environment Verification Commands

### Windows

Check Python:

```powershell
python --version
```

Check Git:

```powershell
git --version
```

Check Git configuration:

```powershell
git config --global --list
```

Check pip:

```powershell
python -m pip --version
```

### Result

```text
Python 3.14.2
Git 2.50.0.windows.2
```

---

## 3. Git Identity Configuration

Git commits contain information about who created them.

Configure username:

```bash
git config --global user.name "AryanHooda-04"
```

Configure email:

```bash
git config --global user.email "your-email@example.com"
```

Verify:

```bash
git config --global --list
```

### Important

Git configuration on Windows and Git configuration inside a Linux VM are separate.

Configuration may need to be performed in both environments.

---

## 4. Git vs GitHub

This distinction is important.

### Git

Git is a **version-control system**.

It tracks:

```text
Files
Changes
Commits
Branches
History
```

It can work entirely on a computer without GitHub.

### GitHub

GitHub is a platform that hosts Git repositories remotely.

Later it will provide:

```text
Remote repositories
Pull requests
Issues
Code reviews
GitHub Actions
Collaboration
```

---

## 5. Basic Linux Commands Learned

### `pwd`

Shows the current working directory.

```bash
pwd
```

Example:

```text
/home/student/devops-day1
```

Think:

> Where am I?

---

### `ls`

Lists files and directories.

```bash
ls
```

---

### `ls -la`

Shows more information, including hidden files.

```bash
ls -la
```

Example:

```text
.git
README.md
docs
scripts
```

Options:

```text
-l = long/detailed listing
-a = include hidden files
```

Linux hidden files and directories normally begin with:

```text
.
```

Example:

```text
.git
```

---

### `cd`

Changes directory.

```bash
cd devops-day1
```

Return to home:

```bash
cd ~
```

---

### `mkdir`

Creates a directory.

```bash
mkdir scripts
```

Multiple directories:

```bash
mkdir scripts docs
```

Create parent directories if needed:

```bash
mkdir -p scripts docs
```

---

### `touch`

Creates an empty file.

```bash
touch README.md
```

---

### `echo`

Prints text.

```bash
echo "Hello"
```

Can also write text into a file:

```bash
echo "# DevOps Learning Journey" > README.md
```

### `>`

Redirects output into a file.

Important:

```text
> overwrites the existing file
```

Later:

```text
>> appends to the file
```

---

### `cat`

Displays file contents.

```bash
cat README.md
```

Example:

```text
# DevOps Learning Journey Starts
Day 1 - Linux environment successfully configured.
```

---

### `whoami`

Shows the current logged-in user.

```bash
whoami
```

Output:

```text
student
```

---

### OS Information

```bash
cat /etc/redhat-release
```

Output:

```text
Red Hat Enterprise Linux release 10.0
```

---

## 6. Linux Directory Created

During Day 1:

```text
devops-day1/
│
├── docs/
├── scripts/
└── README.md
```

Location:

```text
/home/student/devops-day1
```

This practiced:

```text
Directory navigation
Directory creation
File creation
File editing
Linux terminal usage
```

---

## 7. Editing Files with `vi`

Because VS Code is unavailable, a Linux terminal editor was used.

Open:

```bash
vi README.md
```

### Enter Insert Mode

Press:

```text
i
```

Then type normally.

### Stop Editing

Press:

```text
Esc
```

### Save and Quit

Type:

```text
:wq
```

Meaning:

```text
w = write/save
q = quit
```

### Useful `vi` Commands

```text
i       Insert mode
Esc     Command mode
:w      Save
:q      Quit
:wq     Save + quit
:q!     Quit without saving
```

Only the basics are needed for now.

---

## 8. Creating a Git Repository

A normal directory becomes a Git repository using:

```bash
git init
```

Afterward Git creates:

```text
.git/
```

That hidden directory contains Git's internal repository data.

### Important

The `.git` directory is what makes the folder a Git repository.

Deleting:

```text
.git/
```

would remove the repository history and metadata while leaving the normal project files behind.

---

## 9. `git status`

One of the most important Git commands:

```bash
git status
```

Use it frequently.

It tells you things such as:

```text
Current branch
New files
Modified files
Staged files
Untracked files
Whether the working tree is clean
```

Final result:

```text
On branch master

nothing to commit, working tree clean
```

Meaning Git knows about all current changes and everything has been committed.

---

## 10. The Basic Git Workflow

This is one of the most important Day 1 concepts.

```text
Working Directory
       │
       │ git add
       ▼
Staging Area
       │
       │ git commit
       ▼
Git Repository / History
```

### Step 1 — Modify or Create Files

Example:

```bash
touch README.md
```

Git notices the change.

### Step 2 — Stage Changes

```bash
git add .
```

`.` means:

```text
Everything in the current project that should be staged
```

Check:

```bash
git status
```

### Step 3 — Commit

```bash
git commit -m "Complete DevOps Day 1 Linux setup"
```

A commit represents a recorded snapshot or change in project history.

---

## 11. Viewing Git History

Command:

```bash
git log
```

Compact version:

```bash
git log --oneline
```

The repository showed:

```text
cde12b0 (HEAD -> master) My first script
237bc56 Complete DevOps Day 1 Linux Setup
```

That means the repository has two commits.

---

## 12. Understanding a Commit Hash

Example:

```text
237bc56
```

This is the shortened form of a Git commit identifier.

Git uses hashes to uniquely identify commits.

Conceptually:

```text
237bc56
   │
   └── specific snapshot/change in repository history
```

Later this becomes important for:

```text
Rollback
Comparison
Branching
Merging
CI/CD
Release tracking
```

---

## 13. Understanding `HEAD`

Git displayed:

```text
HEAD -> master
```

For now:

```text
HEAD
  ↓
Your current position in Git history
```

And:

```text
master
```

was the currently checked-out branch.

Branches will be covered more deeply later.

---

## 14. First Bash Script

Created:

```text
scripts/hello.sh
```

The script contained:

```bash
echo "Hello from my DevOps Environment"
```

Executed using:

```bash
bash scripts/hello.sh
```

Output:

```text
Hello from my DevOps Environment
```

This was the first simple Linux automation script.

---

## 15. Why Git Detected the Bash Script

After creating:

```text
scripts/hello.sh
```

Git noticed that the repository contents had changed.

Running:

```bash
git status
```

showed the change.

Then:

```bash
git add .
git commit -m "My first script"
```

recorded it into Git history.

Final verification:

```bash
git status
```

returned:

```text
nothing to commit, working tree clean
```

---

## 16. Python Versions Across Environments

The systems have different Python versions:

```text
Windows       Python 3.14.2
Red Hat VM    Python 3.12.9
```

This is normal.

Different servers and environments can have different:

```text
OS versions
Python versions
Libraries
Dependencies
Configuration
```

A major DevOps problem is making software behave consistently across environments.

Later, tools such as:

```text
Virtual environments
Dependency files
Containers
CI/CD
Infrastructure as Code
```

help solve that problem.

---

## 17. Docker Situation

Docker is **not available on the corporate Windows machine**.

It is intentionally deferred.

Docker later becomes a dedicated topic covering:

```text
Images
Containers
Networking
Volumes
Compose
Health checks
Registries
```

A browser-based or approved lab environment can be used when Docker becomes necessary.

Therefore:

```text
Docker unavailable locally ≠ roadmap blocked
```

---

## 18. VS Code Situation

VS Code cannot be installed on the corporate machine.

That is not a blocker.

Current alternatives:

```text
vi/vim
Approved text editor
Git Bash
PowerShell
Linux terminal
Python tools
```

DevOps skill is based on being able to operate systems, not on using a specific IDE.

---

## 19. WSL Situation

WSL installation required elevated permissions and was blocked.

Because the Red Hat Linux VM is already available, WSL is unnecessary.

The Red Hat VM will be used as the primary Linux laboratory.

---

## 20. Day 1 Troubleshooting Lesson

Initial issues:

```text
docker: command not found / not recognized
code: command not recognized
WSL not installed
```

A useful engineering mindset is:

```text
Requirement
   ↓
What skill are we actually trying to learn?
   ↓
Do I already have another approved way to practice it?
   ↓
Adapt environment
```

Instead of:

```text
Tool unavailable → Learning stops
```

The environment was adapted:

```text
WSL      → Red Hat VM
VS Code  → Terminal editor
Docker   → Deferred lab solution
```

This is realistic in enterprise DevOps environments where engineers often work under installation and access restrictions.

---

## 21. Commands to Remember From Day 1

These should gradually become natural:

```bash
pwd
ls
ls -la
cd
mkdir
touch
echo
cat
whoami
vi
python3 --version
git --version
git init
git status
git add .
git commit -m "message"
git log --oneline
bash script.sh
```

---

## 22. Day 1 Git Cheat Sheet

```bash
# Start repository
git init

# Examine repository
git status

# Stage changes
git add .

# Commit changes
git commit -m "Commit message"

# View compact history
git log --oneline

# Check Git configuration
git config --global --list
```

---

## 23. Day 1 Linux Cheat Sheet

```bash
# Current location
pwd

# Files
ls
ls -la

# Navigation
cd folder
cd ~

# Directories
mkdir folder
mkdir -p folder

# Files
touch file.txt

# Display contents
cat file.txt

# Write text
echo "text" > file.txt

# Current user
whoami

# Edit
vi file.txt

# Execute Bash script
bash script.sh
```

---

## 24. What I Should Be Able to Explain

Before considering Day 1 genuinely learned, I should be able to answer these without looking at the notes.

### What does `pwd` do?

Shows the current working directory.

### What is the difference between `ls` and `ls -la`?

`ls -la` provides a detailed listing and includes hidden entries.

### What does `git init` do?

Initializes a Git repository and creates `.git`.

### What does `git status` do?

Shows the current repository and file-change state.

### What does `git add .` do?

Stages current project changes for a future commit.

### What does `git commit` do?

Records staged changes in repository history.

### What is a Git commit hash?

An identifier for a particular commit.

### What does `working tree clean` mean?

There are no uncommitted tracked changes.

### What is `.git`?

The hidden directory containing Git repository metadata and history.

### Git vs GitHub?

```text
Git     = Version control
GitHub  = Remote hosting and collaboration platform
```

### Why can Windows and Linux have different Python versions?

They are independent environments with separately installed runtimes.

---

## 25. Day 1 Completion Record

```text
PHASE 0 — DAY 1
Environment Setup + Linux/Git Fundamentals

Windows Python               ✅
Windows Git                  ✅
Git identity configured      ✅
Terraform available          ✅
Git Bash available           ✅

Red Hat Linux                ✅
Linux terminal               ✅
Python on Linux              ✅
Git on Linux                 ✅

Filesystem navigation        ✅
Directory creation           ✅
File creation/editing        ✅
vi basics                    ✅

Git repository               ✅
Staging changes              ✅
Creating commits             ✅
Viewing history              ✅
Understanding clean tree     ✅

Bash script                  ✅
Running Bash script          ✅

Docker                       ⏸ Deferred
VS Code                      ↪ Substituted
WSL                          ↪ Not required

DAY 1                        ✅ COMPLETE
```

---

## 26. Learning Model Used

The learning approach for the roadmap is:

```text
Learn → Lab → Break → Automate → Document → Prove
```

This file is the **Document** part of Day 1.

The next step is:

> **Phase 0 — Day 2: GitHub, remotes, clone/push/pull, branches, first pull request, and creation of the permanent `python-devops-engineering` repository.**
