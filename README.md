# HUXA — Conseil solaire

Landing page statique de l'activité de conseil photovoltaïque de HUXA (préqualification gratuite, analyse de devis, étude et dimensionnement, accompagnement), cible du QR code de la carte de visite. Destinée à être publiée sur **https://solaire.huxa.io** via GitHub Pages.

- HTML/CSS pur, aucune dépendance ni étape de build.
- Aucun cookie ni traceur publicitaire. Polices Fraunces et IBM Plex Sans hébergées sur le site (`fonts/`). Services externes : Web3Forms (envoi du formulaire de contact par e-mail) et GoatCounter (statistiques de fréquentation, sans cookie).
- Illustrations en SVG inline, aucune image bitmap.

## Fichiers

| Fichier | Rôle |
| --- | --- |
| `index.html` | La page d'accueil (CSS inline). La FAQ (section `faq`) est dupliquée dans les données structurées `FAQPage` en tête de fichier : modifier les deux ensemble. Les tarifs se modifient dans le tableau de la section `tarifs`, dans les étiquettes des cartes « Dès … € » et dans les données structurées (`minPrice`) |
| `mentions-legales.html` | Mentions légales (LCEN) |
| `autorisation-drone.html` | Formulaire d'autorisation de survol par drone, à remplir et faire signer (non référencé, imprimable sur une page A4) |
| `favicon.svg` | Icône du site (le soleil du logo) |
| `logo.png` | Logo carré pour les données structurées (Google) |
| `og-image.png` | Image d'aperçu lors du partage d'un lien (WhatsApp, SMS, réseaux sociaux) |
| `fonts/` | Polices Fraunces et IBM Plex Sans (sous-ensemble latin, licence SIL OFL 1.1) |
| `CNAME` | Domaine personnalisé pour GitHub Pages |
| `robots.txt`, `sitemap.xml` | Référencement |

## Aperçu local

Ouvrir `index.html` dans un navigateur, ou :

```sh
python3 -m http.server 8000
# puis http://localhost:8000
```

## Formulaire de contact (Web3Forms)

Le formulaire envoie les demandes directement par e-mail, sans ouvrir la messagerie du visiteur.

- Compte Web3Forms : `solaire@huxa.io` (https://app.web3forms.com), formulaire « Contact solaire.huxa.io ». Les demandes arrivent dans la boîte partagée `solaire@huxa.io` (destinataire réglé dans *Settings → Email Configuration*).
- La clé d'accès est dans `index.html` (`var CLE_WEB3FORMS="…"`, en bas de page). Elle n'est pas secrète : elle peut figurer dans le code public.

Si la clé vaut `A_COMPLETER`, ou si l'envoi échoue, le formulaire se rabat sur l'ouverture de la messagerie (ancien comportement). Offre gratuite : 250 envois par mois. Les pièces jointes (devis, photos) restent à envoyer par e-mail : le message de confirmation le propose.

## Statistiques de consultation (GoatCounter)

1. Créer un compte gratuit sur https://www.goatcounter.com/signup avec le code **`huxa-solaire`** (le site enverra alors ses données à `https://huxa-solaire.goatcounter.com`). Si ce code n'est pas disponible, en choisir un autre et le remplacer dans `index.html` et `mentions-legales.html` (balise `data-goatcounter` en bas de page).
2. Dans les réglages du site GoatCounter, cocher éventuellement « Ignore IPs » avec sa propre adresse pour ne pas compter ses visites.
3. Le tableau de bord (`https://huxa-solaire.goatcounter.com`) affiche pages vues, visiteurs, provenance (QR code, Google…), navigateurs, écrans et pays.

Événements suivis en plus des pages vues : `formulaire-envoye`, `formulaire-erreur`, `clic-telephone`, `clic-mail-devis`, `clic-mail-contact`.

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
