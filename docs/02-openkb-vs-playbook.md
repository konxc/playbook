# OpenKB vs Playbook — Understanding the Difference

> Two protocols, one goal: **Knowledge retention & collaboration**.

---

## 🎯 Executive Summary

| Aspect | OpenKB | Playbook |
|---|---|---|
| **Purpose** | AI Agent-to-Human communication | Human-to-Human guidelines |
| **Location** | `.openkb/` di setiap repo | `{org}/playbook` standalone repo |
| **Audience** | AI Agents + Developers | Human team members |
| **Scope** | Repository-specific context | Organization-wide guidelines |
| **Git** | SHARED/ tracked, PERSONAL/ ignored | Fully tracked |
| **Created** | Sandikodev (2026) | Industry standard (adapted) |

---

## 📚 OpenKB (Knowledge Base Protocol)

### Overview

**OpenKB** adalah protokol knowledge base yang dikembangkan oleh Sandikodev untuk memfasilitasi komunikasi antara AI Agent dan Human Developer.

**Repository:** TBD (open specification)  
**Implementation:** Sudah digunakan di semua repo SMA UII Yogyakarta

---

### Characteristics

```
Location:    .openkb/ di root repository
Structure:   SHARED/ + PERSONAL/
Tracking:    SHARED/ tracked, PERSONAL/ gitignored
Scope:       Repository-specific context
Audience:    AI Agents + Human Developers
Lifespan:    Sama dengan lifecycle repository
```

---

### Structure

```
.openkb/
├── TEMPLATE.md              # Template untuk knowledge base
├── SHARED/                  # Tracked di git
│   ├── glossary.md          # Istilah & singkatan
│   ├── references.md        # Referensi cepat
│   └── decision-log.md      # Catatan keputusan
│
└── PERSONAL/                # Gitignored
    ├── {user1}/
    │   ├── profile.md
    │   └── instructions.md
    └── {user2}/
        └── ...
```

---

### Purpose

**Untuk AI Agent:**
```markdown
✅ Context repository (tech stack, architecture)
✅ Referensi dokumentasi
✅ Glossary untuk understand terminology
✅ Decision history untuk avoid re-debate
✅ User-specific instructions (dari PERSONAL/)
```

**Untuk Human Developer:**
```markdown
✅ Quick reference (cheatsheet)
✅ Decision log (kenapa diputuskan begini)
✅ Links ke dokumentasi lengkap
✅ Personal notes (tidak di-track)
```

---

### Use Cases

**Scenario 1: New Developer Join**
```
1. Clone repository
2. Baca .openkb/SHARED/glossary.md
3. Baca .openkb/SHARED/references.md
4. Buat .openkb/PERSONAL/{username}/profile.md
5. Start coding dengan context lengkap
```

**Scenario 2: AI Agent Assist**
```
1. Developer tanya ke AI: "Bagaimana cara add new migration?"
2. AI baca .opencode/instructions + .openkb/SHARED/references.md
3. AI give context-aware answer (sesuai stack & convention repo)
4. Developer execute dengan confidence
```

**Scenario 3: Architecture Decision**
```
1. Team decide pakai Livewire bukan React
2. Sandikodev create .openkb/SHARED/decision-log.md
3. Document: Context, Decision, Rationale, Consequences
4. Future: Tidak ada "Kenapa kita pakai Livewire?"
```

---

### Best Practices

**Do's ✅**
```markdown
✅ Keep SHARED/ concise (cheatsheet, bukan novel)
✅ Update glossary saat ada istilah baru
✅ Document decision segera (jangan nanti)
✅ Use PERSONAL/ untuk learning notes
✅ Link ke playbook untuk guidelines umum
```

**Don'ts ❌**
```markdown
❌ Jangan commit sensitive info di PERSONAL/
❌ Jangan duplicate content dari playbook
❌ Jangan biarkan outdated (review per sprint)
❌ Jangan tulis essay (bullet points only)
```

---

## 📘 Playbook (Engineering Guidelines)

### Overview

**Playbook** adalah comprehensive documentation untuk engineering team guidelines, onboarding, dan operational procedures.

**Repository:** `{org}/playbook` (standalone)  
**Implementation:** SMA UII Yogyakarta, future partners

---

### Characteristics

```
Location:    Standalone repository ({org}/playbook)
Structure:   docs/, templates/, adr/, project/
Tracking:    Fully tracked di git
Scope:       Organization-wide guidelines
Audience:    Human team members
Lifespan:    Sama dengan lifecycle organization
```

---

### Structure

