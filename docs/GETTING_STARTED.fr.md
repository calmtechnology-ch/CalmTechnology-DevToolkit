# Guide de démarrage rapide — CalmTechnology-DevToolkit

Bienvenue dans **CalmTechnology-DevToolkit**. Ce guide vous permet d'initialiser et de conduire votre premier workflow d'ingénierie assisté par IA en moins de 5 minutes.

---

## 1. Prérequis
- Un assistant IA capable de lire des fichiers Markdown (tel que Google Antigravity, Claude, ChatGPT, Cursor).
- Un dépôt de projet sous Git (nouveau projet ou projet existant).
- Aucune installation logicielle supplémentaire n'est requise : la version 0.1.0 fonctionne intégralement avec des documents Markdown structurés.

---

## 2. Mise en place en 3 étapes

### Étape 1 : Rendre le toolkit accessible
Placez le dossier `CalmTechnology-DevToolkit` dans votre espace de travail ou dans un dossier adjacent :
```text
mon-projet/
├── docs/                      # Documentation de votre projet
└── CalmTechnology-DevToolkit/ # La boîte à outils méthodologique
```

### Étape 2 : Initialiser la documentation de votre projet
Créez un dossier `docs/` à la racine de votre projet et copiez-y les modèles depuis `CalmTechnology-DevToolkit/templates/` :
- `PROJECT.md`
- `REQUIREMENTS.md`
- `ARCHITECTURE.md`
- `DECISIONS.md`
- `PROJECT_STATE.md`
- `TEST_PLAN.md`
- `TEST_RESULTS.md`
- `KNOWN_ISSUES.md`

### Étape 3 : Lancer votre assistant IA
Transmettez à votre assistant les règles de travail et le workflow de nouveau projet :
```text
Merci de lire CalmTechnology-DevToolkit/AGENTS.md.
Nous débutons un projet selon le workflow CalmTechnology-DevToolkit/workflows/new-project.md.
Active la compétence CalmTechnology-DevToolkit/skills/project-definition/SKILL.md.
Voici la description de mon projet : [Décrivez votre besoin]
```

---

## 3. Les 3 règles d'or à retenir
1. **Pas de code sans exigences formelles** : Définissez toujours vos exigences `REQ-F-xxx` avant toute génération de code.
2. **Consultez toujours `PROJECT_STATE.md` en priorité** : À chaque ouverture d'une nouvelle session de discussion avec l'IA, demandez-lui de lire `docs/PROJECT_STATE.md` pour reprendre le travail sans perte de contexte.
3. **Refusez les tests fictifs** : Si un test n'a pas été réellement exécuté avec preuve à l'appui, son statut est strictement `NOT_RUN`. La compilation ne vaut pas validation fonctionnelle.

---

## 4. Pour aller plus loin
- Consultez le [Guide utilisateur complet](USER_GUIDE.fr.md) / [User Guide (EN)](USER_GUIDE.md).
- Découvrez le cas réel [CoreS3-RuleBot](../examples/CoreS3-RuleBot/README.md).
- Étudiez les points de contrôle [Quality Gates](QUALITY_GATES.md).
