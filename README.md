# Atelier Benvenisti — déploiement

`index.html` est le site complet dans un seul fichier (5,9 Mo, images incluses).
Aucun build, aucune dépendance : il s'ouvre hors ligne et fonctionne tel quel sur
n'importe quel hébergement statique.

## GitHub Pages

1. Créer un dépôt dédié au site, par exemple `benvenisti-site` (voir la note plus bas).
2. Déposer `index.html` à la racine du dépôt, sur la branche `main`.
3. Dépôt → **Settings → Pages** → Source : *Deploy from a branch*, branche `main`, dossier `/ (root)`.
4. Au bout d'une à deux minutes le site est en ligne sur `https://<compte>.github.io/<dépôt>/`.

## Domaine otoart.fr

1. Dépôt → **Settings → Pages → Custom domain** : saisir `otoart.fr`, puis **Save**.
   GitHub crée un fichier `CNAME` dans le dépôt — le laisser en place.
2. Chez le registrar du domaine, créer les enregistrements suivants :

   | Type  | Nom   | Valeur                 |
   |-------|-------|------------------------|
   | A     | `@`   | `185.199.108.153`      |
   | A     | `@`   | `185.199.109.153`      |
   | A     | `@`   | `185.199.110.153`      |
   | A     | `@`   | `185.199.111.153`      |
   | CNAME | `www` | `<compte>.github.io.`  |

3. Ne pas toucher aux enregistrements MX : les adresses e-mail du domaine restent intactes.
4. Une fois la propagation faite (de 1 h à 24 h), cocher **Enforce HTTPS** dans Settings → Pages.

## Mise à jour du site

Le fichier est régénéré depuis le projet de design, puis remplacé dans le dépôt.
Ne pas éditer `index.html` à la main : il est compilé.

## Note sur le dépôt

Le dépôt connecté, `LordZord13/Python---Jupyter-Lab` (branche `Jupyter-Lab`), est un
dépôt Python/Jupyter. GitHub Pages ne publie qu'un seul site par dépôt et servirait
alors le site à côté des notebooks, avec un nom d'URL trompeur. Un dépôt neuf dédié
au site est préférable.
