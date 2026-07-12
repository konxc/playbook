# GitHub Ecosystem — Mitra Digital

> Dokumen lengkap mengenai kewajiban, struktur, dan pengelolaan akun GitHub mitra di bawah Software House Agency & Agency Digital PT Koneksi Jaringan Indonesia.

---

## 0. Preamble

Setiap mitra yang bekerja sama dengan PT Koneksi Jaringan Indonesia — baik itu yayasan, sekolah, organisasi, maupun entitas lainnya — **wajib** memiliki akun GitHub yang dikelola secara terstruktur, jelas, dan transparan.

Ini bukan sekadar formalitas. Ini adalah **bentuk pertanggungjawaban teknis** dari Koneksi sebagai Software House Agency yang menangani ekosistem digital mitra.

Dokumen ini menjelaskan secara lengkap:
- Mengapa akun GitHub wajib ada
- Bagaimana struktur akun dan repo yang benar
- Apa perbedaan antara akun personal dan organisasi
- Bagaimana branch strategy bekerja
- Bagaimana website resmi dan halaman handoff/onboarding bisa hidup dalam satu repo
- Opsi deployment untuk website mitra

---

## 1. Mengapa Akun GitHub Wajib?

### 1.1 Pertanggungjawaban Teknis

Koneksi tidak bekerja secara asal-asalan. Setiap proyek yang dikerjakan di bawah Koneksi — baik itu website yayasan, aplikasi donasi, sistem manajemen sekolah, atau apapun — harus memiliki jejak digital yang bisa dipertanggungjawabkan.

Akun GitHub mitra adalah **single source of truth** untuk:
- Source code seluruh proyek digital mitra
- Dokumentasi teknis (playbook, SOP, onboarding)
- Riwayat perubahan (git history) yang tidak bisa diubah
- Transparansi pengelolaan teknis

### 1.2 Transparansi & Kepercayaan

Ketika yayasan seperti Yayasan Panti Sajadah menerima donasi dari publik, donatur berhak tahu bahwa pengelolaan dilakukan secara profesional. Akun GitHub yang rapi dan terstruktur adalah bukti konkret bahwa:
- Tim IT yayasan serius dalam mengelola aset digital
- Seluruh proyek memiliki dokumentasi yang bisa diaudit
- Handoff/onboarding dilakukan secara terstruktur
- Tidak ada yang disembunyikan dari publik

### 1.3 Knowledge Retention

Salah satu risiko terbesar dalam pengelolaan teknis yayasan adalah **kehilangan pengetahuan** ketika tim IT berganti. Dengan akun GitHub yang proper:
- Seluruh history perubahan tersimpan selamanya
- Dokumentasi tidak hilang ketika orang keluar
- New team bisa langsung produktif dengan membaca playbook
- Tidak ada "bus factor" — pengetahuan ada di repo, bukan di kepala satu orang

---

## 2. Kewajiban Akun GitHub

### 2.1 Email Teknis

Setiap akun GitHub mitra **wajib** dibuat menggunakan email teknis khusus milik yayasan/organisasi terkait.

**Aturan:**
- Email teknis harus email resmi yayasan (bukan email pribadi teknisi)
- Email teknis **TIDAK BOLEH** dipublikasikan secara eksplisit di manapun
- Email teknis hanya digunakan untuk:
  - Login ke akun GitHub
  - Notifikasi GitHub
  - Recovery akun
- Password / 2FA dipegang oleh tim IT yayasan (bukan individu tunggal)

**Contoh:**
```
✅ BENAR: yayasan.sajadah01@gmail.com (email teknis, tidak dipublikasikan)
❌ SALAH: john.doe@gmail.com (email pribadi teknisi)
❌ SALAH: info@sajadah.or.id (email publik, bukan untuk GitHub)
```

### 2.2 Akun GitHub

Akun GitHub harus berupa salah satu dari dua tipe:
1. **Organization Account** (`{org}`) — diutamakan
2. **Personal Account** (`{username}`) — alternatif untuk tim kecil

**Pemilihan tipe akun bergantung pada:**
- Jumlah tim teknis yang mengelola
- Struktur organisasi yayasan
- Kebutuhan akses dan permissions

### 2.3 Collaborator Access

