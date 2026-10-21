# Site de Hors Zone AI

Le site de l'association [Hors Zone AI](https://github.com/hors-zone-ai) : sa mission (aider les devs et les étudiants en informatique à coder avec l'IA, gratuitement ou moins cher), l'accès aux outils d'IA et ses apps. Les deux premières apps, gratuites : **Humanizer** (retoucher un texte fait avec l'IA pour qu'il sonne comme toi) et **Entretien blanc** (répétition d'entretiens). En ligne sur https://hors-zone-ai.github.io/site/.

C'est notre premier projet ouvert. La page doit rester légère et ne rien coûter à faire tourner, alors on s'en tient à peu de choses :

- aucun cookie, aucun outil de mesure d'audience ;
- rien qui se charge depuis un autre site (police, script, image) ;
- pas de JavaScript tant qu'on peut s'en passer : le seul script est celui de l'accueil, qui lit `dons.csv` pour mettre à jour tout seul les chiffres en direct et le bandeau de remerciement (sans lui, ce qui est écrit dans la page reste affiché) ;
- chaque page, avec la feuille de style, pèse moins de 20 Ko.

## Les fichiers

- `index.html` : l'accueil, qui est aussi la page À propos (la vitrine, notre mission, où va l'argent, le bandeau de remerciement).
- `services.html` : nos services : 01 programme de sponsoring sur candidature (Claude Code ou Codex payé par l'asso, avec le formulaire de candidature), 02 offres réduites, 03 nos apps Humanizer et Entretien blanc.
- `rejoindre.html` : nous rejoindre, pour les étudiants devs et les structures, avec le formulaire « Proposer un besoin ».
- `merci.html` : la page affichée après une candidature ou une demande.
- `apropos.html`, `outils.html`, `acces.html`, `mission.html`, `comptes.html` : anciennes adresses, elles redirigent vers les nouvelles pages.
- `dons.csv` : le registre des dons, une ligne par don, sans montant (voir plus bas).
- `mentions-legales.html` : mentions légales et données personnelles.
- `style.css` : la feuille de style commune. Ce qui ne sert qu'à une page (la vitrine, les valeurs et le bandeau de remerciement de l'accueil, le terminal et les apps de Nos services) est dans un bloc `<style>` en haut de cette page, pour que chacune reste sous 20 Ko.
- Après chaque modification de `style.css`, augmenter le numéro de version du lien (`style.css?v=7`, puis `?v=8`…) sur les cinq pages : sans ça, les navigateurs gardent l'ancienne feuille jusqu'à 10 minutes.
- `marque/` : le logo et l'avatar.

Le menu et le pied de page sont recopiés dans chaque page : une modification se fait partout. Seule exception, l'accueil n'a pas la signature « Pas ici. » en pied de page, puisque son titre la porte déjà. Règle d'écriture : rien n'est dit deux fois sur une même page (un surtitre ne répète pas son titre).

Deux formulaires (candidature au programme, besoin d'une structure) envoient vers le même webhook ; le champ caché `source` dit d'où vient chaque envoi.

Les formulaires sont de simples formulaires HTML, sans JavaScript. Ils envoient vers un webhook de l'association, qui vérifie le mail et l'accord, écarte les robots (un champ piège caché) et renvoie vers `merci.html`.

## Le registre des dons

On ne publie ni comptes ni montants : seulement les dons. `dons.csv` contient une ligne par don, en UTF-8, séparateur virgule, sans virgule dans les valeurs :

- `date` : AAAA-MM-JJ ;
- `categorie` : `don` ou `mecenat` ;
- `nom` : `Anonyme` par défaut ; le nom du donateur seulement s'il le demande ;
- `logo` : vide par défaut ; sinon le chemin d'un logo déposé dans le dossier `donateurs/` (SVG, PNG ou WebP, léger), par exemple `donateurs/nom.svg`, seulement si le donateur le demande.

L'accueil lit ce fichier tout seul : le nombre de dons et la date du dernier dans l'encadré en direct, et une tuile par don dans le bandeau « Merci. » (le logo s'il y en a un, sinon le nom). Le nombre de personnes accompagnées s'écrit à la main dans `index.html`. Les chiffres et les tuiles écrits dans la page, affichés sans JavaScript, sont mis à jour dans le même commit que la ligne ajoutée.

## Voir le site sur votre ordinateur

Téléchargez le dépôt et ouvrez `index.html` dans un navigateur. Il n'y a rien à installer.

## Contribuer

Tout est expliqué dans [CONTRIBUTING.md](CONTRIBUTING.md), avec les premières tâches pour débuter.

## Licence

Code publié sous licence MIT, voir [LICENSE](LICENSE).
