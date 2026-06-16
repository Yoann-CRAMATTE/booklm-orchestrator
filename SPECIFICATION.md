# BookLM-Orchestrator Skill — Specification

## 1. OBJECTIF GÉNÉRAL

BookLM-Orchestrator est un skill Claude Code qui analyse des cours complets et les prépare intelligemment pour BookLM (ou tout autre LLM capable de générer contenu pédagogique). Il segmente le contenu selon les objectifs finaux de l'utilisateur (podcasts, slides, fiches révision, flashcards, vidéos), génère des instructions détaillées et prépare des blocs prêts à copier-coller directement dans BookLM pour obtenir des outputs optimisés.

**Slogan** : "Transforme ton cours en contenu pédagogique structuré — tout préparé pour BookLM."

---

## 2. WORKFLOW UTILISATEUR

L'utilisateur suit ce processus :

### Étape 1 : Upload du cours
- Utilisateur upload un PDF, DOCX, TXT ou URL vers le cours complet

### Étape 2 : Questionnaire interactif
Le skill pose des questions critiques :

```
1. Quel(s) format(s) final(aux) souhaites-tu ?
   [ ] Podcast
   [ ] Slides/Présentation
   [ ] Fiches révision
   [ ] Flashcards
   [ ] Vidéo
   [ ] Mix (podcast + slides + fiches)

2. Si podcast(s) : quelle durée cible par episode ?
   [ ] Court (10-15 min)
   [ ] Moyen (25-35 min)
   [ ] Long (40-60 min)
   [ ] Très long (60+ min)

3. Quel est le public cible ?
   [ ] Étudiants en licence
   [ ] Master/études supérieures
   [ ] Professionnels
   [ ] Grand public
   [ ] Autre (préciser)

4. Quels concepts/chapitres veux-tu prioritairement couvrir ?
   [ ] Tout le cours
   [ ] Certains chapitres (lesquels ?)
   [ ] Certaines thématiques clés (lesquelles ?)

5. Veux-tu des styles conversationnels spécifiques ?
   [ ] Académique strict
   [ ] Conversationnel naturel
   [ ] Débat/discussion
   [ ] Enseignement Socratique (questions-réponses)
```

### Étape 3 : Analyse du cours
Le skill analyse le document uploadé et :
- Identifie la structure (chapitres, sections, sous-sections)
- Extrait les concepts clés par section
- Évalue la densité pédagogique
- Détermine les dépendances conceptuelles
- Identifie les points difficiles à expliquer

### Étape 4 : Segmentation intelligente
Basé sur les réponses utilisateur, le skill segmente le cours en chunks optimisés. Par exemple :

**Si podcast 35 min cible :**
- Calcule combien de pods sont nécessaires
- Fragmente le cours pour que chaque podcast couvre une durée cohérente
- Assure que chaque segment est pédagogiquement complet

**Si slides + fiches :**
- Segmente différemment (par concept clé, par chapitre, par niveau de complexité)
- Prépare des blocs adaptés pour chaque format

### Étape 5 : Génération des instructions
Pour chaque segment, le skill génère un **bloc d'instruction** contenant :

```markdown
## PODCAST #1 : [Titre explicite du contenu]

**Durée cible** : 35 minutes
**Chapitres couverts** : Chapitre 1.1 à Chapitre 1.8 (pages 12-45)
**Audience** : Étudiants Master en Administration Publique

**Concepts clés à couvrir (par ordre d'importance)** :
1. Définition et historique de la décentralisation administrative
2. Les trois niveaux de collectivités territoriales en France
3. Principes de subsidiarité et gouvernance multi-niveaux

**Points à bien expliciter** :
- Clarifier la différence entre déconcentration et décentralisation (confusion fréquente)
- Donner 2-3 exemples concrets de compétences par niveau
- Expliquer les enjeux financiers (dotations, fiscalité propre)

**Style conversationnel** : Naturel, avec exemples concrets
**Longueur des explications** : Court-moyen (pas de dérives académiques)
**Points d'emphase** : Les différences entre niveaux, les tensions actuelles

---

**Instructions pour BookLM** :
Copie-colle ce texte dans le champ "Custom Instructions" de ton notebook BookLM :

> Focus sur les chapitres 1.1 à 1.8. Explique clairement : définition/historique de la décentralisation, les trois niveaux de collectivités (commune/département/région), principes de subsidiarité. Insiste sur les différences déconcentration vs décentralisation avec exemples. Parle des compétences par niveau et des enjeux financiers. Style conversationnel naturel. Durée cible : 35 min.
```

