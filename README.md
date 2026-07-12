# KONXCI Playbook — Master Engineering Guidelines

> **Orchestrating excellence across all partner engineering teams.**

**Version:** 1.0.0  
**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev (Founder, PT Koneksi Jaringan Indonesia)

---

## 🎯 Vision

**KONXCI Playbook** adalah master playbook yang meng-orchestrate seluruh engineering playbook partner Koneksi.

> "We don't just build software. We build **repeatable systems** that build **exceptional software**."

### Core Philosophy

1. **Consistency Over Heroics** — Sistem yang baik mengalahkan individual heroics
2. **Documentation as Code** — Dokumentasi adalah first-class citizen
3. **Knowledge Retention** — Knowledge tidak boleh hilang saat orang keluar
4. **Scalable Onboarding** — New member produktif dalam < 1 minggu
5. **AI-Human Collaboration** — OpenKB untuk AI context, Playbook untuk human guidelines

---

## 🏗️ Architecture

```
konxc/playbook (Master)
│
├── docs/                      # Master documentation
│   ├── philosophy.md          # Why playbook-based development
│   ├── openkb-vs-playbook.md  # Perbedaan mendasar
│   ├── workspace-structure.md # Git submodule pattern
│   ├── onboarding-partner.md  # Checklist partner baru
│   └── quality-standard.md    # Audit checklist
│
├── workspace/                 # Partner playbooks (git submodules)
│   ├── smauiiyk/              → SMA-UII-Yogyakarta/playbook
│   ├── client1/               → client1/playbook
│   ├── {org-slug}/            → {org-or-user}/playbook
│   └── ...                    → Future partners
│
└── templates/                 # Templates untuk partner baru
    ├── new-partner-checklist.md
    └── playbook-structure-template.md
```

**Workspace Naming:**
- Flat structure (semua di root `workspace/`)
- Slug-based: `{org-slug}` atau `{username}`
- Organization: `smauiiyk` (dari `SMA-UII-Yogyakarta`)
- Personal: `pantisajadah` (dari GitHub username)

---

## 📚 What's Inside

### [docs/](docs/) — Master Documentation

| Document | Description | For |
|---|---|---|
| [`philosophy.md`](docs/01-philosophy.md) | Why playbook-based development | Leadership |
| [`openkb-vs-playbook.md`](docs/02-openkb-vs-playbook.md) | OpenKB vs Playbook comparison | All members |
| [`workspace-structure.md`](docs/03-workspace-structure.md) | Git submodule workspace pattern | Sandikodev |
| [`onboarding-partner.md`](docs/04-onboarding-partner.md) | Onboarding partner baru | Sandikodev |
| [`quality-standard.md`](docs/05-quality-standard.md) | Quality audit checklist | QA |
| [`github-ecosystem.md`](docs/06-github-ecosystem.md) | GitHub mitra — akun, repo, branch, deployment | All |

---

### [workspace/](workspace/) — Partner Playbooks

#### Current Partners

| Partner | Playbook | Account Type | Status |
|---|---|---|---|
| **SMA UII Yogyakarta** | [`smauiiyk/`](workspace/smauiiyk/) | Organization | ✅ Active (v1.0.0) |
| **Yayasan Panti Sajadah** | [`pantisajadah/`](workspace/pantisajadah/) | Personal | 🚀 Onboarding |
| **{Your Org/Personal}** | `{slug}/` | Organization/Personal | 📝 Coming Soon |

**Account Types:**
```
Organization Accounts (tim >2 orang):
├── smauiiyk/              # SMA-UII-Yogyakarta/playbook
└── {org-slug}/            # {org}/playbook

Personal Accounts (tim 1-2 orang):
├── pantisajadah/          # pantisajadah/playbook
└── {username}/            # {username}/playbook
```

**Examples:**
```
workspace/
├── smauiiyk/              # Git submodule → SMA-UII-Yogyakarta/playbook (org)
├── pantisajadah/          # Git submodule → pantisajadah/playbook (personal)
├── client1/               # Git submodule → client1/playbook (org)
└── {slug}/                # Git submodule → {org-or-user}/playbook
```

