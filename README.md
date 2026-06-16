# BookLM-Orchestrator Skill

> Transforme ton cours en contenu pédagogique structuré — tout préparé pour BookLM.

## À quoi ça sert?

BookLM-Orchestrator analyse tes cours complets et te prépare des **instructions optimisées** pour générer automatiquement :
- 🎙️ **Podcasts** (durée cible configurable)
- 📊 **Slides/Présentations**
- 📝 **Fiches de révision**
- 🔄 **Flashcards**
- 🎬 **Vidéos pédagogiques**
- 🎯 **Mix de formats**

Chaque bloc d'instruction est prêt à **copier-coller directement dans BookLM** pour obtenir un contenu optimisé.

---

## Pour qui?

✅ **Étudiants** : Transforme tes notes de cours en podcasts pour réviser en marchant  
✅ **Enseignants** : Crée du contenu pédagogique professionnel en minutes  
✅ **Créateurs** : Produis des ressources éducatives structurées facilement  
✅ **Professionnels** : Génère de la documentation de formation rapidement  

---

## Comment ça marche?

### 1️⃣ Upload ton cours
```
PDF | DOCX | TXT | URL
```

### 2️⃣ Répondre au questionnaire
```
Format voulu?
Durée des podcasts?
Public cible?
Priorités pédagogiques?
Style conversationnel?
```

### 3️⃣ On analyse & segmente
```
✓ Structure identifiée
✓ Concepts clés extraits
✓ Segmentation optimale calculée
```

### 4️⃣ Tu reçois les blocs d'instruction
```
[PODCAST #1] Durée 35min | Chap 1-3 | Concepts: X, Y, Z
Instructions BookLM prêtes à copier-coller

[PODCAST #2] Durée 35min | Chap 4-6 | Concepts: A, B, C
...
```

### 5️⃣ Tu copies dans BookLM → Boom, contenu généré! 🎯

---

## Exemple : Avant / Après

### ❌ AVANT
```
📄 Cours "Droit de la Décentralisation" (120 pages)
→ Difficile de savoir par où commencer
→ Pas sûr comment bien structurer pour BookLM
→ Risque d'oublier des concepts clés
→ Besoin de comprendre la pédagogie
```

### ✅ APRÈS
```
📝 Segmentation complète (4 podcasts):
   - Podcast 1: Fondamentaux (35 min) — Chap 1-2
   - Podcast 2: Les trois niveaux (35 min) — Chap 3-4
   - Podcast 3: Compétences & finance (35 min) — Chap 5-6
   - Podcast 4: Défis actuels (35 min) — Chap 7-8

📋 Pour chaque podcast: bloc d'instruction prêt à copier
→ Passe-le à BookLM
→ 20 min plus tard → 4 podcasts générés!
```

---

## Installation rapide

### Avec Claude Code CLI
```bash
# Ajouter le skill
npx skills add booklm-orchestrator

# Utiliser
/booklm-orchestrator
```

### Via GitHub
```bash
git clone https://github.com/ycramatte/booklm-orchestrator.git
cd booklm-orchestrator
# Suis les instructions dans GETTING_STARTED.md
```

---

## Premiers pas

Voir [GETTING_STARTED.md](./guides/GETTING_STARTED.md) pour un walkthrough complet.

---

## Documentation

- **[SPECIFICATION.md](./SPECIFICATION.md)** — Fonctionnalités détaillées & architecture
- **[GETTING_STARTED.md](./guides/GETTING_STARTED.md)** — Premier exemple pas à pas
- **[BEST_PRACTICES.md](./guides/BEST_PRACTICES.md)** — Comment bien utiliser le skill
- **[TROUBLESHOOTING.md](./guides/TROUBLESHOOTING.md)** — Problèmes courants & solutions
- **[DOCUMENTATION.md](./DOCUMENTATION.md)** — Docs techniques complètes

---

## Formats supportés

| Format | Exemple durée | Usages typiques |
|--------|--------------|-----------------|
| **Podcast** | 25-60 min | Révision en marchant, contenu immersif |
| **Slides** | 1-2 slides/concept | Présentation rapide, examen |
| **Fiches révision** | 1 fiche/concept | Révision intensive, synthèse |
| **Flashcards** | Pair question/réponse | Mémorisation, auto-test |
| **Vidéo** | 5-15 min | Explication visuelle, tutoriel |
| **Mix** | Combinaison | Approche multi-modal complète |

---

## Paramètres configurables

```
📚 Public cible         → Licence / Master / Professionnel / Grand public
🎯 Durée podcast        → 10-15 min / 25-35 min / 40-60 min / 60+ min
🗣️ Style conversationnel → Académique / Naturel / Débat / Socratique
📊 Granularité          → Fine (+ segments) / Équilibrée / Grosse (- segments)
🌐 Langue              → Français / Anglais
```

---

## Exemples de résultats

Voir le dossier [examples/](./examples/) pour :
- Exemple de cours input
- Outputs générés (podcasts, slides, fiches)

---

## Roadmap

**Phase 1 — MVP (Août 2026)**
- ✅ Analyzer de cours
- ✅ Segmenter intelligent
- ✅ Instructions podcast optimisées

**Phase 2 — Expansion (Septembre 2026)**
- ⏳ Support Slides, Fiches, Flashcards
- ⏳ Questions interactives avancées
- ⏳ Dépendances conceptuelles

**Phase 3 — Intégration (Octobre 2026)**
- ⏳ API BookLM directe (si possible)
- ⏳ Support Vidéo
- ⏳ Analytics

**Phase 4 — Public (Novembre 2026)**
- ⏳ Registry skills officiel
- ⏳ Docs multilingues
- ⏳ Feedback utilisateurs

---

## Licence

**MIT License** — Tu es libre d'utiliser, modifier et distribuer ce skill.

```
Copyright (c) 2026 Yoann CRAMATTE, Grand Belfort DEE-GDU
```

---

## Support & Feedback

📧 Questions? Ouvre une issue sur [GitHub](https://github.com/ycramatte/booklm-orchestrator/issues)

---

**Dernière mise à jour** : Juin 2026  
**Statut** : En développement (Phase 1)