Sandikodev (Koneksi) **wajib** memiliki akses sebagai collaborator ke seluruh repo mitra. Ini bukan untuk mengambil alih, melainkan untuk:
- Audit berkala
- Mentoring teknis
- Emergency support
- Onboarding/ handoff documentation

---

## 3. Tipe Akun GitHub

### 3.1 Organization Account (`{org}`)

**Kapan digunakan:**
- Tim teknis > 2 orang
- Ada struktur organisasi yang jelas (PM, BA, Dev, QA)
- Yayasan/organisasi besar dengan multiple proyek

**Contoh real:**
- `https://github.com/SMA-UII-Yogyakarta` — SMA UII Yogyakarta
- `https://github.com/ITIF-Syuhada` — IT IF Syuhada
- `https://github.com/konxc` — PT Koneksi Jaringan Indonesia

**Karakteristik:**
- Bisa menginvite multiple members
- Bisa set role (Owner, Member, Collaborator)
- Bisa punya org-level profile (`.github` repo)
- Permissions lebih granular

### 3.2 Personal Account (`{username}`)

**Kapan digunakan:**
- Tim teknis 1-2 orang
- Yayasan perorangan atau kecil
- Belum ada struktur org formal

**Contoh real:**
- `https://github.com/pantisajadah` — Yayasan Panti Sajadah
- `https://github.com/amalshalih` — Amal Shalih
- `https://github.com/klubfisika` — Klub Fisika

**Karakteristik:**
- Satu orang = satu akun
- Profile personal (bukan org-level)
- Tidak bisa invite members (hanya add collaborator ke repo)
- Simpel, cocok untuk tim kecil

### 3.3 Decision Tree

```
Partner punya tim > 2 orang?
│
├── YA → Organization Account
│   ├── Buat org di github.com/orgs/new
│   ├── Required repos:
│   │   ├── {org}/.github          (org profile)
│   │   ├── {org}/playbook         (engineering playbook)
│   │   └── {org}/{project}        (website/aplikasi)
│   ├── Branch structure:
│   │   ├── main                   (source code)
│   │   └── gh-pages               (build output)
│   └── Templates di: {org}/.github/
│
└── TIDAK → Personal Account
    ├── Pakai akun personal partner
    ├── Required repos:
    │   ├── {username}/{username}       (personal profile)
    │   ├── {username}/playbook         (engineering playbook)
    │   └── {username}/{username}.github.io  (website resmi + onboarding)
    ├── Branch structure:
    │   ├── main                   (source code website)
    │   ├── handoff                (onboarding/handoff docs)
    │   └── gh-pages               (build output)
    └── Templates di: {username}/playbook/.github/
```

---

## 4. Repository Wajib

### 4.1 Organization Account

| Repo | Visibility | Purpose |
|---|---|---|
| `{org}/.github` | Public | Org profile, README, org-level templates (ISSUE_TEMPLATE, PR template) |
| `{org}/playbook` | Private | Engineering playbook — SOP, workflow, onboarding docs |
| `{org}/{project}` | Public/Private | Website resmi / aplikasi mitra |

### 4.2 Personal Account

| Repo | Visibility | Purpose |
|---|---|---|
| `{username}/{username}` | Public | Personal profile — README yang muncul di github.com/{username} |
| `{username}/playbook` | Private | Engineering playbook — SOP, workflow, onboarding docs |
| `{username}/{username}.github.io` | Public | Website resmi mitra + halaman onboarding/handoff |

### 4.3 Penjelasan Tiap Repo

#### `{username}/{username}` (Personal Account) atau `{org}/.github` (Organization)

Ini adalah **profile repo** — repo yang README-nya otomatis muncul di halaman profil GitHub.

**Organization (`{org}/.github`):**
- Berisi README.md yang menjelaskan tentang organisasi
- Bisa berisi org-level issue/PR templates
- Default repo untuk semua new repos di org
- Menjadi halaman "profil" organisasi di GitHub

**Personal (`{username}/{username}`):**
- Berisi README.md yang menjelaskan tentang yayasan/organisasi
- Muncul di `github.com/{username}` sebagai profil
- Bisa berisi links ke website, playbook, donasi, dll
- Pengganti `{org}/.github` untuk personal account