**Structure Inside Each:**
```
workspace/{slug}/
├── docs/                  # Partner-specific documentation
├── templates/             # Partner templates
├── project/               # Project-specific plans
└── README.md              # Partner overview
```

---

### [templates/](templates/) — Ready-to-use Templates

| Template | Description |
|---|---|
| [`new-partner-checklist.md`](templates/new-partner-checklist.md) | Checklist onboard partner baru |
| [`playbook-structure-template.md`](templates/playbook-structure-template.md) | Template struktur playbook |

---

## 🔑 Key Concepts

### OpenKB vs Playbook

**OpenKB** (`.openkb/`):
- **Purpose:** AI Agent-to-Human communication protocol
- **Location:** Inside every repository (core, webapp, etc.)
- **Structure:** SHARED/ (tracked) + PERSONAL/ (gitignored)
- **Focus:** Context untuk AI Agent (instructions, references, glossary)
- **Created by:** Sandikodev

**Playbook** (`{org}/playbook` repo):
- **Purpose:** Human-to-human engineering guidelines
- **Location:** Standalone repository
- **Structure:** docs/, templates/, adr/, project/
- **Focus:** Onboarding, workflow, SOP, learning path
- **Audience:** Human team members

**Integration:**
```
Repository (e.g., core)
├── .opencode/          → AI Agent config
│   └── references → Link ke playbook
│
├── .openkb/            → Knowledge base
│   └── SHARED/ → Context spesifik repo
│
└── README.md
    └── Link ke {org}/playbook → Guidelines umum
```

---

### Workspace Pattern

**Git Submodule Strategy:**

```bash
# Add partner playbook sebagai submodule
git submodule add git@github.com:SMA-UII-Yogyakarta/playbook.git workspace/smauiiyk

# Update submodule
git submodule update --remote --merge

# Clone dengan submodules
git clone --recursive git@github.com:konxc/playbook.git
```

**Benefits:**
- ✅ Setiap partner punya autonomy
- ✅ Versioning independent
- ✅ Update tanpa break partner lain
- ✅ Clear ownership

---

## 🚀 Quick Start

### Untuk Leadership (Sandikodev)

1. Baca [`philosophy.md`](docs/01-philosophy.md)
2. Onboard partner baru: [`onboarding-partner.md`](docs/04-onboarding-partner.md)
3. Quality audit: [`quality-standard.md`](docs/05-quality-standard.md)

### Untuk Partner Engineer

1. Clone master playbook:
   ```bash
   git clone --recursive git@github.com:konxc/playbook.git
   ```

2. Baca workspace partner Anda:
   ```bash
   cd workspace/smauiiyk
   cat README.md
   ```

3. Follow partner-specific onboarding

### Untuk Product Analyst

1. Pahami perbedaan OpenKB vs Playbook
2. Setup `.openkb/` di setiap repo
3. Link ke playbook di README

---

## 📊 Partner Lifecycle

```
1. Discovery
   └─ Initial contact
   └─ Requirement gathering

2. Onboarding
   └─ Setup workspace submodule
   └─ Create {org}/playbook
   └─ Link ke master playbook

3. Development
   └─ Sprint-based delivery
   └─ Weekly sync
   └─ Quality audit

4. Handover
   └─ Documentation complete
   └─ Training
   └─ Maintenance mode
```

---

## 🎯 Quality Standards

### Minimum Playbook Requirements

Setiap partner playbook **wajib** memiliki:

```markdown
✅ README.md dengan overview
✅ docs/01-getting-started/ (onboarding, setup, roles)
✅ docs/02-workflow/ (git, project management, communication)
✅ docs/03-sop/ (code review, deployment, testing)
✅ docs/04-templates/ (user story, issue, PR)
✅ docs/05-adr/ (architecture decisions)
✅ docs/06-learning-path/ (junior developer roadmap)
✅ docs/07-project/ (project-specific plans)
```

### Audit Checklist

Full checklist di [`quality-standard.md`](docs/05-quality-standard.md)

**Scoring:**
- 90-100%: Excellent ✅
- 70-89%: Good ⚠️
- < 70%: Need Improvement ❌

---

## 👥 Organization

**PT Koneksi Jaringan Indonesia**

