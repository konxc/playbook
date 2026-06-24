# Partner Onboarding Checklist

> Step-by-step guide untuk onboard partner baru ke Koneksi ecosystem.

---

## 📋 Pre-Onboarding

### Requirements (Must Have)

```markdown
✅ Partner organization created di GitHub
✅ Minimal 1 repo aktif (project repo)
✅ Contact person identified (PM/tech lead)
✅ Partnership agreement signed
✅ Initial project scope defined
```

### Nice to Have

```markdown
⚪ Existing documentation
⚪ Previous playbook (jika ada)
⚪ Established workflow
⚪ Team structure defined
```

---

## 🚀 Onboarding Process

### Phase 1: Initial Setup (Day 1-2)

#### Step 1: Create Partner Playbook Repo

**PIC:** Sandikodev

```bash
# 1. Partner buat repo baru di GitHub
# Name: {org}/playbook
# Visibility: Private (default)
# Description: "Engineering playbook for {org}"

# 2. Initialize dengan README
echo "# {org} Playbook" > README.md
echo "" >> README.md
echo "> Engineering guidelines untuk tim {org}" >> README.md

# 3. Push ke GitHub
git init
git add README.md
git commit -m "Initial commit"
git remote add origin git@github.com:{org}/playbook.git
git push -u origin main
```

---

#### Step 2: Add to Master Workspace

**PIC:** Sandikodev

```bash
# Navigate to master playbook
cd konxc/playbook

# Add submodule
git submodule add git@github.com:{org}/playbook.git workspace/orgs/{org-slug}

# Commit
git add .gitmodules workspace/orgs/{org-slug}
git commit -m "Add {org} playbook submodule"
git push origin main
```

---

#### Step 3: Invite to Koneksi Organization

**PIC:** Sandikodev

```
1. Go to: https://github.com/orgs/konxc/people
2. Click "Invite member"
3. Enter GitHub username of partner lead
4. Set role: Member
5. Send invitation
```

---

### Phase 2: Playbook Setup (Day 3-5)

#### Step 4: Copy Playbook Structure Template

**PIC:** Partner Lead

```bash
# Clone partner playbook
git clone git@github.com:{org}/playbook.git
cd playbook

# Copy template dari master playbook
cp ../konxc/playbook/templates/playbook-structure-template.md .
cp -r ../konxc/playbook/templates/docs-template/ docs/

# Commit structure
git add .
git commit -m "Setup initial playbook structure"
git push origin main
```

---

#### Step 5: Populate Core Documentation

**PIC:** Partner Lead + Sandikodev (mentoring)

**Priority Order:**
```
Week 1:
✅ docs/01-getting-started/onboarding.md
✅ docs/01-getting-started/environment-setup.md
✅ docs/01-getting-started/team-roles.md

Week 2:
✅ docs/02-workflow/git-github-workflow.md
✅ docs/02-workflow/communication.md

Week 3:
✅ docs/03-sop/code-review.md
✅ docs/04-templates/pull-request.md

Week 4:
✅ docs/07-project/project-overview.md
✅ docs/07-project/sprint-1-plan.md
```

---

#### Step 6: Setup .openkb/ Structure

**PIC:** Partner Tech Lead

```bash
# Create .openkb structure
mkdir -p .openkb/SHARED
mkdir -p .openkb/PERSONAL

# Create TEMPLATE.md
cat > .openkb/TEMPLATE.md << 'EOF'
# {org} Knowledge Base

## Structure
- SHARED/ → Tracked knowledge base
- PERSONAL/ → Gitignored personal notes
EOF

# Create SHARED files
cat > .openkb/SHARED/glossary.md << 'EOF'
# Glossary

## Project-Specific Terms
- Term 1: Definition
- Term 2: Definition
EOF

# Add to git
git add .openkb/
git commit -m "Setup .openkb structure"
git push origin main
```

---

### Phase 3: Team Onboarding (Week 2)

#### Step 7: Onboard Team Members

**PIC:** Partner Lead

**Checklist:**
```markdown
✅ Invite all team members to GitHub org
✅ Enable 2FA untuk semua member
✅ Setup WhatsApp group untuk tim
✅ Jadwalkan onboarding session
✅ Distribute onboarding checklist
```

**Onboarding Session Agenda:**
```
Duration: 2 jam
Attendees: All team members

Agenda:
1. Introduction to Playbook (30 menit)
2. OpenKB overview (30 menit)
3. Git workflow demo (30 menit)
4. Q&A + hands-on practice (30 menit)
```

---

#### Step 8: First Sprint Planning

**PIC:** Sandikodev (facilitator) + Partner Lead

**Preparation:**
```markdown
✅ Product backlog ready (Trello/GitHub Issues)
✅ User stories written (minimal 5)
✅ Acceptance criteria defined
✅ Team capacity calculated
```

**Meeting Agenda:**
```
Duration: 90 menit

1. Sprint Goal (10 menit)
2. Backlog Review (20 menit)
3. Estimation (30 menit)
4. Task Assignment (20 menit)
5. Commitment (10 menit)
```

