# Configuration GitHub — BookLM-Orchestrator Repository

Voici toutes les informations à renseigner sur la page "Create a new repository" de GitHub :

---

## CHAMPS PRINCIPAUX

### 1. **Repository name**
```
booklm-orchestrator
```
*(court, minuscules, tirets à la place des espaces)*

### 2. **Description** (facultatif mais recommandé)
```
Claude Code skill that intelligently segments courses and generates optimized instructions for BookLM (podcasts, slides, study guides, flashcards, videos). Co-created for educational content generation.
```

### 3. **Visibility**
- ✅ **Public** (tu veux le partager publiquement sur le registry skills)

### 4. **Initialize this repository with:**

#### ☑️ Add a README file
- ✅ OUI (important pour expliquer rapidement à quoi ça sert)

#### ☑️ Add .gitignore
- Template : **Python** (si tu vas avoir du code Python pour l'analyse, sinon Node.js)
- Ou : **Node** (si c'est du JS)
- Ou : **Aucun** (c'est un skill purement MD, pas de code compilé)
- **Recommandation** : Python ou aucun

#### ☑️ Choose a license
- ✅ OUI, ajoute une licence
- **Recommandée** : **MIT License** (libre d'utilisation, largement acceptée pour les skills open-source)
- Alternative : **Apache 2.0** (si tu veux plus de protection légale)

---

## CHAMPS AVANCÉS (si disponibles)

### 5. **Add .gitignore template**
Si tu choisis :
- **Python** : ignorera `__pycache__/`, `.env`, `venv/`, etc.
- **Node** : ignorera `node_modules/`, `.env`, `dist/`, etc.

### 6. **Choose a license**
**Sélectionne : MIT License**

Texte standard MIT :
```
MIT License

Copyright (c) 2026 Yoann CRAMATTE, Grand Belfort DEE-GDU

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, and/or sell copies of the
Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## STRUCTURE INITIALE (À ajouter après création)

Une fois le repo créé, tu auras :
```
booklm-orchestrator/
├── README.md              (déjà créé par GitHub)
├── LICENSE                (déjà créé si tu choisis MIT)
├── .gitignore             (optionnel)
├── SKILL.md               (tu ajoutes)
├── DOCUMENTATION.md       (tu ajoutes)
├── CHANGELOG.md           (tu ajoutes)
│
├── src/                   (tu crées)
│   ├── analyzer.md
│   ├── segmenter.md
│   ├── instruction-generator.md
│   ├── format-handler.md
│   └── utils.md
│
├── examples/              (tu crées)
│   ├── example-input-course.md
│   ├── example-output-podcasts.md
│   └── ...
│
├── templates/             (tu crées)
│   ├── instruction-podcast.md
│   ├── instruction-slides.md
│   └── ...
│
└── guides/                (tu crées)
    ├── GETTING_STARTED.md
    ├── BEST_PRACTICES.md
    └── TROUBLESHOOTING.md
```

---

## TAGS & TOPICS (optionnel mais recommandé)

Si tu veux que le repo soit découvrable, ajoute des "Topics" :

```
booklm
claude-code
skill
educational-technology
course-structure
podcast-generation
learning-paths
artificial-intelligence
```

---

## PARAMÈTRES REPOSITORY (Après création)

### Visibility
- ✅ Public

### About section (éditable après création)
- **Description** : "AI-powered course segmentation and BookLM instruction generator"
- **Website** : (laisser vide ou ajouter un lien vers ta page)
- **Topics** : ajoute ceux listés ci-dessus

### Collaborators & teams (optionnel)
- Ajoute collaborateurs si besoin (ou reste solo)

### Branch protection rules (optionnel)
- Pas critique pour un skill en développement initial

---

## CHECKLIST AVANT DE CRÉER

- [ ] Nom : `booklm-orchestrator` ✓
- [ ] Visibility : Public ✓
- [ ] Initialize with README : OUI ✓
- [ ] Add .gitignore : OUI (Python ou Node) ✓
- [ ] Add LICENSE : OUI (MIT) ✓
- [ ] Description : remplie ✓

---

## APRÈS CRÉATION : Étapes suivantes

1. **Clone** le repo localement :
   ```bash
   git clone https://github.com/[TON_USERNAME]/booklm-orchestrator.git
   cd booklm-orchestrator
   ```

2. **Ajoute les fichiers** (SKILL.md, DOCUMENTATION.md, structure src/, examples/, templates/, guides/)

3. **Commit initial** :
   ```bash
   git add .
   git commit -m "Initial commit: BookLM-Orchestrator specification and structure"
   git push origin main
   ```

4. **Create** un dossier `.claude/` dans le repo :
   ```bash
   mkdir .claude
   touch .claude/CLAUDE.md
   ```
   
   Dans `.claude/CLAUDE.md`, ajoute :
   ```markdown
   # BookLM-Orchestrator Development Context

   ## Project Goal
   Intelligent course segmentation and BookLM instruction generation skill.

   ## Key Resources
   - `/SKILL.md` - Skill declaration
   - `/DOCUMENTATION.md` - Full technical documentation
   - `/src/` - Core logic files
   - `/templates/` - Instruction templates

   ## Skills Used During Creation
   - Skill Creator Skill
   - Speechify/TTS Optimization Skill
   - Educational Formalization Skill
   ```

5. **Push** et commence le développement dans Claude Code

---

## EXEMPLE DE GITHUB URL

Une fois créé, ton repository sera à :
```
https://github.com/[TON_USERNAME]/booklm-orchestrator
```

Par exemple, si ton username GitHub est `ycramatte` :
```
https://github.com/ycramatte/booklm-orchestrator
```

---

## NOTES

- **Collaborateur** : C'est toi qui crées le repo dans ton compte GitHub personnel ou d'organisation
- **License** : MIT permet que d'autres utilisent le skill librement
- **Public** : Permet aux gens de le découvrir et de l'installer via `npx skills add`
- **README** : Sera la première chose que les gens voient — garde-le clair et accueillant

---

*Créé pour BookLM-Orchestrator Skill Project*
*Juin 2026*
