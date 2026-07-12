# Playbook Structure Template

> Template untuk setup playbook partner baru.

---

## ⚡ Account Type

| | Organization | Personal |
|---|---|---|
| **Repo name** | `{org}/playbook` | `{username}/playbook` |
| **Extra repos** | `{org}/.github` | Tidak perlu |
| **Website repo** | `{org}/{project}` | `{username}/{username}.github.io` |
| **Templates location** | `{org}/.github/` (repo terpisah) | `{username}/playbook/.github/` (di dalam playbook) |

---

## 📁 Directory Structure

### Organization Account

```
{org}/playbook/
│
├── README.md
├── LICENSE
├── .gitignore
├── .github/                     ← (opsional, bisa juga di {org}/.github)
│   ├── ISSUE_TEMPLATE/
│   │   ├── feature-request.md
│   │   └── bug-report.md
│   └── pull_request_template.md
│
├── docs/
│   ├── 01-getting-started/
│   │   ├── onboarding.md
│   │   ├── environment-setup.md
│   │   └── team-roles.md
│   │
│   ├── 02-workflow/
│   │   ├── git-github-workflow.md
│   │   ├── project-management.md
│   │   └── communication.md
│   │
│   ├── 03-sop/
│   │   ├── code-review.md
│   │   ├── deployment.md
│   │   └── testing.md
│   │
│   ├── 04-templates/
│   │   ├── user-story.md
│   │   ├── github-issue.md
│   │   ├── pull-request.md
│   │   └── sprint-planning.md
│   │
│   ├── 05-adr/
│   │   ├── 001-title.md
│   │   └── ...
│   │
│   ├── 06-learning-path/
│   │   └── junior-dev-roadmap.md
│   │
│   └── 07-project/
│       ├── project-overview.md
│       ├── sprint-1-plan.md
│       └── mvp-scope.md
│
└── templates/
    └── ... (optional, additional templates)
```

### Personal Account

```
{username}/playbook/
│
├── README.md
├── LICENSE
├── .gitignore
├── .github/                     ← pengganti {org}/.github (repo terpisah)
│   ├── ISSUE_TEMPLATE/
│   │   ├── feature-request.md
│   │   └── bug-report.md
│   └── pull_request_template.md
│
├── docs/
│   ├── 01-getting-started/
│   │   ├── onboarding.md
│   │   ├── environment-setup.md
│   │   └── team-roles.md
│   │
│   ├── 02-workflow/
│   │   ├── git-github-workflow.md
│   │   ├── project-management.md
│   │   └── communication.md
│   │
│   ├── 03-sop/
│   │   ├── code-review.md
│   │   ├── deployment.md
│   │   └── testing.md
│   │
│   ├── 04-templates/
│   │   ├── user-story.md
│   │   ├── github-issue.md
│   │   ├── pull-request.md
│   │   └── sprint-planning.md
│   │
│   ├── 05-adr/
│   │   └── ...
│   │
│   ├── 06-learning-path/
│   │   └── junior-dev-roadmap.md
│   │
│   └── 07-project/
│       ├── project-overview.md
│       └── mvp-scope.md
│
├── .openkb/
│   ├── SHARED/
│   └── PERSONAL/               ← gitignored
│
└── templates/
    └── ...

{username}/{username}.github.io/
│
├── main                        ← source code website
├── handoff                     ← onboarding documentation
└── gh-pages                    ← build output untuk deployment
```

---

## 📝 File Templates

### README.md

```markdown
# {org} — Engineering Playbook

> Operating system untuk tim engineering {org}.

**Version:** 1.0.0  
**Last Updated:** {date}  
**Maintained by:** {name}

---

## 🎯 Vision

{Vision statement}

---

## 👥 Tim Engineering

| GitHub Username | Nama | Role | Fokus |
|---|---|---|---|
| @{username} | {name} | {role} | {focus} |

---

## 📚 Quick Start

### Untuk Product Analyst
1. Baca [`docs/04-templates/user-story.md`](docs/04-templates/user-story.md)
2. Buat user story di Trello
3. Link ke GitHub Issue

### Untuk Developer
1. Baca [`docs/01-getting-started/onboarding.md`](docs/01-getting-started/onboarding.md)
2. Setup environment
3. Pahami workflow
4. Ambil Issue dari GitHub Project

### Untuk Reviewer
1. Code Review Checklist: [`docs/03-sop/code-review.md`](docs/03-sop/code-review.md)
2. Sprint Planning Template: [`docs/04-templates/sprint-planning.md`](docs/04-templates/sprint-planning.md)

---

## 🛠️ Tech Stack

```
Backend  : {stack}
Frontend : {stack}
Database : {stack}
Auth     : {stack}
Deploy   : {stack}
```

---

## 📊 Project Management

| Tool | Purpose | Link |
|---|---|---|
| **Trello** | Product Roadmap | [Board](link) |
| **GitHub Projects** | Engineering Task | [Project](link) |
| **GitHub Issues** | Technical Task | [Issues](link) |

---

## 📞 Contact

**{org}**  
📧 Email: {email}  
📱 WhatsApp: {link}

---

**Last Updated:** {date}  
**Maintained by:** @{username}
```

