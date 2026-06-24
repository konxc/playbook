# Quality Standard — Playbook Audit Checklist

> Ensuring consistency and quality across all partner playbooks.

---

## 🎯 Audit Overview

**Purpose:** Ensure semua partner playbook memenuhi minimum quality standard Koneksi.

**Frequency:** Quarterly (Q1, Q2, Q3, Q4)

**Auditor:** Sandikodev

**Scoring:**
- 90-100%: Excellent ✅
- 70-89%: Good ⚠️
- < 70%: Need Improvement ❌

---

## 📊 Section 1: Documentation Completeness (25%)

### 1.1 README.md (5%)

```markdown
❌ 0%: No README
⚠️ 2%: README exists but minimal
✅ 5%: README complete dengan:
   - Vision & mission
   - Team structure
   - Quick start guide
   - Links to key docs
   - Contact info
```

---

### 1.2 Getting Started (5%)

```markdown
Required docs:
❌ 0%: No docs
⚠️ 3%: 1-2 docs present
✅ 5%: All 3 docs present:
   - onboarding.md
   - environment-setup.md
   - team-roles.md

Quality check:
✅ Step-by-step instructions
✅ Screenshots/code examples
✅ Troubleshooting section
✅ Links to resources
```

---

### 1.3 Workflow Documentation (5%)

```markdown
Required docs:
❌ 0%: No docs
⚠️ 3%: 1-2 docs present
✅ 5%: All 3 docs present:
   - git-github-workflow.md
   - project-management.md (Trello/GitHub Projects)
   - communication.md

Quality check:
✅ Clear workflow diagrams
✅ Examples & templates
✅ Best practices
✅ Common issues & solutions
```

---

### 1.4 SOP (5%)

```markdown
Required docs:
❌ 0%: No docs
⚠️ 3%: 1-2 docs present
✅ 5%: All 3 docs present:
   - code-review.md
   - deployment.md
   - testing.md

Quality check:
✅ Checklist-driven
✅ Quality criteria defined
✅ Metrics tracked
✅ Continuous improvement
```

---

### 1.5 Templates (5%)

```markdown
Required templates:
❌ 0%: No templates
⚠️ 3%: 1-2 templates
✅ 5%: All 4 templates:
   - user-story.md
   - github-issue.md
   - pull-request.md
   - sprint-planning.md

Quality check:
✅ Ready-to-use (copy-paste)
✅ Examples included
✅ Instructions clear
✅ Regularly updated
```

---

## 📊 Section 2: Implementation (25%)

### 2.1 Git Workflow (10%)

```markdown
✅ Branch Protection (4%)
   - main branch protected
   - Require PR before merge
   - Require 1+ approval
   - Include administrators

✅ Commit Quality (3%)
   - Conventional commits used
   - Descriptive messages
   - No "fix bug", "update code"

✅ PR Process (3%)
   - PR template used
   - Code review conducted
   - CI checks passing
   - Merge strategy consistent
```

---

### 2.2 Documentation Usage (10%)

```markdown
✅ Onboarding Followed (4%)
   - New members use onboarding docs
   - Environment setup successful
   - First PR merged within 3 days
   - Feedback positive

✅ Workflow Adherence (3%)
   - Git workflow followed
   - Project management tool used
   - Communication guidelines followed
   - Standup meetings held

✅ SOP Implementation (3%)
   - Code review checklist used
   - Deployment checklist used
   - Testing procedures followed
   - Incidents documented
```

---

### 2.3 Template Usage (5%)

```markdown
✅ User Stories (2%)
   - Template used consistently
   - Acceptance criteria clear
   - Priority assigned
   - Linked to issues

✅ Issues (1%)
   - Issue template used
   - Labels applied
   - Assignees set
   - Milestones tracked

✅ Pull Requests (2%)
   - PR template used
   - Description complete
   - Checklist completed
   - Reviewer tagged
```

---

## 📊 Section 3: Project Metrics (25%)

### 3.1 Velocity (10%)

