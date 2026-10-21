# Contribuer au site

Merci de passer par ici. Ce site est le premier projet ouvert de Hors Zone AI, et il est volontairement petit : c'est un bon endroit pour une première contribution.

## Comment ça se passe

1. Choisissez une tâche marquée `good first issue` et dites en commentaire que vous la prenez.
2. Travaillez dans votre fork, sur une branche à part.
3. Ouvrez une pull request qui explique ce que vous avez changé et comment vous l'avez vérifié.
4. On relit chaque pull request avant de la fusionner.

## Signer vos commits

Chaque commit est signé avec `git commit -s`. Cette commande ajoute une ligne `Signed-off-by` qui atteste que vous avez le droit de proposer ce code ([Developer Certificate of Origin](https://developercertificate.org)). Vous gardez vos droits d'auteur, et votre contribution est publiée sous licence MIT, comme le reste du dépôt.

## Les règles du site

- Le site est en français, avec sa version anglaise dans `en/` : un texte modifié l'est dans les deux langues.
- Aucun cookie, aucun outil de mesure d'audience.
- Rien qui se charge depuis un autre site : ni police, ni script, ni image.
- Pas de JavaScript tant qu'on peut s'en passer.
- La page d'accueil et sa feuille de style restent sous 20 Ko à elles deux.
- Les textes ne promettent rien qui n'existe pas encore.

## Premières tâches

- Vérifier l'accessibilité de la page (contrastes, ordre des titres, navigation au clavier) et corriger ce qui coince.
- Ajouter un thème sombre qui suit le réglage de l'appareil, sans JavaScript.
- Ajouter une vérification automatique (GitHub Actions) qui échoue si la page d'accueil et sa feuille de style dépassent 20 Ko.
- Valider le HTML des deux pages dans GitHub Actions.
- Ajouter une feuille de style pour l'impression.
- Tester la page avec une connexion lente simulée et noter le temps d'affichage dans une issue.