**Output:**
```markdown
✅ Sprint goal defined
✅ Tasks assigned
✅ Sprint backlog created
✅ Team committed
```

---

### Phase 4: Quality Audit (Week 4)

#### Step 9: Self-Assessment

**PIC:** Partner Lead

**Checklist:**
```markdown
## Documentation
- [ ] README.md complete
- [ ] Onboarding docs written
- [ ] Workflow docs clear
- [ ] SOP documented
- [ ] Templates available

## Implementation
- [ ] .openkb/ structure setup
- [ ] .opencode/ configured (jika pakai AI)
- [ ] Git workflow followed
- [ ] PR template used
- [ ] Code review conducted

## Project
- [ ] Sprint 1 completed
- [ ] Velocity tracked
- [ ] Retrospective done
- [ ] Action items identified
```

---

#### Step 10: Formal Audit

**PIC:** Sandikodev

**Audit Process:**
```markdown
1. Review self-assessment (30 menit)
2. Check playbook completeness (1 jam)
3. Interview team members (30 menit)
4. Review code quality (1 jam)
5. Generate audit report (30 menit)
```

**Scoring:**
```
90-100%: Excellent ✅ (certified)
70-89%:  Good ⚠️ (certified with notes)
< 70%:   Need Improvement ❌ (re-audit in 2 weeks)
```

---

## 📊 Post-Onboarding

### Month 1 Check-in

**Agenda:**
```markdown
✅ Review sprint velocity
✅ Check documentation quality
✅ Identify blockers
✅ Plan improvements
```

**Metrics:**
```
- Sprint velocity: Target 10-15 pts/sprint
- Code coverage: Target > 70%
- PR review time: Target < 24 jam
- Team satisfaction: Target > 4.0/5.0
```

---

### Quarter 1 Audit

**Comprehensive Review:**
```markdown
✅ Playbook updated?
✅ Process followed?
✅ Quality maintained?
✅ Team growing?
✅ Customer satisfied?
```

**Output:**
```markdown
✅ Q1 audit report
✅ Improvement plan
✅ Q2 goals
✅ Certification renewal (if passed)
```

---

## 🎯 Success Criteria

### Immediate (Week 1)

```markdown
✅ Playbook repo created
✅ Structure template copied
✅ .openkb/ setup
✅ Team invited
```

### Short-term (Month 1)

```markdown
✅ First sprint completed
✅ Documentation 70%+ complete
✅ Team onboarded
✅ First audit passed (> 70%)
```

### Long-term (Quarter 1)

```markdown
✅ Consistent velocity
✅ Quality audit > 80%
✅ Team independent
✅ Customer satisfied
```

---

## 📝 Templates

### Invitation Email Template

```
Subject: Welcome to Koneksi Ecosystem - {org} Onboarding

Dear {Partner Name},

Welcome to the Koneksi ecosystem! We're excited to have you as a partner.

Next Steps:
1. Create GitHub organization: {org}
2. Create playbook repo: {org}/playbook
3. Invite Sandikodev as collaborator
4. Schedule kickoff meeting: [Calendar Link]

Resources:
- Partner Onboarding Guide: [Link]
- Playbook Template: [Link]
- OpenKB Documentation: [Link]

Looking forward to our partnership!

Best regards,
Sandikodev
Founder, PT Koneksi Jaringan Indonesia
```

---

### Kickoff Meeting Agenda

```
Duration: 2 jam
Attendees: Sandikodev, Partner Lead, Tech Lead

Agenda:
1. Introduction (15 menit)
2. Koneksi Philosophy (30 menit)
3. Playbook Overview (30 menit)
4. OpenKB Demo (30 menit)
5. Q&A (15 menit)

Preparation:
- Partner: Prepare questions
- Sandikodev: Prepare demo environment
```

---

## 🐛 Common Issues

### Issue: Partner overwhelmed dengan documentation

**Solution:**
```markdown
✅ Break down into smaller tasks
✅ Prioritize: Onboarding docs first
✅ Provide templates (copy-paste friendly)
✅ Schedule weekly check-ins
✅ Pair writing session (Sandikodev + Partner)
```

---

### Issue: Team resistance to new process

**Solution:**
```markdown
✅ Explain "why" (philosophy session)
✅ Show benefits (metrics from other partners)
✅ Start small (gradual adoption)
✅ Celebrate quick wins
✅ Address concerns individually
```

---

### Issue: Playbook becomes outdated

**Solution:**
```markdown
✅ Assign documentation owner
✅ Review per sprint (retrospective)
✅ Update as part of DoD
✅ Automate where possible
✅ Quarterly audit
```

---

## 📚 Resources

### For Partners
- [`playbook-structure-template.md`](../templates/playbook-structure-template.md)
- [`quality-standard.md`](05-quality-standard.md)
- SMA-UII-Yogyakarta/playbook (reference)

### For Sandikodev
- Onboarding checklist (this doc)
- Audit rubric (quality-standard.md)
- Master playbook (this repo)

---

**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev  
**Version:** 1.0.0