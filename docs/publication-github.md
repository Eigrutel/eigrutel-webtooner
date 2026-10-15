# Publier webtooner 1.0.0 sur GitHub

## Préparer le dépôt

Nom suggéré : **eigrutel-webtooner**. Description proposée :

> Outil libre et autonome pour découper des cases, assembler un webtoon et exporter un bandeau ou ses morceaux. Eigrutel Lab. FR/EN.

Décompresser l’archive fournie. Déposer **son contenu directement à la racine du dépôt**, pas le ZIP et pas un dossier englobant supplémentaire. `index.html` et `webtooner.html` doivent être au même niveau. Conserver `favicon`, `docs` et `licenses` avec leur contenu.

Les fichiers `notice.md`, `changelog.md` et `license.md` utilisent les minuscules demandées. Tous les liens respectent cette casse. Ne pas générer une autre licence depuis un modèle GitHub qui remplacerait le régime fourni.

Le code de l’application est déjà le code source complet. Aucune compilation, dépendance à installer ou secret à configurer.

## GitHub Pages

Dans les réglages du dépôt, activer GitHub Pages depuis la branche principale, dossier racine. L’URL annoncée par GitHub sera l’adresse à utiliser. La racine ouvre la présentation `index.html`. Le lien interne ouvre `webtooner.html`.

Le nom du dépôt n’est pas codé en dur dans les liens internes : le même dossier peut être hébergé ailleurs. Dans About, ajouter l’URL obtenue ou le lien Eigrutel Lab : https://www.stripmee.com/eigrutel-lab/.

## Première release

- Tag : `v1.0.0`
- Titre : `webtooner 1.0.0`
- Texte : copier [release-1.0.0.md](release-1.0.0.md).
- Pièce jointe principale : `webtooner.html`.
- Pièce jointe facultative : l’archive complète fournie.

GitHub génère également les archives du code source à partir du tag. Créer le tag après avoir déposé les fichiers stables. Le bouton de téléchargement de la présentation pointe directement vers le HTML et fonctionne même avant la création d’une release.

## Contrôle après publication

Ouvrir la page publique et vérifier les boutons, le favicon et les liens de documentation. Tester un import et un export puis télécharger un projet. Une copie locale et une copie hébergée n’utilisent pas nécessairement la même zone de sauvegarde : transférer le fichier `.webtooner` pour reprendre son travail.

Ce dossier prépare les fichiers ; il ne crée pas le dépôt, n’active pas Pages et ne publie pas de release automatiquement.
