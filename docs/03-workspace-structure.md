# Workspace Structure — Git Submodule Pattern

> Orchestrating multiple partner playbooks in one master repository.

---

## 🎯 Overview

Master playbook menggunakan **Git Submodule** untuk meng-integrasikan playbook dari semua partner Koneksi.

**Kenapa Submodule?**
- ✅ Autonomy: Setiap partner punya repo sendiri
- ✅ Versioning: Independent versioning per partner
- ✅ Ownership: Clear ownership (partner maintain sendiri)
- ✅ Sync: Easy update dari upstream
- ✅ Size: Master repo tetap kecil

---

## 📁 Directory Structure

```
konxc/playbook/
│
├── docs/                      # Master documentation
├── templates/                 # Templates untuk partner baru
│
├── workspace/                 # Partner playbooks (submodules)
│   ├── smauiiyk/              → git@github.com:SMA-UII-Yogyakarta/playbook.git
│   ├── client1/               → git@github.com:client1/playbook.git
│   ├── personal-user/         → git@github.com:Sandikodev/playbook.git
│   └── {slug}/                → git@github.com:{org-or-user}/playbook.git
│
└── .gitmodules                # Submodule configuration
```

**Naming Convention:**
- Gunakan **slug name** (lowercase, hyphen-separated)
- Untuk organization: `{org-slug}` (e.g., `smauiiyk`, `client1`)
- Untuk personal account: `{username}` (e.g., `pantisajadah`, `sandikodev`)
- Semua langsung di root `workspace/` (flat structure)

### Account Type Differences

| | Organization | Personal |
|---|---|---|
| **Profile repo** | `{org}/.github` — org profile & default repo | `{username}/{username}` — personal profile & GitHub README |
| **Playbook repo** | `{org}/playbook` | `{username}/playbook` |
| **Website repo** | `{org}/{project}.github.io` | `{username}/{username}.github.io` |
| **Workspace slug** | `{org}` | `{username}` |
| **Submodule URL** | `git@github.com:{org}/playbook.git` | `git@github.com:{username}/playbook.git` |
| **Branch (website)** | `main` + `gh-pages` | `main` + `handoff` + `gh-pages` |
| **Templates** | `{org}/.github/` (repo terpisah) | `{username}/playbook/.github/` (di playbook) |
| **Credential** | Org owner mengelola | Tim IT yayasan mengelola |

---

## 🔧 Git Submodule Commands

### Adding a New Partner

```bash
# Navigate to workspace directory
cd workspace

# Add SMA UII Yogyakarta playbook (organization)
git submodule add git@github.com:SMA-UII-Yogyakarta/playbook.git smauiiyk

# Add personal account playbook (individual)
git submodule add git@github.com:pantisajadah/playbook.git pantisajadah

# Add another client playbook
git submodule add git@github.com:client1/playbook.git client1
```

**Result:**
```
workspace/
├── smauiiyk/                  # Organization submodule
├── pantisajadah/              # Personal account submodule
└── client1/                   # Organization submodule
```

**Slug Naming:**
- `smauiiyk` → dari `github.com/SMA-UII-Yogyakarta/playbook` (org)
- `pantisajadah` → dari `github.com/pantisajadah/playbook` (personal)
- `client1` → dari `github.com/client1/playbook` (org)

---

### Cloning with Submodules

```bash
# Option 1: Clone dengan submodules langsung
git clone --recursive git@github.com:konxc/playbook.git

# Option 2: Clone biasa, lalu init submodules
git clone git@github.com:konxc/playbook.git
cd playbook
git submodule init
git submodule update
```

---

### Updating Submodules

```bash
# Update semua submodules ke latest commit
git submodule update --remote --merge

# Update submodule tertentu saja
git submodule update --remote workspace/smauiiyk

# Check status submodules
git submodule status
```

---

### Removing a Submodule

```bash
# 1. Deinit submodule
git submodule deinit workspace/smauiiyk

# 2. Remove dari .git/modules
rm -rf .git/modules/workspace/smauiiyk

# 3. Remove dari workspace
rm -rf workspace/smauiiyk

# 4. Remove dari .gitmodules
git add .gitmodules
git commit -m "Remove smauiiyk submodule"
```

---

## 📊 .gitmodules File

**Auto-generated structure:**

```ini
[submodule "workspace/smauiiyk"]
    path = workspace/smauiiyk
    url = git@github.com:SMA-UII-Yogyakarta/playbook.git
    branch = main

[submodule "workspace/orgs/client1"]
    path = workspace/orgs/client1
    url = git@github.com:client1/playbook.git
    branch = main
```

