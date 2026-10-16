# HUXA — Conseil solaire

Landing page statique de l'activité de conseil photovoltaïque de HUXA (préqualification gratuite, analyse de devis, étude et dimensionnement, accompagnement), cible du QR code de la carte de visite. Destinée à être publiée sur **https://solaire.huxa.io** via GitHub Pages.

- HTML/CSS pur, aucune dépendance ni étape de build.
- Aucun cookie ni traceur ; seules les polices Google Fonts (Fraunces, IBM Plex Sans) sont chargées.
- Illustrations en SVG inline, aucune image bitmap.

## Fichiers

| Fichier | Rôle |
| --- | --- |
| `index.html` | La page d'accueil (CSS inline). Les tarifs se modifient dans le tableau de la section `tarifs`, dans les étiquettes des cartes « Dès … € » et dans les données structurées (`minPrice`) |
| `mentions-legales.html` | Mentions légales (LCEN) |
| `autorisation-drone.html` | Formulaire d'autorisation de survol par drone, à remplir et faire signer (non référencé, imprimable sur une page A4) |
| `favicon.svg` | Icône du site (le soleil du logo) |
| `CNAME` | Domaine personnalisé pour GitHub Pages |
| `robots.txt`, `sitemap.xml` | Référencement |

## Aperçu local

Ouvrir `index.html` dans un navigateur, ou :

```sh
python3 -m http.server 8000
# puis http://localhost:8000
```

## À compléter dans `autorisation-drone.html`

- `[ASSUREUR ET N° DE CONTRAT À COMPLÉTER]` : RC drone professionnelle

## Mise en ligne (GitHub Pages)

1. **Rendre le dépôt public** : *Settings → General → Danger Zone → Change visibility → Public* (GitHub Pages sur dépôt privé nécessite un abonnement payant).
2. **Activer Pages** : *Settings → Pages → Build and deployment* → Source « Deploy from a branch », branche `main`, dossier `/ (root)` → *Save*.
3. **Domaine personnalisé** : dans la même page, *Custom domain* = `solaire.huxa.io` → *Save* (le fichier `CNAME` du dépôt le contient déjà).
4. **DNS** chez le registraire de `huxa.io` : créer un enregistrement
   `solaire  CNAME  homebelval.github.io.`
5. Attendre la validation DNS (quelques minutes à quelques heures), puis cocher **Enforce HTTPS** dans *Settings → Pages*.
6. Vérifier https://solaire.huxa.io sur mobile, puis scanner le QR code de la carte.

Recommandé : vérifier le domaine `huxa.io` dans *Settings du compte → Pages → Verified domains* pour empêcher toute prise de contrôle du sous-domaine.
