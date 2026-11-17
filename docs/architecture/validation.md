# Validation et maintenance

## État de validation

Le propriétaire du projet a retenu cette livraison comme première version stable publique, 1.0.0. Ce passage modifie l’identité publique, l’en-tête et la documentation ; les fonctions de la version de préparation restent conservées.

Des tests locaux JavaScript ont été exécutés avec simulation du DOM, Canvas et IndexedDB. Ils ne constituent pas un essai visuel dans Safari iPad.

| Domaine | Vérifications réalisées |
| --- | --- |
| Exports existants | PNG/JPG, PNG long et repli sans CompressionStream |
| Présentation | Marges latérales seules, droits en bas, filigrane excluant espaces et marges |
| Découpe en morceaux | Ordre, noms, dimensions, dernier morceau, ZIP lisible |
| Raccords | Recomposition des pixels comparée au bandeau entier ; un écart de rendu de 1 niveau sur un canal a été constaté sur un pixel du jeu d’essai, lié à la rastérisation selon le décalage |
| Réglages | Préréglages WEBTOON/Tapas, refus d’une hauteur nulle, persistance des choix |
| Reprise | Images, sources de recadrage, espaces, réglages et focus non terminé |
| Sauvegarde | Projet portable, repli sur instantané précédent, conflit entre fenêtres, données invalides |
| Livraison | Liens locaux, syntaxe JavaScript, identité et en-tête, archive du dépôt |

## Recette manuelle recommandée sur iPad

1. Ouvrir l’application, importer une image et créer trois cases.
2. Tester déplacement, poignées, zoom et cadenas au tactile.
3. Réordonner les cases ; ouvrir un focus, appliquer puis annuler un autre cadrage.
4. Ajouter deux espaces et comparer l’aperçu et l’export.
5. Ajouter une marge, un filigrane et un pied de droits.
6. Exporter PNG et JPG entiers, puis un ZIP de morceaux avec dernier morceau plus court.
7. Décompresser et vérifier les raccords et le pied de droits.
8. Télécharger un projet, fermer et rouvrir l’application, puis réimporter le projet.
9. Vérifier rotation, petit écran, téléchargement et statut de sauvegarde dans Safari.

## Points à préserver

- Aucun effacement du travail à la fin d’un export.
- Différence entre marges individuelles (quatre côtés) et marges du bandeau (deux côtés).
- Coordonnées de dessin indépendantes du zoom d’affichage.
- Sources de recadrage conservées pour les cases éditées.
- Mention de droits unique dans le plan global.
- Version de schéma indépendante de la version publique.
- Pas de scripts, fontes ou traitements tiers distants.
- Textes visibles sans tiret cadratin.

## Évolution de version

Mettre à jour le commentaire d’en-tête, `appVersion` dans les sauvegardes, les métadonnées et le numéro visible de la présentation, puis le README et le changelog. Ne changer la version du schéma que si son format change réellement et avec une migration documentée. Les textes normatifs des licences doivent rester intacts.

## Validation de la version 1.1.0

- Analyse syntaxique de tout le JavaScript et contrôle des identifiants HTML.
- Tests de logique avec objets navigateur simulés : réduction à 480 px, découpage en segments, ordre multi-images, libération des URLs Blob, vidage pendant le chargement.
- Contrôle des liens locaux et comparaison des fichiers avec l’archive 1.0.0.
- Le lecteur a été validé par l’utilisateur dans la conversation. Les tests automatisés ci-dessus ne constituent pas une mesure de mémoire ni un test de rendu navigateur ; le lancement du navigateur de test est indisponible dans cet environnement.