**Manual edit (optional):**
```ini
# Add custom config
[submodule "workspace/smauiiyk"]
    path = workspace/smauiiyk
    url = git@github.com:SMA-UII-Yogyakarta/playbook.git
    branch = main
    shallow = true             # Shallow clone (untuk faster setup)
    update = checkout          # Update strategy
```

---

## 🔄 Workflow Patterns

### Daily Workflow (Sandikodev)

```bash
# 1. Pull latest master playbook
git pull origin main

# 2. Update all submodules
git submodule update --remote --merge

# 3. Check submodule status
git submodule status

# 4. Make changes to master docs (if needed)
git add docs/...
git commit -m "docs: update philosophy"

# 5. Push changes
git push origin main
```

---

### Partner Update Workflow

```bash
# Scenario: SMA UII playbook updated upstream

# 1. Navigate to submodule
cd workspace/smauiiyk

# 2. Pull latest from upstream
git pull origin main

# 3. Navigate back to master
cd ../..

# 4. Commit submodule update
git add workspace/smauiiyk
git commit -m "Update SMA UII playbook to latest"

# 5. Push to master
git push origin main
```

---

### Creating a New Partner Workspace

**Organization Account:**
```bash
# 1. Partner create playbook repo di GitHub
# https://github.com/client1/playbook (new repo)

# 2. Sandikodev add submodule
cd konxc/playbook
git submodule add git@github.com:client1/playbook.git workspace/client1
git commit -m "Add client1 playbook submodule"
git push origin main

# 3. Partner clone dengan submodules
git clone --recursive git@github.com:client1/playbook.git

# 4. Partner populate playbook
# (follow playbook-structure-template.md)

# 5. Partner push ke playbook repo
git push origin main

# 6. Master playbook auto-linked (via submodule)
```

**Personal Account:**
```bash
# 1. Partner create playbook repo di GitHub
# https://github.com/username/playbook (new repo)

# 2. Partner create website repo dengan branch structure
# https://github.com/username/username.github.io
# Branch: main (source), handoff (onboarding), gh-pages (build)

# 3. Sandikodev add submodule
cd konxc/playbook
git submodule add git@github.com:username/playbook.git workspace/username
git commit -m "Add username playbook submodule"
git push origin main

# 4. Partner clone dengan submodules
git clone --recursive git@github.com:username/playbook.git

# 5. Partner populate playbook
# (follow playbook-structure-template.md — personal account section)

# 6. Partner setup credential management
# SSH key, 2FA, access control

# 7. Partner push ke playbook repo
git push origin main

# 8. Master playbook auto-linked (via submodule)
```

---

## 🎯 Best Practices

### Do's ✅

```markdown
✅ Use relative paths untuk submodule
   workspace/smauiiyk (bukan absolute path)

✅ Commit .gitmodules
   File ini penting untuk submodule tracking

✅ Update submodules regularly
   Minimal sekali per sprint

✅ Test submodule links
   Pastikan link valid sebelum commit

✅ Document submodule structure
   Update README dengan workspace info
```

---

### Don'ts ❌

```markdown
❌ Jangan edit submodule content langsung di master
   Edit di repo partner, lalu update submodule

❌ Jangan force push submodule
   Bisa break link untuk semua orang

❌ Jangan skip .gitmodules commit
   Submodule tidak akan ter-deteksi

❌ Jangan use shallow clone untuk production
   (kecuali untuk faster CI/CD)

❌ Jangan nested submodules terlalu dalam
   Max 2 levels (workspace/orgs/client)
```

---

## 🐛 Troubleshooting

### Issue: Submodule not found

**Symptom:**
```bash
$ git submodule status
fatal: No url found for submodule path 'workspace/smauiiyk' in .gitmodules
```

**Solution:**
```bash
# Check .gitmodules file
cat .gitmodules

# If missing, re-add submodule
git submodule add git@github.com:SMA-UII-Yogyakarta/playbook.git workspace/smauiiyk
git commit -m "Fix smauiiyk submodule"
```

---

### Issue: Submodule stuck at old commit

**Symptom:**
```bash
$ git submodule status
-abc123 workspace/smauiiyk (heads/main)
```

**Solution:**
```bash
# Update ke latest commit
git submodule update --remote workspace/smauiiyk

# Commit update
git add workspace/smauiiyk
git commit -m "Update smauiiyk to latest"
git push
```

---

### Issue: Can't clone with submodules

**Symptom:**
```bash
$ git clone --recursive git@github.com:konxc/playbook.git
Cloning into 'playbook'...
fatal: could not read Username for 'https://github.com': No such device or address
```

