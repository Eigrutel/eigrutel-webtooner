# webtooner

**Version stable 1.0.0 • 15 octobre 2026**

Eigrutel Lab - Atelier d’outils libres pour la bande dessinée.
Programme conçu et développé par **Simon Léturgie** dans le cadre d’**Eigrutel BD Academy**.

**Découper des cases, les assembler en webtoon et préparer leur publication.**

[Ouvrir l’application](webtooner.html) · [Présentation](index.html) · [Guide](docs/utilisation.md) · [Architecture](docs/architecture/README.md)

## Utilisation

Télécharger le dépôt, décompresser puis ouvrir `webtooner.html` dans un navigateur récent. L’application fonctionne localement, sans installation ni compte. Elle peut aussi être hébergée comme un site statique, notamment sur GitHub Pages. Aucun serveur applicatif, compilation ou bibliothèque tierce n’est nécessaire.

1. Charger une image et sélectionner une case, ou ajouter des images entières.
2. Mémoriser, nommer et ordonner les cases. Cliquer sur une miniature pour reprendre son cadrage.
3. Choisir largeur, espaces et marges du bandeau.
4. Ajouter, si souhaité, filigrane et mentions de droits.
5. Créer puis télécharger le bandeau entier ou ses morceaux numérotés.

L’export conserve le travail en cours pour produire d’autres formats.

## Fonctionnalités

| Domaine | Possibilités |
| --- | --- |
| Découpe | Sélection souris/tactile, dimensions, cadenas, zoom, déplacement de la vue |
| Cases | Renommage, ordre, recadrage focus, images originales conservées pour reprendre le cadrage |
| Assemblage | Largeur libre, espacement global, bandes transparentes ajoutées avec « + espace » |
| Présentation | Marges latérales, fond, transparence PNG, filigrane, droits en fin de bandeau |
| Exports | JPG/PNG, cases individuelles, ZIP de cases, bandeau entier, ZIP de morceaux |
| Formats de publication | Hauteur réglable, préréglages WEBTOON et Tapas, alertes de limites |
| Projets | Sauvegarde automatique locale, version précédente, fichier portable `.webtooner` |
| Langues | Français et anglais |

## Données et sauvegarde

Les images sont traitées dans le navigateur. Le programme ne les envoie à aucun serveur et n’intègre ni traceur ni télémétrie. Les liens externes ne s’ouvrent qu’à votre initiative.

Le travail est enregistré dans IndexedDB sur le navigateur et l’origine utilisés. Un changement d’adresse, de navigateur, d’appareil ou l’effacement des données peut rendre cette copie inaccessible. L’ouverture en fichier local dépend des politiques du navigateur. **Télécharger le projet** produit une sauvegarde indépendante avec les images ; **Ouvrir un projet** permet de la reprendre ailleurs. Les images exportées ne remplacent pas ce fichier de travail.

## Contenu du dépôt

| Fichier ou dossier | Rôle |
| --- | --- |
| `webtooner.html` | Application autonome, source complète |
| `index.html` | Page de présentation avec ouverture et téléchargement |
| `favicon/` | Icône locale |
| `notice.md` | Auteur, attribution et marques réservées |
| `license.md`, `licenses/` | Régime de licences et texte GNU AGPL |
| `changelog.md` | Historique public |
| `docs/utilisation.md` | Notice d’utilisation |
| `docs/architecture/` | Architecture, données, exports et validation |
| `docs/publication-github.md` | Dépôt, GitHub Pages et release |
| `docs/release-1.0.0.md` | Texte prêt pour la première release |

## Limites et validation

Le navigateur et la mémoire disponible déterminent les dimensions réellement exportables. La découpe peut traverser une case ou un texte : elle suit une hauteur fixe, sans analyse du dessin. Les préréglages vérifient des dimensions et des poids ; ils ne publient rien et ne garantissent pas l’acceptation éditoriale par une plateforme.

Les tests locaux ont vérifié les exports, les raccords des morceaux, les marges, le filigrane, les mentions et la restauration des projets. La vérification visuelle et tactile sur iPad reste à effectuer. Voir [la fiche de validation](docs/architecture/validation.md).

## Licences et attribution

Copyright © 2026 Simon Léturgie.

- Code : **GNU AGPL v3.0 ou version ultérieure**, `AGPL-3.0-or-later`.
- Documentation et modèles : **CC BY-SA 4.0**, sauf mention contraire.
- Marques, logos et signes distinctifs **Eigrutel**, **Eigrutel Lab**, **Eigrutel BD Academy** réservés.
- Les créations importées et exportées conservent leurs propres droits.

Voir [license.md](license.md) et [notice.md](notice.md).

[Eigrutel Lab](https://www.stripmee.com/eigrutel-lab/) · [Eigrutel BD Academy](https://www.stripmee.com/eigrutel-bd-academy-2/)

## English

**webtooner 1.0.0** is a standalone, bilingual tool for cropping comic panels, arranging a vertical webtoon and exporting either a complete strip or numbered image pieces in a ZIP file.

Open `webtooner.html` in a recent browser. No account, build step, backend or third-party library is required. All artwork processing stays on your device. Local automatic saving uses IndexedDB; download a `.webtooner` project for a portable backup including images. Browser storage can be cleared or become unavailable.

The app includes crop locking, focus editing, panel spacing, side margins, translucent watermarks, a rights footer, PNG/JPG exports and WEBTOON/Tapas presets. Platform limits may change. Fixed-height splitting can cut through artwork or lettering. iPad visual and touch validation remains pending.

Created by Simon Léturgie for Eigrutel BD Academy and Eigrutel Lab. Code: AGPL-3.0-or-later. Documentation/templates: CC-BY-SA-4.0. Eigrutel brands reserved. User artwork retains its own rights.
