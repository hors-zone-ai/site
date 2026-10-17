# Site de Hors Zone AI

Le site de l'association [Hors Zone AI](https://github.com/hors-zone-ai) : sa mission (l'IA à chances égales), ses outils et l'inscription à leur bêta. Les deux premiers outils, gratuits pour les 16 à 25 ans : **Révise** (fiches, quiz et cartes mémoire à partir de tes cours) et **Entretien blanc** (répétition d'entretiens). En ligne sur https://hors-zone-ai.github.io/site/.

C'est notre premier projet ouvert. La page doit rester légère et ne rien coûter à faire tourner, alors on s'en tient à peu de choses :

- aucun cookie, aucun outil de mesure d'audience ;
- rien qui se charge depuis un autre site (police, script, image) ;
- pas de JavaScript tant qu'on peut s'en passer ;
- la page d'accueil et sa feuille de style pèsent moins de 20 Ko à elles deux.

## Les fichiers

- `index.html` : la page d'accueil (mission, nos outils, ce qui nous anime, nous rejoindre) et les deux formulaires (bêta pour les étudiants, besoin pour les associations et autres structures).
- `merci.html` : la page affichée après une inscription.
- `comptes.html` : nos comptes, ouverts : les chiffres, où va l'argent, merci aux soutiens.
- `comptes.csv` : les comptes, une ligne par opération (voir plus bas).
- `mentions-legales.html` : mentions légales et données personnelles.
- `style.css` : la seule feuille de style.
- `marque/` : le logo et l'avatar.

Les formulaires sont de simples formulaires HTML, sans JavaScript. Ils envoient vers un webhook de l'association, qui vérifie le mail et l'accord, écarte les robots (un champ piège caché) et renvoie vers `merci.html`.

## Les comptes

`comptes.csv` contient une ligne par opération, en UTF-8, séparateur virgule :

- `date` : AAAA-MM-JJ ;
- `sens` : `recette` ou `depense` ;
- `categorie` : `acces-claude`, `outils` ou `frais` pour une dépense ; `don`, `mecenat`, `subvention` ou `cotisation` pour une recette ;
- `libelle` : un don s'écrit « Don anonyme », sauf si le donateur demande à voir son nom ;
- `montant_eur` : en euros, avec un point pour les centimes.

Les chiffres de `comptes.html` et de l'accueil sont mis à jour dans le même commit que la ligne ajoutée.

## Voir le site sur votre ordinateur

Téléchargez le dépôt et ouvrez `index.html` dans un navigateur. Il n'y a rien à installer.

## Contribuer

Tout est expliqué dans [CONTRIBUTING.md](CONTRIBUTING.md), avec les premières tâches pour débuter.

## Licence

Code publié sous licence MIT, voir [LICENSE](LICENSE).
