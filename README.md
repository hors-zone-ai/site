# Site de Hors Zone AI

Le site de l'association [Hors Zone AI](https://github.com/hors-zone-ai) : sa mission (aider les devs et les étudiants en informatique à coder avec l'IA, gratuitement ou moins cher), l'accès aux outils d'IA et ses apps. Les deux premières apps, gratuites : **Humanizer** (retoucher un texte fait avec l'IA pour qu'il sonne comme toi) et **Entretien blanc** (répétition d'entretiens). En français, avec une version anglaise. En ligne sur https://hors-zone-ai.github.io/site/ (en anglais : https://hors-zone-ai.github.io/site/en/).

C'est notre premier projet ouvert. La page doit rester légère et ne rien coûter à faire tourner, alors on s'en tient à peu de choses :

- aucun cookie, aucun outil de mesure d'audience ;
- rien qui se charge depuis un autre site (police, script, image) ;
- pas de JavaScript tant qu'on peut s'en passer : le seul script est celui de l'accueil (dans les deux langues), qui lit `dons.csv` pour mettre à jour tout seul les chiffres en direct et le bandeau de remerciement (sans lui, ce qui est écrit dans la page reste affiché) ;
- des pages légères : chaque page, avec la feuille de style, reste sous 40 Ko, sans image lourde ni police téléchargée (les titres utilisent les polices serif déjà installées, Charter sur Mac).

## Les fichiers

- `index.html` : l'accueil, refait le 26/10 après un benchmark de 12 sites d'associations : accroche et bouton « Candidater », trois engagements, trois portes (tu codes, tu veux aider, tu représentes une structure), comment ça marche, nos apps, ce qui nous guide, en toute transparence (chiffres en direct, merci, où va l'argent), qui porte l'asso, questions.
- `services.html` : le programme de sponsoring (« Le programme » dans le menu) : l'accroche, l'outil au choix (Claude Code ou Codex), les règles, le formulaire de candidature, puis les offres réduites (bientôt). Les étapes et les apps sont sur l'accueil, pas ici, pour ne rien dire deux fois.
- `rejoindre.html` : nous rejoindre : deux portes (tu codes, vous êtes une structure) et le formulaire « Proposer un besoin ».
- `merci.html` : la page affichée après une candidature ou une demande.
- `apropos.html`, `outils.html`, `acces.html`, `mission.html`, `comptes.html` : anciennes adresses, elles redirigent vers les nouvelles pages.
- `dons.csv` : le registre des dons, une ligne par don, sans montant, plus une ligne `maj` quand on vérifie les chiffres (voir plus bas).
- `mentions-legales.html` : mentions légales et données personnelles.
- `style.css` : la feuille de style commune : en-tête, sections pleine largeur (le contenu dans `.int`), cartes, formulaires, pied de page. Ce qui ne sert qu'à l'accueil (engagements, étapes, apps, transparence, équipe, questions) est dans un bloc `<style>` en haut de l'accueil.
- Après chaque modification de `style.css`, augmenter le numéro de version du lien (`style.css?v=10`, puis `?v=11`…) sur les dix pages, françaises et anglaises : sans ça, les navigateurs gardent l'ancienne feuille jusqu'à 10 minutes.
- `en/` : la version anglaise, une page par page française : `index.html`, `services.html`, `join.html` (Nous rejoindre), `thanks.html` (merci), `legal.html` (mentions légales, la version française fait foi). Même feuille de style, liée en `../style.css`.
- `marque/` : le logo et l'avatar.

Le menu et le pied de page sont recopiés dans chaque page : une modification se fait partout. Chaque page a sa jumelle dans l'autre langue (lien FR ou EN en haut à droite, balises `hreflang`) : un texte modifié l'est dans les deux langues. En haut de chaque page, un menu fixe avec le bouton « Candidater » ; en bas, un pied de page en quatre colonnes. Règles d'écriture : rien n'est dit deux fois sur une même page, et chaque section n'a qu'un titre, sans surtitre au-dessus (seule l'accroche de l'accueil garde le sien).

Deux formulaires (candidature au programme, besoin d'une structure) envoient vers le même webhook ; le champ caché `source` dit d'où vient chaque envoi (« site en, … » pour les pages anglaises). Les formulaires anglais envoient aussi `langue=en` : le webhook renvoie alors vers `en/thanks.html`.

Les formulaires sont de simples formulaires HTML, sans JavaScript. Ils envoient vers un webhook de l'association, qui vérifie le mail et l'accord, écarte les robots (un champ piège caché) et renvoie vers `merci.html`.

## Le registre des dons

On ne publie ni comptes ni montants : seulement les dons. `dons.csv` contient une ligne par don, en UTF-8, séparateur virgule, sans virgule dans les valeurs :

- `date` : AAAA-MM-JJ ;
- `categorie` : `don` ou `mecenat` ; ou `maj` pour dire que les chiffres ont été vérifiés ce jour-là, sans nouveau don (ni nom ni logo) ;
- `nom` : `Anonyme` par défaut ; le nom du donateur seulement s'il le demande ;
- `logo` : vide par défaut ; sinon le chemin d'un logo déposé dans le dossier `donateurs/` (SVG, PNG ou WebP, léger), par exemple `donateurs/nom.svg`, seulement si le donateur le demande.

Les deux accueils, français et anglais, lisent ce fichier tout seuls : le nombre de dons et la date de la dernière ligne (don ou vérification) dans l'encadré en direct, et une tuile par don dans le bandeau « Merci. » (le logo s'il y en a un, sinon le nom). Le nombre de personnes accompagnées s'écrit à la main dans `index.html`. Les chiffres et les tuiles écrits dans la page, affichés sans JavaScript, sont mis à jour dans le même commit que la ligne ajoutée.

## Voir le site sur votre ordinateur

Téléchargez le dépôt et ouvrez `index.html` dans un navigateur. Il n'y a rien à installer.

## Contribuer

Tout est expliqué dans [CONTRIBUTING.md](CONTRIBUTING.md), avec les premières tâches pour débuter.

## In English

This repository holds the website of Hors Zone AI, a French non-profit that helps developers and computer science students code with AI, for free or for less. French pages sit at the root, their English versions in `en/`: any text change goes into both languages. House rules: no cookies, nothing loaded from another site, no JavaScript unless it is needed, every page under 20 KB with the stylesheet. To contribute, pick an issue, work in a fork and open a pull request, with commits signed using `git commit -s`.

## Licence

Code publié sous licence MIT, voir [LICENSE](LICENSE).
