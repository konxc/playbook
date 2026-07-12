# New Partner Checklist

> Step-by-step checklist untuk onboard partner baru ke Koneksi ecosystem.

---

## 📋 Checklist Overview

**Duration:** 2 minggu  
**PIC:** Sandikodev  
**Output:** Partner siap production dengan playbook complete

---

## ⚡ Partner Account Type

**Tentukan tipe akun terlebih dahulu:**

| | Organization | Personal |
|---|---|---|
| **Gunakan jika** | Tim >2 orang | Tim 1-2 orang, yayasan perorangan |
| **Contoh** | SMA-UII-Yogyakarta | pantisajadah |
| **Skip langkah** | — | Langkah bertanda `[ORG ONLY]` |

---

## ✅ Pre-Onboarding (Before Day 1)

```markdown
- [ ] Partnership agreement signed
- [ ] GitHub account created (org ATAU personal — lihat tipe di atas)
- [ ] Contact person identified
- [ ] Initial project scope defined
- [ ] Team size confirmed
- [ ] Kickoff meeting scheduled
```

---

## 📅 Week 1: Foundation

### Day 1: Repository Setup

**Organization Account:**
```markdown
- [ ] Create {org}/playbook repository
- [ ] Create {org}/.github repository (org-level templates)
- [ ] Initialize playbook dengan README.md
- [ ] Add Sandikodev sebagai collaborator
- [ ] Clone playbook repo locally
- [ ] Copy playbook structure template
- [ ] Commit initial structure
```

**Personal Account:**
```markdown
- [ ] Create {username}/playbook repository
- [ ] Create {username}/{username}.github.io repository
- [ ] Initialize playbook dengan README.md
- [ ] Add Sandikodev sebagai collaborator
- [ ] Clone playbook repo locally
- [ ] Copy playbook structure template
- [ ] Setup branch structure untuk github.io:
  - [ ] main = source code
  - [ ] handoff = onboarding documentation
  - [ ] gh-pages = build output
- [ ] Commit initial structure
```

**Template:**
```bash
# Copy dari master playbook
cp konxc/playbook/templates/docs-template/ docs/
cp konxc/playbook/templates/templates/ templates/
```

---

### Day 2: Core Documentation

```markdown
- [ ] docs/01-getting-started/onboarding.md
- [ ] docs/01-getting-started/environment-setup.md
- [ ] docs/01-getting-started/team-roles.md
- [ ] Review dengan Sandikodev
- [ ] Commit & push
```

**Tips:**
- Copy dari SMA-UII-Yogyakarta/playbook sebagai reference
- Adjust sesuai kebutuhan org
- Keep it simple (MVP first)

---

### Day 3: Workflow Documentation

```markdown
- [ ] docs/02-workflow/git-github-workflow.md
- [ ] docs/02-workflow/communication.md
- [ ] Setup GitHub Projects board
- [ ] Setup Trello board (optional)
- [ ] Commit & push
```

**Reference:**
- https://github.com/SMA-UII-Yogyakarta/playbook/tree/main/docs/02-workflow

---

### Day 4: SOP & Templates

**Organization Account:**
```markdown
- [ ] docs/03-sop/code-review.md
- [ ] docs/04-templates/github-issue.md
- [ ] docs/04-templates/pull-request.md
- [ ] Setup issue templates di {org}/.github/ISSUE_TEMPLATE/
- [ ] Setup PR template di {org}/.github/pull_request_template.md
- [ ] Commit & push
```

**Personal Account:**
```markdown
- [ ] docs/03-sop/code-review.md
- [ ] docs/04-templates/github-issue.md
- [ ] docs/04-templates/pull-request.md
- [ ] Setup issue templates di {username}/playbook/.github/ISSUE_TEMPLATE/
- [ ] Setup PR template di {username}/playbook/.github/pull_request_template.md
- [ ] Commit & push
```

---

### Day 5: OpenKB Setup

```markdown
- [ ] Create .openkb/ directory
- [ ] Create .openkb/SHARED/ directory
- [ ] Create .openkb/PERSONAL/ directory
- [ ] Add .openkb/PERSONAL/ ke .gitignore
- [ ] Create .openkb/TEMPLATE.md
- [ ] Create .openkb/SHARED/glossary.md
- [ ] Create .openkb/SHARED/references.md
- [ ] Create .openkb/SHARED/decision-log.md
- [ ] Commit & push
```

---

## 📅 Week 2: Implementation

### Day 6-7: Team Onboarding