```
playbook/
├── README.md
├── docs/
│   ├── 01-getting-started/
│   │   ├── onboarding.md
│   │   ├── environment-setup.md
│   │   └── team-roles.md
│   ├── 02-workflow/
│   │   ├── git-github-workflow.md
│   │   ├── trello-workflow.md
│   │   └── communication.md
│   ├── 03-sop/
│   │   ├── code-review.md
│   │   ├── deployment.md
│   │   └── testing.md
│   ├── 04-templates/
│   │   ├── user-story.md
│   │   ├── github-issue.md
│   │   └── pull-request.md
│   ├── 05-adr/
│   │   ├── 001-monorepo.md
│   │   └── ...
│   ├── 06-learning-path/
│   │   └── junior-dev-roadmap.md
│   └── 07-project/
│       ├── smart-absen-overview.md
│       └── ...
│
├── templates/
└── LICENSE
```

---

### Purpose

**Untuk Organization:**
```markdown
✅ Standardize processes (onboarding, workflow, SOP)
✅ Retain knowledge (tidak hilang saat orang keluar)
✅ Scale team (junior dapat perform seperti senior)
✅ Quality assurance (checklist-driven)
✅ Compliance (audit trail)
```

**Untuk Team Members:**
```markdown
✅ Clear expectations (role & responsibilities)
✅ Self-serve onboarding (tidak perlu tanya terus)
✅ Reference untuk daily work (SOP, templates)
✅ Learning path (growth trajectory)
✅ Historical context (ADR, decision log)
```

---

### Use Cases

**Scenario 1: New Member Onboarding**
```
Day 1:
1. HR invite ke GitHub org
2. New member clone {org}/playbook
3. Baca docs/01-getting-started/onboarding.md
4. Follow checklist (environment setup, etc)
5. Day 2: First PR merged

Week 1:
1. Baca docs/02-workflow/git-github-workflow.md
2. Pahami branching strategy
3. Complete first real task

Month 1:
1. Follow docs/06-learning-path/junior-dev-roadmap.md
2. Weekly check-in dengan mentor
3. Independent contributor
```

**Scenario 2: Process Improvement**
```
Problem: Code review lama (> 48 jam)

Solution:
1. Baca docs/03-sop/code-review.md
2. Identify bottleneck (reviewer overload)
3. Update SOP: Add co-reviewer
4. Create PR ke playbook
5. Team review & merge
6. New process implemented
```

**Scenario 3: Quality Audit**
```
Quarterly audit:
1. Open docs/05-quality-standard.md
2. Checklist per section:
   - Onboarding: ✅ Complete
   - Workflow: ✅ Followed
   - SOP: ⚠️ Code review need improvement
   - Templates: ✅ Updated
3. Action items created
4. Track improvement next quarter
```

---

### Best Practices

**Do's ✅**
```markdown
✅ Keep playbook alive (update per sprint)
✅ Link antar docs (navigation mudah)
✅ Use templates (consistency)
✅ Document decisions (ADR)
✅ Version control (tag releases)
```

**Don'ts ❌**
```markdown
❌ Jangan biarkan outdated (review regular)
❌ Jangan tulis sekali, lupa selamanya
❌ Jangan terlalu verbose (concise & actionable)
❌ Jangan duplicate (DRY principle)
❌ Jangan ignore feedback (continuous improvement)
```

---

## 🔄 Integration Pattern

### How They Work Together

```
Repository Structure:
my-repo/
├── README.md
│   └── "Untuk guidelines, lihat: {org}/playbook"
│
├── .opencode/
│   ├── opencode.json
│   │   └── references:
│   │       └── playbook: "../{org}/playbook"
│   └── SHARED/
│       ├── project-context.md
│       └── agent-rules.md
│
├── .openkb/
│   ├── TEMPLATE.md
│   ├── SHARED/
│   │   ├── glossary.md
│   │   ├── references.md
│   │   └── decision-log.md
│   └── PERSONAL/ (gitignored)
│
└── docs/ (optional, repo-specific)
    └── api.md
```

---

### Information Flow

```
Playbook ({org}/playbook)
    ↓
General guidelines (onboarding, workflow, SOP)
    ↓
    └─ Link dari README.md
    └─ Referenced di .opencode/opencode.json

.openkb/SHARED/ (di setiap repo)
    ↓
Repository-specific context
    ↓
    └─ Glossary (istilah spesifik repo)
    └─ References (link ke docs internal)
    └─ Decision log (kenapa diputuskan begini)

.openkb/PERSONAL/ (gitignored)
    ↓
Personal notes & AI instructions
    ↓
    └─ User profile
    └─ Custom instructions untuk AI
    └─ Learning notes

.opencode/ (AI Agent config)
    ↓
AI-specific configuration
    ↓
    └─ Instructions (behavior AI)
    └─ References (link ke playbook & .openkb)
    └─ Agents (build, plan, review, docs)
```

