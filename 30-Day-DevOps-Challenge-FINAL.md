# 🚀 The 30-Day DevOps Challenge (Hiring-Manager-Reviewed Edition)
### From Computer Engineering Student to Internship-Ready DevOps Engineer

> **Mentor's Note:** This is not a course. It is a *build log*. Every day you ship something real, push it to GitHub, and write about it. By Day 30 you will have a portfolio that speaks louder than any certificate — a working, production-style system: `Nginx → Go API → Redis → PostgreSQL → Docker → Kubernetes → GitHub Actions → Terraform → AWS`, monitored with Prometheus and Grafana.

> **Hiring Manager's Note:** This version was reviewed against what actually gets an entry-level DevOps candidate through a real interview loop at a large tech company. Three things changed from a typical tutorial-roadmap: (1) **Python is included**, because it's the most commonly required scripting language in DevOps/Cloud internship JDs; (2) **security scanning is built into every relevant day** (secrets, containers, IaC, dependencies) — this is no longer optional at any serious company; (3) **interview and resume preparation is treated as a deliverable**, not an afterthought, because a flawless capstone that you can't talk about fluently in an interview does not get you hired. One low-signal "busywork" day was cut to make room.
>
> **On pacing:** 30 consecutive high-effort days is not realistic alongside coursework/exams. Treat "Day N" as a *unit of work*, not a calendar day — batch two units on a free weekend day, skip a day around an exam, but don't skip the order. What matters is finishing all 30 units before you start applying, not finishing them in exactly 30 calendar days.

---

## Day 0 — Setup: Position Yourself Before You Build
### Goal
Set up the infrastructure of your *job search*, not just your code, before writing a single script.