**Contoh isi README.md profil:**
```markdown
# Yayasan Panti Sajadah

> Sadaqah Jariyah Dambaan Ummah — Technopreneur Qur'ani

## Tentang Kami

Yayasan yang bergerak di bidang pendidikan dan sosial, dengan fokus pada
pemberdayasan anak yatim dan dhuafa.

## Links

- [Website Resmi](https://pantisajadah.github.io)
- [Playbook](https://github.com/pantisajadah/playbook)
- [Donasi](https://donasi.sajadah.or.id)

## Contact

📧 yayasan.sajadah01@gmail.com
📱 +62 831-4645-2122
```

#### `{username}/playbook` atau `{org}/playbook`

Repo ini adalah **engineering playbook** — dokumen hidup yang berisi seluruh SOP, workflow, dan panduan teknis untuk tim.

**Visibility:** Private (default) — hanya tim internal dan collaborator yang bisa akses.

**Isi wajib:**
```
playbook/
├── README.md
├── LICENSE
├── .gitignore
├── .github/                    ← Templates (personal) atau reference ke {org}/.github (org)
│   ├── ISSUE_TEMPLATE/
│   │   ├── feature-request.md
│   │   └── bug-report.md
│   └── pull_request_template.md
├── docs/
│   ├── 01-getting-started/     ← Onboarding, setup, roles
│   ├── 02-workflow/            ← Git workflow, project management
│   ├── 03-sop/                 ← Code review, deployment, testing
│   ├── 04-templates/           ← User story, issue, PR templates
│   ├── 05-adr/                 ← Architecture Decision Records
│   ├── 06-learning-path/       ← Junior developer roadmap
│   └── 07-project/             ← Project-specific plans
├── .openkb/                    ← Knowledge base untuk AI context
│   ├── SHARED/
│   └── PERSONAL/               ← gitignored
└── templates/
```

**Catatan penting:**
- Repo playbook ini yang di-link sebagai submodule ke master playbook (`konxc/playbook/workspace/{slug}`)
- Repo ini harus selalu up-to-date karena menjadi acuan seluruh tim
- Sandikodev memiliki akses sebagai collaborator untuk audit dan mentoring

#### `{username}/{username}.github.io` atau `{org}/{project}.github.io`

Ini adalah **website resmi mitra** sekaligus **halaman onboarding/handoff**.

**Visibility:** Public (wajib untuk GitHub Pages).

**Dual-purpose design:**
1. **Branch `main`** → Source code website resmi ( Astro.js, Next.js, dll)
2. **Branch `handoff`** → Dokumentasi onboarding/handoff teknis
3. **Branch `gh-pages`** → Build output untuk GitHub Pages deployment

**Mengapa dual-purpose?**
- Satu repo, dua fungsi — efisien dan mudah dikelola
- Website resmi dan onboarding docs saling terhubung
- Tim IT bisa switch antara website development dan onboarding docs
- Semua terpusat di satu tempat

---

## 5. Branch Strategy

### 5.1 Organization Account

```
{org}/{project}.github.io
├── main          ← Source code (development)
└── gh-pages      ← Build output (production)
```

**Sederhana:** hanya 2 branch karena onboarding docs di `{org}/.github` atau `{org}/playbook`.

### 5.2 Personal Account

```
{username}/{username}.github.io
├── main          ← Source code website (development)
├── handoff       ← Onboarding/handoff documentation
└── gh-pages      ← Build output (production)
```

**3 branch karena:**
- `main` = tempat development website utama
- `handoff` = dokumentasi onboarding yang bisa diakses publik
- `gh-pages` = output build untuk deployment

### 5.3 Penjelasan Tiap Branch

#### Branch `main`

Source code website resmi mitra. Ini adalah branch development utama.

**Konten:**
- Source code website (Astro.js, Next.js, Hugo, dll)
- Konfigurasi build (package.json, astro.config.mjs, dll)
- Static assets (images, fonts, icons)
- Content (markdown, MDX, dll)

**Deploy trigger:** Push ke `main` → GitHub Actions build → deploy ke `gh-pages` (atau Vercel/Cloudflare)

#### Branch `handoff`

Dokumentasi onboarding/handoff teknis untuk tim IT yayasan.

**Konten:**
- `HANDOFF.md` — Dokumentasi lengkap untuk tim baru
- `ONBOARDING.md` — Step-by-step onboarding
- Architecture diagrams
- Credential handoff checklist
- Environment setup guide

