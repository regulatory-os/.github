<div align="center">

# 🏛️ Regulatory OS

### Open Source Platform for Financial Compliance

**OS** = **O**pen **S**ource + **O**perating **S**ystem

*Démocratiser l'accès aux outils de conformité réglementaire financière*

[![License: AGPL-3.0](https://img.shields.io/badge/License-AGPL--3.0-blue.svg)](https://opensource.org/licenses/AGPL-3.0)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-blue)](https://www.typescriptlang.org/)
[![React](https://img.shields.io/badge/React-18.3-61dafb)](https://reactjs.org/)
[![Supabase](https://img.shields.io/badge/Supabase-Backend-green)](https://supabase.com/)

[🌐 Website](https://regulatoryos.fr) • [📖 Documentation](https://github.com/regulatory-os/regulatory-os/blob/main/CONTRIBUTING.md) • [💬 Contact](https://regulatoryos.fr/contact)

</div>

---

## 🎯 Notre Mission

Créer un véritable **"système d'exploitation"** pour la conformité réglementaire en combinant :

- 🤖 **Mini-programmes IA** — Outils de conformité propulsés par l'intelligence artificielle (Claude, Mistral)
- 📚 **Documents & Templates** — Bibliothèque de ressources réglementaires gratuites
- ✍️ **Articles de blog** — Analyses et guides sur les sujets LRCG (Legal, Risk, Compliance, Governance)

---

## 📦 Nos Repositories

### 🌐 Plateforme Principale

| Repository | Description | Tech Stack |
|------------|-------------|------------|
| **[regulatory-os](https://github.com/regulatory-os/regulatory-os)** | Plateforme web complète avec tous les outils intégrés | React + TypeScript + Supabase |

### 🛠️ Outils Standalone

| Repository | Description | Statut | Démo |
|------------|-------------|--------|------|
| **[marketing-compliance](https://github.com/regulatory-os/marketing-compliance)** | Vérification contenus marketing AMF<br/>5 référentiels, 262 obligations, workflow 3 phases | ✅ Disponible | [Essayer](https://regulatoryos.fr/tools/marketing-compliance) |
| **[ICT-contractuel-checks](https://github.com/regulatory-os/ICT-contractuel-checks)** | Audit contrats d'externalisation ICT<br/>DORA Art. 30, EBA Guidelines, Arrêté 3/11/2014 | ✅ Disponible | [Essayer](https://regulatoryos.fr/tools/ict-check) |
| **[African-screening](https://github.com/regulatory-os/African-screening)** | Screening listes sanctions africaines<br/>UEMOA, CEDEAO, Mali, Burkina Faso, Niger | ✅ Disponible | [Essayer](https://regulatoryos.fr/tools/africa-sanctions) |

### 📚 Configuration

| Repository | Description |
|------------|-------------|
| **[.github](https://github.com/regulatory-os/.github)** | Profil organisation et fichiers communautaires |

---

## 🛠️ Outils & Fonctionnalités

### 🎯 Marketing Compliance

Vérification automatisée des contenus marketing selon la réglementation AMF.

**Référentiels supportés** :
- DOC-2011-24 — Communications publicitaires placements collectifs (OPCVM, FIA, SCPI)
- DOC-2010-05 — Instruments financiers complexes (produits structurés, EMTN)
- DOC-2019-06 — Allégations ESG / extra-financières
- DOC-2017-06 — Biens divers
- ARPP-PSFI — Déontologie publicité financière

**Workflow en 3 phases** :
1. **Qualification (~5s)** — Identification type produit, textes applicables, conditions actives
2. **Révision humaine** — Correction avant analyse coûteuse
3. **Analyse complète (~60s)** — Vérification contre 262 obligations réglementaires

**Fonctionnalités** :
- Upload PDF/DOCX avec extraction OCR
- Analyse visuelle (taille polices, emplacement mentions)
- Rapport interactif avec actions correctives
- Export résultats

**[→ Essayer l'outil](https://regulatoryos.fr/tools/marketing-compliance)**

---

### 🔒 ICT-Check

Audit automatisé par IA de la conformité des contrats d'externalisation ICT.

**Référentiels** :
- DORA (Règlement UE 2022/2554) — Art. 30 sur l'externalisation
- EBA Guidelines on Outsourcing (EBA/GL/2019/02)
- Arrêté du 3 novembre 2014 (France)

**Fonctionnalités** :
- Upload PDF/DOCX (contrats jusqu'à 200 pages)
- Analyse IA avec Claude Opus 4.5
- Rapport de conformité par article
- Export PDF des résultats

**[→ Essayer l'outil](https://regulatoryos.fr/tools/ict-check)**

---

### 🌍 Africa Sanctions Screening

Screening contre les listes de sanctions africaines.

**Sources** :
- UEMOA (BCEAO) — Liste sanctions financières
- CEDEAO — Sanctions régionales
- Mali, Burkina Faso, Niger — Listes nationales

**Fonctionnalités** :
- Recherche fuzzy (tolérance fautes de frappe)
- Filtres par liste de sanctions
- Export PDF des résultats
- Mise à jour régulière des datasets

**[→ Essayer l'outil](https://regulatoryos.fr/tools/africa-sanctions)**

---

## 🚀 Démarrage Rapide

```bash
# Cloner et installer la plateforme complète
git clone https://github.com/regulatory-os/regulatory-os.git
cd regulatory-os
npm install

# Configuration requise : Supabase + API keys (Claude, Mistral)
# Voir la documentation complète pour les instructions détaillées
```

**[📖 Guide d'installation complet](https://github.com/regulatory-os/regulatory-os#-installation-complète)**

---

## 📊 Roadmap

| Module | Description | Statut |
|--------|-------------|--------|
| Marketing Compliance | Analyse AMF multi-référentiels (workflow 3 phases) | ✅ Disponible |
| ICT-Check | Audit externalisation ICT (DORA, EBA) | ✅ Disponible |
| Sanctions Screening | Listes africaines (UEMOA, CEDEAO) | ✅ Disponible |
| Veille Réglementaire | Suivi automatisé évolutions réglementaires | 🚧 En développement |
| Contrôle Interne | Cartographie des risques et contrôles | 📋 Planifié |
| AML Screening | KYC/AML avec listes internationales | 📋 Planifié |
| DORA Compliance | Suite complète outils DORA | 📋 Planifié |

---

## 💡 Stack Technique

| Catégorie | Technologies |
|-----------|--------------|
| **Frontend** | React 18.3, TypeScript 5.9, Vite 7.3 |
| **UI** | Tailwind CSS 3.4, shadcn/ui, Radix UI |
| **Backend** | Supabase (PostgreSQL + Auth + Storage + Edge Functions) |
| **State** | TanStack Query, React Hook Form + Zod |
| **IA** | Mistral AI (SEO, traduction), Anthropic Claude (analyse documents) |
| **PDF** | jsPDF, pdfjs-dist, html2canvas |
| **Sécurité** | DOMPurify (XSS), Cloudflare Turnstile (anti-bot) |

---

## 🤝 Contribuer

Les contributions sont les bienvenues ! Consultez notre [guide de contribution](https://github.com/regulatory-os/regulatory-os/blob/main/CONTRIBUTING.md).

**Comment contribuer** :

1. **Fork** le repository concerné
2. **Créer une branche** : `git checkout -b feature/amazing-feature`
3. **Commiter** : `git commit -m 'feat: add amazing feature'`
4. **Push** : `git push origin feature/amazing-feature`
5. **Ouvrir une Pull Request**

**Idées de contributions** :
- 🐛 Signaler des bugs
- 💡 Proposer de nouvelles fonctionnalités
- 📝 Améliorer la documentation
- 🌍 Ajouter des traductions
- 🔧 Optimiser le code
- 📊 Ajouter de nouveaux référentiels réglementaires
- ⭐ Donner une étoile aux projets

---

## 💼 Cas d'Usage

### Pour les Compliance Officers

- ✅ Automatiser la vérification des documents marketing
- ✅ Auditer les contrats d'externalisation ICT
- ✅ Screener contre les sanctions africaines
- ✅ Accéder à une bibliothèque de templates conformité

### Pour les Développeurs

- ✅ Intégrer les outils via API
- ✅ Déployer on-premise pour données sensibles
- ✅ Personnaliser les référentiels réglementaires
- ✅ Contribuer au projet open source

### Pour les Régulateurs

- ✅ Comprendre les outils utilisés par l'industrie
- ✅ Auditer le code source
- ✅ Proposer des améliorations réglementaires

---

## 📄 Licence & Modèle Commercial

### Licence AGPL-3.0

**Ce que vous pouvez faire** :
- ✅ Utiliser librement en interne
- ✅ Modifier et adapter le code
- ✅ Déployer on-premise dans votre infrastructure
- ✅ Auditer le code source

**Ce que vous ne pouvez pas faire** :
- ❌ Revendre comme SaaS propriétaire sans partager le code
- ❌ Redistribuer sans partager vos modifications

### Besoin d'une Licence Commerciale ?

Si vous souhaitez :
- Intégrer dans un produit propriétaire
- Revendre comme service white-label
- Support et consulting personnalisé

👉 **[Contactez-nous](https://regulatoryos.fr/contact)**

---

## 📫 Contact & Support

**Robin Jacquet** — Fondateur de Regulatory OS

- 🌐 [regulatoryos.fr](https://regulatoryos.fr)
- 💼 [LinkedIn](https://www.linkedin.com/in/robin-jacquet/)
- ✉️ robin.jacquet@regulatoryos.fr
- 💬 [GitHub Discussions](https://github.com/orgs/regulatory-os/discussions)

**Besoin d'aide ?**
- 📖 [Documentation complète](https://github.com/regulatory-os/regulatory-os/blob/main/CONTRIBUTING.md)
- 🐛 [Signaler un bug](https://github.com/regulatory-os/regulatory-os/issues)
- 💡 [Demander une feature](https://github.com/regulatory-os/regulatory-os/issues/new?labels=enhancement)

---

## 🌟 Supporters

Un grand merci à tous nos contributeurs et supporters !

[![Stargazers](https://reporoster.com/stars/regulatory-os/regulatory-os)](https://github.com/regulatory-os/regulatory-os/stargazers)

---

<div align="center">

**Libérez la conformité. Librement.**

Made with ❤️ by the Regulatory OS community

</div>