```markdown
✅ Consistency (5%)
   - Sprint velocity tracked
   - Variance < 20%
   - Trend stable/improving
   
   Scoring:
   ✅ 5%: Variance < 10%
   ⚠️ 3%: Variance 10-20%
   ❌ 0%: Variance > 20%

✅ Predictability (5%)
   - Committed vs completed
   - Carry-over < 20%
   - Sprint goal achieved
   
   Scoring:
   ✅ 5%: > 90% completion
   ⚠️ 3%: 70-90% completion
   ❌ 0%: < 70% completion
```

---

### 3.2 Quality (10%)

```markdown
✅ Code Coverage (4%)
   - Unit tests written
   - Coverage tracked
   - Trend improving
   
   Scoring:
   ✅ 4%: > 80% coverage
   ⚠️ 2%: 70-80% coverage
   ❌ 0%: < 70% coverage

✅ Bug Rate (3%)
   - Bugs tracked
   - Critical bugs < 5%
   - Bug trend decreasing
   
   Scoring:
   ✅ 3%: < 3% bug rate
   ⚠️ 2%: 3-5% bug rate
   ❌ 0%: > 5% bug rate

✅ PR Review Time (3%)
   - Review time tracked
   - Average < 24 jam
   - No PR stuck > 48 jam
   
   Scoring:
   ✅ 3%: < 12 jam average
   ⚠️ 2%: 12-24 jam average
   ❌ 0%: > 24 jam average
```

---

### 3.3 Team Health (5%)

```markdown
✅ Retrospective (2%)
   - Held every sprint
   - Action items created
   - Follow-up conducted
   
   Scoring:
   ✅ 2%: Every sprint, action items tracked
   ⚠️ 1%: Most sprints, inconsistent follow-up
   ❌ 0%: Rarely or never

✅ Learning Path (3%)
   - Junior dev roadmap exists
   - Progress tracked
   - Skills improving
   
   Scoring:
   ✅ 3%: Active learning, measurable progress
   ⚠️ 2%: Roadmap exists, inconsistent progress
   ❌ 0%: No roadmap or progress
```

---

## 📊 Section 4: OpenKB Implementation (15%)

### 4.1 Structure (5%)

```markdown
✅ .openkb/ Directory (3%)
   - SHARED/ exists
   - PERSONAL/ exists (gitignored)
   - TEMPLATE.md present
   
   Scoring:
   ✅ 3%: Complete structure
   ⚠️ 1%: Partial structure
   ❌ 0%: No .openkb/

✅ SHARED/ Content (2%)
   - glossary.md
   - references.md
   - decision-log.md
   
   Scoring:
   ✅ 2%: All 3 files, updated
   ⚠️ 1%: 1-2 files, outdated
   ❌ 0%: No files
```

---

### 4.2 Usage (5%)

```markdown
✅ AI Integration (3%)
   - .opencode/ configured
   - References to playbook
   - AI-assisted development
   
   Scoring:
   ✅ 3%: Full integration, daily use
   ⚠️ 2%: Configured, occasional use
   ❌ 0%: No integration

✅ Knowledge Sharing (2%)
   - Decision log updated
   - Glossary maintained
   - References current
   
   Scoring:
   ✅ 2%: Regular updates
   ⚠️ 1%: Occasional updates
   ❌ 0%: No updates
```

---

### 4.3 Personal Notes (5%)

```markdown
✅ PERSONAL/ Structure (3%)
   - Per-user directories
   - profile.md present
   - instructions.md (optional)
   
   Scoring:
   ✅ 3%: All team members have PERSONAL/
   ⚠️ 1%: Some members only
   ❌ 0%: No PERSONAL/

✅ Quality (2%)
   - Learning notes
   - Custom instructions
   - Regular updates
   
   Scoring:
   ✅ 2%: Active usage, quality content
   ⚠️ 1%: Minimal content
   ❌ 0%: Empty or outdated
```

---

## 📊 Section 5: Continuous Improvement (10%)

### 5.1 Playbook Updates (5%)