### Practical Task
- Create/clean your GitHub profile: professional photo, bio, pinned repos placeholder, and a profile README repo (same name as your username)
- Update LinkedIn: headline mentioning "DevOps / Cloud Engineering," an About section stating you're doing a hands-on 30-day build challenge (this alone gets recruiter attention when you post weekly)
- Identify 10 target companies/internship postings and read 3 DevOps/Cloud internship JDs closely — note every technology and skill they list (you'll compare this list against your resume on Day 30)
- Set up your local environment: WSL Ubuntu, VS Code with Remote-WSL extension, `git config` with your real name/email, SSH key added to GitHub

### Deliverables
- Clean GitHub + LinkedIn profiles
- A `target-roles.md` note listing 10 target postings and their common required skills (you'll revisit this exact file on Day 30)

### Why This Matters in Real DevOps Jobs
Nobody hires from a perfect codebase alone — recruiters and hiring managers find you through your public presence first. Treat Day 0 as seriously as Day 1.

### Estimated Time
1.5 hours

---

## 📋 How This Roadmap Works

| Element | Purpose |
|---|---|
| **Goal** | The single outcome for the day — if you achieve only this, the day was a success |
| **Theory (15–30 min)** | Just enough conceptual grounding to not build blindly |
| **Practical Task** | The core build — hands-on, in your terminal, in VS Code |
| **Mini Challenge** | A harder stretch task to push past "tutorial-following" into real problem-solving |
| **Commands to Practice** | The muscle-memory commands of the day |
| **Deliverables** | What must exist by end of day (files, repo, running service) |
| **GitHub Repository Structure** | Exactly how to organize what you push |
| **README Requirements** | What a hiring manager should see if they open your repo |
| **LinkedIn Post Idea** | A ready-to-adapt post so you build a public learning log |
| **Common Mistakes** | What junior engineers get wrong here — so you don't |
| **Extra Learning (Optional)** | Official docs only, no random tutorials |
| **Estimated Time** | Realistic time budget (you're a student, not a full-time engineer yet) |

**Rules for yourself:**
1. Don't skip the "why" — interviewers ask "why Redis and not just PostgreSQL caching?" not "how do you spell Redis?"
2. Commit to GitHub **every single day**, even for small tasks. Your contribution graph is part of your resume.
3. If a day takes longer than estimated, that's fine — depth beats speed. But don't stall more than 2x the estimate; move on and revisit.
4. Every repo needs a README that explains itself to a stranger.

---

## 🗺️ The 30-Day Map

| Week | Theme | Weekly Project | Core Tech |
|---|---|---|---|
| Day 0 | Career setup | GitHub/LinkedIn profiles, target-role research | — |
| Week 1 (Days 1–7) | Linux, Bash, Python & Git Foundations | Linux + Python Automation Toolkit (secret-scanned, tested) | Linux, Bash, Python, Git, GitHub, gitleaks |
| Week 2 (Days 8–14) | Go, Docker & Databases | Containerized Go REST API + Compose Stack (vulnerability-scanned) | Golang, Docker, Docker Compose, PostgreSQL, Redis, Trivy, gosec |
| Week 3 (Days 15–21) | Kubernetes | Kubernetes-Deployed API Platform | Kubernetes, Helm, Nginx Ingress, NetworkPolicy |
| Week 4 (Days 22–28) | Cloud, IaC & CI/CD | AWS Infrastructure via Terraform + GitHub Actions Pipeline | AWS, Terraform, tfsec, GitHub Actions, Dependabot |
| Final Sprint (Days 29–30) | Production Integration + Interview Prep | The Capstone: Full Cloud-Native Platform + Resume/Mock Interview | Everything combined + Prometheus/Grafana |

---

# 📅 WEEK 1 — Linux, Bash & Git Foundations
**Why this week matters:** Every DevOps job — no matter how much Kubernetes or Terraform is on the job description — runs on Linux fundamentals and disciplined version control. Interviewers filter out candidates in the first 10 minutes if they fumble basic shell usage or can't explain a `.gitignore`. This week turns "comfortable with Linux basics" into "can automate real operational tasks."

---

## Day 1
### Goal
Build a Bash script that audits a Linux system (disk, memory, CPU, users, open ports) and outputs a clean report.

### Theory (15–30 min)
Read about the Linux filesystem hierarchy (`/etc`, `/var`, `/proc`), and how `df`, `free`, `top`, `who`, and `ss` retrieve system state. Understand that DevOps engineers are frequently first responders for "the server is slow" — this script is literally what you'd run first.

### Practical Task
Write `system_audit.sh` that:
- Prints disk usage (`df -h`), memory (`free -h`), CPU load (`uptime`), logged-in users (`who`), and listening ports (`ss -tulnp`)
- Formats output with headers and colors (`tput` or ANSI codes)
- Accepts a `--output=file.txt` flag to save the report

### Mini Challenge
Add a `--alert` flag that exits with code 1 and prints a warning if disk usage on `/` exceeds 80%.

### Commands to Practice
```bash
df -h; free -h; uptime; who; ss -tulnp
chmod +x system_audit.sh
./system_audit.sh --output=report.txt --alert
```

### Deliverables
- `system_audit.sh` (executable, tested on WSL Ubuntu)
- Sample `report.txt` output committed
- `README.md` explaining usage and flags

### GitHub Repository Structure
```
linux-automation-toolkit/
├── scripts/
│   └── system_audit.sh
├── examples/
│   └── sample_report.txt
├── README.md
└── LICENSE
```
> This is the repo you'll keep adding to all week — one toolkit, growing daily.

### README Requirements
- What the script does and why it's useful in real ops work
- Usage examples with flags
- Sample output screenshot or text block
- "How to run" section (chmod, execution)

### LinkedIn Post Idea
> "Day 1 of my 30-Day DevOps Challenge 🚀 Built a Bash system-audit script that reports disk, memory, CPU & open ports — the same first move any on-call engineer makes when a server misbehaves. Repo in comments. #DevOps #Linux #Bash #100DaysOfCode"

### Common Mistakes
- Hardcoding paths instead of using variables
- Not quoting variables (`$VAR` vs `"$VAR"`) — breaks on spaces
- Forgetting `set -euo pipefail` at the top, so errors fail silently

### Extra Learning (Optional)
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/)
- [Linux Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs-3.0.html)

### Estimated Time
2.5–3 hours

---

## Day 2
### Goal
Automate log analysis: parse real log files to extract errors, count occurrences, and summarize.

### Theory (15–30 min)
Learn `grep`, `awk`, `sed`, and regular expressions. Understand why log parsing is a daily DevOps task — debugging incidents starts with logs, not dashboards.

### Practical Task
Write `log_analyzer.sh` that:
- Takes a log file path as an argument
- Extracts lines matching `ERROR`, `WARN`, `CRITICAL`
- Uses `awk` to count occurrences per severity level
- Uses `sed` to extract timestamps and find the busiest hour of errors

### Mini Challenge
Download a real public sample log (e.g., an Apache/Nginx access log) and extend the script to report the top 5 requested URLs and top 5 IPs by request count.

### Commands to Practice
```bash
grep -E "ERROR|WARN|CRITICAL" app.log
awk '{print $1}' access.log | sort | uniq -c | sort -nr | head -5
sed -n 's/.*\[\(.*\)\].*/\1/p' app.log
```

### Deliverables
- `log_analyzer.sh` added to `scripts/`
- Sample log file + generated summary report committed

### GitHub Repository Structure
```
linux-automation-toolkit/
├── scripts/
│   ├── system_audit.sh
│   └── log_analyzer.sh
├── examples/
│   ├── sample_report.txt
│   ├── sample_access.log
│   └── log_summary.txt
├── README.md
```

### README Requirements
Update main README with a "Scripts Included" table listing each script, purpose, and usage.

### LinkedIn Post Idea
> "Day 2: Wrote a log analyzer with grep/awk/sed that finds top error hours and top offending IPs from raw logs. No fancy tools — just core Unix text processing, which is still how most real debugging starts. #Linux #DevOps #Bash"

### Common Mistakes
- Using `grep` when `awk` is more appropriate for column-based data (and vice versa)
- Not handling gzipped log files (`.log.gz`)
- Over-engineering regex instead of using simple field splitting

### Extra Learning (Optional)
- [AWK one-liners explained](https://www.gnu.org/software/gawk/manual/gawk.html)

### Estimated Time
2.5–3 hours

---

## Day 3
### Goal
Build a backup automation script with rotation logic (like a real ops cronjob).

### Theory (15–30 min)
Understand `tar`, `gzip`, `rsync`, and cron scheduling syntax. Learn why backup rotation (keep last N backups) matters for disk management in production.

### Practical Task
Write `backup_rotate.sh` that:
- Archives a target directory into a timestamped `.tar.gz`
- Stores backups in `/backups/`
- Deletes backups older than N days (configurable)
- Logs every run with timestamp and result to `backup.log`

### Mini Challenge
Add a cron entry (documented in README, not actually needed to run continuously) that would run this script nightly at 2 AM, and add a dry-run mode (`--dry-run`) that shows what would be deleted without deleting.

### Commands to Practice
```bash
tar -czf backup_$(date +%F).tar.gz /path/to/dir
find /backups -type f -mtime +7 -exec rm {} \;
crontab -e   # 0 2 * * * /path/to/backup_rotate.sh
```

### Deliverables
- `backup_rotate.sh`
- `backup.log` sample
- Cron documentation in README

### GitHub Repository Structure
```
linux-automation-toolkit/
├── scripts/
│   ├── system_audit.sh
│   ├── log_analyzer.sh
│   └── backup_rotate.sh
├── examples/
├── README.md
```

### README Requirements
Add a "Scheduling with Cron" section showing the exact crontab line and explanation of cron syntax fields.

### LinkedIn Post Idea
> "Day 3: Automated backups with rotation — tar + find + cron. Small script, but this exact pattern protects real production data every night. #DevOps #Automation #Linux"

### Common Mistakes
- Deleting backups with `rm -rf` without testing `find` output first (`--dry-run` habit matters)
- Not making backup paths configurable
- Forgetting timezone issues in cron (UTC vs local)

### Extra Learning (Optional)
- [Crontab Guru](https://crontab.guru/) (for syntax testing, not a tutorial site)
- `man rsync`

### Estimated Time
2–2.5 hours

---

## Day 4
### Goal
Deepen Git skills beyond `add/commit/push`: branching strategy, rebasing, and resolving conflicts intentionally.

### Theory (15–30 min)
Understand Git branching models (feature branches, trunk-based development), the difference between `merge` and `rebase`, and why teams enforce Pull Request workflows.

### Practical Task
On your `linux-automation-toolkit` repo:
- Create a `feature/env-check-script` branch
- Write a new script `env_check.sh` that validates required tools (`docker`, `git`, `curl`, etc.) are installed and prints versions
- Deliberately create a merge conflict by editing README on `main` and on your branch, then resolve it manually
- Rebase your branch onto latest `main` before merging

### Mini Challenge
Set up branch protection rules on GitHub (require PR review before merge, even if you're solo) and use GitHub's PR UI to merge with a squash commit.

### Commands to Practice
```bash
git checkout -b feature/env-check-script
git rebase main
git merge --no-ff feature/env-check-script
git log --oneline --graph --all
```

### Deliverables
- `env_check.sh` merged via PR
- A documented merge conflict resolution (screenshot or commit message explaining it)

### GitHub Repository Structure
```
linux-automation-toolkit/
├── scripts/
│   └── env_check.sh
```
(added to existing structure)

### README Requirements
Add a `CONTRIBUTING.md` explaining your branching strategy (even though you're solo — this shows you understand team workflows).

### LinkedIn Post Idea
> "Day 4: Practiced real Git workflows — feature branches, rebase, conflict resolution, and branch-protected PRs. Understanding *why* teams rebase before merging is a small thing that separates junior from job-ready. #Git #GitHub #DevOps"

### Common Mistakes
- Rebasing shared/public branches (never rebase what others have pulled)
- Force-pushing without `--force-with-lease`
- Resolving conflicts by blindly picking one side without understanding both changes

### Extra Learning (Optional)
- [Git Branching Model — Pro Git Book](https://git-scm.com/book/en/v2)
- [GitHub Docs: About Pull Requests](https://docs.github.com/en/pull-requests)

### Estimated Time
2.5 hours

---

## Day 5
### Goal
Rebuild your system-audit logic in Python — the language most DevOps/Cloud internship JDs actually list — and call your first AWS API.

### Theory (15–30 min)
Understand why Python dominates DevOps tooling (Ansible, most CI glue scripts, AWS SDKs) despite Bash being faster to reach for. Learn `subprocess`, `argparse`, and get a first look at `boto3` (AWS SDK for Python).

### Practical Task
Write `sysaudit.py` (a Python port + upgrade of Day 1's script) that:
- Uses `psutil` to report CPU, memory, disk, and process count (cross-platform, no shelling out where avoidable)
- Uses `argparse` for `--output` and `--alert` flags (same behavior as Day 1, better structure)
- Adds a `--s3-upload=<bucket>` flag that uses `boto3` to upload the report to an S3 bucket (create a free-tier bucket first)
- Includes type hints and a `requirements.txt`

### Mini Challenge
Write a second script, `ec2_lister.py`, using `boto3` to list all EC2 instances in your account (empty for now) with their state, type, and tags — this exact pattern (inventory scripts) is one of the most common real DevOps automation tasks.

### Commands to Practice
```bash
python3 -m venv venv && source venv/bin/activate
pip install boto3 psutil
python3 sysaudit.py --output=report.txt --s3-upload=my-bucket
python3 ec2_lister.py --profile devops-challenge
```

### Deliverables
- `sysaudit.py` and `ec2_lister.py`
- `requirements.txt`
- Sample S3 upload confirmed (screenshot of the object in the bucket)

### GitHub Repository Structure
```
linux-automation-toolkit/
├── python/
│   ├── sysaudit.py
│   ├── ec2_lister.py
│   └── requirements.txt
├── scripts/
```

### README Requirements
Add a "Why Python Alongside Bash" section — 3-4 sentences on when you'd reach for each, since interviewers ask this directly.

### LinkedIn Post Idea
> "Day 5: Ported my Bash system-audit script to Python with boto3, and wrote an EC2 inventory script — the exact pattern real DevOps teams use for account visibility. Bash for quick glue, Python for anything that needs to talk to an API. #Python #AWS #DevOps"

### Common Mistakes
- Shelling out to `subprocess` for things Python libraries already do natively (e.g., using `subprocess.run(['df','-h'])` instead of `shutil.disk_usage` or `psutil`)
- Not using a virtual environment, polluting global Python packages
- Hardcoding AWS credentials in code instead of using named profiles/environment variables

### Extra Learning (Optional)
- [Boto3 Documentation](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html)
- [Python `argparse` Docs](https://docs.python.org/3/library/argparse.html)

### Estimated Time
3 hours

---

## Day 6
### Goal
Build a security-fundamentals habit before you write another line of infrastructure code: secret scanning, SSH hardening, and a personal security checklist.

### Theory (15–30 min)
Understand why leaked credentials in Git history are the #1 real-world cause of cloud account compromise, and why "add it to `.gitignore` after the fact" doesn't remove it from history. Learn basic SSH hardening (key-only auth, disabling root login) and the concept of a security baseline checklist (e.g., CIS Benchmarks).

### Practical Task
- Install and run `gitleaks` against every repo you've created so far — confirm zero findings (or fix any you find, and understand *why* they were flagged)
- Add a pre-commit hook (using `pre-commit` framework) that runs `gitleaks protect` before every commit, going forward, on all your repos
- Write a `security-checklist.md`: SSH key-only auth, `ufw`/firewall basics, keeping packages patched (`apt update && apt upgrade`), and least-privilege principles — treat this as a personal runbook you'll reuse all challenge
- Combine your Week 1 scripts (Bash + Python) into a single lightweight toolkit folder with a shared `README.md` command reference — simple and functional, not over-engineered

### Mini Challenge
Deliberately commit a fake AWS key to a scratch repo, confirm `gitleaks` blocks the commit locally, then push the same repo to GitHub and check that GitHub's own secret scanning (Push Protection) also catches it — understanding both layers of defense.

### Commands to Practice
```bash
gitleaks detect --source . -v
pre-commit install
pre-commit run --all-files
ssh-keygen -t ed25519 -C "you@example.com"
```

### Deliverables
- `gitleaks` clean scan across all repos
- `.pre-commit-config.yaml` committed to each repo
- `security-checklist.md`

### GitHub Repository Structure
```
linux-automation-toolkit/
├── scripts/
├── python/
├── security-checklist.md
├── .pre-commit-config.yaml
├── docs/
├── README.md
```

### README Requirements
Add a "Security Practices" section listing what's automated (pre-commit secret scanning) and what's manual (the checklist) — this single section is a strong interview talking point.

### LinkedIn Post Idea
> "Day 6: Before writing more infra code, I set up gitleaks + pre-commit hooks to catch secrets before they ever hit a commit, and wrote a personal SSH/Linux hardening checklist. Security has to be a habit from day one, not a retrofit. #DevSecOps #Security #DevOps"

### Common Mistakes
- Assuming `.gitignore` protects secrets already committed in history (it doesn't — history must be scrubbed with tools like `git filter-repo` or BFG)
- Treating security scanning as a one-time check instead of an automated, ongoing gate
- Disabling password SSH auth without confirming key-based auth works first (locks you out)

### Extra Learning (Optional)
- [Gitleaks](https://github.com/gitleaks/gitleaks)
- [GitHub Push Protection Docs](https://docs.github.com/en/code-security/secret-scanning/push-protection-for-repositories-and-organizations)
- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks)

### Estimated Time
2.5 hours

---

## Day 7 — 🏗️ Week 1 Mini Project: **Linux Automation Toolkit v1.0**
### Goal
Polish, document, and ship the toolkit as a professional open-source-style project.

### Theory (15–30 min)
Study what makes an open-source README compelling (badges, clear install steps, examples, license). This is your first real portfolio piece.

### Practical Task
- Add unit-style tests: `bats` (Bash Automated Testing System) for at least 2 Bash scripts, and `pytest` for `sysaudit.py`
- Add a GitHub Actions workflow that runs `shellcheck`, `pylint`/`ruff`, and `gitleaks` on every push (your first real CI pipeline — more on this in Week 4)
- Tag a `v1.0.0` release on GitHub

### Mini Challenge
Write a `Makefile` with targets like `make install`, `make test`, `make lint`, `make security` to standardize toolkit usage — a Makefile as a single entrypoint is the professional equivalent of the old "custom CLI dispatcher" idea, without reinventing tooling that already exists.

### Commands to Practice
```bash
bats tests/
pytest python/
shellcheck scripts/*.sh
gitleaks detect --source .
git tag -a v1.0.0 -m "Linux Automation Toolkit v1.0"
git push origin v1.0.0
```

### Deliverables
- Fully working `linux-automation-toolkit` repo, tagged `v1.0.0`
- CI badge in README showing passing lint + security checks
- At least 2 `bats` tests and 2 `pytest` tests

### GitHub Repository Structure
```
linux-automation-toolkit/
├── .github/
│   └── workflows/
│       └── ci.yml          # shellcheck + pylint/ruff + gitleaks + tests
├── scripts/
│   ├── system_audit.sh
│   ├── log_analyzer.sh
│   ├── backup_rotate.sh
│   └── env_check.sh
├── python/
│   ├── sysaudit.py
│   └── ec2_lister.py
├── tests/
│   ├── test_system_audit.bats
│   └── test_backup_rotate.bats
├── security-checklist.md
├── .pre-commit-config.yaml
├── docs/
├── examples/
├── Makefile
├── VERSION
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

### README Requirements
- Project badges (build status, license, last commit)
- Architecture/flow diagram (simple ASCII or draw.io export) showing how the scripts and Makefile relate
- Full command reference
- "What I learned this week" section — write this for yourself and for recruiters

### LinkedIn Post Idea (Project Showcase)
> "🎉 Shipped v1.0 of my Linux Automation Toolkit — Bash + Python scripts, tested (bats + pytest), scanned for secrets, linted via GitHub Actions on every push. This week I went from 'comfortable with Linux basics' to writing production-style, security-conscious automation. Repo link below. #DevOps #Linux #Bash #Python #OpenSource #100DaysOfCode"
>
> **Hashtags:** #DevOps #Linux #Bash #Python #Git #GitHub #CI #OpenSource #CloudComputing #100DaysOfCode

### Common Mistakes
- Shipping without tests — "it works on my machine" isn't a deliverable
- Weak README that doesn't explain *why* the project exists
- Not tagging releases (versioning discipline matters even solo)

### Extra Learning (Optional)
- [ShellCheck](https://www.shellcheck.net/)
- [Bats-core](https://github.com/bats-core/bats-core)

### Estimated Time
3.5–4 hours

### 🎤 Week 1 Interview Prep
| Likely Question | What They're Testing |
|---|---|
| "Walk me through what happens when you type a command in the terminal and hit Enter." | Shell/process fundamentals |
| "How would you find what's eating disk space on a server with no monitoring installed?" | Real troubleshooting instinct, not memorized commands |
| "When would you reach for Python instead of Bash?" | Judgment, not just syntax knowledge |
| "How do you make sure a secret never ends up in Git history?" | Security-by-default thinking |

**Resume bullet draft (write your own version now, refine on Day 30):**
> "Built and shipped an open-source Linux automation toolkit (Bash + Python) with automated testing, secret scanning, and CI linting, reducing manual system-audit and backup tasks to single commands."

---

# 📅 WEEK 2 — Golang, Docker & Databases
**Why this week matters:** DevOps engineers who can also write the software they deploy are far more valuable — you'll debug faster, write better Dockerfiles, and design smarter CI pipelines. Go is the language of the cloud-native ecosystem itself (Docker, Kubernetes, Terraform are all written in Go), so learning it is directly relevant, not a detour.

---

## Day 8
### Goal
Build a minimal Go REST API from scratch (no framework) with health and version endpoints.

### Theory (15–30 min)
Learn Go's `net/http` package, `main()` structure, and Go modules (`go.mod`). Understand why Go's static binaries make it ideal for tiny Docker images (a theme that returns on Day 9).

### Practical Task
Create `go-rest-api/` with:
- `GET /health` → `{"status":"ok"}`
- `GET /version` → reads version from an env var
- `GET /info` → returns hostname, uptime, and Go runtime version
- Structured JSON logging using `log/slog`

### Mini Challenge
Add graceful shutdown handling (`context` + `os.Signal`) so the server drains in-flight requests before exiting — a real production requirement for zero-downtime deploys.

### Commands to Practice
```bash
go mod init github.com/<you>/go-rest-api
go run main.go
go build -o api .
curl localhost:8080/health
```

### Deliverables
- Working Go API with 3 endpoints
- Graceful shutdown implemented
- Basic `go test` for the health endpoint

### GitHub Repository Structure
```
go-rest-api/
├── cmd/
│   └── api/
│       └── main.go
├── internal/
│   └── handlers/
│       └── handlers.go
├── go.mod
├── go.sum
├── README.md
```

### README Requirements
Explain each endpoint, how to run locally, and why graceful shutdown matters for production deploys.

### LinkedIn Post Idea
> "Day 8: Started building a Go REST API from scratch — no framework, just net/http, structured logging, and graceful shutdown. Go is the language behind Docker, Kubernetes & Terraform, so learning it makes me a better DevOps engineer, not just a developer. #Golang #DevOps"

### Common Mistakes
- Not closing the HTTP server gracefully (abrupt kills drop in-flight requests)
- Ignoring error returns from `http.ListenAndServe`
- Hardcoding the port instead of reading from env var with a sane default

### Extra Learning (Optional)
- [A Tour of Go](https://go.dev/tour/)
- [Effective Go](https://go.dev/doc/effective_go)

### Estimated Time
3 hours

---

## Day 9
### Goal
Containerize the Go API with a production-grade multi-stage Dockerfile.

### Theory (15–30 min)
Learn Docker layer caching, multi-stage builds, and why `FROM scratch` or `distroless` images matter for security and size. Understand `.dockerignore`.

### Practical Task
Write a multi-stage `Dockerfile`:
- Stage 1: `golang:1.22-alpine` builder, compiles a static binary
- Stage 2: `gcr.io/distroless/static` (or `scratch`), copies only the binary
- Result should be under 15MB

### Mini Challenge
Add a `HEALTHCHECK` instruction to the Dockerfile and benchmark image size before/after multi-stage (document both in README). Then scan the final image with **Trivy** and fix any HIGH/CRITICAL vulnerabilities it finds — this is a standard gate in every real container pipeline.

### Commands to Practice
```bash
docker build -t go-rest-api:v1 .
docker images | grep go-rest-api
docker run -p 8080:8080 go-rest-api:v1
docker history go-rest-api:v1
trivy image go-rest-api:v1
```

### Deliverables
- Multi-stage `Dockerfile`
- `.dockerignore`
- Image size comparison table in README
- Trivy scan output committed, with 0 HIGH/CRITICAL findings (or documented justification for any accepted risk)

### GitHub Repository Structure
```
go-rest-api/
├── Dockerfile
├── .dockerignore
├── cmd/
├── internal/
├── README.md
```

### README Requirements
Add a "Docker" section: build/run commands, image size before/after optimization, and an explanation of each Dockerfile stage.

### LinkedIn Post Idea
> "Day 9: Shrunk my Go API's Docker image from ~800MB to under 15MB using multi-stage builds + distroless base images. Smaller images = faster deploys, smaller attack surface. #Docker #Golang #DevOps"

### Common Mistakes
- Copying the entire source tree into the final image instead of just the binary
- Forgetting `CGO_ENABLED=0` when building a static binary for scratch/distroless
- Not using `.dockerignore`, bloating build context

### Extra Learning (Optional)
- [Docker Multi-Stage Builds — Official Docs](https://docs.docker.com/build/building/multi-stage/)
- [Distroless Images](https://github.com/GoogleContainerTools/distroless)

### Estimated Time
2.5–3 hours

---

## Day 10
### Goal
Add PostgreSQL persistence to the Go API using Docker Compose.

### Theory (15–30 min)
Learn Docker Compose networking (services resolve each other by name), volumes for data persistence, and environment-based configuration. Understand connection pooling basics.

### Practical Task
- Add a `/tasks` CRUD endpoint (simple to-do items) backed by PostgreSQL using `database/sql` + `pgx` driver
- Write `docker-compose.yml` with two services: `api` and `db` (postgres:16-alpine), with a named volume for data persistence
- Use environment variables for DB connection string

### Mini Challenge
Add a database migration step using `golang-migrate` so schema changes are versioned, not manually applied.

### Commands to Practice
```bash
docker compose up --build
docker compose exec db psql -U postgres -d tasksdb
migrate -path migrations -database "$DATABASE_URL" up
docker compose down -v
```

### Deliverables
- `/tasks` CRUD endpoints (Create, Read, Update, Delete)
- `docker-compose.yml` with API + PostgreSQL
- Migration files

### GitHub Repository Structure
```
go-rest-api/
├── docker-compose.yml
├── migrations/
│   ├── 0001_create_tasks.up.sql
│   └── 0001_create_tasks.down.sql
├── internal/
│   ├── handlers/
│   └── db/
│       └── db.go
├── Dockerfile
├── README.md
```

### README Requirements
Add architecture diagram (API ↔ Postgres), full API reference table (method, path, body, response), and migration instructions.

### LinkedIn Post Idea
> "Day 10: Connected my Go API to PostgreSQL via Docker Compose, with versioned schema migrations instead of manual SQL. This is the difference between a toy project and something a team could actually maintain. #Docker #PostgreSQL #Golang #DevOps"

### Common Mistakes
- Storing DB credentials directly in `docker-compose.yml` instead of `.env` (and not gitignoring `.env`)
- Not using connection pooling, exhausting DB connections under load
- Skipping migrations and manually running `CREATE TABLE` (untracked schema drift)

### Extra Learning (Optional)
- [PostgreSQL Official Docs](https://www.postgresql.org/docs/)
- [Docker Compose Docs](https://docs.docker.com/compose/)
- [golang-migrate](https://github.com/golang-migrate/migrate)

### Estimated Time
3.5 hours

---

## Day 11
### Goal
Add Redis caching to reduce database load and implement a rate limiter.

### Theory (15–30 min)
Understand cache-aside pattern, TTL expiration, and why Redis (in-memory) is used alongside PostgreSQL (durable) rather than instead of it. Learn basic rate-limiting algorithms (token bucket / fixed window).

### Practical Task
- Add Redis as a third Compose service
- Implement cache-aside on `GET /tasks/:id` (check Redis first, fall back to Postgres, populate cache with TTL)
- Implement a simple IP-based rate limiter middleware using Redis `INCR` + `EXPIRE`

### Mini Challenge
Add cache invalidation on `PUT`/`DELETE` so stale data is never served, and add a `/metrics-lite` endpoint showing cache hit/miss counts.

### Commands to Practice
```bash
docker compose exec redis redis-cli
redis-cli> GET task:1
redis-cli> TTL task:1
redis-cli> INCR ratelimit:127.0.0.1
```

### Deliverables
- Redis integrated into Compose stack
- Cache-aside logic implemented and tested
- Rate limiter middleware with configurable limits

### GitHub Repository Structure
```
go-rest-api/
├── internal/
│   ├── cache/
│   │   └── redis.go
│   ├── middleware/
│   │   └── ratelimit.go
├── docker-compose.yml
├── README.md
```

### README Requirements
Add a "Caching Strategy" section explaining cache-aside pattern with a sequence diagram (ASCII is fine), and rate-limit configuration.

### LinkedIn Post Idea
> "Day 11: Added Redis caching (cache-aside pattern) and a Redis-backed rate limiter to my Go API. Watching response times drop from ~40ms to ~2ms on cache hits made the 'why Redis' question click instantly. #Redis #Golang #Docker #DevOps"

### Common Mistakes
- Caching without TTLs (stale data forever)
- Not invalidating cache on writes (serving outdated data)
- Rate limiting per-server instead of shared state (breaks when you scale to multiple instances — this is exactly why Redis is used instead of in-memory counters)

### Extra Learning (Optional)
- [Redis Official Docs](https://redis.io/docs/latest/)
- [Redis Caching Patterns](https://redis.io/docs/latest/develop/use/patterns/)

### Estimated Time
3 hours

---

## Day 12
### Goal
Add automated testing and API documentation to make the project professional-grade.

### Theory (15–30 min)
Learn Go's `testing` package, table-driven tests, and `httptest` for handler testing. Understand OpenAPI/Swagger's role in API contracts.

### Practical Task
- Write unit tests for handlers using `httptest.NewRecorder()`
- Write integration tests that spin up against the Compose stack (or `testcontainers-go` if you want to go further)
- Generate an OpenAPI 3.0 spec (`openapi.yaml`) documenting all endpoints, and serve Swagger UI via a container in Compose

### Mini Challenge
Add a GitHub Actions workflow (preview of Week 4) that runs `go test ./...` **and** `gosec ./...` (Go static application security testing) on every push — your first real CI pipeline for code, not just scripts, with a security gate built in from day one.

### Commands to Practice
```bash
go test ./... -v -cover
go test -run TestCreateTask -v
docker compose up swagger-ui
```

### Deliverables
- Test suite with >70% handler coverage
- `openapi.yaml`
- Working Swagger UI at `localhost:8081`
- `.github/workflows/go-test.yml`

### GitHub Repository Structure
```
go-rest-api/
├── .github/
│   └── workflows/
│       └── go-test.yml
├── internal/
│   └── handlers/
│       ├── handlers.go
│       └── handlers_test.go
├── api/
│   └── openapi.yaml
├── README.md
```

### README Requirements
Add a "Testing" section with coverage badge, and an "API Documentation" section linking to Swagger UI with a screenshot.

### LinkedIn Post Idea
> "Day 12: Added unit + integration tests and a full OpenAPI spec with Swagger UI to my Go API, plus a GitHub Actions workflow that runs tests on every push. A project isn't 'done' until it's tested and documented. #Golang #Testing #CI #DevOps"

### Common Mistakes
- Testing only the "happy path" and skipping error cases
- Letting the OpenAPI spec drift out of sync with actual code
- Writing tests that depend on execution order (not isolated)

### Extra Learning (Optional)
- [Go Testing Package Docs](https://pkg.go.dev/testing)
- [OpenAPI Specification](https://swagger.io/specification/)

### Estimated Time
3.5 hours

---

## Day 13
### Goal
Harden the Compose stack for a "staging-like" environment: secrets, resource limits, and multi-environment configs.

### Theory (15–30 min)
Learn Docker Compose override files (`docker-compose.override.yml`, `docker-compose.prod.yml`), resource constraints (`mem_limit`, `cpus`), and secrets handling.

### Practical Task
- Split configs into `docker-compose.yml` (base), `docker-compose.dev.yml`, and `docker-compose.prod.yml`
- Add resource limits to each service
- Move secrets to Docker secrets or a `.env.example` pattern (never commit real secrets)
- Add a healthcheck to every service and use `depends_on: condition: service_healthy`

### Mini Challenge
Add Nginx as a reverse proxy in front of the API within Compose (your first taste of the final architecture), handling gzip and basic security headers.

### Commands to Practice
```bash
docker compose -f docker-compose.yml -f docker-compose.prod.yml up
docker compose config
docker stats
```

### Deliverables
- Multi-environment Compose setup
- Nginx reverse proxy in front of API
- `.env.example` with all required variables documented

### GitHub Repository Structure
```
go-rest-api/
├── docker-compose.yml
├── docker-compose.dev.yml
├── docker-compose.prod.yml
├── nginx/
│   └── nginx.conf
├── .env.example
├── README.md
```

### README Requirements
Add "Environments" section explaining dev vs prod compose usage, and document the Nginx layer's role.

### LinkedIn Post Idea
> "Day 13: Added Nginx as a reverse proxy, resource limits, healthchecks, and multi-environment Compose configs to my stack — moving it from 'runs on my machine' toward 'staging-ready'. #Docker #Nginx #DevOps"

### Common Mistakes
- Committing real `.env` files with secrets to Git
- No resource limits (one container can starve the whole host)
- Using `depends_on` without health conditions (service starts before dependency is actually ready)

### Extra Learning (Optional)
- [Nginx Official Docs](https://nginx.org/en/docs/)
- [Docker Compose Environment Variables](https://docs.docker.com/compose/environment-variables/)

### Estimated Time
3 hours

---

## Day 14 — 🏗️ Week 2 Mini Project: **Containerized Go REST API + Compose Stack v1.0**
### Goal
Ship a polished, fully documented, multi-service application as a portfolio project.

### Theory (15–30 min)
Review the full request path you've built: `Nginx → Go API → Redis (cache) → PostgreSQL (persistence)`. Understand this is a real, defensible architecture pattern used in production systems.

### Practical Task
- Final polish pass: consistent error responses (JSON error envelope), input validation, structured logging correlation IDs
- Write a `Makefile` with `make up`, `make down`, `make test`, `make logs`
- Tag `v1.0.0` release

### Mini Challenge
Add a `docker-compose.yml` profile or script that seeds the database with sample data for demo purposes (`make seed`).

### Commands to Practice
```bash
make up
make test
make seed
git tag -a v1.0.0 -m "Go REST API + Compose stack v1.0"
```

### Deliverables
- Fully working, documented, tested multi-container application
- Architecture diagram in README
- `v1.0.0` GitHub release

### GitHub Repository Structure
```
go-rest-api/
├── .github/workflows/
├── cmd/api/
├── internal/
│   ├── handlers/
│   ├── db/
│   ├── cache/
│   └── middleware/
├── migrations/
├── nginx/
├── api/openapi.yaml
├── docker-compose*.yml
├── Dockerfile
├── Makefile
├── .env.example
├── README.md
├── CONTRIBUTING.md
└── LICENSE
```

### README Requirements
- Architecture diagram: `Client → Nginx → Go API → Redis / PostgreSQL`
- Full setup instructions (`make up` should just work)
- API reference table
- Screenshots: Swagger UI, `docker compose ps` output, sample curl responses
- Badges: CI status, Go version, license

### LinkedIn Post Idea (Project Showcase)
> "🎉 Week 2 complete: Shipped a Go REST API with PostgreSQL persistence, Redis caching, Nginx reverse proxy, full test suite, OpenAPI docs, and CI — all orchestrated with Docker Compose. This is the exact architecture pattern behind countless real backend services. Repo below. #Golang #Docker #PostgreSQL #Redis #Nginx #DevOps #100DaysOfCode"
>
> **Hashtags:** #DevOps #Golang #Docker #DockerCompose #PostgreSQL #Redis #Nginx #Backend #CloudNative

### Common Mistakes
- Treating "it runs" as "it's done" — polish, docs, and tests are part of the deliverable
- Inconsistent error handling across endpoints
- Not writing a `Makefile`/single entrypoint, making the project harder to demo in an interview

### Extra Learning (Optional)
- [The Twelve-Factor App](https://12factor.net/) — read this fully, it will reframe how you design every project going forward

### Estimated Time
4 hours

### 🎤 Week 2 Interview Prep
| Likely Question | What They're Testing |
|---|---|
| "Why did you choose Redis for caching instead of just optimizing your SQL queries?" | Understanding trade-offs, not tool loyalty |
| "Walk me through what happens when two requests try to update the same row at the same time." | Concurrency/data-consistency awareness |
| "Why is your final Docker image smaller than 15MB — what's actually in it?" | Container internals, not just Dockerfile syntax |
| "How would you find a memory leak in a containerized Go service?" | Debugging methodology under pressure |

**Resume bullet draft:**
> "Designed and containerized a Go REST API with PostgreSQL persistence and Redis caching (cache-aside pattern), achieving ~20x latency reduction on cache hits; automated testing and vulnerability scanning (gosec, Trivy) in CI."

---

# 📅 WEEK 3 — Kubernetes
**Why this week matters:** Docker Compose runs one host. Kubernetes runs a fleet. Almost every DevOps/SRE job posting lists Kubernetes as a core requirement — not because it's trendy, but because it's the de facto standard for running containerized workloads reliably at scale. This week you move your Week 2 application from "runs on my laptop" to "runs on a cluster, survives pod crashes, and scales."

---

## Day 15
### Goal
Set up a local Kubernetes cluster and deploy your Go API as a raw Pod, then a Deployment.

### Theory (15–30 min)
Review core objects: Pod, Deployment, ReplicaSet, Service. Understand the control loop concept (desired state vs actual state) that underlies all of Kubernetes.

### Practical Task
- Install `kind` or `minikube` (kind recommended for WSL) and `kubectl`
- Write a raw `pod.yaml` for the Go API image, apply it, observe it, delete it
- Write a `deployment.yaml` with 2 replicas, apply it, kill a pod manually and watch Kubernetes self-heal

### Mini Challenge
Push your Go API image to Docker Hub (or GitHub Container Registry) so the cluster pulls a real remote image instead of a local one — set up `kind load docker-image` as an alternative for local testing.

### Commands to Practice
```bash
kind create cluster --name devops-challenge
kubectl apply -f pod.yaml
kubectl get pods -w
kubectl delete pod <name>   # watch it NOT come back (bare pod)
kubectl apply -f deployment.yaml
kubectl delete pod <name>   # watch it self-heal (deployment)
```

### Deliverables
- Running kind cluster
- `pod.yaml` and `deployment.yaml` manifests
- Screenshot/log of self-healing behavior after pod deletion

### GitHub Repository Structure
```
k8s-deployment/
├── manifests/
│   ├── pod.yaml
│   └── deployment.yaml
├── README.md
```
> New repo for this week — or a `k8s/` folder inside `go-rest-api` if you prefer one unified project. We recommend a **separate repo** so your portfolio shows distinct, scannable projects.

### README Requirements
Explain Pod vs Deployment, and document the self-healing test with before/after `kubectl get pods` output.

### LinkedIn Post Idea
> "Day 15: Deployed my Go API to a local Kubernetes cluster (kind). Deleted a pod manually and watched the Deployment controller recreate it automatically — seeing the reconciliation loop in action made 'desired state' click instantly. #Kubernetes #DevOps #CloudNative"

### Common Mistakes
- Deploying bare Pods in "production" instead of Deployments (no self-healing)
- Not setting `imagePullPolicy` correctly when testing local images with kind
- Confusing `kubectl delete pod` behavior between Pods and Deployment-managed pods

### Extra Learning (Optional)
- [Kubernetes Official Docs — Concepts](https://kubernetes.io/docs/concepts/)
- [kind Documentation](https://kind.sigs.k8s.io/)

### Estimated Time
3 hours

---

## Day 16
### Goal
Expose your API using Services and understand Kubernetes networking basics.

### Theory (15–30 min)
Learn the difference between `ClusterIP`, `NodePort`, and `LoadBalancer` Service types, and how `kube-proxy` routes traffic to pod IPs via labels/selectors.

### Practical Task
- Create a `ClusterIP` Service and access it via `kubectl port-forward`
- Create a `NodePort` Service and access it via the node's IP
- Add proper `labels` and `selectors`, and verify with `kubectl get endpoints`

### Mini Challenge
Break your Service on purpose (mismatched selector labels), diagnose it using `kubectl describe svc` and `kubectl get endpoints`, then fix it — this diagnostic skill is exactly what's tested in interviews.

### Commands to Practice
```bash
kubectl apply -f service.yaml
kubectl port-forward svc/go-api 8080:80
kubectl get endpoints go-api
kubectl describe svc go-api
```

### Deliverables
- `service.yaml` (ClusterIP + NodePort variants)
- Documented "break it, fix it" debugging exercise

### GitHub Repository Structure
```
k8s-deployment/
├── manifests/
│   ├── deployment.yaml
│   └── service.yaml
├── docs/
│   └── debugging-services.md
├── README.md
```

### README Requirements
Add a "Networking" section explaining Service types with a table (type, use case, when to use).

### LinkedIn Post Idea
> "Day 16: Learned Kubernetes Services the hard way — broke my own Service with a label mismatch, then debugged it with `kubectl describe` and `get endpoints`. Nothing teaches networking like breaking it on purpose. #Kubernetes #DevOps"

### Common Mistakes
- Confusing Service selectors with Deployment labels (they must match!)
- Using `NodePort` in "production" thinking (it's for dev/testing, not real external exposure)
- Not checking `kubectl get endpoints` first when a Service seems broken

### Extra Learning (Optional)
- [Kubernetes Services Docs](https://kubernetes.io/docs/concepts/services-networking/service/)

### Estimated Time
2.5 hours

---

## Day 17
### Goal
Manage configuration and secrets properly using ConfigMaps and Secrets.

### Theory (15–30 min)
Understand why config shouldn't be baked into images, the difference between ConfigMaps (non-sensitive) and Secrets (base64-encoded, should be paired with encryption-at-rest / external secret managers in real production).

### Practical Task
- Extract your API's environment variables into a `ConfigMap`
- Move DB credentials into a `Secret`
- Reference both in your Deployment via `envFrom`
- Deploy PostgreSQL and Redis to the cluster as separate Deployments + Services (using PersistentVolumeClaims for Postgres)

### Mini Challenge
Add a `StatefulSet` for PostgreSQL instead of a Deployment, and explain in the README why StatefulSets exist for stateful workloads (stable network identity, ordered deployment, persistent storage per replica).

### Commands to Practice
```bash
kubectl create configmap api-config --from-env-file=.env.example
kubectl create secret generic db-secret --from-literal=DB_PASSWORD=changeme
kubectl apply -f statefulset-postgres.yaml
kubectl get pvc
```

### Deliverables
- `configmap.yaml`, `secret.yaml` (with placeholder values, never real secrets)
- PostgreSQL StatefulSet + PVC
- Redis Deployment
- Full stack running in-cluster: API + Postgres + Redis

### GitHub Repository Structure
```
k8s-deployment/
├── manifests/
│   ├── api/
│   │   ├── deployment.yaml
│   │   ├── service.yaml
│   │   ├── configmap.yaml
│   │   └── secret.yaml
│   ├── postgres/
│   │   ├── statefulset.yaml
│   │   ├── service.yaml
│   │   └── pvc.yaml
│   └── redis/
│       ├── deployment.yaml
│       └── service.yaml
├── README.md
```

### README Requirements
Add "Configuration Management" section, and clearly state: "Secrets here are placeholders — real production secrets should use a vault/external secrets operator" (shows security maturity).

### LinkedIn Post Idea
> "Day 17: Deployed a full stack in Kubernetes — API + PostgreSQL (StatefulSet with PVC) + Redis — using ConfigMaps and Secrets for configuration. Understanding *why* stateful workloads need StatefulSets (not Deployments) was the big unlock today. #Kubernetes #PostgreSQL #DevOps"

### Common Mistakes
- Treating Kubernetes Secrets as fully secure (they're base64, not encrypted, by default)
- Using a Deployment for Postgres instead of a StatefulSet (loses stable identity/storage guarantees)
- Forgetting `PersistentVolumeClaim` and losing data on pod restart

### Extra Learning (Optional)
- [ConfigMaps Docs](https://kubernetes.io/docs/concepts/configuration/configmap/)
- [StatefulSets Docs](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)

### Estimated Time
3.5 hours

---

## Day 18
### Goal
Add resource management, autoscaling, and self-healing configuration (probes).

### Theory (15–30 min)
Learn `requests`/`limits`, liveness/readiness/startup probes, and the Horizontal Pod Autoscaler (HPA). Understand why probes prevent "zombie" pods that are running but not actually healthy.

### Practical Task
- Add `resources.requests` and `resources.limits` (CPU/memory) to all Deployments
- Add `livenessProbe` and `readinessProbe` hitting your API's `/health` endpoint
- Install `metrics-server` in kind and configure an `HorizontalPodAutoscaler` targeting 50% CPU

### Mini Challenge
Load-test your API using `hey` or `k6` to actually trigger the HPA scaling up, and capture `kubectl get hpa -w` output showing replicas increasing.

### Commands to Practice
```bash
kubectl apply -f hpa.yaml
kubectl top pods
hey -z 60s -c 50 http://localhost:8080/health
kubectl get hpa -w
```

### Deliverables
- Probes configured on all deployments
- Resource requests/limits set
- HPA manifest + evidence of it scaling under load

### GitHub Repository Structure
```
k8s-deployment/
├── manifests/
│   ├── api/
│   │   ├── deployment.yaml   # updated with probes + resources
│   │   └── hpa.yaml
├── load-tests/
│   └── results.md
├── README.md
```

### README Requirements
Add "Resilience & Scaling" section with probe explanations and load-test results/screenshots showing HPA scaling.

### LinkedIn Post Idea
> "Day 18: Load-tested my API in Kubernetes and watched the HorizontalPodAutoscaler scale replicas from 2 to 6 in real time based on CPU usage. This is what 'cloud-native scalability' actually looks like, not just a buzzword. #Kubernetes #DevOps #SRE"

### Common Mistakes
- Setting liveness probes too aggressively (causes restart loops under normal load spikes)
- No resource limits → one pod can consume the whole node
- Confusing liveness (restart if failing) with readiness (remove from Service if not ready) probes

### Extra Learning (Optional)
- [Kubernetes Probes Docs](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)
- [Horizontal Pod Autoscaler Docs](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/)

### Estimated Time
3.5 hours

---

## Day 19
### Goal
Add an Ingress controller to route external traffic properly (replacing NodePort/port-forward).

### Theory (15–30 min)
Understand Ingress vs Service, how an Ingress Controller (Nginx Ingress) works as a reverse proxy at the cluster edge, and host/path-based routing.

### Practical Task
- Install the Nginx Ingress Controller in kind
- Write an `Ingress` resource routing `api.local` to your Go API Service
- Add `/etc/hosts` entry to test locally
- Enable TLS using a self-signed cert (via `cert-manager` in dev mode or manually)

### Mini Challenge
Add path-based routing so `/api` goes to your Go API and `/swagger` goes to a Swagger UI Deployment (deploy Swagger UI in-cluster too).

### Commands to Practice
```bash
kubectl apply -f ingress-nginx-deploy.yaml
kubectl apply -f ingress.yaml
curl -H "Host: api.local" http://localhost/health
kubectl get ingress
```

### Deliverables
- Working Nginx Ingress Controller
- `ingress.yaml` with host + path rules
- TLS termination (self-signed, documented as dev-only)

### GitHub Repository Structure
```
k8s-deployment/
├── manifests/
│   ├── ingress/
│   │   └── ingress.yaml
├── README.md
```

### README Requirements
Add architecture diagram: `Client → Ingress (Nginx) → Service → Pods`, and document TLS setup steps.

### LinkedIn Post Idea
> "Day 19: Replaced NodePort with a proper Nginx Ingress Controller for host- and path-based routing into my cluster, plus TLS termination. This is the same pattern (Nginx at the edge) I used in Week 2's Docker Compose stack — now running at cluster scale. #Kubernetes #Nginx #DevOps"

### Common Mistakes
- Forgetting `ingressClassName` field (Ingress silently does nothing without it on newer Kubernetes)
- Not understanding that Ingress needs a controller installed — the resource alone does nothing
- Skipping `/etc/hosts` setup and being confused why `curl` fails

### Extra Learning (Optional)
- [Kubernetes Ingress Docs](https://kubernetes.io/docs/concepts/services-networking/ingress/)
- [Nginx Ingress Controller Docs](https://kubernetes.github.io/ingress-nginx/)

### Estimated Time
3 hours

---

## Day 20
### Goal
Organize everything with Helm — package your app as a reusable, templated chart.

### Theory (15–30 min)
Understand Helm as "a package manager for Kubernetes" — templating, values files, and why teams use Helm instead of raw YAML for anything beyond a toy project.

### Practical Task
- Run `helm create go-api-chart` and convert your raw manifests into templates
- Parameterize replica count, image tag, resource limits, and env vars via `values.yaml`
- Create `values-dev.yaml` and `values-prod.yaml` overrides
- Deploy with `helm install` and upgrade with `helm upgrade`

### Mini Challenge
Add a Helm chart for the entire stack (API + Postgres + Redis) as subcharts or an umbrella chart, so `helm install my-stack ./chart` deploys everything in one command.

### Commands to Practice
```bash
helm create go-api-chart
helm install go-api ./go-api-chart -f values-dev.yaml
helm upgrade go-api ./go-api-chart --set image.tag=v1.1
helm rollback go-api 1
helm uninstall go-api
```

### Deliverables
- Working Helm chart(s) for the full stack
- `values-dev.yaml` and `values-prod.yaml`
- Documented `helm upgrade`/`rollback` demonstration

### GitHub Repository Structure
```
k8s-deployment/
├── charts/
│   └── go-api-chart/
│       ├── Chart.yaml
│       ├── values.yaml
│       ├── values-dev.yaml
│       ├── values-prod.yaml
│       └── templates/
│           ├── deployment.yaml
│           ├── service.yaml
│           ├── ingress.yaml
│           ├── hpa.yaml
│           └── _helpers.tpl
├── README.md
```

### README Requirements
Add "Helm Deployment" section with install/upgrade/rollback commands and an explanation of templating with `values.yaml`.

### LinkedIn Post Idea
> "Day 20: Packaged my entire Kubernetes stack as a Helm chart — one command (`helm install`) now deploys API, Postgres, Redis, Ingress, and autoscaling together. Also practiced `helm rollback` — because deploys fail, and recovering fast matters more than never failing. #Kubernetes #Helm #DevOps"

### Common Mistakes
- Over-templating too early (start simple, template what actually varies)
- Not pinning chart/app versions, causing "works on my cluster" drift
- Ignoring `helm lint` before installing

### Extra Learning (Optional)
- [Helm Official Docs](https://helm.sh/docs/)
- [Helm Best Practices](https://helm.sh/docs/chart_best_practices/)

### Estimated Time
3.5 hours

---

## Day 21 — 🏗️ Week 3 Mini Project: **Kubernetes-Deployed API Platform v1.0**
### Goal
Ship a complete, resilient, Helm-packaged Kubernetes platform as a standalone portfolio project.

### Theory (15–30 min)
Review the full journey: raw Pods → Deployments → Services → ConfigMaps/Secrets → Probes/HPA → Ingress → Helm. This progression *is* the mental model interviewers expect you to explain.

### Practical Task
- Consolidate everything into a clean Helm-based repo
- Add a `README` architecture diagram of the full in-cluster topology
- Write a `docs/runbook.md`: "If the API is down, here's how to debug it" (a real on-call artifact)

### Mini Challenge
Add a `kubectl-based` or `helm test` smoke test that verifies the health endpoint responds after every deploy — a lightweight taste of deployment verification. Also add a `NetworkPolicy` restricting the Postgres pod to only accept traffic from the API pods (not from every pod in the namespace) — the default "any pod can talk to any pod" behavior is a real security gap interviewers ask about.

### Commands to Practice
```bash
helm install platform ./charts/go-api-chart -f values-prod.yaml
helm test platform
kubectl get all -n default
```

### Deliverables
- Full Kubernetes platform repo, Helm-installable in one command
- `docs/runbook.md`
- Tagged `v1.0.0` release

### GitHub Repository Structure
```
k8s-deployment/
├── charts/
│   └── go-api-chart/
├── docs/
│   ├── architecture.md
│   └── runbook.md
├── load-tests/
├── README.md
├── LICENSE
```

### README Requirements
- Full architecture diagram: `Client → Ingress → Service → Deployment (API pods) → Postgres StatefulSet / Redis`
- One-command install instructions
- Screenshots: `kubectl get pods`, HPA scaling, Helm release history
- Runbook link

### LinkedIn Post Idea (Project Showcase)
> "🎉 Week 3 complete: My Go API now runs on Kubernetes with self-healing Deployments, ConfigMaps/Secrets, liveness/readiness probes, HPA autoscaling, Nginx Ingress with TLS, and a Helm chart for one-command deploys. Wrote a runbook too, because real ops work means someone else needs to be able to fix it at 3AM. #Kubernetes #Helm #DevOps #CloudNative #100DaysOfCode"
>
> **Hashtags:** #Kubernetes #Helm #DevOps #CloudNative #SRE #Nginx #Golang #100DaysOfCode

### Common Mistakes
- Skipping the runbook — documentation of *failure modes* is as important as documentation of setup
- Not testing `helm upgrade`/`rollback` before calling it "done"
- Presenting Kubernetes YAML without explaining the "why" behind each object in interviews

### Extra Learning (Optional)
- [Kubernetes Production Best Practices (CNCF)](https://www.cncf.io/blog/)
- [Kubernetes the Hard Way (for deep understanding, optional)](https://github.com/kelseyhightower/kubernetes-the-hard-way)

### Estimated Time
4 hours

### 🎤 Week 3 Interview Prep
| Likely Question | What They're Testing |
|---|---|
| "A pod is stuck in CrashLoopBackOff — walk me through how you'd debug it." | Systematic K8s troubleshooting (`describe`, `logs`, events) |
| "Why does your database run in a StatefulSet and your API in a Deployment?" | Stateful vs. stateless workload understanding |
| "How does traffic actually get from the internet to one of your pods?" | Full networking path (Ingress → Service → Pod), not memorized YAML |
| "What happens if you don't set resource limits?" | Cluster resource management / noisy-neighbor awareness |

**Resume bullet draft:**
> "Deployed a multi-service application to Kubernetes with autoscaling (HPA), self-healing Deployments, NetworkPolicy-restricted database access, and TLS-terminated Ingress; packaged the full stack as a Helm chart for one-command installs."

---

# 📅 WEEK 4 — Cloud, Infrastructure as Code & CI/CD
**Why this week matters:** This is the week that turns "I can containerize and orchestrate an app" into "I can provision and operate real cloud infrastructure, automatically, with a paper trail." Terraform and GitHub Actions are the two tools most entry-level DevOps job descriptions name explicitly. Monitoring (Prometheus/Grafana) is what separates "deployed it" from "know if it's actually healthy."

---

## Day 22
### Goal
Set up AWS foundations correctly: IAM users, least-privilege policies, and the AWS CLI.

### Theory (15–30 min)
Understand IAM users vs roles, why root account usage is discouraged, and least-privilege policy design. Learn AWS CLI profile configuration.

### Practical Task
- Create an IAM user for yourself (never use root) with MFA enabled
- Create a custom least-privilege IAM policy (not `AdministratorAccess`) scoped to the services you'll use this week (EC2, VPC, S3, IAM read)
- Configure `aws configure` with a named profile
- Set a **budget alert** in AWS Billing (critical — do this before anything else)

### Mini Challenge
Write the IAM policy as JSON by hand (not via console clicking) and explain each statement in comments/README — this is exactly the skill tested when debugging "access denied" errors in real jobs.

### Commands to Practice
```bash
aws configure --profile devops-challenge
aws sts get-caller-identity --profile devops-challenge
aws iam create-policy --policy-name devops-challenge-policy --policy-document file://policy.json
```

### Deliverables
- IAM user + custom policy JSON committed (no real account IDs/secrets)
- AWS CLI configured and verified via `sts get-caller-identity`
- Budget alert screenshot

### GitHub Repository Structure
```
aws-terraform-infra/
├── docs/
│   ├── iam-policy.json
│   └── budget-setup.md
├── README.md
```

### README Requirements
Add a "Cost & Safety" section explaining the budget alert setup and least-privilege policy rationale — this signals maturity to reviewers.

### LinkedIn Post Idea
> "Day 22: Started my AWS + Terraform week the right way — no root account, custom least-privilege IAM policy written by hand, MFA enabled, and a budget alert set BEFORE provisioning anything. Cloud cost discipline is a DevOps skill, not an afterthought. #AWS #Cloud #DevOps"

### Common Mistakes
- Using root credentials or `AdministratorAccess` "just to get it working"
- Skipping the budget alert (the #1 cause of "surprise $400 bill" horror stories)
- Committing AWS access keys to Git (use `.gitignore` + AWS CLI profiles, always)

### Extra Learning (Optional)
- [AWS IAM Best Practices](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [AWS Free Tier Details](https://aws.amazon.com/free/)

### Estimated Time
2.5 hours

---

## Day 23
### Goal
Provision your first AWS infrastructure with Terraform: a VPC from scratch.

### Theory (15–30 min)
Understand Terraform's core loop (`init`, `plan`, `apply`, `destroy`), state files, and providers. Learn VPC fundamentals: subnets, route tables, internet gateways, availability zones.

### Practical Task
- Write Terraform to create a VPC with 2 public and 2 private subnets across 2 AZs, an Internet Gateway, and route tables
- Use variables (`variables.tf`) and outputs (`outputs.tf`) — no hardcoded values
- Store state locally first (remote state comes Day 24)

### Mini Challenge
Draw the VPC architecture (subnets, route tables, IGW) using a diagram tool and include it in the README — being able to visually explain your own infra is an interview skill. Run **tfsec** (or **Checkov**) against your module and fix any findings — IaC security scanning is now a standard CI gate, and you should be fixing findings before they ever reach a pipeline.

### Commands to Practice
```bash
terraform init
terraform fmt
terraform validate
terraform plan -out=tfplan
terraform apply tfplan
tfsec .
terraform destroy   # practice tearing down too — cost discipline
```

### Deliverables
- Working Terraform VPC module
- `terraform plan` output committed as a text artifact
- VPC architecture diagram
- Clean `tfsec` scan (or documented exceptions)

### GitHub Repository Structure
```
aws-terraform-infra/
├── modules/
│   └── vpc/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── environments/
│   └── dev/
│       ├── main.tf
│       ├── variables.tf
│       └── terraform.tfvars
├── README.md
```

### README Requirements
Add architecture diagram, variables reference table, and explicit "how to destroy" instructions (cost safety).

### LinkedIn Post Idea
> "Day 23: Provisioned my first real AWS network with Terraform — a VPC with public/private subnets across 2 AZs, fully as code. `terraform plan` before `apply` is now muscle memory. #Terraform #AWS #InfrastructureAsCode #DevOps"

### Common Mistakes
- Running `terraform apply` without reviewing `plan` output first
- Hardcoding CIDR blocks/AZ names instead of using variables
- Forgetting to `destroy` dev resources, silently accumulating AWS costs

### Extra Learning (Optional)
- [Terraform Official Docs](https://developer.hashicorp.com/terraform/docs)
- [AWS VPC Documentation](https://docs.aws.amazon.com/vpc/)

### Estimated Time
3.5 hours

---

## Day 24
### Goal
Add remote state management and provision compute (EC2) inside your VPC.

### Theory (15–30 min)
Understand why local state is dangerous for teams (no locking, no shared source of truth). Learn S3 + DynamoDB for remote state + locking. Learn EC2 basics: AMIs, security groups, key pairs.

### Practical Task
- Create an S3 bucket + DynamoDB table (via Terraform, bootstrapped once) for remote state with locking
- Migrate your VPC state to the S3 backend
- Provision an EC2 instance in a public subnet with a security group allowing only SSH (your IP) and HTTP
- SSH in and manually run your Docker image on it as a sanity check

### Mini Challenge
Write a `user_data` script (cloud-init) that installs Docker and runs your Go API container automatically on instance boot — no manual SSH steps needed. Also apply a consistent **tagging strategy** (`Project`, `Environment`, `Owner`, `CostCenter`) to every resource via a shared Terraform `locals` block — this is exactly how real organizations track cloud spend by team, and "how would you track cost across teams?" is a common interview question.

### Commands to Practice
```bash
terraform init -migrate-state
terraform apply
ssh -i key.pem ec2-user@<public-ip>
aws ec2 describe-instances --profile devops-challenge
```

### Deliverables
- Remote state configured (S3 + DynamoDB lock table)
- EC2 instance running your containerized API via `user_data`
- Security group restricting access appropriately

### GitHub Repository Structure
```
aws-terraform-infra/
├── bootstrap/
│   └── remote-state/
│       └── main.tf
├── modules/
│   ├── vpc/
│   └── ec2/
│       ├── main.tf
│       ├── variables.tf
│       ├── outputs.tf
│       └── user_data.sh
├── environments/dev/
├── README.md
```

### README Requirements
Add "Remote State" section explaining the S3+DynamoDB pattern, and "Compute" section documenting the `user_data` bootstrap process.

### LinkedIn Post Idea
> "Day 24: Set up Terraform remote state with S3 + DynamoDB locking, then provisioned an EC2 instance that auto-installs Docker and launches my API on boot via cloud-init — zero manual SSH steps required. #Terraform #AWS #DevOps #IaC"

### Common Mistakes
- Leaving Security Groups open to `0.0.0.0/0` on SSH (huge security risk)
- Not enabling state locking, risking concurrent-apply corruption
- Forgetting to destroy EC2 instances after testing (billing!)

### Extra Learning (Optional)
- [Terraform Remote State Docs](https://developer.hashicorp.com/terraform/language/state/remote)
- [AWS EC2 User Data Docs](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html)

### Estimated Time
3.5 hours

---

## Day 25
### Goal
Build your first GitHub Actions CI pipeline: automated build, test, and Docker image push.

### Theory (15–30 min)
Understand GitHub Actions core concepts: workflows, jobs, steps, runners, and secrets management via GitHub encrypted secrets. Understand why CI exists (catch problems before they reach main/production).

### Practical Task
- Write `.github/workflows/ci.yml` for your `go-rest-api` repo that: runs on every push/PR, runs `go vet`, `go test`, `gosec`, and `gitleaks`, builds the Docker image, scans it with `trivy`, and pushes to GitHub Container Registry (GHCR) tagged with the git SHA
- Store GHCR credentials as GitHub Secrets (or use `GITHUB_TOKEN` which GHCR supports natively)
- Enable **Dependabot** (`.github/dependabot.yml`) for both Go modules and Docker base images, so dependency updates are proposed automatically

### Mini Challenge
Add a matrix build testing against two Go versions, and add a job that only runs on `main` branch pushes (not PRs) to prevent unnecessary image pushes from feature branches. Configure the pipeline to **fail the build** on any HIGH/CRITICAL Trivy finding — a real quality gate, not just a report.

### Commands to Practice
```bash
git push origin main    # triggers the workflow
gh run list
gh run watch
docker pull ghcr.io/<you>/go-rest-api:<sha>
```

### Deliverables
- Working `ci.yml` workflow
- At least one successful pipeline run visible in the Actions tab
- Image visible in GHCR (or Docker Hub) with SHA tag

### GitHub Repository Structure
```
go-rest-api/
├── .github/
│   └── workflows/
│       ├── go-test.yml   # from Day 12
│       └── ci.yml        # build + push
```

### README Requirements
Add a CI badge at the top, and a "CI/CD Pipeline" section explaining each job/step.

### LinkedIn Post Idea
> "Day 25: Built my first full CI pipeline with GitHub Actions — test, build, and push a versioned Docker image to GHCR automatically on every push to main. No more manual `docker build && docker push`. #GitHubActions #CICD #DevOps"

### Common Mistakes
- Pushing images on every PR from forks (security risk — untrusted code shouldn't get registry write access)
- Not tagging images meaningfully (using only `latest` makes rollbacks impossible)
- Storing secrets in plaintext in the workflow file instead of GitHub Secrets

### Extra Learning (Optional)
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [GitHub Container Registry Docs](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-container-registry)

### Estimated Time
3 hours

---

## Day 26
### Goal
Extend CI into CD: automatically deploy to your Kubernetes cluster (or EC2) on merge to main.

### Theory (15–30 min)
Understand deployment strategies (rolling update vs blue-green vs canary — conceptually), and GitOps-adjacent patterns (declarative deploys triggered by CI). Learn `kubectl`/`helm` usage inside GitHub Actions runners.

### Practical Task
- Extend your workflow with a `deploy` job that: authenticates to your cluster (kubeconfig via GitHub Secret, or re-creates a kind cluster in CI for demo purposes since a real cluster isn't always reachable from GitHub-hosted runners), then runs `helm upgrade --install` with the new image tag
- Add manual approval (GitHub Environments with required reviewers) before the deploy job runs — simulating a real production gate

### Mini Challenge
Implement a rollback job that can be triggered manually (`workflow_dispatch`) to `helm rollback` to the previous release if something goes wrong.

### Commands to Practice
```bash
gh workflow run deploy.yml
gh workflow run rollback.yml --ref main
helm upgrade go-api ./charts/go-api-chart --set image.tag=$GITHUB_SHA
```

### Deliverables
- `deploy.yml` workflow with a manual approval gate
- `rollback.yml` workflow, manually triggerable
- Documented end-to-end flow: push → test → build → approve → deploy

### GitHub Repository Structure
```
go-rest-api/
├── .github/
│   └── workflows/
│       ├── ci.yml
│       ├── deploy.yml
│       └── rollback.yml
├── README.md
```

### README Requirements
Add a full CI/CD pipeline diagram (push → test → build → approve → deploy → rollback path), and explain the approval gate's purpose.

### LinkedIn Post Idea
> "Day 26: Extended CI into full CD — GitHub Actions now deploys to Kubernetes via Helm automatically after tests pass, gated behind a manual approval step, with a one-click rollback workflow as a safety net. This is what 'ship with confidence' actually looks like. #CICD #GitHubActions #Kubernetes #DevOps"

### Common Mistakes
- Auto-deploying to production with zero approval gates (fine for personal projects, dangerous as a habit)
- Not having a rollback plan — deploy pipelines without a documented "undo" are incomplete
- Storing kubeconfig/cluster credentials insecurely instead of as encrypted GitHub Secrets

### Extra Learning (Optional)
- [GitHub Environments & Protection Rules](https://docs.github.com/en/actions/deployment/targeting-different-environments/using-environments-for-deployment)
- [GitOps Principles — CNCF](https://opengitops.dev/)

### Estimated Time
3.5 hours

---

## Day 27
### Goal
Add observability: instrument your Go API with Prometheus metrics.

### Theory (15–30 min)
Understand the four golden signals (latency, traffic, errors, saturation) and Prometheus's pull-based scraping model vs push-based alternatives. Learn metric types: counter, gauge, histogram.

### Practical Task
- Add `prometheus/client_golang` to your API, exposing `/metrics` with: request count (counter, labeled by route/status), request duration (histogram), and active connections (gauge)
- Deploy Prometheus in your Kubernetes cluster (via Helm chart `kube-prometheus-stack` or standalone) with a `ServiceMonitor`/scrape config targeting your API

### Mini Challenge
Write a PromQL query calculating your API's error rate (`5xx / total requests`) over a 5-minute window, and document it in README as a "reusable query" — this is exactly what SREs write for alerting rules.

### Commands to Practice
```bash
curl localhost:8080/metrics
helm install prometheus prometheus-community/kube-prometheus-stack
kubectl port-forward svc/prometheus-operated 9090
# PromQL: rate(http_requests_total{status=~"5.."}[5m])
```

### Deliverables
- `/metrics` endpoint exposing custom application metrics
- Prometheus deployed and successfully scraping the API
- Documented PromQL queries (error rate, p95 latency)

### GitHub Repository Structure
```
go-rest-api/
├── internal/
│   └── metrics/
│       └── metrics.go
k8s-deployment/
├── manifests/
│   └── monitoring/
│       ├── servicemonitor.yaml
│       └── prometheus-values.yaml
├── docs/
│   └── promql-queries.md
```

### README Requirements
Add "Observability" section explaining each metric exposed and why it matters (the four golden signals framing).

### LinkedIn Post Idea
> "Day 27: Instrumented my Go API with Prometheus metrics — request rate, error rate, and latency histograms — and deployed Prometheus in Kubernetes to scrape them. Wrote my first PromQL queries for error rate and p95 latency. Observability isn't optional in production. #Prometheus #Observability #Kubernetes #DevOps"

### Common Mistakes
- Exposing high-cardinality labels (e.g., labeling by user ID) which can crash Prometheus at scale
- Not using histograms for latency (averages hide tail latency problems)
- Forgetting to secure the `/metrics` endpoint in real production (internal-only exposure)

### Extra Learning (Optional)
- [Prometheus Official Docs](https://prometheus.io/docs/introduction/overview/)
- [Google SRE Book — Monitoring Distributed Systems](https://sre.google/sre-book/monitoring-distributed-systems/)

### Estimated Time
3.5 hours

---

## Day 28 — 🏗️ Week 4 Mini Project: **AWS Infra + CI/CD + Monitoring Stack v1.0**
### Goal
Build Grafana dashboards on top of your Prometheus metrics and finalize the entire automated infra + pipeline + observability stack.

### Theory (15–30 min)
Understand dashboard design principles: what to show an on-call engineer at 3AM (top-level health first, drill-down second). Learn Grafana data sources and alerting basics.

### Practical Task
- Deploy Grafana (via `kube-prometheus-stack`, likely already included from Day 27) and build a custom dashboard: request rate, error rate, p95/p99 latency, pod CPU/memory
- Add a Grafana Alert rule (e.g., error rate > 5% for 5 minutes) that would notify (document the notification channel setup, e.g., a webhook — doesn't need to be live)
- Export the dashboard as JSON and commit it (Dashboards-as-Code)

### Mini Challenge
Write a `terraform` module (or document the manual steps) that could provision this entire environment (VPC + EC2/EKS-ready networking) from a single `terraform apply` in a fresh AWS account — proving the whole Week 4 stack is reproducible.

### Commands to Practice
```bash
kubectl port-forward svc/grafana 3000:80
# Import dashboard JSON via Grafana UI or provisioning config
terraform plan -out=tfplan   # full environment plan
```

### Deliverables
- Grafana dashboard (JSON exported, committed to repo)
- Documented alert rule
- Full Week 4 repo: Terraform infra + CI/CD workflows + monitoring stack, all documented as one reproducible system

### GitHub Repository Structure
```
aws-terraform-infra/
├── bootstrap/
├── modules/
│   ├── vpc/
│   └── ec2/
├── environments/
│   └── dev/
├── monitoring/
│   ├── dashboards/
│   │   └── go-api-dashboard.json
│   └── alerts/
│       └── error-rate-alert.yaml
├── docs/
│   ├── architecture.md
│   └── promql-queries.md
├── README.md
└── LICENSE
```

### README Requirements
- Full architecture diagram: AWS VPC/EC2 (or EKS-ready) + Terraform + GitHub Actions pipeline + Prometheus/Grafana
- Screenshots of the Grafana dashboard
- Cost breakdown / cleanup instructions (`terraform destroy`)
- "Reproducibility" section: how someone could deploy this from zero

### LinkedIn Post Idea (Project Showcase)
> "🎉 Week 4 complete: Provisioned AWS infrastructure with Terraform (remote state, VPC, EC2), built a full GitHub Actions CI/CD pipeline with approval gates and rollback, and instrumented everything with Prometheus + Grafana dashboards and alerts. Infrastructure as code, automated deploys, real observability — this is the DevOps loop. #Terraform #AWS #GitHubActions #Prometheus #Grafana #DevOps #100DaysOfCode"
>
> **Hashtags:** #DevOps #Terraform #AWS #GitHubActions #CICD #Prometheus #Grafana #SRE #InfrastructureAsCode #100DaysOfCode

### Common Mistakes
- Building dashboards with too many panels (noise over signal — pick the golden signals)
- Not documenting `terraform destroy` steps, leaving reviewers unsure how to safely test your repo
- Treating monitoring as "extra credit" instead of a core deliverable — in real jobs, unmonitored systems are considered unfinished

### Extra Learning (Optional)
- [Grafana Documentation](https://grafana.com/docs/grafana/latest/)
- [Dashboards as Code — Grafana Provisioning](https://grafana.com/docs/grafana/latest/administration/provisioning/)

### Estimated Time
4 hours

### 🎤 Week 4 Interview Prep
| Likely Question | What They're Testing |
|---|---|
| "Why remote state with locking instead of local state?" | Team-safety reasoning, not just Terraform syntax |
| "Your deploy pipeline just failed after a merge to main — walk me through what you check first." | Incident triage under a CI/CD mental model |
| "How would you track which team is responsible for a surprise AWS bill?" | Cost/tagging discipline |
| "Your error rate just spiked 5x on the Grafana dashboard — what do you look at first, second, third?" | Structured incident response, not panic |

**Resume bullet draft:**
> "Provisioned AWS infrastructure (VPC, EC2) via Terraform with remote state, IaC security scanning (tfsec), and cost-allocation tagging; built a GitHub Actions CI/CD pipeline with approval gates, automated rollback, and Prometheus/Grafana observability."

---

# 🏁 FINAL SPRINT (Days 29–30) — The Capstone Project
**Why this matters:** This is what gets screenshotted into your resume, pinned to your GitHub profile, and pulled up during interviews. It's not a new build from scratch — it's the *integration* of everything into one coherent, production-style architecture. Interviewers care less about individual tools and more about whether you can reason about a whole system end-to-end.

### 🏗️ Final Architecture

```
                         ┌─────────────────────┐
                         │      Internet        │
                         └──────────┬───────────┘
                                    │
                         ┌──────────▼───────────┐
                         │   Nginx (Ingress)     │  ← TLS termination, routing
                         └──────────┬───────────┘
                                    │
                         ┌──────────▼───────────┐
                         │  Go REST API (Pods)   │  ← business logic, metrics
                         │  (Deployment + HPA)   │
                         └──────┬─────────┬──────┘
                                │         │
                    ┌───────────▼─┐    ┌──▼──────────────┐
                    │    Redis     │    │   PostgreSQL     │
                    │  (cache)     │    │ (StatefulSet+PVC)│
                    └──────────────┘    └──────────────────┘

              All of the above runs inside:
                    ┌──────────────────────────┐
                    │       Kubernetes          │
                    └────────────┬──────────────┘
                                 │
                    ┌────────────▼──────────────┐
                    │   Provisioned by Terraform  │
                    │   (VPC, EC2/EKS-ready net)  │
                    └────────────┬──────────────┘
                                 │
                    ┌────────────▼──────────────┐
                    │   Deployed by GitHub        │
                    │   Actions (CI/CD pipeline)  │
                    └────────────┬──────────────┘
                                 │
                    ┌────────────▼──────────────┐
                    │        AWS (Cloud)          │
                    └──────────────────────────────┘

        Observed throughout by: Prometheus (metrics) + Grafana (dashboards)
```

### Why Each Component Exists (be ready to explain this in interviews)

| Component | Why It's There |
|---|---|
| **Nginx** | Single entry point; handles TLS, routing, and shields backend pods from being directly internet-facing |
| **Go REST API** | The actual business logic; chosen for performance, small footprint, and native cloud-native tooling alignment |
| **Redis** | Reduces database load for hot-read data; enables shared rate-limiting state across replicas |
| **PostgreSQL** | Durable, relational source of truth — data that must survive restarts and be queryable/consistent |
| **Docker** | Consistent, portable packaging — "works on my machine" becomes "works everywhere" |
| **Kubernetes** | Self-healing, scaling, and declarative orchestration of all the above across multiple nodes |
| **GitHub Actions** | Automates test → build → deploy, removing manual error-prone steps and enforcing quality gates |
| **Terraform** | Reproducible, version-controlled infrastructure — no more "who clicked what in the console" |
| **AWS** | The actual compute/network substrate everything runs on |
| **Prometheus + Grafana** | Answers "is it actually working?" — the question that matters most once something is live |

---

## Day 29
### Goal
Integrate all previous repos into one capstone deployment and validate the entire flow end-to-end.

### Theory (15–30 min)
Review the concept of a "deployment pipeline as a system" — not individual tools, but the full path from `git push` to a monitored, running service. This is the mental model senior engineers use to reason about incidents.

### Practical Task
- Create the capstone repo (see Portfolio section below for structure) that references/vendors your Week 2–4 work
- Run the entire flow live: make a code change → push → CI tests/builds → CD deploys via Helm → verify in Grafana that request metrics reflect the change (e.g., watch request count tick up as you `curl` the new endpoint)
- Fix any integration gaps you discover (this is normal and expected — document them, don't hide them)

### Mini Challenge
Deliberately introduce a bug, push it, watch it fail CI (should be blocked from deploying), then fix it and watch it succeed — proving your pipeline's quality gate actually works, not just exists.

**Systems design warm-up (write, don't build):** Almost every cloud internship interview loop includes a lightweight design question. Write a one-page answer to: *"This API currently handles 10 requests/second. How would you redesign it to handle 10,000 requests/second?"* Cover: horizontal scaling (more pods/HPA tuning), read replicas for Postgres, a CDN/cache layer, connection pooling, and where your current architecture would actually break first. This single page is one of the highest-leverage artifacts you'll produce all month.

### Commands to Practice
```bash
git commit -am "feat: add /stats endpoint"
git push origin main
gh run watch
kubectl get pods -w
```

### Deliverables
- End-to-end working flow, demonstrated and documented
- A written "failure and fix" case study (the deliberate bug exercise)

### GitHub Repository Structure
See capstone structure in the Portfolio section below.

### README Requirements
Draft (not final) version of the capstone README with the architecture diagram embedded.

### LinkedIn Post Idea
> "Day 29: Ran my full pipeline end-to-end — pushed a code change, watched GitHub Actions test and build it, Helm deploy it to Kubernetes, and Grafana reflect the new traffic in real time. Then broke it on purpose to prove the CI quality gate actually blocks bad code. #DevOps #CICD #Kubernetes #100DaysOfCode"

### Common Mistakes
- Not actually testing the failure path (a pipeline that's never seen a failing test hasn't proven it can catch one)
- Integration gaps discovered late because components were never run together before this day
- Rushing the capstone without validating each layer individually first

### Extra Learning (Optional)
- [The Site Reliability Engineering Workbook (Google, free online)](https://sre.google/workbook/table-of-contents/)

### Estimated Time
4 hours

---

## Day 30 — 🏆 FINAL CAPSTONE: Production-Style Cloud-Native Platform
### Goal
Finalize, document, and publicly ship the capstone project as the centerpiece of your DevOps portfolio.

### Theory (15–30 min)
Study what makes a capstone project convincing to a hiring manager: clear architecture communication, evidence of operational thinking (not just "it deploys"), and honesty about trade-offs/limitations. Review your own 30-day journey — you'll be asked "walk me through a project" in interviews; this is your answer.

### Practical Task
- Write the final, polished capstone `README.md` (see template in Portfolio section)
- Record a 2–3 minute demo video or GIF walking through: architecture → code push → pipeline → live metrics in Grafana
- Write a `docs/decisions.md` (lightweight ADR-style) documenting key trade-offs: e.g., "Why StatefulSet over Deployment for Postgres," "Why manual approval gate before deploy"
- Tag `v1.0.0` and write GitHub Release notes summarizing the whole system
- Clean up AWS resources you no longer need (`terraform destroy` where appropriate) — cost discipline to the end
- Pull up your `target-roles.md` from Day 0. For each required skill listed across your 10 target postings, map it to a specific thing you built. Anything with no match, note honestly — that's your next learning priority after Day 30, not a reason to panic
- Rewrite your resume's projects section using the 5 resume-bullet drafts from this challenge (Day 7, 14, 21, 28, and the capstone) — quantify wherever you have real numbers (image size reduction, latency improvement, etc.)

### Mini Challenge
Write a one-page "Incident Response" doc: if the Grafana dashboard showed a 20% error rate spike right now, walk through exactly which dashboards/logs/commands you'd check first, in order. This single artifact demonstrates operational maturity most junior candidates never show.

**Mock interview (do this out loud, not just in your head):** Record yourself (phone camera is fine) answering these three, unscripted, in under 2 minutes each:
1. "Walk me through your capstone project's architecture." (technical communication)
2. "Tell me about a time something broke and how you fixed it." (use the Day 29 deliberate-bug story — STAR format: Situation, Task, Action, Result)
3. "Why DevOps, and why us?" (motivation — tie back to your Day 0 company research)

Watch the recording once. You'll immediately hear your own filler words and unclear explanations — fix them before a real interview does it for you.

### Commands to Practice
```bash
git tag -a v1.0.0 -m "Capstone: Production-Style Cloud-Native Platform"
git push origin v1.0.0
gh release create v1.0.0 --notes-file RELEASE_NOTES.md
terraform destroy   # clean up billable resources
```

### Deliverables
- Fully documented, tagged, publicly shareable capstone repository
- Demo video/GIF
- `docs/decisions.md`, `docs/incident-response.md`, and a one-page systems-design writeup
- Clean AWS billing state
- Updated resume with 5 quantified project bullets
- A recorded (private, for yourself) mock-interview run

### GitHub Repository Structure
See full capstone structure below in the Portfolio section.

### README Requirements
The complete, final version — see the README template in the Portfolio section. This is the single most important README of the challenge.

### LinkedIn Post Idea (Capstone Showcase — your biggest post)
> "🚀 30 Days of DevOps: From Linux basics to a full production-style cloud-native platform.
>
> Over the past 30 days I built, end-to-end:
> ✅ A Linux + Python automation toolkit (tested, secret-scanned, CI-linted)
> ✅ A Go REST API with PostgreSQL + Redis, containerized with security-scanned multi-stage Docker builds
> ✅ The same stack deployed to Kubernetes — self-healing, autoscaling, NetworkPolicy-restricted, Ingress + TLS, packaged as a Helm chart
> ✅ AWS infrastructure provisioned entirely with Terraform (remote state, tfsec-scanned, cost-tagged)
> ✅ A full GitHub Actions CI/CD pipeline with security gates, approval steps, and rollback
> ✅ Prometheus + Grafana observability with dashboards and alerting
>
> Every single day was a hands-on build, pushed to GitHub, no shortcuts. The capstone repo ties it all into one architecture: Nginx → Go API → Redis → PostgreSQL → Docker → Kubernetes → GitHub Actions → Terraform → AWS.
>
> Repo, architecture diagram, and demo video linked below. Open to entry-level DevOps/Cloud opportunities — always happy to talk shop. 🙌
>
> #DevOps #CloudEngineering #Kubernetes #Terraform #AWS #Golang #Docker #CICD #100DaysOfCode #OpenToWork"

### Common Mistakes
- Ending without a demo video — text-only READMEs get skimmed, not read
- Not writing `decisions.md` — explaining trade-offs is what separates "followed steps" from "understood the system"
- Leaving AWS resources running after the challenge, racking up unnecessary cost
- Treating Day 30 as "the end" instead of the baseline you now iterate on (add more services, add alerting integrations, try EKS, etc.)

### Extra Learning (Optional)
- [Architecture Decision Records (ADR) — GitHub's adr repo](https://github.com/joelparkerhenderson/architecture-decision-record)
- [CNCF Cloud Native Landscape](https://landscape.cncf.io/) — explore what's next after this challenge

### Estimated Time
4–5 hours

---

# 🎯 Interview & Resume Preparation Guide
**Why this section exists:** A hiring manager reads your resume for 30 seconds and interviews you for 45 minutes. This challenge gives you the substance; this section makes sure that substance actually lands.

## Resume Translation Table

| What You Built | Resume Bullet Pattern |
|---|---|
| Week 1 toolkit | "Built [X] using [tech], reducing/automating [manual task], with [testing/security measure]" |
| Week 2 API | "Designed and containerized [X], achieving [quantified result], tested via [tool]" |
| Week 3 K8s | "Deployed [X] to Kubernetes with [resilience feature], packaged as [Helm/artifact]" |
| Week 4 infra | "Provisioned [X] via Terraform with [security/cost practice], automated via [CI/CD tool]" |
| Capstone | "Architected an end-to-end cloud-native platform spanning [N] technologies, from IaC provisioning through CI/CD to production monitoring" |

**Rule of thumb:** every bullet should answer "so what?" A recruiter doesn't care that you used Kubernetes; they care that pods self-heal, requests autoscale, or deploys got safer. Lead with the outcome, name the tool second.

## Common Technical Interview Questions by Category

| Category | Sample Questions |
|---|---|
| Linux/Networking | "Explain what happens during a `ping`." · "Difference between TCP and UDP, and when each matters." · "How does DNS resolution work?" |
| Git | "Merge vs. rebase — when would you use each?" · "How do you recover a commit you accidentally reset away?" |
| Docker | "Why use multi-stage builds?" · "What's the difference between an image and a container?" |
| Kubernetes | "Deployment vs. StatefulSet vs. DaemonSet — when does each apply?" · "How does a Service find its pods?" |
| CI/CD | "What would you check first if a pipeline that worked yesterday fails today?" · "How do you handle secrets in a pipeline?" |
| Cloud/AWS | "Difference between a security group and a NACL." · "How would you design for high availability across AZs?" |
| Behavioral | "Tell me about a time you disagreed with a technical decision." · "Describe a time you had to learn something quickly under a deadline." |

## Behavioral Answers: Use STAR, Every Time
**S**ituation → **T**ask → **A**ction → **R**esult. Every "tell me about a time" question gets this structure. Your Day 29 deliberate-bug exercise and any real debugging moment from this challenge are ready-made STAR stories — write 3-4 of them out in full before interviewing, don't improvise them live.

## What to Do When You Don't Know an Answer
Say what you *do* know, state your reasoning process, and be explicit about what you'd look up. "I haven't used EKS specifically, but I've run Kubernetes via kind and understand the control plane model — I'd expect the main differences to be around IAM integration and managed node groups, and I'd check the AWS docs to confirm" is a strong answer. Silence or guessing confidently is not.

---

# 📁 Portfolio & GitHub Presentation Guide

## Recommended Repository Names

| Project | Repository Name |
|---|---|
| Week 1 | `linux-automation-toolkit` |
| Week 2 | `go-rest-api` (or `go-rest-api-docker-compose`) |
| Week 3 | `k8s-deployment` (or `go-api-kubernetes-platform`) |
| Week 4 | `aws-terraform-infra` |
| Capstone | `cloud-native-devops-platform` |

> **Tip:** Pin all 5 repos on your GitHub profile. Add a profile `README.md` (create a repo named exactly your GitHub username) that briefly summarizes the 30-day journey and links to each project with a one-line description.

## Capstone Repository Structure

```
cloud-native-devops-platform/
├── .github/
│   └── workflows/
│       ├── ci.yml
│       ├── deploy.yml
│       └── rollback.yml
├── api/                        # Go REST API source (or git submodule/subtree from go-rest-api)
│   ├── cmd/
│   ├── internal/
│   └── Dockerfile
├── infra/                      # Terraform
│   ├── modules/
│   └── environments/
├── k8s/                        # Helm chart(s)
│   └── charts/
├── monitoring/
│   ├── dashboards/
│   └── alerts/
├── docs/
│   ├── architecture.md
│   ├── decisions.md
│   ├── incident-response.md
│   └── demo.gif
├── README.md
├── LICENSE
└── RELEASE_NOTES.md
```

## README Template (use for every project, especially the capstone)

```markdown
# Project Name

![CI](badge-url) ![License](badge-url) ![Last Commit](badge-url)

One-paragraph summary: what this is and why it exists.

## Architecture
[Diagram here]

## Why These Technologies
Brief rationale table (tech → reason).

## Getting Started
Step-by-step, copy-pasteable setup instructions.

## API / Usage Reference
Table of endpoints/commands.

## Screenshots / Demo
[GIF or screenshots]

## What I Learned
2-4 honest sentences — this is what interviewers actually read.

## Trade-offs & Limitations
Be honest — this builds more credibility than pretending it's perfect.

## License
```

## Screenshots & Diagrams to Include
- Terminal output of key commands succeeding (`kubectl get pods`, `terraform apply`, `helm test`)
- Grafana dashboard screenshot
- GitHub Actions pipeline green checkmarks
- Architecture diagram (draw.io, Excalidraw, or even clean ASCII like the one in this guide)
- Before/after comparisons where relevant (e.g., Docker image size)

## Badges Worth Adding
- Build status (GitHub Actions)
- License
- Go version
- "Last commit" activity badge
- Optional: Docker image size badge (via shields.io + registry)

---

# 💼 Weekly LinkedIn Content Plan

| Week | Learning Post Theme | Showcase Post Theme | Hashtags |
|---|---|---|---|
| 1 | "Why Linux fundamentals still matter" | Linux Automation Toolkit v1.0 launch | #Linux #Bash #DevOps #Git #100DaysOfCode |
| 2 | "Why I'm learning Go as a DevOps engineer" | Go API + Docker Compose stack launch | #Golang #Docker #PostgreSQL #Redis #DevOps |
| 3 | "What building on Kubernetes actually teaches you" | K8s Platform + Helm chart launch | #Kubernetes #Helm #CloudNative #DevOps |
| 4 | "Terraform + GitHub Actions: automating everything" | AWS infra + CI/CD + monitoring launch | #Terraform #AWS #GitHubActions #Grafana #Prometheus |
| Capstone | "30 days, one architecture: what I learned" | Full capstone showcase (see Day 30 post) | #DevOps #CloudEngineering #100DaysOfCode #OpenToWork |

---

# 📚 High-Quality Resources (Official Docs Only)

| Topic | Resource |
|---|---|
| Linux/Bash | [GNU Bash Manual](https://www.gnu.org/software/bash/manual/) |
| Git | [Pro Git Book](https://git-scm.com/book/en/v2) |
| GitHub | [GitHub Docs](https://docs.github.com/) |
| Docker | [Docker Official Docs](https://docs.docker.com/) |
| Docker Compose | [Compose Docs](https://docs.docker.com/compose/) |
| Go | [A Tour of Go](https://go.dev/tour/) · [Effective Go](https://go.dev/doc/effective_go) |
| PostgreSQL | [PostgreSQL Docs](https://www.postgresql.org/docs/) |
| Redis | [Redis Docs](https://redis.io/docs/latest/) |
| Kubernetes | [Kubernetes Docs](https://kubernetes.io/docs/home/) |
| Helm | [Helm Docs](https://helm.sh/docs/) |
| Nginx | [Nginx Docs](https://nginx.org/en/docs/) |
| Terraform | [Terraform Docs](https://developer.hashicorp.com/terraform/docs) |
| AWS | [AWS Documentation](https://docs.aws.amazon.com/) |
| GitHub Actions | [GitHub Actions Docs](https://docs.github.com/en/actions) |
| Prometheus | [Prometheus Docs](https://prometheus.io/docs/introduction/overview/) |
| Grafana | [Grafana Docs](https://grafana.com/docs/grafana/latest/) |
| CNCF Landscape | [landscape.cncf.io](https://landscape.cncf.io/) |
| SRE Practices | [Google SRE Book](https://sre.google/sre-book/table-of-contents/) (free, official) |
| 12-Factor App | [12factor.net](https://12factor.net/) |

---

# ✅ Final Checklist Before Calling It "Done"

**Build:**
- [ ] 5 GitHub repositories (or 4 + capstone), each with a strong README
- [ ] Every repo has at least one tagged release
- [ ] Capstone repo has an architecture diagram, demo video/GIF, and decisions doc
- [ ] All units of work have corresponding commits (contribution graph shows the work)
- [ ] AWS resources cleaned up / `terraform destroy` run where no longer needed

**Security (a real reviewer will check these):**
- [ ] Zero secrets in any Git history (`gitleaks` clean across all repos)
- [ ] Container images scanned with Trivy, no unresolved HIGH/CRITICAL findings
- [ ] Terraform scanned with tfsec/Checkov, no unresolved findings
- [ ] Least-privilege IAM policy used throughout (never `AdministratorAccess`)

**Career readiness (this is what actually gets you the interview):**
- [ ] Resume updated with 5 quantified bullets, one per project
- [ ] LinkedIn posts published weekly, plus the final capstone showcase post
- [ ] `target-roles.md` compared against your actual repos — gaps identified honestly
- [ ] At least 3 STAR-format behavioral stories written out in full
- [ ] Mock interview recorded and self-reviewed at least once
- [ ] You can explain, out loud, without notes, *why* every component in the final architecture exists — including what you'd change with more time

---

> **Mentor's closing note:** You didn't watch 30 days of tutorials. You built, broke, debugged, and shipped 30 days of real systems — with security built in, not bolted on, and with the career-prep work most candidates skip. That's the actual job, and that's what actually gets you the interview. Now go apply — and when someone asks "tell me about a project," you have five real answers, not one.

