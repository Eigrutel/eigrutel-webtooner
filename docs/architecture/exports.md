# Rendu et exports

## Cases individuelles

Les découpes mémorisées sont des PNG sans marge. `settings()` distingue le profil Réseau, limité au grand côté sans agrandissement, et Impression, en pixels d’origine à 300 dpi. Les marges individuelles s’appliquent sur les quatre côtés ; les millimètres sont convertis à 300 dpi en mode Impression. Le JPG est aplati sur le fond ; le PNG peut conserver l’alpha.

`dims()` borne un Canvas de découpe à 32 760 px par dimension et 80 millions de pixels. Le navigateur peut imposer des limites inférieures.

## Plan du bandeau

`plan()` utilise la largeur finale W et la marge latérale M. La largeur de dessin est `W - 2M`. La hauteur de chaque case est arrondie proportionnellement, avec un minimum de 1 pixel. Les lignes du plan portent leur position `top`, leur `scaledHeight` et l’espace `before`.

L’espacement global s’applique avant chaque vraie case après la première. Les bandes `isSpacer` s’ajoutent à ces espaces sans multiplier le nombre d’espacements automatiques. La hauteur du pied de droits s’ajoute une seule fois à la fin. Les marges du bandeau restent latérales.

L’aperçu utilise des images, blocs HTML et SVG. L’export utilise Canvas, `paintOverlays()` et les mêmes coordonnées globales. Le filigrane est centré et découpé aux limites de chaque case ; les espaces et le pied de droits sont exclus.

## Bandeau entier

- JPG : Canvas complet, limite de hauteur 32 760 px.
- PNG avec `CompressionStream` : calcul par tranches de 512 lignes, filtrage PNG et compression deflate. Cette voie évite un Canvas géant pour tout le bandeau.
- PNG sans `CompressionStream` : repli sur Canvas complet, avec la même limite de hauteur que cette voie.

La limite globale de l’assemblage reste de 180 millions de pixels et 1 000 000 px de hauteur. Largeur : de 1 à 8 192 px. Espacement : de 0 à 8 192 px. Ces garde-fous n’assurent pas la disponibilité de mémoire sur tous les appareils.

## Morceaux numérotés

La hauteur H est un entier entre 1 et 8 192 px. Pour un bandeau de hauteur T, le nombre de morceaux est `ceil(T / H)`. Le morceau i commence à `i * H` et mesure `min(H, T - i * H)`. Il n’y a ni chevauchement de lignes ni blanc terminal ajouté.

`exportCanvas(p, type, offset, tileHeight)` dessine les portions qui rencontrent la tranche et déplace le rendu de `offset`. Les mentions et filigranes conservent leurs positions dans le bandeau, même lorsqu’une coupure les traverse. Les morceaux sont encodés un par un, puis regroupés dans le ZIP. Les blobs encodés restent en mémoire jusqu’à la création de l’archive ; ce n’est pas un téléchargement ZIP en streaming.

Noms : `nom-001.png`, `nom-002.png`, etc., ou `.jpg`. Le dernier morceau peut être plus court. La découpe est géométrique : aucune détection des cases, des bulles ou des lignes de texte.

L’archive utilise la fonction ZIP interne, CRC-32, noms UTF-8 et stockage sans recompression. Les PNG/JPG sont déjà compressés. Les limites ZIP classiques sont vérifiées : 65 535 entrées et offsets sur 32 bits. L’annulation interrompt le traitement sans vider les cases ; une erreur ne publie pas de résultat partiel.

## Préréglages et contrôles

| Cible | Réglage appliqué | Avertissement après encodage |
| --- | --- | --- |
| Personnalisé | Dimensions conservées | Aucune vérification spécifique à une plateforme |
| WEBTOON | Largeur 800, hauteur 1 280 | Largeur >800, hauteur choisie >1 280, image >2 000 000 octets, total >20 000 000 octets ou >100 images |
| Tapas | Largeur 940, hauteur conservée | Largeur >940 ou image >=10 000 000 octets |

Les seuils en octets sont conservateurs. Le contrôle porte sur les images avant archivage. Le poids affiché du ZIP est exprimé en unités de 1 048 576 octets. Les alertes permettent encore de télécharger le résultat ; elles ne corrigent pas automatiquement la qualité ni les dimensions.

Tapas ne fixe plus de hauteur maximale pour JPG/PNG ; l’ancienne valeur 4 000 px n’est pas une contrainte appliquée. Les deux services peuvent découper automatiquement les longues images à l’import. Les contraintes peuvent évoluer et doivent être revérifiées avant de modifier les préréglages.

Sources officielles consultées le 15 octobre 2026 :

- [Tapas, File Size Overview](https://help.tapas.io/hc/en-us/articles/360052100813-File-Size-Overview)
- [Tapas, suppression de la limite de hauteur](https://tapas.io/newsfeed/180)
- [WEBTOON, découpe automatique](https://m.webtoons.com/en/notice/detail?noticeNo=1766)
- [WEBTOON Academy, conditions de fichiers](https://m.webtoons.com/fr/creators101/webtoon-academy)
- [WEBTOON, Creator Resource Handbook](https://webtoons-static.pstatic.net/creator101/en/pdf/Creators-Resource-Handbook-Updated.pdf?dt=2024011501)