**Akses:** Publik — siapapun bisa membaca bagaimana teknis yayasan dikelola.

**Mengapa branch terpisah?**
- Website dan onboarding docs punya audience berbeda
- Website untuk publik, onboarding untuk tim teknis
- Update website tidak mengganggu onboarding docs
- Tim baru bisa langsung baca handoff tanpa perlu clone repo

#### Branch `gh-pages`

Build output untuk deployment GitHub Pages.

**Konten:**
- Static HTML/CSS/JS hasil build
- Optimized images
- Sitemap
- RSS feed

**Deploy trigger:** Push ke `gh-pages` → GitHub Pages serve

---

## 6. GitHub Pages Deployment

### 6.1 Settings di GitHub

Halaman settings untuk GitHub Pages:
`https://github.com/{mitra}/{mitra}.github.io/settings/pages`

**Build and deployment:**
```
Source: Deploy from a branch
Branch: gh-pages / / (root)
```

Atau jika menggunakan CI/CD:

```
Source: GitHub Actions
Workflow: (pilih workflow yang sesuai)
```

### 6.2 Deploy from Branch

Menggunakan branch `gh-pages` sebagai sumber deployment.

**Setup:**
```bash
# 1. Build project ke local dist/
bun run build

# 2. Copy output ke branch gh-pages
git checkout gh-pages
git rm -rf .
cp -r dist/* .
git add .
git commit -m "deploy: update build output"
git push origin gh-pages

# 3. Kembali ke main
git checkout main
```

**GitHub Pages Settings:**
- Source: `Deploy from a branch`
- Branch: `gh-pages` / `/ (root)`

**Kelebihan:**
- Simple, tidak perlu CI/CD pipeline
- Langsung dari branch
- Mudah di-debug

**Kekurangan:**
- Manual build (kecuali di-automate via GitHub Actions)
- Build output ada di repo (bisa besar)

### 6.3 GitHub Actions (Recommended)

Menggunakan GitHub Actions untuk automasi build dan deploy.

**Contoh workflow:**
```yaml
# .github/workflows/deploy.yml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: oven-sh/setup-bun@v1
      - run: bun install
      - run: bun run build
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - id: deployment
        uses: actions/deploy-pages@v3
```

**GitHub Pages Settings:**
- Source: `GitHub Actions`

**Kelebihan:**
- Fully automated
- Build output tidak di-commit ke repo
- Parallel builds, caching, dll
- Professional workflow

**Kekurangan:**
- Perlu setup workflow
- GitHub Actions minutes terbatas (free tier: 2000 min/month)

### 6.4 Custom Domain

Untuk website resmi yayasan, disarankan menggunakan custom domain.

**Contoh:**
- `pantisajadah.github.io` → `sajadah.or.id`
- `smauiiyk.github.io` → `sma-uii-yogya.sch.id`

**Setup:**
1. Tambahkan file `CNAME` di repo root:
   ```
   sajadah.or.id
   ```

2. Set DNS di domain registrar:
   ```
   Type: A
   Name: @
   Value: 185.199.108.153

   Type: A
   Name: @
   Value: 185.199.109.153

   Type: A
   Name: @
   Value: 185.199.110.153

   Type: A
   Name: @
   Value: 185.199.111.153

   Type: CNAME
   Name: www
   Value: {username}.github.io
   ```

3. Tunggu DNS propagation (5-30 menit)

4. Enable HTTPS di GitHub Pages settings

### 6.5 Alternatif Deployment

GitHub Pages bukan satu-satunya opsi. Website mitra bisa di-deploy di:

| Platform | Type | Kelebihan | Cocok Untuk |
|---|---|---|---|
| **GitHub Pages** | Static | Gratis, simple, integrated | Website statis, JAMStack |
| **Vercel** | Edge/Serverless | Gratis tier, edge functions, analytics | Fullstack, serverless |
| **Cloudflare Pages** | Edge | Gratis, cepat, Workers integration | Static + edge |
| **Cloudflare Workers** | Serverless | Gratis tier, global edge | API, fullstack |
| **Netlify** | Static/Serverless | Gratis, form handling, identity | Static sites |
| **Self-hosted VPS** | Docker | Full control, unlimited | Custom needs |
| **cPanel Hosting** | Shared | Murah, familiar | PHP, Node.js (terbatas) |

