# Données et persistance

## État en mémoire

La source active est conservée avec son Blob, son nom et son URL objet. Le rectangle contient `x`, `y`, `w`, `h` en pixels de source. Le zoom, le défilement, le mode déplacement et le cadenas décrivent la vue.

`cases` est une liste ordonnée. Une entrée comporte `id`, `name`, `width`, `height`, `blob`, `url`, `source`, `isSpacer` et, si disponibles, `cropRect` et `cropSource`. Le recadrage en focus conserve l’image originale de la case pour permettre de réélargir sa découpe. Un espace est une vraie image transparente marquée `isSpacer`.

Les URL objet sont temporaires. Les sauvegardes conservent les Blobs ; la restauration recrée les URL. Les URL inutilisées sont révoquées lorsque les images sont remplacées ou retirées.

## IndexedDB

| Élément | Valeur |
| --- | --- |
| Base | `eigrutel-webtooner-project` |
| Version de base | `1` |
| Object store | `projects` |
| Instantané courant | `latest` |
| Instantané précédent | `previous` |
| Format de projet | `eigrutel-webtooner` |
| Version de schéma | `1` |
| Version publique de l’application | `appVersion: "1.0.0"` |

Un instantané comprend langue, contrôles, source, vue principale, éventuel focus en cours et cases avec leurs médias. `savedAt` et `token` identifient l’écriture. Les deux instantanés sont mis à jour dans une transaction ; la durabilité stricte est demandée lorsque le navigateur la prend en charge.

La sauvegarde est différée de 300 ms pour regrouper les saisies. Pendant une opération occupée elle est reportée. Les écritures sont sérialisées, puis répétées si une révision plus récente arrive. `pointerup`, le passage en arrière-plan et `pagehide` demandent une écriture. `beforeunload` avertit en cas de travail non sauvegardé ou d’opération en cours, selon les possibilités du navigateur.

Avant écriture, le token de `latest` est comparé au token connu. Un changement par une autre fenêtre bloque l’écrasement et invite à télécharger sa copie. Une sauvegarde persistante est demandée au navigateur au mieux de ses possibilités ; elle n’est pas garantie.

Au démarrage, `latest` est validé et ses images décodées. Si sa restauration échoue, `previous` est essayé. Un échec est signalé. Ce mécanisme ne remplace pas une copie externe et ne constitue pas un historique complet.

## Préférences héritées

`localStorage` conserve `cutter-language` et `cutter-assembly-v1`. Ces noms internes restent inchangés malgré le nom public webtooner. Le projet IndexedDB mémorise aussi les réglages complets, y compris mode d’export, cible et hauteur des morceaux.

## Fichier portable

Le fichier `.webtooner` est un JSON UTF-8 dont l’enveloppe contient :

```json
{
  "format": "webtooner-backup",
  "version": 1,
  "project": {},
  "assets": {}
}
```

Les objets ci-dessus sont volontairement vides pour illustrer la structure ; ce n’est pas un projet importable. Chaque média est placé dans `assets` avec son type MIME et ses données Base64. Les références prennent la forme `{ "$asset": "asset-1" }`. Les Blobs identiques par identité sont dédupliqués pendant la sérialisation.

L’import vérifie enveloppe, schéma, médias, dimensions, identifiants et coordonnées avant de remplacer l’état. Limites codées : 512 Mio pour le fichier, 10 000 cases et types image PNG/JPEG/WebP. La préparation des images précède le remplacement pour préserver le projet en cas de fichier invalide.

Le schéma reste en version 1 lors du passage public à 1.0.0. Les projets des versions de préparation utilisant ce schéma restent compatibles ; aucun numéro de base n’est réinitialisé.

## Confidentialité

Aucun envoi de médias ni suivi distant n’est prévu. Le stockage dépend de l’origine : une nouvelle URL ou un fichier local ouvert différemment peut disposer d’un autre stockage. Les données ne sont pas chiffrées par l’application. Le projet portable contient les images et doit être partagé en conséquence.
