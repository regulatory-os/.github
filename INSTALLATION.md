# 🚀 Guide d'Installation - Regulatory OS

Guide complet pour installer et déployer les outils Regulatory OS.

---

## 📦 Option 1 : Plateforme Intégrée (Recommandé)

Déployez tous les outils dans une seule application.

### 1. Cloner et Installer

```bash
# Cloner le projet principal
git clone https://github.com/regulatory-os/regulatory-os.git
cd regulatory-os

# Installer les dépendances
npm install
```

### 2. Configuration des Variables d'Environnement

Créez un fichier `.env` à la racine du projet :

```env
# Supabase - Backend
VITE_SUPABASE_URL=https://votre-project.supabase.co
VITE_SUPABASE_ANON_KEY=votre-cle-anonyme

# Admin - UUID de l'administrateur
VITE_ADMIN_UUID=votre-admin-uuid

# Cloudflare Turnstile (protection anti-bot)
VITE_TURNSTILE_SITE_KEY=votre-site-key
```

### 3. Configuration Supabase

#### 3.1. Créer un Projet Supabase

1. Aller sur https://supabase.com
2. Créer un nouveau projet
3. Récupérer l'URL et la clé anonyme dans **Settings > API**

#### 3.2. Installer Supabase CLI

```bash
# Installer Supabase CLI globalement
npm install -g supabase
```

#### 3.3. Se Connecter et Lier le Projet

```bash
# Se connecter à Supabase
supabase login

# Lier le projet local au projet Supabase
supabase link --project-ref votre-project-ref
```

#### 3.4. Appliquer les Migrations

```bash
# Appliquer les migrations de base de données
supabase db push
```

#### 3.5. Déployer les Edge Functions

```bash
# Déployer toutes les Edge Functions
supabase functions deploy mistral-admin
supabase functions deploy qualify-marketing-document --no-verify-jwt
supabase functions deploy analyze-marketing-compliance --no-verify-jwt
supabase functions deploy analyze-ict-check --no-verify-jwt
supabase functions deploy validate-file
supabase functions deploy send-contact-email
```

### 4. Obtenir les Clés API

#### 4.1. Mistral AI

**Utilisation** : SEO, traduction, GEO, audit
**Coût** : ~0.25€ / 1M tokens

1. Créer un compte sur https://console.mistral.ai/
2. Aller dans **API Keys**
3. Cliquer sur **Create new key**
4. Copier la clé

#### 4.2. Anthropic Claude

**Utilisation** : Analyse documents (ICT, Marketing)
**Coût** : ~3€ / 1M tokens input, ~15€ / 1M tokens output

1. Créer un compte sur https://console.anthropic.com/
2. Aller dans **API Keys**
3. Cliquer sur **Create Key**
4. Copier la clé

#### 4.3. Cloudflare Turnstile

**Utilisation** : Protection anti-bot
**Coût** : Gratuit

1. Créer un compte sur https://dash.cloudflare.com/
2. Aller dans **Turnstile**
3. Cliquer sur **Add Site**
4. Remplir les informations du site
5. Copier **Site Key** et **Secret Key**

#### 4.4. Supabase

**Utilisation** : Backend complet
**Coût** : Gratuit jusqu'à 500MB de base de données

Les clés sont disponibles dans votre projet Supabase :
1. Aller dans **Settings > API**
2. Copier **Project URL** et **anon public** key

### 5. Configurer les Secrets Supabase

```bash
# Clé Mistral AI (pour SEO, traduction, GEO)
supabase secrets set MISTRAL_ADMIN_API=votre-cle-mistral

# Clés Anthropic Claude (pour analyse documents)
supabase secrets set ANTHROPIC_API_KEY=votre-cle-claude
supabase secrets set ANTHROPIC_MARKETING_CHECK_API=votre-cle-claude

# Cloudflare Turnstile (protection anti-bot)
supabase secrets set TURNSTILE_SECRET_KEY=votre-secret-turnstile
```

### 6. Lancer l'Application

```bash
# Développement
npm run dev

# Production
npm run build
npm run preview
```

L'application sera disponible sur **http://localhost:5173**

---

## 🛠️ Option 2 : Outils Standalone

Déployez chaque outil indépendamment.

### ICT-Check

Audit de conformité des contrats d'externalisation ICT.

```bash
# Cloner le repository
git clone https://github.com/regulatory-os/ICT-contractuel-checks.git
cd ICT-contractuel-checks

# Installer les dépendances
npm install

# Configurer .env
# VITE_SUPABASE_URL=...
# VITE_SUPABASE_ANON_KEY=...

# Déployer la fonction Supabase
supabase functions deploy analyze-ict-check --no-verify-jwt

# Configurer le secret
supabase secrets set ANTHROPIC_API_KEY=votre-cle-claude

# Lancer
npm run dev
```

### Marketing Compliance

Vérification des contenus marketing AMF.