**Rekomendasi per tipe mitra:**
- **Yayasan kecil (1-2 tim):** GitHub Pages (gratis, simpel)
- **Yayasan menengah (3-5 tim):** Vercel atau Cloudflare Pages
- **Organisasi besar:** Self-hosted VPS atau Vercel Pro

**Catatan:** Website bisa dimulai dari GitHub Pages, lalu dimigrate ke platform lain jika kebutuhan bertambah. Yang penting source code tetap di GitHub.

---

## 7. Contoh Struktur — Yayasan Panti Sajadah

### 7.1 Akun

```
github.com/pantisajadah (Personal Account)
├── Email: yayasan.sajadah01@gmail.com (TEKNIS, tidak dipublikasikan)
├── Password: dipegang tim IT
└── 2FA: aktif
```

### 7.2 Repos

```
github.com/pantisajadah
├── pantisajadah/                    ← Profile repo (public)
│   └── README.md                   ← Profil yayasan, links, contact
│
├── playbook/                       ← Engineering playbook (private)
│   ├── README.md
│   ├── docs/
│   │   ├── 01-getting-started/
│   │   ├── 02-workflow/
│   │   ├── 03-sop/
│   │   └── ...
│   └── .github/
│       └── ISSUE_TEMPLATE/
│
├── pantisajadah.github.io/         ← Website resmi + onboarding (public)
│   ├── main                        ← Source code (Astro.js)
│   ├── handoff                     ← Onboarding docs (HANDOFF.md)
│   └── gh-pages                    ← Build output (HTML/CSS/JS)
│
└── donasi/                         ← Aplikasi donasi (private)
    └── ...                         ← Qwik + Turso + Midtrans
```

### 7.3 Master Playbook Link

```
konxc/playbook/workspace/pantisajadah/
└── → git@github.com:pantisajadah/playbook.git (submodule)
```

### 7.4 Branch Flow

```
pantisajadah.github.io
│
├── main (development)
│   ├── astro.config.mjs
│   ├── src/pages/
│   ├── src/content/
│   └── public/
│
├── handoff (onboarding)
│   ├── HANDOFF.md
│   ├── ONBOARDING.md
│   └── docs/
│
└── gh-pages (production)
    ├── index.html
    ├── *.html
    └── _astro/
```

---

## 8. Contoh Struktur — SMA UII Yogyakarta

### 8.1 Akun

```
github.com/SMA-UII-Yogyakarta (Organization Account)
├── Owner: Sandikodev
├── Members: Tim IT SMA UII
└── Visibility: Public
```

### 8.2 Repos

```
github.com/SMA-UII-Yogyakarta
├── .github/                        ← Org profile (public)
│   └── README.md                   ← Profil organisasi
│
├── playbook/                       ← Engineering playbook (private)
│   ├── docs/
│   └── .github/
│
├── core/                           ← Backend Laravel
├── aksesekolah/                    ← Monorepo entrypoint
├── smauiiyk.github.io/            ← Website SMA
└── ...
```

### 8.3 Master Playbook Link

```
konxc/playbook/workspace/smauiiyk/
└── → git@github.com:SMA-UII-Yogyakarta/playbook.git (submodule)
```

---

## 9. Contoh Struktur — Mitra Lain

### Yayasan Amal Shalih

```
github.com/amalshalih (Personal Account)
├── amalshalih/                     ← Profile repo
├── playbook/                       ← Engineering playbook
└── amalshalih.github.io/          ← Website resmi
    ├── main
    ├── handoff
    └── gh-pages
```

### IT IF Syuhada

```
github.com/ITIF-Syuhada (Organization Account)
├── .github/                        ← Org profile
├── playbook/                       ← Engineering playbook
├── syuhada.github.io/             ← Website resmi
│   ├── main
│   └── gh-pages
└── ...
```

### Klub Fisika

```
github.com/klubfisika (Personal Account)
├── klubfisika/                     ← Profile repo
├── playbook/                       ← Engineering playbook
└── klubfisika.github.io/          ← Website resmi
    ├── main
    ├── handoff
    └── gh-pages
```

### Yayasan UII Yogyakarta

```
github.com/Yayasan-UII (Organization Account)
├── .github/                        ← Org profile
├── playbook/                       ← Engineering playbook
├── yayasan-uii.github.io/         ← Website resmi
│   ├── main
│   └── gh-pages
└── ...
```

