# Challenge - Inspection et Analyse d'un Repository GIT

## Consignes générales

Ce challenge a pour but d'évaluer votre capacité à **explorer, comprendre et analyser l'historique d'un projet GIT**.

### Règles

- **Aucune interface graphique n'est autorisée**, vous devez travailler **exclusivement en ligne de commande** (sauf pour le FORK depuis Github)
- **L'utilisation d'outils d'intelligence artificielle est strictement interdite.**
- Vous pouvez utiliser la documentation à l'adresse suivante: https://git-scm.com/book/fr/v2
- **Objectif : comprendre l'évolution du code et reconstituer les décisions prises.**

## Travail à effectuer

Le dépôt d'origine à utiliser est disponible à l'adresse suivante :
```bash
https://github.com/ETML-RRY/324_inspection_git.git
```

### Partie 1 - Préparation

1. Faites un *FORK* du dépôt sur votre compte GitHub (Attention il faut copier toutes les branches donc il faut **décocher** la case "Copy the main branch only" sur l'interface de Github)
2. Ajoutez votre enseignant comme collaborateur à votre dépôt forké.
3. Vous trouverez une réplique de ces instructions dans le fichier README.md de votre dépôt.
4. Répondez directement aux questions dans le fichier README.md qui est au format **Markdown**
5. Pour chaque points, veuillez noter la ou les commandes `git` utilisées vous permettant de répondre à la question.
6. Pour chaque partie, effectuez au minimum un commit et un push lorsque vous avez complété les réponses de la partie correspondante.

> Le format Markdown: [https://www.markdownguide.org/basic-syntax/](https://www.markdownguide.org/basic-syntax/)


### Partie 2 — Exploration de base

1. Combien de branches existent dans le dépôt ? Citez-les.\
 il y a 5 branches.\
 git branch -a

  dark-mode\
  header\
  login\
  typo\
  main

2. Quels sont les **tags** disponibles ? A quoi correspondent-ils ? \
ils correspondent au version des releases disponible\
git tag\
v0.1\
v0.2

3. Quelle est la **branche principale** du projet ?\
git branch
main

### Partie 3 — Historique et commits

4. Quel est le message du **premier commit** du projet ?\
git log --reverse\
 Initial commit: structure HTML/CSS/JS + README + docs

5. Trouvez le commit où une **clé API** a été ajoutée par erreur. Quel est son identifiant (hash court) ?\
git log --grep="API" --oneline\
bea2d1a

6. Quel commit a ensuite corrigé cette erreur ?\
git log --grep="API" --oneline\
1b682c9 chore(config): retire la clé API et documente la bonne pratique

7. Trouvez le commit où le **titre de la page d'accueil** a été corrigé.\
git log --grep="titre" --oneline\
6317c07 (origin/hotfix/typo) hotfix: corrige la typo 'Wolrd' dans le titre

8. Quel est le message du commit qui a **ajouté le fichier `CHANGELOG.md`** et quelle commande avez-vous utilisé ?\
 git log --oneline --name-status\
docs: ajoute un changelog de base

### Partie 4 — Branches et fusions

9. Quelles branches ont été fusionnées dans `main` ? \
 git log --merges --oneline\
login, typo et header

10. Quelle branche **n'a pas été fusionnée** ? Pourquoi, selon vous ? \
git branch -a --no-merged main\
remotes/origin/experiment/dark-mode n'est pas merge car il est dans la branche experiment qui potentiellement est une branche bac à sable

### Partie 5 — Analyse du contenu

11. Quelle est la **différence principale** entre les fichiers `index.html` dans les versions `v0.1` et `v0.2` et quelle commande permet de le voir rapidement ? \
git diff v0.1 v0.2 -- index.html\
La principale différence est l’ajout de la barre de navigation dans l’en-tête de la page.

12. Que contient la branche `feature/login` ? \
git branch -v\
74cc148 feature(login): ajoute page de connexion et pseudo-fonction JS

13. Dans quelle branche a été ajouté le code pour le **mode sombre** ?  \
git log --all -S "dark" --oneline\
dans la branche dark-mode

14. Quelle bonne pratique de sécurité est évoquée dans les commits du fichier `config.js` ?\
git log -- config.js\
retire la clé API et documente la bonne pratique

### Partie 6 — Réflexion

15. Pourquoi est-il important de **taguer** des versions dans un projet ?  \
Les tags dans Git servent à marquer des points précis de l’historique, généralement pour identifier des versions stables ou importantes.

16. Que peut-on déduire du style de travail de l'équipe à partir de cet historique GIT ? \
l’équipe semble suivre un workflow Git structuré, des commits atomiques, avec des branches dédiées aux fonctionnalités, correctifs et expérimentations, des merges réguliers dans main, et une gestion claire des versions avec des tags.

Bonne chance, et surtout... **ne vous perdez pas dans le log !** 😉