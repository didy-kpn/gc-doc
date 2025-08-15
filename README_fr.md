# gemini-cli-spec

Ce dépôt contient un ensemble de commandes et de modèles personnalisés pour permettre un flux de travail de développement puissant, piloté par les spécifications, au sein du Gemini CLI.

Ce flux de travail vous guide, ainsi que l'IA, à travers un processus structuré de développement logiciel, de l'idée initiale à la mise en œuvre, garantissant des résultats de haute qualité et une documentation claire.

## Flux de travail de développement piloté par les spécifications de Gemini CLI

### Aperçu

Le flux de travail de développement piloté par les spécifications de Gemini CLI est une méthodologie structurée pour développer des logiciels en collaboration avec un assistant IA. Il formalise le processus de développement en phases distinctes et séquentielles, chacune ayant un objectif et un livrable clairs. En suivant ce flux de travail, vous pouvez vous assurer que chaque fonctionnalité est bien définie, conçue et décomposée en tâches gérables avant même d'écrire la moindre ligne de code.

**Principaux avantages :**
- **Clarté et Précision** : Garantit que les exigences et la conception sont clairement définies et approuvées avant la mise en œuvre.
- **Assurance Qualité** : Intègre une validation automatisée et une approbation humaine obligatoire à chaque étape.
- **Cohérence** : Utilise des modèles pour créer une documentation cohérente et de haute qualité.
- **Efficacité** : Fournit un processus clair, étape par étape, qui rationalise le développement assisté par l'IA.

### Prérequis

Pour utiliser ce flux de travail, vous avez besoin d'un environnement Gemini CLI fonctionnel. Le flux de travail est défini par les fichiers situés dans le répertoire `.gemini/` de ce projet. Tant que vous exécutez `gemini` depuis le répertoire racine de ce projet, les commandes personnalisées seront disponibles.

### Comment l'utiliser

Le flux de travail suit une séquence de commandes. Vous devez les exécuter dans l'ordre spécifié pour chaque fonctionnalité que vous développez.

**Le cycle de vie du développement pour une nouvelle fonctionnalité `<spec-name>` :**

1.  **Configuration des documents d'orientation (Optionnel mais recommandé)**
    - Exécutez `/spec steering` pour analyser votre projet et créer des documents fondamentaux (`product.md`, `tech.md`, `structure.md`) qui guideront l'IA.

2.  **Initialisation de la spécification**
    - Exécutez `/spec create <spec-name>`
    - Cela crée un répertoire dédié et un fichier `spec.json` pour suivre la progression de votre nouvelle fonctionnalité.

3.  **Définition des exigences**
    - Exécutez `/spec requirements <spec-name>`
    - L'IA génère un fichier `requirements.md`, détaillant les "user stories" et les critères d'acceptation au format EARS.

4.  **Création de la conception technique**
    - Exécutez `/spec design <spec-name>`
    - Après votre approbation des exigences, l'IA génère un fichier `design.md`, incluant l'architecture, les modèles de données, les points de terminaison d'API, et plus encore.

5.  **Génération des tâches de mise en œuvre**
    - Exécutez `/spec tasks <spec-name>`
    - Après votre approbation de la conception, l'IA la décompose en une liste de petites tâches de codage atomiques dans `tasks.md`.

6.  **Mise en œuvre des tâches**
    - Exécutez `/spec implement <spec-name> <task-id>`
    - Mettez en œuvre chaque tâche une par une, en suivant une approche de Développement Piloté par les Tests (TDD).

7.  **Vérification de la progression**
    - À tout moment, exécutez `/spec status <spec-name>` pour voir l'état actuel de votre spécification.

### Commandes

| Commande                                  | Description                                                                                                                              |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `/spec create <spec-name>`                | Initialise une nouvelle spécification. Crée le répertoire de la spec et le fichier de suivi `spec.json`.                                           |
| `/spec requirements <spec-name>`          | Génère un fichier `requirements.md` détaillé basé sur le contexte du projet et les modèles.                                                      |
| `/spec design <spec-name>`                | Génère un document technique complet `design.md` après votre approbation des exigences.                                           |
| `/spec tasks <spec-name>`                 | Génère une liste de tâches de codage atomiques et exécutables dans `tasks.md` après votre approbation de la conception.                                          |
| `/spec implement-contract <spec-name> <task-id>` | Phase 1 : Implémente les contrats d'API et génère un fichier `testcase.md` pour une tâche. |
| `/spec implement-red <spec-name> <task-id>`      | Phase 2 : Crée un test qui échoue sur la base des cas de test (Rouge). |
| `/spec implement-green <spec-name> <task-id>`    | Phase 3 : Écrit le code minimum pour faire passer le test (Vert). |
| `/spec implement-refactor <spec-name> <task-id>` | Phase 4 : Refactorise le code, finalise la tâche et effectue le nettoyage. |
| `/spec status <spec-name>`                | Affiche la progression actuelle d'une spécification, y compris les phases terminées et le pourcentage d'achèvement des tâches.                   |
| `/spec steering`                          | Crée ou met à jour intelligemment les documents d'orientation de base (`product.md`, `tech.md`, `structure.md`) qui fournissent un contexte à l'échelle du projet. |

---

## Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

Copyright (c) 2025 didy
