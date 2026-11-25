# Guide de démarrage rapide — CalmTechnology-DevToolkit

Bienvenue dans **CalmTechnology-DevToolkit**. Ce guide vous explique comment débuter avec votre assistant IA en moins de 5 minutes, sans avoir à lire toute la méthodologie au préalable.

---

## 1. Organisation partagée (Aucune installation logicielle requise)

Le toolkit fonctionne intégralement à base de fichiers Markdown. Conservez un dossier unique `CalmTechnology-DevToolkit` dans votre répertoire parent, partagé entre tous vos projets :

```text
Documents/
└── Antigravity-5.1/
    ├── CalmTechnology-DevToolkit/   # Boîte à outils méthodologique partagée
    ├── ProjetA/                     # Projet A (avec ses propres docs/ et src/)
    └── ProjetB/                     # Projet B (avec ses propres docs/ et src/)
```

Aucun sous-module Git, lien symbolique ou copie intégrale n'est requis.

---

## 2. Les 3 situations courantes

Sélectionnez la situation correspondant à votre objectif :

### Situation A — Créer un nouveau projet
1. Ouvrez le dossier de votre nouveau projet.
2. Dans le chat avec votre assistant IA, transmettez le prompt court :
   ```text
   Utilise CalmTechnology-DevToolkit.
   Initialise la documentation de ce projet selon le workflow new-project.
   Ne commence pas à programmer.
   ```
3. Exprimez votre concept et vos contraintes. L'assistant va :
   - Créer `docs/` et initialiser `PROJECT.md`, `REQUIREMENTS.md` et `PROJECT_STATE.md`.
   - Évaluer le Quality Gate QG-01 (Definition Ready).

### Situation B — Importer un projet existant
1. Ouvrez le dossier de votre projet existant dans votre éditeur.
2. Dans le chat avec votre assistant IA, transmettez le prompt court :
   ```text
   Utilise CalmTechnology-DevToolkit.
   Examine ce projet existant et initialise sa documentation à partir du code réel.
   Ne modifie aucun fichier source.
   ```
3. L'assistant examine le code réel, rétro-conçoit les exigences de base, consigne les tests existants, génère `docs/PROJECT_STATE.md` et propose la suite sans toucher au code source.

### Situation C — Continuer un projet déjà intégré
1. Ouvrez un projet disposant déjà de `docs/PROJECT_STATE.md`.
2. Dans le chat avec votre assistant IA, transmettez le prompt court :
   ```text
   Utilise CalmTechnology-DevToolkit.
   Lis PROJECT_STATE.md, vérifie l'état réel du projet et propose la prochaine étape.
   Ne modifie pas le code.
   ```
3. L'assistant lit la mémoire vivante du projet, contrôle les modifications récentes, identifie les fonctionnalités protégées et propose la prochaine action ciblée.

---

## 3. Les principes essentiels à retenir
1. **Pas de code sans exigences formelles** : Spécifiez toujours vos exigences `REQ-F-xxx` avant de modifier le code.
2. **Consultez `PROJECT_STATE.md` en priorité** : Il constitue la source unique de vérité partagée entre sessions IA.
3. **Refusez les tests fictifs** : Tout test non exécuté est strictement `NOT_RUN` (ou `BLOCKED` si le matériel est indisponible). La compilation ne vaut pas validation fonctionnelle.
4. **Signalez les chemins inaccessibles** : Si l'assistant ne peut pas accéder au dossier du toolkit, il doit obligatoirement le signaler plutôt que faire semblant de l'avoir chargé.

---

## 4. Pour aller plus loin
- Consultez le [Guide utilisateur complet (FR)](USER_GUIDE.fr.md) / [User Guide (EN)](USER_GUIDE.md).
- Découvrez le cas d'école [CoreS3-RuleBot](../examples/CoreS3-RuleBot/README.md).
- Étudiez les points de contrôle [Quality Gates](QUALITY_GATES.md).