| Role | Person | GitHub |
|---|---|---|
| Founder & Architect | Sandikodev | [@Sandikodev](https://github.com/Sandikodev) |

**Partner Teams**

| Partner | Account Type | Project | Team Size |
|---|---|---|---|
| SMA UII Yogyakarta | Organization | SMART Absen | 4 (1 PM, 1 BA, 2 Dev) |
| Yayasan Panti Sajadah | Personal | Website + Donation App | 1-2 (IT + Sandikodev) |

---

## 🌐 Ecosystem

### Related Repositories

| Repo | Description |
|---|---|
| [`konxc/playbook`](https://github.com/konxc/playbook) | **Master Playbook** (this repo) |
| [`SMA-UII-Yogyakarta/playbook`](https://github.com/SMA-UII-Yogyakarta/playbook) | SMA UII Engineering Playbook (org) |
| [`SMA-UII-Yogyakarta/core`](https://github.com/SMA-UII-Yogyakarta/core) | Backend Laravel |
| [`SMA-UII-Yogyakarta/aksesekolah`](https://github.com/SMA-UII-Yogyakarta/aksesekolah) | Monorepo entrypoint |
| [`pantisajadah/playbook`](https://github.com/pantisajadah/playbook) | Panti Sajadah Playbook (personal) |
| [`pantisajadah/pantisajadah.github.io`](https://github.com/pantisajadah/pantisajadah.github.io) | Website Panti Sajadah (personal) |

### OpenKB Protocol

OpenKB adalah protokol knowledge base yang dikembangkan oleh Sandikodev:

- **Spec:** TBD (akan didokumentasikan di repo terpisah)
- **Implementation:** Sudah digunakan di semua repo SMA UII
- **Integration:** `.openkb/` directory di setiap repo

---

## 📈 Metrics

### Master Playbook Metrics

```
- Total partner playbooks: 1 (target: 5 by EOY 2026)
- Average quality score: TBD (first audit Q3 2026)
- Partner satisfaction: TBD (survey Q3 2026)
```

### Partner Metrics

```
SMA UII Yogyakarta:
- Team velocity: 13-14 story points/sprint
- Code coverage: > 70%
- PR review time: < 24 jam
- Bug rate: < 5%
```

---

## 🎓 Learning Resources

### Internal
- [`SMA-UII-Yogyakarta/playbook`](https://github.com/SMA-UII-Yogyakarta/playbook) — Reference implementation
- OpenKB Specification (coming soon)

### External
- [Atlassian Team Playbook](https://www.atlassian.com/team-playbook)
- [Spotify Engineering Culture](https://spotify.github.io/engineering-culture/)
- [GitLab Handbook](https://handbook.gitlab.com/)

---

## 🤝 Contributing

### Untuk Partner

Setiap partner dapat contribute ke master playbook dengan:
1. Fork repo
2. Create branch: `feature/improvement-name`
3. Commit perubahan
4. Create Pull Request
5. Review oleh Sandikodev

### Untuk Sandikodev

Direct push ke `main` diperbolehkan untuk:
- Emergency fixes
- Partner onboarding
- Quality audit updates

---

## 📞 Contact

**PT Koneksi Jaringan Indonesia**  
📧 Email: hello@koneksi.id  
📱 WhatsApp: [Contact Link](https://wa.me/...)  
🌐 Website: https://koneksi.id (coming soon)

**For Partnership:**
- Email: partnership@koneksi.id
- Subject: "Playbook Partnership Inquiry"

---

## 📄 License

**Proprietary** — PT Koneksi Jaringan Indonesia

All rights reserved.  
This playbook and its contents are confidential and intended for internal use only.

---

## 🏆 Acknowledgments

**Created by:** Sandikodev  
**Inspired by:** 
- Atlassian Team Playbook
- Spotify Engineering Culture
- GitLab Handbook
- Amazon Working Backwards

**First Partner:** SMA UII Yogyakarta  
**Implementation Date:** Juni 2026

---

**Last Updated:** Juni 2026  
**Version:** 1.0.0  
**Next Review:** Q3 2026

[See Release History](https://github.com/konxc/playbook/releases)