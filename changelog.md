# Changelog

Toutes les modifications importantes de **webtooner** sont documentées ici.
Le format s’inspire de [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/). Le projet adopte le [versionnage sémantique](https://semver.org/lang/fr/).

## [1.1.0] - 2026-11-17

### Ajouté

- Lecteur Webtoon intégré accessible après le bouton de langue, avec interface FR/EN.
- Chargement de plusieurs images locales, notamment PNG et JPG/JPEG, dans l’ordre naturel de leurs noms.
- Ajout d’images par URL directe, à la suite de la lecture.
- Colonne de lecture étroite sur fond sombre, barre de défilement fine, progression et retour en haut.
- Bouton Vider pour retirer les images et annuler un chargement en cours.

### Optimisé

- Aperçus limités à 480 px de large et segments de 2048 px de haut au maximum.
- Compression WebP lorsque disponible, chargement différé des segments et traitement séquentiel des sources.
- Libération des ressources des originaux après conversion et des aperçus lors du vidage ou du remplacement.
- Affichage direct de repli pour les images distantes dont le serveur bloque l’optimisation, avec un message explicatif.

### Documentation

- Présentation, guide utilisateur, documentation technique et version de l’application actualisés.
- Format des projets et sauvegardes inchangé ; la lecture est indépendante du montage et n’est pas sauvegardée dans le projet.

## [1.0.0] - 2026-10-15

Première version stable publique. Les numéros utilisés pendant la préparation ne constituent pas un historique de versions publiques.

### Ajouté

- Application autonome HTML/CSS/JavaScript, interface français et anglais.
- Import JPG, PNG et WebP ; sélection, zoom et déplacement de la vue.
- Verrouillage des dimensions de sélection et recadrage des cases dans une fenêtre focus.
- Mémorisation, renommage, réorganisation et export des cases.
- Exports JPG/PNG individuels ou ZIP, profils réseau et impression à 300 dpi.
- Assemblage vertical avec largeur réglable, espacement global et bandes transparentes cumulables.
- Marges gauche et droite du bandeau, fond et transparence PNG.
- Filigrane semi-transparent et mentions de droits en fin de bandeau.
- Formulations éditables de copyright, crédits et licences Creative Commons.
- Export du bandeau entier ou par morceaux numérotés dans un ZIP.
- Hauteur des morceaux réglable, préréglages WEBTOON et Tapas, alertes de dimensions et de poids.
- Sauvegarde locale IndexedDB, instantané précédent et protection contre les écritures concurrentes.
- Téléchargement et ouverture de projets `.webtooner` comprenant les images.

### Présentation et documentation

- Nom public `webtooner`, fichier `webtooner.html`, en-tête stable 1.0.0.
- Charte Eigrutel Lab, icône locale et footer Eigrutel BD Academy.
- Textes de l’interface sans tiret cadratin.
- Page `index.html`, README, notice, licences, guide utilisateur, dossier d’architecture et instructions de publication.

### Licences

- Code : GNU AGPL v3.0 ou ultérieure.
- Documentation et modèles : CC BY-SA 4.0, sauf mention contraire.
- Marques, logos et signes distinctifs Eigrutel, Eigrutel Lab et Eigrutel BD Academy réservés.

## English summary

### [1.1.0] - 2026-11-17

Integrated bilingual Webtoon reader with multiple local images, natural filename ordering, direct image URLs, a thin scrollbar, reading progress, back-to-top and Clear controls. Lightweight previews use a maximum width of 480 px, sequential processing and lazy-loaded segments up to 2048 px tall. Original files remain unchanged. Remote optimization depends on server permissions, with direct display as a fallback. Project format is unchanged; reader images are session-only.


### [1.0.0] - 2026-10-15

First stable public release: local image cropping and panel management, vertical assembly, spacing, side margins, watermark, rights footer, whole-image and numbered ZIP exports, WEBTOON/Tapas presets, automatic local saving and portable project backups. Includes a bilingual application, presentation page, user guide, architecture documentation and publication instructions.

Source code: AGPL-3.0-or-later. Documentation and templates: CC-BY-SA-4.0. Eigrutel brands and distinctive signs reserved. User artwork retains its own rights.