### Yayasan Masjid Syuhada Yogyakarta

```
github.com/Masjid-Syuhada (Organization Account)
├── .github/                        ← Org profile
├── playbook/                       ← Engineering playbook
├── masjid-syuhada.github.io/     ← Website resmi
│   ├── main
│   └── gh-pages
└── ...
```

---

## 10. Workflow — Dari Nol Sampai Deploy

### 10.1 Timeline

```
Hari 1:
├── Buat akun GitHub (org/personal)
├── Buat email teknis yayasan
├── Setup 2FA
└── Buat repo wajib (profile, playbook, website)

Hari 2-3:
├── Setup branch structure (main, handoff, gh-pages)
├── Clone repos locally
├── Generate SSH key
└── Setup SSH config

Hari 4-5:
├── Copy playbook template
├── Mulai populate documentation
├── Setup GitHub Actions workflow
└── Deploy website pertama

Minggu 2-4:
├── Isi playbook documentation
├── Develop website
├── Setup custom domain
└── Handoff ke tim IT yayasan
```

### 10.2 Step-by-Step

#### Step 1: Buat Email Teknis

```bash
# Buat email teknis yayasan (contoh: Gmail)
# Email ini HANYA untuk GitHub, tidak untuk publik

# Contoh:
# yayasan.sajadah01@gmail.com  (untuk Pantai Sajadah)
# amalshalih.it@gmail.com      (untuk Amal Shalih)
```

#### Step 2: Buat Akun GitHub

```bash
# Buka https://github.com
# Klik "Sign up"
# Masukkan email teknis + password
# Verify email
# Setup 2FA (wajib!)
```

#### Step 3: Buat Repos Wajib

```bash
# Untuk Personal Account:

# 1. Profile repo
#    Name: {username}/{username}
#    Visibility: Public

# 2. Playbook repo
#    Name: {username}/playbook
#    Visibility: Private

# 3. Website repo
#    Name: {username}/{username}.github.io
#    Visibility: Public
```

#### Step 4: Setup Branch Structure

```bash
# Clone website repo
git clone git@github.com:{username}/{username}.github.io.git
cd {username}.github.io

# Branch main sudah default

# Buat branch handoff
git checkout -b handoff
# Tambahkan HANDOFF.md
git add . && git commit -m "docs: add handoff documentation"
git push -u origin handoff

# Kembali ke main
git checkout main
```

#### Step 5: Setup Deployment

```bash
# Option A: GitHub Actions (recommended)
mkdir -p .github/workflows
# Buat file deploy.yml (lihat Section 6.3)

# Option B: Manual deploy ke gh-pages
git checkout --orphan gh-pages
git rm -rf .
# Copy build output
git add . && git commit -m "deploy: initial build"
git push -u origin gh-pages
git checkout main
```

#### Step 6: Link ke Master Playbook

```bash
# Sandikodev yang melakukan:
cd konxc/playbook
git submodule add git@github.com:{username}/playbook.git workspace/{username}
git commit -m "Add {username} playbook submodule"
git push origin main
```

#### Step 7: Add Collaborator

```bash
# Di GitHub:
# Settings → Manage access → Invite member
# Masukkan username Sandikodev
# Role: Collaborator (atau Member untuk org)
```

---

## 11. Credential Management

### 11.1 Yang Wajib Dipegang Tim IT

| Item | Pemegang | Catatan |
|---|---|---|
| Email teknis | Tim IT | Jangan dipublikasikan |
| Password GitHub | Tim IT | Gunakan password manager |
| 2FA codes | Tim IT | Backup codes disimpan aman |
| SSH private key | Tim IT | Jangan commit ke repo |
| Domain registrar access | Tim IT | Untuk DNS management |

### 11.2 Yang Bisa Diberikan ke Koneksi

| Item | Akses | Catatan |
|---|---|---|
| GitHub collaborator | Write access | Untuk audit & mentoring |
| Repository access | Read/Write | Sesuai kebutuhan |
| Deployment access | View only | Untuk monitoring |

### 11.3 SSH Key Setup