**Solution:**
```bash
# Use SSH instead of HTTPS
git clone --recursive git@github.com:konxc/playbook.git

# Or setup SSH key
ssh-keygen -t ed25519
# Add to GitHub
git config --global url."git@github.com:".insteadOf "https://github.com/"
```

---

### Issue: Submodule shows as modified

**Symptom:**
```bash
$ git status
modified:   workspace/smauiiyk (new commits)
```

**Solution:**
```bash
# Ini normal - submodule ada update dari upstream
# Update ke latest
git submodule update --remote

# Atau biarkan jika ingin tetap di commit lama
# (untuk stability)
```

---

## 📈 Scaling Strategy

### Phase 1: Single Partner (Current)

```
workspace/
└── smauiiyk/
```

**Characteristics:**
- 1 partner
- Flat structure
- Simple management

---

### Phase 2: Multiple Partners (Q3 2026)

```
workspace/
├── smauiiyk/       # SMA UII Yogyakarta (org)
├── pantisajadah/   # Panti Sajadah (personal)
├── client1/        # Client 1 (org)
└── sandikodev/     # Personal/Sandikodev
```

**Characteristics:**
- 3-5 partners (mix of org + personal)
- Flat structure (all in root workspace/)
- Slug-based naming
- Need automation

---

### Phase 3: Many Partners (2027+)

```
workspace/
├── education/
│   └── smauiiyk/
├── healthcare/
│   ├── hospital1/
│   └── clinic2/
├── enterprise/
│   └── company1/
└── personal/
    └── sandikodev/
```

**Characteristics:**
- 10+ partners
- Grouped by industry (optional)
- Flat within groups
- Full automation
```
    └── client2/
```

**Characteristics:**
- 5+ partners
- Nested structure (orgs/)
- Automation required

---

### Phase 4: Enterprise (2027+)

```
workspace/
├── education/
│   ├── smauiiyk/
│   └── school2/
├── healthcare/
│   ├── hospital1/
│   └── clinic2/
└── enterprise/
    └── company1/
```

**Characteristics:**
- Industry-based grouping
- 20+ partners
- Full automation

---

## 🔐 Security Considerations

### Access Control

```bash
# Master playbook (konxc/playbook)
- Write access: Sandikodev only
- Read access: All partners

# Partner playbook - Organization (smauiiyk/playbook)
- Write access: Partner team
- Read access: Sandikodev (audit)

# Partner playbook - Personal (pantisajadah/playbook)
- Write access: Tim IT yayasan + Sandikodev (collaborator)
- Read access: Sandikodev (audit)
```

---

### Private vs Public

```markdown
Master Playbook (konxc/playbook):
- Visibility: Public (showcase methodology)
- Submodules: Can be private or public

Partner Playbook (Organization):
- Visibility: Private (client confidentiality)
- Exception: Open source clients can be public

Partner Playbook (Personal):
- Visibility: Private (default)
- Website repo ({username}.github.io): Public (untuk GitHub Pages)
```

---

### SSH Key Management

```bash
# Generate separate keys for different accounts
ssh-keygen -t ed25519 -f ~/.ssh/id_konxc
ssh-keygen -t ed25519 -f ~/.ssh/id_smauii
ssh-keygen -t ed25519 -f ~/.ssh/id_pantisajadah

# Add to respective GitHub accounts
# ~/.ssh/config:

Host github.com-konxc
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_konxc

Host github.com-smauii
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_smauii

Host github.com-pantisajadah
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_pantisajadah
```

---

## 📊 Metrics

### Submodule Health

```bash
# Check all submodules status
git submodule status

# Output format:
# -abc123 workspace/smauiiyk (not initialized)
# +def456 workspace/smauiiyk (new commits)
#  789ghi workspace/smauiiyk (up to date)

# Legend:
# - : Not initialized
# + : Has new commits
# (space) : Up to date
```

---

### Update Frequency

| Partner | Last Update | Status |
|---|---|---|
| SMA UII Yogyakarta | Daily | ✅ Active |
| Client 1 | TBD | 📝 Coming Soon |

**Target:** All partners update至少 weekly

---

## 📚 Resources

### Git Submodule Documentation
- [Official Git Docs](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
- [Atlassian Git Submodules](https://www.atlassian.com/git/tutorials/git-submodule)
- [GitHub Submodules](https://docs.github.com/en/repositories/working-with-files/managing-large-files/about-git-submodules)

### Internal References
- [`onboarding-partner.md`](04-onboarding-partner.md) — Partner onboarding checklist
- [`quality-standard.md`](05-quality-standard.md) — Quality audit

---

**Last Updated:** Juni 2026  
**Maintained by:** Sandikodev  
**Version:** 1.0.0