---

## 📊 Decision Matrix

### When to Use What

| Scenario | Use OpenKB | Use Playbook | Use Both |
|---|---|---|---|
| **New repo setup** | ✅ Create .openkb/ | ❌ | ✅ (link ke playbook) |
| **New member onboarding** | ❌ | ✅ docs/01-getting-started/ | ✅ (general + repo-specific) |
| **AI Agent setup** | ✅ .opencode/ + .openkb/ | ❌ | ✅ (reference ke playbook) |
| **Architecture decision** | ✅ decision-log.md | ✅ ADR | ✅ (repo + org context) |
| **Process documentation** | ❌ | ✅ docs/02-workflow/ | ❌ |
| **Quick reference** | ✅ glossary.md | ❌ | ❌ |
| **Learning path** | ❌ | ✅ docs/06-learning-path/ | ❌ |
| **Personal notes** | ✅ PERSONAL/ | ❌ | ❌ |

---

## 🎯 Key Differences Deep Dive

### 1. Scope & Granularity

**OpenKB:**
```
Scope:      Single repository
Granularity: Very specific (repo context)
Example:    "Database connection string di repo core"
Lifespan:   Sama dengan repo
```

**Playbook:**
```
Scope:      Entire organization
Granularity: General (org-wide)
Example:    "Git workflow untuk semua repo"
Lifespan:   Sama dengan organization
```

---

### 2. Git Tracking

**OpenKB:**
```git
.openkb/
  SHARED/      → Tracked (committed)
  PERSONAL/    → Gitignored (local only)
  TEMPLATE.md  → Tracked
```

**Playbook:**
```git
playbook/
  docs/        → Fully tracked
  templates/   → Fully tracked
  adr/         → Fully tracked
  Everything   → Tracked
```

---

### 3. Audience

**OpenKB:**
```
Primary:   AI Agents (via .opencode/)
Secondary: Human Developers (quick reference)
Tertiary:  New members (repo context)
```

**Playbook:**
```
Primary:   Human team members
Secondary: Leadership (quality audit)
Tertiary:  AI Agents (general context)
```

---

### 4. Content Type

**OpenKB:**
```
- Glossary (istilah spesifik repo)
- References (link internal docs)
- Decision log (per repo decisions)
- Personal notes (not tracked)
- AI instructions (behavior)
```

**Playbook:**
```
- Onboarding guides
- Workflow documentation
- SOP (Standard Operating Procedures)
- Templates (user story, issue, PR)
- Learning paths
- Project plans
- ADR (Architecture Decision Record)
```

---

### 5. Maintenance

**OpenKB:**
```
Owner:     Repo lead / tech lead
Update:    Per sprint (atau sesuai need)
Review:    Sprint retrospective
Lifecycle: Sama dengan repo
```

**Playbook:**
```
Owner:     Organization lead (Sandikodev)
Update:    Continuous (PR dari partner)
Review:    Quarterly audit
Lifecycle: Sama dengan organization
```

---

## 💡 Real-World Example: SMA UII Yogyakarta

### Implementation

```
SMA UII Ecosystem:

GitHub Organization: SMA-UII-Yogyakarta
├── Repository: aksesekolah (monorepo entrypoint)
│   ├── README.md
│   │   └── Link ke: github.com/SMA-UII-Yogyakarta/playbook
│   │
│   ├── .opencode/
│   │   ├── opencode.json
│   │   │   └── references.playbook: "../aksesekolah/docs"
│   │   └── SHARED/
│   │       ├── project-context.md
│   │       └── agent-rules.md
│   │
│   ├── .openkb/
│   │   ├── TEMPLATE.md
│   │   ├── SHARED/
│   │   │   ├── glossary.md
│   │   │   ├── references.md
│   │   │   └── decision-log.md
│   │   │       └── "Decision: Monorepo dengan submodule"
│   │   └── PERSONAL/
│   │       ├── sandikodev/
│   │       │   └── profile.md (gitignored)
│   │       └── ahmad-hanif/
│   │           └── profile.md (gitignored)
│   │
│   └── docs/
│       └── 01-brief-project.md
│
├── Repository: core (backend Laravel)
│   ├── README.md
│   │   └── Link ke: github.com/SMA-UII-Yogyakarta/playbook
│   │
│   ├── .opencode/
│   │   └── ... (sama dengan aksesekolah)
│   │
│   └── .openkb/
│       └── ... (sama dengan aksesekolah)
│
└── Repository: playbook (standalone)
    ├── README.md
    ├── docs/
    │   ├── 01-getting-started/
    │   ├── 02-workflow/
    │   ├── 03-sop/
    │   ├── 04-templates/
    │   ├── 05-adr/
    │   ├── 06-learning-path/
    │   └── 07-project/
    ├── templates/
    └── LICENSE
```