```bash
# Generate SSH key khusus untuk akun mitra
ssh-keygen -t ed25519 -f ~/.ssh/id_{username} -C "tech@{org-domain}"

# Tambahkan ke SSH config
cat >> ~/.ssh/config << EOF
Host github.com-{username}
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_{username}
EOF

# Tambahkan public key ke GitHub
cat ~/.ssh/id_{username}.pub
# Copy output → GitHub Settings → SSH Keys → Add
```

### 11.4 gh CLI Setup

```bash
# Install gh CLI (jika belum)
# https://cli.github.com/

# Login dengan akun mitra
GH_CONFIG_DIR=~/.config/gh-{username} gh auth login

# Gunakan prefix untuk setiap command
GH_CONFIG_DIR=~/.config/gh-{username} gh repo list
```

---

## 12. Access Control Matrix

### 12.1 Per Repo

| Repo | Tim IT | Sandikodev | Publik |
|---|---|---|---|
| `{username}/{username}` | Read/Write | Read | Read |
| `{username}/playbook` | Read/Write | Read/Write | ❌ |
| `{username}/{username}.github.io` (main) | Read/Write | Read/Write | Read |
| `{username}/{username}.github.io` (handoff) | Read/Write | Read/Write | Read |
| `{username}/{username}.github.io` (gh-pages) | Read/Write | Read | Read |

### 12.2 Per Branch

| Branch | Tim IT | Sandikodev | GitHub Pages | Publik |
|---|---|---|---|---|
| `main` | Read/Write | Read/Write | — | Read |
| `handoff` | Read/Write | Read/Write | — | Read |
| `gh-pages` | Read/Write | Read | Serve | Read |

---

## 13. Troubleshooting

### 13.1 Website Tidak Muncul di GitHub Pages

**Ceklist:**
- [ ] Repo visibility = Public
- [ ] Branch `gh-pages` ada dan berisi `index.html`
- [ ] GitHub Pages enabled di Settings
- [ ] Source branch = `gh-pages`
- [ ] Custom domain (jika ada) sudah dikonfigurasi

### 13.2 Build Gagal di GitHub Actions

**Ceklist:**
- [ ] Workflow file ada di `.github/workflows/`
- [ ] `bun` atau `node` sudah di-setup di workflow
- [ ] `bun install` berhasil
- [ ] `bun run build` berhasil
- [ ] Output directory (`dist/` atau `build/`) benar

### 13.3 SSH Key Tidak Bekerja

```bash
# Test koneksi
ssh -T git@github.com-{username}

# Jika gagal, cek:
# 1. Public key sudah ditambahkan ke GitHub
# 2. SSH config benar
# 3. Private key permissions (600)
chmod 600 ~/.ssh/id_{username}
```

### 13.4 Submodule Tidak Terdeteksi

```bash
# Di master playbook
git submodule init
git submodule update

# Jika masih gagal
git submodule update --init --recursive
```

---

## 14. Maintenance

### 14.1 Weekly

- [ ] Update playbook documentation
- [ ] Check GitHub Actions status
- [ ] Review open issues/PRs

### 14.2 Monthly

- [ ] Audit access control
- [ ] Update dependencies
- [ ] Review deployment logs

### 14.3 Quarterly

- [ ] Full quality audit (lihat `05-quality-standard.md`)
- [ ] Review branch strategy
- [ ] Update credential rotation
- [ ] Backup important data

---

## 15. Referensi

### 15.1 Internal

| Dokumen | Lokasi | Description |
|---|---|---|
| [`01-philosophy.md`](01-philosophy.md) | `docs/` | Mengapa playbook-based development |
| [`03-workspace-structure.md`](03-workspace-structure.md) | `docs/` | Git submodule workspace pattern |
| [`04-onboarding-partner.md`](04-onboarding-partner.md) | `docs/` | Checklist onboarding partner |
| [`05-quality-standard.md`](05-quality-standard.md) | `docs/` | Quality audit checklist |

### 15.2 External

- [GitHub Docs — Repositories](https://docs.github.com/en/repositories)
- [GitHub Docs — GitHub Pages](https://docs.github.com/en/pages)
- [GitHub Docs — Organizations](https://docs.github.com/en/organizations)
- [GitHub Docs — SSH Keys](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)

---

**Last Updated:** Juli 2026
**Maintained by:** Sandikodev
**Version:** 1.0.0
**Status:** Active — Live document yang akan terus di-update seiring bertambahnya mitra