### Étape 6 : Livrable final
Le skill génère un document structuré contenant :
- **Liste complète des segments** (avec titres, chapitres couverts, durée, concepts)
- **Bloc d'instructions pour chaque segment** (prêt à copier-coller dans BookLM)
- **Résumé pédagogique** (pourquoi cette segmentation, dépendances entre blocs)
- **Guide d'utilisation** (comment utiliser avec BookLM, bonnes pratiques)

---

## 3. INPUTS DU SKILL

### Fichier cours
- Format accepté : PDF, DOCX, TXT, URL vers document
- Taille : jusqu'à 50 MB
- Langue : FR, EN (extensible)

### Réponses utilisateur
- Questionnaire interactif (voir Étape 2)
- Libre appréciation sur concepts prioritaires
- Préférences de style

---

## 4. OUTPUTS DU SKILL

### Format principal
Un document markdown contenant :

```
BOOKLM-ORCHESTRATOR OUTPUT
──────────────────────────

📋 RÉSUMÉ D'ANALYSE
- Nombre de pages/chapitres analysés
- Densité pédagogique estimée
- Dépendances conceptuelles identifiées
- Nombre de segments générés

🎯 SEGMENTATION PROPOSÉE
- Segment 1 : [titre] | chapitres X-Y | durée | concepts clés
- Segment 2 : [titre] | chapitres X-Y | durée | concepts clés
- ...

📝 BLOCS D'INSTRUCTIONS (Copyable)
[Pour chaque segment : instruction prête à copier-coller dans BookLM]

📚 GUIDE D'UTILISATION
[Comment utiliser les blocs, bonnes pratiques, troubleshooting]
```

### Exports optionnels
- CSV avec liste des segments (pour suivi)
- JSON avec métadonnées (pour intégrations futures)

---

## 5. PARAMÈTRES CONFIGURABLES

| Paramètre | Valeur par défaut | Options |
|-----------|------------------|---------|
| **Format final** | Podcast | Podcast, Slides, Fiches, Flashcards, Vidéo, Mix |
| **Durée podcast** | 30 min | 10-15, 25-35, 40-60, 60+ min |
| **Public cible** | Master | Licence, Master, Pro, Grand public |
| **Style conversationnel** | Naturel | Académique, Naturel, Débat, Socratique |
| **Granularité segmentation** | Équilibrée | Fine (plus de segments), Grosse (moins de segments) |
| **Langue output** | FR | FR, EN |

---

## 6. EXEMPLES CONCRETS D'UTILISATION

### Exemple 1 : Cours de Master en Droit de la Décentralisation

**Input utilisateur** :
- Cours : "Droit de la Décentralisation - Master Année 1" (120 pages)
- Formats : Podcast 35 min
- Public : Étudiants Master
- Priorité : Tout couvrir

**Output du skill** :
- 4 podcasts de ~35 min chacun
- Podcast 1 : Fondamentaux et histoire (chap 1-2)
- Podcast 2 : Les trois niveaux de collectivités (chap 3-4)
- Podcast 3 : Compétences et financements (chap 5-6)
- Podcast 4 : Défis actuels et droit comparé (chap 7-8)

Chaque podcast a un bloc d'instruction précis, prêt à BookLM.

### Exemple 2 : Cours avec Mix de formats

**Input utilisateur** :
- Cours : "Introduction aux Systèmes d'Information" (80 pages)
- Formats : Podcast 25 min + Slides + Fiches révision
- Public : Étudiants Licence

**Output du skill** :
- 3 podcasts de 25 min (segmentation conversation)
- 15 slides (1 slide par concept clé)
- 12 fiches révision (format question-réponse)

Chaque format a ses blocs d'instruction adaptés.

---

## 7. STRUCTURE TECHNIQUE DU SKILL (Fichiers)

