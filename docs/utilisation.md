# Utiliser webtooner 1.0.0

## 1. Charger et découper

Ouvrir `webtooner.html`. Charger un JPG, PNG ou WebP, puis tracer ou ajuster la sélection. Les champs largeur et hauteur correspondent aux pixels de l’image originale. Le zoom ne change que l’affichage.

Fermer le cadenas pour déplacer la zone sans modifier ses dimensions ni la recréer par un clic extérieur. Le rouvrir pour redimensionner. « Déplacer la vue » sert à naviguer dans l’image. Cliquer sur « Mémoriser la case » pour conserver la découpe. Charger une autre image conserve les cases précédentes.

## 2. Organiser les cases

Renommer les cartes, les déplacer par glisser-déposer ou avec les boutons Monter/Descendre. Cliquer sur une miniature pour ouvrir le recadrage en focus. Appliquer valide la nouvelle découpe ; Annuler la laisse intacte. L’image de départ de la case reste disponible pour reprendre son cadrage.

« Ajouter des images entières » permet d’importer directement plusieurs cases.

« + espace » crée une bande transparente de 40 px à la largeur d’assemblage courante. Déplacer sa carte entre les cases. Plusieurs bandes se cumulent. Leur hauteur finale évolue proportionnellement si la largeur ou les marges changent ensuite. Elles prennent la couleur du fond, ou restent transparentes pour un PNG transparent.

## 3. Exporter les cases

Le profil Réseau limite le grand côté sans agrandir. Le profil Impression conserve les pixels et inscrit une résolution de 300 dpi. Une marge optionnelle s’ajoute sur les quatre côtés de chaque export individuel. Exporter une case seule ou toutes les cases dans un ZIP.

Ces réglages sont distincts de ceux du bandeau. Les exports ne vident pas le travail.

## 4. Assembler le bandeau

Choisir la largeur finale, l’espacement global entre cases et JPG ou PNG. Les proportions des dessins sont conservées. Le réglage de marge commun ajoute ici uniquement une marge gauche et droite, incluse dans la largeur finale.

Le filigrane superpose un texte à chaque case avec couleur, taille et opacité. Il ne s’applique pas aux bandes d’espace ni au pied de droits. Le champ Droits / copyright / CC est ajouté à la fin du bandeau. « Formulations » propose des textes à copier, modifier ou insérer. Remplacer les noms et titres proposés ; choisir soi-même les droits de diffusion de son œuvre.

## 5. Exporter en morceaux

1. Choisir « En plusieurs morceaux (ZIP) ».
2. Choisir Personnalisé, WEBTOON ou Tapas.
3. Régler la hauteur des morceaux en pixels de sortie.
4. Cliquer sur « Créer le bandeau », puis « Télécharger ».
5. Décompresser le ZIP et charger les images dans l’ordre numérique sur le service choisi.

Le préréglage WEBTOON règle la largeur à 800 px et la hauteur à 1 280 px. Tapas règle la largeur à 940 px et conserve la hauteur personnalisée. Les dimensions restent modifiables. La dernière image est plus courte lorsque nécessaire, sans blanc ajouté. Les mentions restent à leur emplacement en fin de bandeau, sans répétition sur chaque morceau.

La découpe suit une hauteur fixe et peut traverser une case ou une ligne de texte. Les morceaux remis bout à bout reconstituent le bandeau. Les alertes de dépassement n’empêchent pas de télécharger le ZIP : corriger les dimensions ou la qualité JPG avant publication si nécessaire. Le poids du ZIP n’est pas le poids des images à charger.

WEBTOON et Tapas disposent aussi d’une découpe automatique à l’import. Les paramètres connus sont documentés dans [exports.md](architecture/exports.md).

## 6. Reprendre son travail

Le statut de sauvegarde indique si le travail est enregistré sur cet appareil. La réouverture sur le même navigateur et à la même adresse tente de le restaurer. « Version précédente » restaure l’instantané précédent, pas un historique illimité.

Télécharger régulièrement le projet `.webtooner`, surtout avant de changer d’appareil, d’adresse, de navigateur ou de nettoyer ses données. Pour le reprendre, utiliser « Ouvrir un projet ». Cette opération remplace le travail en cours après confirmation. En cas d’alerte de conflit entre fenêtres, télécharger sa copie avant de continuer.

La sauvegarde du navigateur améliore la récupération après fermeture, mais ne garantit pas la conservation en cas d’effacement, de panne ou de quota dépassé.

## English quick guide

Load an image, select and store panels, then arrange them in the desired order. Lock the crop dimensions to move the selection without resizing. Click a panel thumbnail to edit its crop. Add spacing, side margins, a watermark and rights text as needed.

Choose a whole-strip export or numbered pieces. Set the piece height, create the export, download the ZIP, extract it and upload images in numerical order. The final piece may be shorter. Fixed-height slicing can cross artwork or text. Export does not clear your work.

Download a `.webtooner` project to keep an independent backup. Automatic saving is tied to the browser and origin and can be cleared. Use Open project to restore a portable backup.

Copyright © 2026 Simon Léturgie / Eigrutel Lab / Eigrutel BD Academy. Documentation CC BY-SA 4.0.
