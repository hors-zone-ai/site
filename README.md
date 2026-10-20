# Site de Hors Zone AI

Le site de l'association [Hors Zone AI](https://github.com/hors-zone-ai) : sa mission (aider les devs et les étudiants en informatique à coder avec l'IA, gratuitement ou moins cher), l'accès aux outils d'IA et ses apps. Les deux premières apps, gratuites : **Révise** (fiches, quiz et cartes mémoire à partir de tes cours) et **Entretien blanc** (répétition d'entretiens). En ligne sur https://hors-zone-ai.github.io/site/.

C'est notre premier projet ouvert. La page doit rester légère et ne rien coûter à faire tourner, alors on s'en tient à peu de choses :

- aucun cookie, aucun outil de mesure d'audience ;
- rien qui se charge depuis un autre site (police, script, image) ;
- pas de JavaScript tant qu'on peut s'en passer : le seul script est celui des chiffres en direct de l'accueil, qui lit `comptes.csv` pour se mettre à jour tout seul (sans lui, les chiffres écrits dans la page restent affichés) ;
- chaque page, avec la feuille de style, pèse moins de 20 Ko.

## Les fichiers

- `index.html` : l'accueil, qui est aussi la page À propos (la vitrine, notre mission, qui est derrière, nos comptes ouverts).
- `services.html` : nos services : 01 programme de sponsoring sur candidature (Claude Code ou Codex payé par l'asso, avec le formulaire de candidature), 02 offres réduites, 03 nos apps Révise et Entretien blanc.
- `rejoindre.html` : nous rejoindre, pour les étudiants devs et les structures, avec le formulaire « Proposer un besoin ».
- `merci.html` : la page affichée après une candidature ou une demande.
- `apropos.html`, `outils.html`, `acces.html`, `mission.html`, `comptes.html` : anciennes adresses, elles redirigent vers les nouvelles pages.
- `comptes.csv` : les comptes, une ligne par opération (voir plus bas).
- `mentions-legales.html` : mentions légales et données personnelles.
- `style.css` : la feuille de style commune. Ce qui ne sert qu'à une page (la vitrine et les valeurs de l'accueil, le terminal de Nos services) est dans un bloc `<style>` en haut de cette page, pour que chacune reste sous 20 Ko.
- Après chaque modification de `style.css`, augmenter le numéro de version du lien (`style.css?v=4`, puis `?v=5`…) sur les six pages : sans ça, les navigateurs gardent l'ancienne feuille jusqu'à 10 minutes.
- `marque/` : le logo et l'avatar.

Le menu et le pied de page sont recopiés dans chaque page : une modification se fait partout.

Deux formulaires (candidature au programme, besoin d'une structure) envoient vers le même webhook ; le champ caché `source` dit d'où vient chaque envoi.

Les formulaires sont de simples formulaires HTML, sans JavaScript. Ils envoient vers un webhook de l'association, qui vérifie le mail et l'accord, écarte les robots (un champ piège caché) et renvoie vers `merci.html`.

## Les comptes

`comptes.csv` contient une ligne par opération, en UTF-8, séparateur virgule :

- `date` : AAAA-MM-JJ ;
- `sens` : `recette` ou `depense` ;
- `categorie` : `acces-claude`, `outils` ou `frais` pour une dépense ; `don`, `mecenat`, `subvention` ou `cotisation` pour une recette ;
- `libelle` : un don s'écrit « Don anonyme », sauf si le donateur demande à voir son nom ; un accès `acces-claude` porte le pseudonyme de la personne accompagnée, jamais son nom, par exemple « Claude Code (dev 01) » ;
- `montant_eur` : en euros, avec un point pour les centimes.

L'accueil lit ce fichier tout seul : le total des dons (`don` et `mecenat`), le nombre de devs que ces dons peuvent financer pendant 6 mois, et les personnes accompagnées, comptées d'après les pseudonymes « dev 01 », « dev 02 »… des dépenses `acces-claude`. Les chiffres écrits dans la page, affichés sans JavaScript, sont mis à jour dans le même commit que la ligne ajoutée.

## Voir le site sur votre ordinateur

Téléchargez le dépôt et ouvrez `index.html` dans un navigateur. Il n'y a rien à installer.

## Contribuer

Tout est expliqué dans [CONTRIBUTING.md](CONTRIBUTING.md), avec les premières tâches pour débuter.

## Licence

Code publié sous licence MIT, voir [LICENSE](LICENSE).