```markdown
✅ Update Frequency (3%)
   - Updated per sprint
   - Changelog maintained
   - Version tagged
   
   Scoring:
   ✅ 3%: Regular updates, changelog
   ⚠️ 2%: Occasional updates
   ❌ 0%: No updates

✅ Quality Improvement (2%)
   - Feedback incorporated
   - Best practices added
   - Templates improved
   
   Scoring:
   ✅ 2%: Continuous improvement
   ⚠️ 1%: Some improvements
   ❌ 0%: No improvement
```

---

### 5.2 Contribution (5%)

```markdown
✅ Master Playbook Contribution (3%)
   - Share improvements
   - Report issues
   - Participate in community
   
   Scoring:
   ✅ 3%: Active contributor
   ⚠️ 2%: Occasional contributor
   ❌ 0%: No contribution

✅ Knowledge Sharing (2%)
   - Share learnings
   - Present at meetups
   - Write blog posts
   
   Scoring:
   ✅ 2%: Active sharing
   ⚠️ 1%: Occasional sharing
   ❌ 0%: No sharing
```

---

## 📈 Scoring & Certification

### Score Calculation

```
Total Score = Section1 + Section2 + Section3 + Section4 + Section5
            = 25% + 25% + 25% + 15% + 10%
            = 100%
```

---

### Certification Levels

```
🏆 Platinum (95-100%):
   - Role model for other partners
   - Can mentor new partners
   - Featured in case studies

✅ Gold (90-94%):
   - Excellent implementation
   - Certified partner
   - Renewal: 6 months

⚠️ Silver (70-89%):
   - Good implementation
   - Certified with notes
   - Renewal: 3 months

❌ Bronze (< 70%):
   - Need improvement
   - Re-audit in 2 weeks
   - Support provided
```

---

## 📝 Audit Report Template

```markdown
# Playbook Audit Report

**Partner:** {org}  
**Date:** {date}  
**Auditor:** Sandikodev

## Scores

| Section | Score | Max | % |
|---|---|---|---|
| 1. Documentation | X | 25% | X% |
| 2. Implementation | X | 25% | X% |
| 3. Project Metrics | X | 25% | X% |
| 4. OpenKB | X | 15% | X% |
| 5. Improvement | X | 10% | X% |
| **Total** | **X** | **100%** | **X%** |

## Certification Level

**Level:** {Platinum/Gold/Silver/Bronze}  
**Valid Until:** {date}

## Strengths

- Strength 1
- Strength 2
- Strength 3

## Areas for Improvement

- Area 1 (Priority: High)
- Area 2 (Priority: Medium)
- Area 3 (Priority: Low)

## Action Items

1. [ ] Action item 1 (Owner: {name}, Due: {date})
2. [ ] Action item 2 (Owner: {name}, Due: {date})
3. [ ] Action item 3 (Owner: {name}, Due: {date})

## Next Audit

**Date:** {date}  
**Focus Areas:** {areas}

---

**Signed:**
Sandikodev (Auditor)
{Partner Lead} (Partner Representative)
```

---

## 🎯 Quick Self-Assessment

### Pre-Audit Checklist

```markdown
Before formal audit, ensure:

✅ All required docs present
✅ Templates up-to-date
✅ Git workflow followed
✅ Metrics tracked
✅ .openkb/ structure complete
✅ Team interviewed
✅ Code reviewed
✅ Sprint retrospective done
```

---

### Red Flags (Automatic Fail)

```markdown
❌ No README.md
❌ No onboarding docs
❌ Git workflow not followed
❌ Code coverage < 50%
❌ Critical bugs in production
❌ .openkb/ not implemented
❌ No sprint planning
❌ Team cannot explain process
```

---

## 📚 Resources

### For Partners
- Self-assessment checklist
- Audit preparation guide
- Best practices from Platinum partners

### For Auditors
- Audit rubric (detailed scoring)
- Interview questions
- Sample audit reports

---

**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev  
**Version:** 1.0.0