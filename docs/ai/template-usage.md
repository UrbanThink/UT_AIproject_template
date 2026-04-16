# Utiliser ce dépôt comme template

Ce fichier explique rapidement comment utiliser ce dépôt `UT_AIproject_template` comme modèle pour de nouveaux projets, et quelles étapes effectuer après la création.

## But
Fournir une arborescence standardisée pour démarrer de nouveaux projets avec les règles, prompts, agents et skills AI déjà configurés.

## 1) Créer un nouveau projet depuis le template (méthode recommandée)

- Sur GitHub : ouvre la page du dépôt `UT_AIproject_template` → bouton **Use this template** → crée le nouveau repo (choisis public/private).

- Après création : clone, ajuste les métadonnées, configure CI et protections de branche.

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

- Revise les fichiers dans `.github/instructions/` et supprime ou adapte les règles non pertinentes.
- Ajuste les `prompts` si certains workflows ne s'appliquent pas.
- Ajuste les `skills` (checklist, templates) pour refléter le process operational du nouveau projet.
- Documente dans `docs/ai/` toute décision spécifique (outils, conventions de nommage, pipelines).

## 5) Gouvernance du template

- Versionne le template via les **releases** et publie un `CHANGELOG.md` pour suivre les évolutions.
- Désigne un mainteneur (fichier `MAINTAINERS.md`) responsable des mises à jour du template.
- Pour propager une mise à jour majeure vers les projets existants, documente une procédure de mise à jour (pull depuis template, script de migration, ou PR manuel).

## 6) Si tu veux que je publie le dépôt comme template GitHub

Je peux :
- créer `MAINTAINERS.md` et `CHANGELOG.md` automatiquement,
- activer le repo comme template via l'API GitHub (nécessite token avec droits repo).

Dis‑moi si tu veux que je crée `MAINTAINERS.md` maintenant, ou si tu veux que j'active la publication (je te demanderai un token ou tu pourras exécuter la commande `gh` localement).

---

Fini — personnalise les éléments de la checklist selon ton équipe et dis‑moi si je dois automatiser la publication template.