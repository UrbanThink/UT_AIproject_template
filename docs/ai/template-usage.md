# Utiliser ce dépôt comme template

Ce fichier explique rapidement comment utiliser ce dépôt `UT_AIproject_template` comme modèle pour de nouveaux projets, et quelles étapes effectuer après la création.

## But
Fournir une arborescence standardisée pour démarrer de nouveaux projets avec les règles, prompts, agents et skills AI déjà configurés.

## 1) Créer un nouveau projet depuis le template (méthode recommandée)

- Sur GitHub : ouvrir la page du dépôt `UT_AIproject_template` → bouton **Use this template** → créer le nouveau repo (public ou private).

- Après création : cloner, ajuster les métadonnées, configurer CI et protections de branche.

## 2) Méthode CLI (alternatif)

- Avec GitHub CLI (si disponible) :

```bash
gh repo create <org>/new-project --template=<org>/UT_AIproject_template --public
```

- Ou clonage manuel et réinitialisation de l'historique :

```bash
git clone https://github.com/<org>/UT_AIproject_template.git new-project
cd new-project
rm -rf .git
git init
git add .
git commit -m "Initial commit - from UT_AIproject_template template"
# créer le repo distant puis :
git remote add origin git@github.com:<org>/new-project.git
git branch -M main
git push -u origin main
```

## 3) Checklist immédiate après création

- [ ] Mettre à jour `README.md` (titre, description, badges).
- [ ] Mettre à jour `docs/ai/template-usage.md` localement pour noter choix spécifiques.
- [ ] Vérifier et adapter `.github/copilot-instructions.md` si le projet a des règles globales différentes.
- [ ] Configurer CI (secrets, runners), branch protection, labels, issue templates.
- [ ] Ajouter `CODEOWNERS` si nécessaire.
- [ ] Lancer les checks de base (lint, tests smoke) et corriger les problèmes.
- [ ] Créer la première release/tag (par ex. `v0.1.0`).

## 4) Personnalisation recommandée

- Réviser les fichiers dans `.github/instructions/` et supprimer ou adapter les règles non pertinentes.
- Ajuster les `prompts` si certains workflows ne s'appliquent pas.
- Ajuster les `skills` (checklist, templates) pour refléter le processus opérationnel du nouveau projet.
- Documenter dans `docs/ai/` toute décision spécifique (outils, conventions de nommage, pipelines).

## 5) Gouvernance du template

- Versionner le template via les **releases** et publier un `CHANGELOG.md` pour suivre les évolutions.
- Désigner un mainteneur (fichier `MAINTAINERS.md`) responsable des mises à jour du template.
- Pour propager une mise à jour majeure vers les projets existants, documenter une procédure de mise à jour (pull depuis template, script de migration, ou PR manuel).

## 6) Activer le dépôt comme template GitHub

Pour que le bouton **Use this template** apparaisse sur GitHub :

1. Aller dans **Settings** du dépôt.
2. Cocher **Template repository**.
3. Optionnel : créer `MAINTAINERS.md` et `CHANGELOG.md` pour la gouvernance.