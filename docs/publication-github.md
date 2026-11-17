# Mettre à jour webtooner 1.1.0 sur GitHub

Décompresser l’archive puis déposer le contenu du dossier `eigrutel-webtooner` à la racine du dépôt existant. Conserver la structure des dossiers. Ne pas déposer le ZIP dans le dépôt.

## Fichiers modifiés

- `webtooner.html`
- `index.html`
- `README.md`
- `notice.md`
- `changelog.md`
- `docs/utilisation.md`
- `docs/publication-github.md`
- `docs/architecture/README.md`
- `docs/architecture/validation.md`

Le favicon et les licences sont inchangés. Il est possible de remplacer seulement les fichiers ci-dessus, ou de déposer tout le contenu de l’archive.

Message de commit : `Ajout du lecteur Webtoon intégré - v1.1.0`

## Nouvelle release

Créer la release après le commit sur la branche principale.

- Tag : `v1.1.0`
- Titre : `webtooner 1.1.0 - Lecteur Webtoon intégré`
- Pièce jointe : `webtooner.html` fourni dans cette archive.
- Archive complète facultative : GitHub génère déjà les archives du code source pour le tag.

### Français

Ajout d’un lecteur Webtoon intégré, accessible après le bouton de langue.

- Charger plusieurs images PNG/JPG ou ajouter des images par URL directe.
- Lire les images à la suite, avec barre de défilement fine, progression et retour en haut.
- Utiliser Vider pour retirer les images et libérer les ressources du lecteur.
- Profiter d’aperçus allégés, limités à 480 px de large et chargés par segments.
- Conserver les fichiers d’origine et le format des projets existants.

Interface français/anglais. L’optimisation des images distantes dépend des autorisations du site source ; un affichage direct est utilisé en repli lorsque possible.

### English

Added an integrated Webtoon reader, accessible next to the language button.

- Load multiple PNG/JPG images or append images using direct URLs.
- Read images continuously with a thin scrollbar, reading progress and a back-to-top control.
- Use Clear to remove images and release reader resources.
- View lightweight previews, limited to 480 px wide and loaded in segments.
- Keep original files and the existing project format unchanged.

French/English interface. Remote image optimization depends on the source server’s permissions; direct display is used as a fallback when available.

## Après publication

Ouvrir l’application publique, actualiser la page, tester le lecteur avec plusieurs images et vérifier Vider. Contrôler aussi un import, un export et la sauvegarde d’un projet. Ne pas recréer le dépôt ni changer les réglages GitHub Pages existants.
