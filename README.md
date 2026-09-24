# Kemenn — site vitrine

Site statique, une seule page. Aucune dépendance, aucun build.

```
index.html      le site (FR / NL / EN / DE)
logiciel.html   la démo du logiciel, servie sur /logiciel
og.jpg          image de partage (réseaux sociaux, messageries)
favicon.svg     icône d'onglet
logo.svg        logo Kemenn
vercel.json     en-têtes, URL sans .html, redirection /demo → /logiciel
```

## Mise en ligne sur Vercel

1. Créer un dépôt sur GitHub (par exemple `kemenn-web`) et y pousser ces fichiers :

```bash
git init
git add .
git commit -m "Site vitrine Kemenn"
git branch -M main
git remote add origin git@github.com:<ton-compte>/kemenn-web.git
git push -u origin main
```

2. Sur [vercel.com](https://vercel.com) : **Add New → Project → Import Git Repository**, choisir le dépôt.
3. Framework Preset : **Other**. Laisser les commandes de build vides, Output Directory vide.
4. **Deploy**. Le site est en ligne sur `<projet>.vercel.app` en une minute environ.

Chaque `git push` sur `main` redéploie automatiquement.

## Domaine kemenn.be

Dans le projet Vercel : **Settings → Domains → Add**, saisir `kemenn.be`, puis créer chez ton registrar
les enregistrements DNS que Vercel affiche (en général un `A` vers `76.76.21.21` pour le domaine nu
et un `CNAME` vers `cname.vercel-dns.com` pour `www`). Le certificat HTTPS est automatique.

## Avant la mise en ligne publique

- **La marque.** Le site affiche `Kemenn®`. Le symbole ® suppose une marque déposée : tant que le dépôt
  BOIP n'est pas effectué, utiliser `™`.
- **Les mentions légales.** Les pages du pied de page contiennent des champs à compléter :
  société, adresse, numéro BCE, numéro de TVA, responsable de la publication, hébergeur.
- **Les photos.** Vérifier la licence des photos produits utilisées dans les visuels.
- **L'email de contact.** `hello@kemenn.be` doit exister avant de le publier.

## Poids de la page

`index.html` pèse environ 3 Mo, car toutes les images sont encodées en base64 dans le fichier.
Ça fonctionne, mais le premier affichage est lent sur mobile. Étape suivante : sortir les images
dans `/img` et les charger en `lazy`.