---

### .gitignore

```gitignore
# Personal knowledge base
.openkb/PERSONAL/

# OS files
Thumbs.db
.DS_Store

# IDE
.idea/
.vscode/
*.swp
*.swo

# Environment
.env
.env.local
```

---

### LICENSE (MIT)

```
MIT License

Copyright (c) {year} {org}

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🚀 Setup Commands

### Organization Account

```bash
# 1. Clone playbook repo
git clone git@github.com:{org}/playbook.git
cd playbook

# 2. Copy template structure
cp ../konxc/playbook/templates/docs-template/ docs/
cp ../konxc/playbook/templates/templates/ templates/

# 3. Create .github structure
mkdir -p .github/ISSUE_TEMPLATE

# 4. Copy templates
cp ../konxc/playbook/.github/ISSUE_TEMPLATE/feature-request.md .github/ISSUE_TEMPLATE/
cp ../konxc/playbook/.github/ISSUE_TEMPLATE/bug-report.md .github/ISSUE_TEMPLATE/
cp ../konxc/playbook/.github/pull_request_template.md .github/

# 5. Create .openkb structure
mkdir -p .openkb/SHARED
mkdir -p .openkb/PERSONAL

# 6. Add to .gitignore
echo ".openkb/PERSONAL/" >> .gitignore

# 7. Initial commit
git add .
git commit -m "feat: initial playbook structure"
git push -u origin main
```

### Personal Account

```bash
# 1. Clone playbook repo
git clone git@github.com:{username}/playbook.git
cd playbook

# 2. Copy template structure
cp ../konxc/playbook/templates/docs-template/ docs/
cp ../konxc/playbook/templates/templates/ templates/

# 3. Create .github structure (di dalam playbook, bukan repo terpisah)
mkdir -p .github/ISSUE_TEMPLATE

# 4. Copy templates
cp ../konxc/playbook/.github/ISSUE_TEMPLATE/feature-request.md .github/ISSUE_TEMPLATE/
cp ../konxc/playbook/.github/ISSUE_TEMPLATE/bug-report.md .github/ISSUE_TEMPLATE/
cp ../konxc/playbook/.github/pull_request_template.md .github/

# 5. Create .openkb structure
mkdir -p .openkb/SHARED
mkdir -p .openkb/PERSONAL

# 6. Add to .gitignore
echo ".openkb/PERSONAL/" >> .gitignore

# 7. Initial commit
git add .
git commit -m "feat: initial playbook structure"
git push -u origin main

# 8. Setup website repo dengan branch structure
git clone git@github.com:{username}/{username}.github.io.git
cd {username}.github.io

# Branch main = source code (sudah ada)

# Buat branch handoff
git checkout -b handoff
# ... tambahkan onboarding docs
git add .
git commit -m "feat: onboarding documentation"
git push -u origin handoff

# Buat branch gh-pages
git checkout --orphan gh-pages
git rm -rf .
# ... copy build output
git add .
git commit -m "Initial gh-pages"
git push -u origin gh-pages

git checkout main
```

---

## 📋 Minimum Viable Playbook (MVP)

**Week 1 Priority:**

```markdown
✅ README.md
✅ docs/01-getting-started/onboarding.md
✅ docs/01-getting-started/environment-setup.md
✅ docs/01-getting-started/team-roles.md
✅ docs/02-workflow/git-github-workflow.md
✅ docs/04-templates/github-issue.md
✅ docs/04-templates/pull-request.md
✅ .openkb/SHARED/glossary.md
✅ .openkb/SHARED/references.md
```

**Week 2 Priority:**

```markdown
✅ docs/02-workflow/communication.md
✅ docs/03-sop/code-review.md
✅ docs/03-sop/deployment.md
✅ docs/03-sop/testing.md
✅ docs/04-templates/user-story.md
✅ docs/04-templates/sprint-planning.md
✅ docs/07-project/project-overview.md
✅ docs/07-project/sprint-1-plan.md
```

---

## 🎯 Quality Checklist

Before submitting for audit:

```markdown
## Documentation
- [ ] All required docs present
- [ ] Examples included
- [ ] Links working
- [ ] No placeholder text

## Implementation
- [ ] .openkb/ structure setup
- [ ] .github/ templates setup
- [ ] Git workflow documented
- [ ] SOP documented

## Project
- [ ] Sprint planning done
- [ ] Tasks assigned
- [ ] Velocity tracked
- [ ] Retrospective done
```

---

## 📚 References

- SMA-UII-Yogyakarta/playbook (reference implementation)
- konxc/playbook/docs/04-onboarding-partner.md
- konxc/playbook/docs/05-quality-standard.md

---

**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev