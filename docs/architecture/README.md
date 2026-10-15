# Architecture de webtooner 1.0.0

Dossier technique de la version stable du 15-10-2026. Auteur : Simon Léturgie, Eigrutel Lab / Eigrutel BD Academy. Documentation CC BY-SA 4.0.

## Périmètre

Application autonome dans `webtooner.html` : HTML, CSS et JavaScript intégrés. Pas de build, dépendance JavaScript externe, API distante, service worker ou backend. `index.html` est une page de présentation indépendante. Le favicon est un asset local facultatif pour le fonctionnement.

L’application est issue de Cutter/Strip. Des identifiants de stockage hérités sont volontairement conservés pour ne pas interrompre la récupération des préférences. Le numéro public 1.0.0 est indépendant de la version du schéma de données.

## Organisation logique

Ces composants sont des fonctions et groupes de code dans le même fichier, pas des modules physiques distincts.

| Composant | Repères dans le code | Responsabilité |
| --- | --- | --- |
| Interface et langue | `words`, `t`, `translate` | Textes FR/EN, événements et aide |
| État de découpe | `image`, `rect`, `selectionLocked`, `cases` | Source, rectangle, verrou et collection ordonnée |
| Sélection | `normalize`, `updateSelection`, événements pointer/clavier | Coordonnées de source, redimensionnement et déplacement |
| Focus | `focusSession`, `openFocus`, `closeFocus` | Réutilisation de la surface de découpe et retour à l’état principal |
| Exports de cases | `settings`, `renderExport`, `runExport` | Résolution, marges, encodage et téléchargements |
| ZIP | `zip`, CRC-32 | Archives ZIP sans bibliothèque tierce |
| Présentation du bandeau | `rightsLayout`, `watermarkLayout`, `paintOverlays` | Mise en page des droits et filigranes |
| Assemblage | `window.assembly`, `plan`, `stats` | Dimensions, aperçu, validation et export vertical |
| Sauvegarde | `window.projectStore` | Journal IndexedDB et sauvegardes portables |

## Chaîne de traitement

1. L’import décode une image locale et crée une URL objet pour son affichage.
2. La sélection travaille dans les pixels de la source ; le zoom reste une transformation d’affichage.
3. Mémoriser crée une découpe PNG, stockée avec ses dimensions et son nom.
4. L’assemblage calcule les hauteurs à largeur cible, les espaces, les marges et le pied de droits.
5. L’aperçu DOM/SVG représente ce plan ; les exports le dessinent sur Canvas.
6. Les blobs produits sont téléchargés par liens temporaires. La collection reste disponible.
7. Les changements d’état déclenchent une sauvegarde différée.

## Interfaces du dépôt

| Fichier | Usage |
| --- | --- |
| `webtooner.html` | Point d’entrée de l’application |
| `index.html` | Page d’accueil du dépôt publié |
| `.webtooner` | Projet portable JSON contenant médias et état |
| PNG/JPG | Images finies, sans état d’édition |
| ZIP | Ensemble de cases ou de morceaux numérotés |

## Documents détaillés

- [Données et persistance](donnees.md)
- [Rendu et exports](exports.md)
- [Validation et maintenance](validation.md)
- [Utilisation](../utilisation.md)
- [Publication GitHub](../publication-github.md)

## Principes de maintenance

Conserver les schémas et identifiants de stockage tant qu’aucune migration n’est prévue. Ne pas modifier les fonctions de cadrage à l’occasion d’une simple retouche de présentation. Documenter toute évolution dans `changelog.md`. Conserver les mentions d’auteur et de licence. Les versions dérivées ne doivent pas se présenter comme une publication officielle d’Eigrutel sans autorisation.