```bash
# Cloner le repository
git clone https://github.com/regulatory-os/marketing-compliance.git
cd marketing-compliance

# Installer les dépendances
npm install

# Configurer .env
# VITE_SUPABASE_URL=...
# VITE_SUPABASE_ANON_KEY=...

# Déployer les fonctions Supabase
supabase functions deploy qualify-marketing-document --no-verify-jwt
supabase functions deploy analyze-marketing-compliance --no-verify-jwt

# Configurer le secret
supabase secrets set ANTHROPIC_MARKETING_CHECK_API=votre-cle-claude

# Lancer
npm run dev
```

### Africa Sanctions Screening

Screening contre les listes de sanctions africaines.

```bash
# Cloner le repository
git clone https://github.com/regulatory-os/African-screening.git
cd African-screening

# Installer les dépendances
npm install

# Configurer .env
# VITE_SUPABASE_URL=...
# VITE_SUPABASE_ANON_KEY=...

# Pas besoin de clés IA (recherche locale sur datasets)

# Lancer
npm run dev
```

---

## 📊 Récapitulatif des Services & Coûts

| Service | Prix | Utilisation | Gratuit ? |
|---------|------|-------------|-----------|
| **Supabase** | Gratuit jusqu'à 500MB DB | Backend complet | ✅ (jusqu'à 500MB) |
| **Mistral AI** | ~0.25€ / 1M tokens | SEO, traduction, GEO | ❌ (pay-as-you-go) |
| **Anthropic Claude** | ~3€ / 1M input, ~15€ / 1M output | Analyse documents | ❌ (pay-as-you-go) |
| **Cloudflare Turnstile** | Gratuit | Protection anti-bot | ✅ |

### Estimation Coûts Mensuels

**Usage modéré** (100 analyses/mois) :
- Mistral AI : ~2€
- Anthropic Claude : ~10€
- Supabase : 0€ (Free tier)
- Turnstile : 0€
- **TOTAL : ~12€/mois**

**Usage intensif** (1000 analyses/mois) :
- Mistral AI : ~15€
- Anthropic Claude : ~100€
- Supabase : 0-25€ (selon usage)
- Turnstile : 0€
- **TOTAL : ~115-140€/mois**

---

## 💡 Architecture Technique

### Stack Commun

| Catégorie | Technologies |
|-----------|--------------|
| **Frontend** | React 18.3, TypeScript 5.9, Vite 7.3 |
| **UI** | Tailwind CSS 3.4, shadcn/ui, Radix UI |
| **Backend** | Supabase (PostgreSQL + Auth + Storage + Edge Functions) |
| **State** | TanStack Query, React Hook Form + Zod |
| **IA** | Mistral AI (SEO, traduction), Anthropic Claude (analyse documents) |
| **PDF** | jsPDF, pdfjs-dist, html2canvas |
| **Sécurité** | DOMPurify (XSS), Cloudflare Turnstile (anti-bot) |

### Edge Functions (Deno Runtime)

Les analyses IA longues (>30s) utilisent le **streaming NDJSON** pour éviter les timeouts Supabase (60s).

**Pattern standard** :
1. Validations synchrones (Turnstile, rate limit)
2. `createStreamResponse()` pour l'analyse
3. Heartbeats toutes les 15s pendant appels Claude
4. Événements : `start`, `step`, `batch`, `heartbeat`, `done`, `error`

**Optimisations** :
- **Prompt caching** — ~80% réduction tokens sur batches répétitifs (Marketing Compliance)
- **Batched analysis** — Traitement par lots pour grandes listes d'obligations
- **Retry logic** — Exponential backoff sur erreurs réseau

---

## 🐛 Résolution de Problèmes

### Erreur : "Supabase CLI not found"

```bash
# Installer globalement
npm install -g supabase

# Vérifier l'installation
supabase --version
```

### Erreur : "Invalid API key"

- Vérifier que la clé API est correcte
- Vérifier que le secret est bien configuré avec `supabase secrets list`
- Re-déployer la fonction après modification des secrets

### Erreur : "CORS policy"

- Vérifier que votre domaine est autorisé dans Supabase
- Aller dans **Authentication > URL Configuration**
- Ajouter votre domaine local (`http://localhost:5173`) et production

### Edge Function timeout

- Les fonctions Supabase ont un timeout de 60s
- Le streaming NDJSON permet de contourner cette limite
- Vérifier que les heartbeats sont envoyés toutes les 15s

---

## 📫 Support

**Besoin d'aide ?**

- 📖 [Documentation GitHub](https://github.com/regulatory-os/regulatory-os)
- 🐛 [Signaler un bug](https://github.com/regulatory-os/regulatory-os/issues)
- 💬 [GitHub Discussions](https://github.com/orgs/regulatory-os/discussions)
- ✉️ robin.jacquet@regulatoryos.fr
- 🌐 https://regulatoryos.fr

---

<div align="center">

**Libérez la conformité. Librement.**

Made with ❤️ by the Regulatory OS community

</div>