```
booklm-orchestrator/
├── SKILL.md                    # Déclaration du skill
├── README.md                   # Guide utilisateur complet
├── SPECIFICATION.md            # Cette spécification technique
├── DOCUMENTATION.md            # Documentation technique détaillée
├── CHANGELOG.md                # Historique des versions
│
├── src/
│   ├── analyzer.md             # Logique d'analyse du cours
│   ├── segmenter.md            # Logique de segmentation
│   ├── instruction-generator.md # Génération des blocs d'instructions
│   ├── format-handler.md        # Gestion des différents formats
│   └── utils.md                # Utilitaires communs
│
├── examples/
│   ├── example-input-course.md  # Exemple de cours (input)
│   ├── example-output-podcasts.md  # Exemple d'output (podcasts)
│   ├── example-output-slides.md    # Exemple d'output (slides)
│   └── example-output-fiches.md    # Exemple d'output (fiches)
│
├── templates/
│   ├── instruction-podcast.md   # Template d'instruction podcast
│   ├── instruction-slides.md    # Template d'instruction slides
│   ├── instruction-fiches.md    # Template d'instruction fiches
│   └── instruction-flashcards.md # Template flashcards
│
└── guides/
    ├── GETTING_STARTED.md       # Démarrage rapide
    ├── BEST_PRACTICES.md        # Bonnes pratiques d'utilisation
    └── TROUBLESHOOTING.md       # Dépannage courant
```

---

## 8. DOCUMENTATION PUBLIQUE (Ce qui sera sur Registry)

### README.md (Accessible)
Explique en langage simple :
- À quoi sert BookLM-Orchestrator
- Qui devrait l'utiliser (étudiants, enseignants, créateurs de contenu)
- Avant/Après (exemple concret)
- Installation rapide
- Premier exemple

### GETTING_STARTED.md (Pas trop technique)
Pas de jargon. Étapes par images/exemples.

### Documentation technique (Pour développeurs)
- Logique d'analyse
- Comment ajouter des formats
- API interne

---

## 9. LANGUES & ACCESSIBILITÉ

**Langues** : 
- Documentation : Français + Anglais (lisible par tous)
- Skill : Peut interagir en FR et EN

**Accessibilité** :
- Pas d'acronymes non expliqués
- Exemples concrets à chaque concept
- Explication visuelle si possible (diagrammes simple en ASCII/Mermaid)

---

## 10. PROCHAINES ÉTAPES (Roadmap)

**Phase 1 (MVP)** :
- [ ] Analyser et segmenter un cours (logique de base)
- [ ] Générer instructions pour podcast format
- [ ] Livrable MD simple

**Phase 2 (Expansion)** :
- [ ] Support slides, fiches, flashcards
- [ ] Questions interactives plus robustes
- [ ] Meilleure gestion des dépendances conceptuelles

**Phase 3 (Intégration)** :
- [ ] Intégration directe BookLM API (si disponible)
- [ ] Support vidéo
- [ ] Analytics (quels formats marchent le mieux)

**Phase 4 (Public)** :
- [ ] Publication sur Registry skills
- [ ] Documentation multilingue complète
- [ ] Feedback utilisateurs & itération

---

## 11. OUTILS ET SKILLS DE CRÉATION

Pendant la création de BookLM-Orchestrator, nous utilisons des skills et outils existants pour **garantir la qualité, la structure et l'optimisation audio** :

### Skill Creator Skill
**Rôle** : Guide de bonne structure pour le skill
- Comment organiser les fichiers MD
- Comment structurer SKILL.md pour que le skill soit découvrable
- Bonnes pratiques de documentation
- Architecture interne (hooks, agents, flows)
- Versionning et déploiement

### Speechify Skill (ou TTS Optimization Skill)
**Rôle** : Optimise les instructions générées pour la lecture audio
- Assure que les blocs d'instruction restent lisibles en TTS
- Évalue la longueur des phrases (pas trop long pour l'audio)
- Recommande des reformulations pour clarté orale
- Gère la ponctuation et les symboles problématiques en TTS
- Vérifie que les blocs copiables dans BookLM sont bien adaptés à la génération audio

### Skill de Formalisation Pédagogique
**Rôle** : Valide la qualité pédagogique des segmentations
- Vérifie les dépendances conceptuelles
- Recommande les meilleurs découpes pédagogiques
- Valide que chaque segment est autonome et complet
- S'assure que les "concepts clés" identifiés sont vraiment pertinents

### Éventuellement : Skill Audio/Podcast
**Rôle** : Pour tester nos instructions directement
- Génère un mini-podcast test à partir d'un bloc d'instruction
- Valide que la segmentation fonctionne en pratique
- Recommande des ajustements d'instruction pour meilleure qualité audio

---

*Documentation publique — Dernière mise à jour : juin 2026*
*Statut : Spécification — prête pour développement*