```markdown
- [ ] Invite team members ke GitHub org
- [ ] Enable 2FA untuk semua member
- [ ] Setup WhatsApp group
- [ ] Conduct onboarding session (2 jam)
  - [ ] Playbook overview
  - [ ] OpenKB demo
  - [ ] Git workflow demo
  - [ ] Hands-on practice
- [ ] Each member creates .openkb/PERSONAL/{username}/profile.md
```

---

### Day 8: First Sprint Planning

```markdown
- [ ] Prepare product backlog
- [ ] Write user stories (minimal 5)
- [ ] Schedule sprint planning meeting
- [ ] Conduct sprint planning (90 menit)
  - [ ] Sprint goal defined
  - [ ] Tasks estimated
  - [ ] Tasks assigned
  - [ ] Team committed
- [ ] Create sprint milestone di GitHub
- [ ] Update Trello/GitHub Projects
```

---

### Day 9: First Development Day

```markdown
- [ ] Developer ambil first task
- [ ] Buat branch dari GitHub Issue
- [ ] Coding dengan AI assist (jika ada)
- [ ] Self-review sebelum PR
- [ ] Create PR dengan template
- [ ] Tag reviewer
```

---

### Day 10: Review & Retrospective

```markdown
- [ ] Code review first PR
- [ ] Merge PR (jika approved)
- [ ] Conduct sprint retrospective (60 menit)
  - [ ] What went well?
  - [ ] What to improve?
  - [ ] Action items
- [ ] Update playbook berdasarkan retrospective
- [ ] Plan sprint 2
```

---

## 🎯 Week 2 Deliverables

```markdown
✅ Playbook complete (minimal 70%)
✅ .openkb/ structure setup
✅ Team onboarded
✅ First sprint completed
✅ First PR merged
✅ Retrospective done
✅ Action items identified
```

---

## 📊 Self-Assessment (End of Week 2)

**Organization Account:**
```markdown
## Documentation
- [ ] README.md complete
- [ ] Onboarding docs written
- [ ] Workflow docs clear
- [ ] SOP documented
- [ ] Templates available

## Implementation
- [ ] {org}/.github templates setup
- [ ] .openkb/ structure setup
- [ ] Git workflow followed
- [ ] PR template used
- [ ] Code review conducted
- [ ] Sprint planning done

## Project
- [ ] Sprint 1 completed
- [ ] Velocity tracked
- [ ] Retrospective done
- [ ] Action items identified

Score: __/100%
Target: > 70%
```

**Personal Account:**
```markdown
## Documentation
- [ ] README.md complete
- [ ] Onboarding docs written
- [ ] Workflow docs clear
- [ ] SOP documented
- [ ] Templates available (di playbook/.github/)

## Implementation
- [ ] .openkb/ structure setup
- [ ] Git workflow followed
- [ ] PR template used
- [ ] Code review conducted
- [ ] Sprint planning done
- [ ] Branch structure verified (main/handoff/gh-pages)

## Infrastructure
- [ ] {username}/{username}.github.io repo exists
- [ ] Branch handoff exists dengan onboarding docs
- [ ] SSH key setup untuk akun personal
- [ ] Credential dipegang tim IT yayasan

## Project
- [ ] Sprint 1 completed
- [ ] Velocity tracked
- [ ] Retrospective done
- [ ] Action items identified

Score: __/100%
Target: > 70%
```

---

## 🏆 Certification

### Bronze Level (< 70%)
```
❌ Need improvement
⏱️ Re-audit in 2 weeks
📚 Additional support provided
```

### Silver Level (70-89%)
```
✅ Certified partner
⏱️ Renewal in 3 months
📈 Continuous improvement required
```

### Gold Level (90-94%)
```
✅ Excellent implementation
⏱️ Renewal in 6 months
🌟 Can mentor new partners
```

### Platinum Level (95-100%)
```
🏆 Role model partner
⏱️ Renewal in 12 months
📖 Featured in case studies
```

---

## 📝 Notes

**Common Pitfalls:**
- Documentation terlalu detail (keep it simple)
- Skip onboarding session (critical!)
- No retrospective (continuous improvement)
- .openkb/ tidak di-track (harus SHARED/ tracked)

**Success Factors:**
- Sandikodev mentoring (critical)
- Copy from reference (SMA UII)
- MVP approach (70% complete is OK)
- Regular check-ins (daily in week 1)

---

## 📞 Support

**Contact:**
- Sandikodev: @Sandikodev (GitHub)
- WhatsApp: [Group Link]
- Email: sandiko@koneksi.id

**Office Hours:**
- Senin-Jumat: 09:00-17:00 WIB
- Emergency: WhatsApp anytime

---

**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev  
**Version:** 1.0.0