---

### Workflow Example: New Developer (Fathan)

**Step 1: Organization Onboarding**
```
1. HR invite ke GitHub org SMA-UII-Yogyakarta
2. Fathan accept invitation
3. Fathan clone github.com/SMA-UII-Yogyakarta/playbook
4. Baca docs/01-getting-started/onboarding.md
5. Follow checklist (setup GitHub, enable 2FA, etc)
```

**Step 2: Repository Onboarding**
```
1. Fathan clone github.com/SMA-UII-Yogyakarta/core
2. Baca README.md
3. Click link ke playbook
4. Baca docs/01-getting-started/environment-setup.md
5. Setup Laragon, PHP, MySQL, Node.js
6. Baca .openkb/SHARED/glossary.md (istilah spesifik core)
7. Buat .openkb/PERSONAL/fathan/profile.md (local notes)
```

**Step 3: First Task**
```
1. Fathan baca docs/02-workflow/git-github-workflow.md
2. Understand branching strategy
3. Create branch: feature/12-login-page
4. Coding dengan AI assist (GitHub Copilot)
5. AI baca .opencode/ + .openkb/ untuk context
6. Commit dengan conventional commit
7. Create PR dengan template dari playbook
```

**Result:**
- ✅ Fathan onboarded dalam 2 hari
- ✅ Context lengkap (general dari playbook, specific dari .openkb)
- ✅ AI assist context-aware
- ✅ Knowledge retained (playbook + .openkb SHARED)
```

---

## 📈 Evolution

### OpenKB Roadmap

```
v1.0 (Current):
✅ SHARED/ + PERSONAL/ structure
✅ TEMPLATE.md
✅ Glossary, references, decision-log
✅ Implementation di SMA UII repos

v2.0 (Planned):
📝 Open specification (public repo)
📝 Tooling (CLI untuk generate .openkb/)
📝 AI Agent integration (standard protocol)
📝 Adoption di partner lain
```

### Playbook Roadmap

```
v1.0 (Current):
✅ Master playbook (konxc/playbook)
✅ Partner playbook (SMA-UII-Yogyakarta/playbook)
✅ Workspace structure (git submodules)
✅ Quality standard

v2.0 (Planned):
📝 More partners (5+ by EOY 2026)
📝 Automated quality audit
📝 Playbook generator (template)
📝 Certification program
```

---

## 🎓 FAQ

### Q: Kenapa tidak gabung saja OpenKB dan Playbook?

**A:** Karena purpose dan scope berbeda.

```
OpenKB = Repository-specific, AI-focused
Playbook = Organization-wide, human-focused

Gabung = Too coupled, hard to maintain
```

**Analogy:**
```
OpenKB = Personal notebook (per kelas)
Playbook = University handbook (untuk semua jurusan)
```

---

### Q: Apakah OpenKB wajib di setiap repo?

**A:** Ya, untuk repo yang menggunakan AI Agent.

```
Jika repo pakai AI assist (Copilot, dll):
✅ Wajib ada .openkb/ + .opencode/

Jika repo tidak pakai AI:
❌ Tidak perlu .openkb/
✅ Cukup link ke playbook di README
```

---

### Q: Apakah Playbook wajib untuk setiap partner?

**A:** Ya, ini requirement partnership dengan Koneksi.

```
New partner checklist:
1. Create {org}/playbook repo
2. Follow structure template
3. Link ke master playbook (konxc/playbook)
4. Add workspace submodule
5. Quality audit (pass > 70%)
```

---

### Q: Siapa yang maintain OpenKB?

**A:** Tech lead / repo lead untuk masing-masing repo.

```
Responsibilities:
- Update glossary (ada istilah baru)
- Document decisions (ADR alternative)
- Review PERSONAL/ structure (optional)
- Ensure links valid
```

---

### Q: Siapa yang maintain Playbook?

**A:** Organization lead (Sandikodev) dengan kontribusi dari partner.

```
Responsibilities:
- Review PR dari partner
- Quarterly audit
- Update templates
- Quality assurance
```

---

## 📚 References

### Internal
- [`philosophy.md`](01-philosophy.md) — Why playbook-based development
- [`workspace-structure.md`](03-workspace-structure.md) — Git submodule pattern
- SMA-UII-Yogyakarta/playbook — Reference implementation

### External
- [OpenKB Specification](https://github.com/sandikodev/openkb) (TBD)
- [Knowledge Management Best Practices](https://www.atlassian.com/knowledge-management)

---

**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev  
**Version:** 1.0.0