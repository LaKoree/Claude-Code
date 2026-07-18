# 🍋 Guide Gumroad complet — vendre tes fonds d'écran FLUX

Tout ce qu'il faut, de la création du compte jusqu'à l'argent sur ton compte bancaire.
Compte **~20 min** pour la première mise en place.

---

## 1. Pourquoi Gumroad (le principe)

Gumroad est une plateforme de vente de **produits numériques**. Tu y déposes tes fichiers, elle s'occupe
de tout le reste :

- ✅ **Page de paiement** sécurisée (carte, PayPal, Apple/Google Pay)
- ✅ **Livraison automatique** du fichier à l'acheteur (email + page de téléchargement)
- ✅ **TVA européenne** collectée et reversée à ta place (Gumroad est « merchant of record »)
- ✅ **Facture** générée pour le client

En échange, Gumroad prend une commission d'environ **10 % + frais de traitement** (~3,5 % + 0,30 €)
par vente. Cher au %, mais tu ne gères ni serveur, ni livraison, ni TVA — parfait pour démarrer.

> Ton site FLUX ne « contient » pas le paiement : chaque bouton **ouvre ta page Gumroad**. Tu colles
> simplement les liens Gumroad dans `index.html`.

---

## 2. Créer ton compte

1. Va sur **gumroad.com** → **Start selling**.
2. Inscris-toi (email + mot de passe, ou compte Google).
3. Renseigne ton **pays = France** et le **nom de ta boutique** (ex. `FLUX`). Ça te donne une adresse
   du type `https://flux.gumroad.com`.
4. Confirme ton email.

---

## 3. Configurer les paiements (pour être payé) — à faire tôt

Menu **Settings → Payments** :

- **Payout method** : renseigne ton **IBAN** (virement bancaire) ou ton **PayPal**.
- **Informations d'identité** : nom, adresse, date de naissance (obligatoire, c'est la vérification
  légale KYC — comme pour ouvrir un compte).
- **Rythme de versement** : Gumroad paie **chaque semaine (le vendredi)** dès que ton solde dépasse
  le seuil minimum (~10 $). L'argent d'une vente est versé après un court délai de sécurité.

> Tant que cette étape n'est pas complète, tu peux vendre mais tu ne recevras pas les virements.
> Fais-la dès le début.

---

## 4. Créer tes produits

Menu **Products → New product**. Pour FLUX, tout est en **Digital product** (paiement unique, aucun
abonnement). Crée ceux-ci :

| Produit | Prix | Contenu à téléverser |
|---|---|---|
| **Fond FLUX (à l'unité)** | 3,99 € | 1 fond (HTML + éventuellement la vidéo) |
| **Pack [Nom du thème]** — un produit par pack | 14,99 € | Les 6-8 fonds du thème |
| **Collection FLUX à vie** | 49 € | Tous les fonds |

> 💡 Commence avec **2-3 produits** (à l'unité + 1 pack + la collection). Tu ajouteras les autres packs
> au fur et à mesure.

### Étapes pour chaque produit

1. **Type** : *Digital product* → **Next**.
2. **Name** : ex. « Pack Aurora Boréale — Fonds d'écran dynamiques 4K ».
3. **Price** : mets le prix fixe (ex. `14.99`). Laisse décoché « pay what you want ».
4. **Next: Customize** → tu arrives sur l'éditeur du produit :
   - **Description** : vends le rêve. Ex. « 8 fonds d'écran vivants en 4K, thème Aurora Boréale.
     Formats téléphone + PC inclus. Optimisés batterie. Installation en 30 s. »
   - **Cover / Thumbnail** : ajoute une **image d'aperçu** attractive (une capture de l'animation).
     C'est ce qui fait cliquer — soigne-la.
   - **Content** : **téléverse tes fichiers** (les `.html` du dossier `wallpapers/`, et/ou les `.mp4`).
     Tu peux mettre plusieurs fichiers dans un même produit (pour un pack).
   - **Call to action** : le texte du bouton (« I want this! » → tu peux mettre « Je le veux ! »).
5. **Publish** (bouton en haut). Le produit est en ligne.

### Livraison : rien à faire

Dès qu'un client paie, Gumroad lui envoie **automatiquement** un email + une page de téléchargement
avec tes fichiers. Tu n'as rien à envoyer manuellement.

---

## 5. Récupérer les liens et les coller dans le site

Sur chaque produit publié : onglet **Share** → **Copy URL** (du type
`https://flux.gumroad.com/l/aurora`). Le morceau après `/l/` s'appelle le **permalink** et est
personnalisable (Settings du produit).

Ouvre **`index.html`**, tout en haut, et remplis le bloc :

```js
window.FLUX_STORE = {
  checkout: {
    single:   "https://flux.gumroad.com/l/fond-unite",
    pack:     "https://flux.gumroad.com/l/pack",        // lien par défaut d'un pack
    lifetime: "https://flux.gumroad.com/l/collection-a-vie"
  },
  items: {
    // Recommandé : un lien précis par pack (sinon "pack" ci-dessus est utilisé)
    "Pack Aurora Boréale": "https://flux.gumroad.com/l/aurora",
    "Pack Deep Space":     "https://flux.gumroad.com/l/deep-space",
    // … un par pack. Et éventuellement par fond à l'unité :
    // "Aurora Nord": "https://flux.gumroad.com/l/aurora-nord",
  },
  contactEmail: "ton-email@exemple.com"
};
```

Enregistre → commit → push (ou édite le fichier directement sur GitHub, crayon ✏️ → *Commit*).
Les boutons « Acheter le pack », « Passer à vie » et « Acheter » ouvrent maintenant tes vraies pages
de paiement. ✅

> **Comment les boutons choisissent le lien :** un bouton de pack envoie le nom du pack ; si ce nom
> existe dans `items`, ce lien est utilisé, sinon c'est `checkout.pack`. Pareil pour les fonds à
> l'unité avec `checkout.single`. Donc au minimum, remplis `single`, `pack` et `lifetime`.

---

## 6. Créer un code promo de lancement

Produit (ou boutique) → **Checkout → Offer codes → New offer code** :

- **Code** : ex. `LANCEMENT30`
- **Type** : pourcentage (`30%`) ou montant fixe.
- **Limites** : nombre d'utilisations max, date d'expiration (ex. 48 h).

Annonce-le dans tes stories TikTok/Insta pour créer l'urgence.

---

## 7. Après une vente

- Le client reçoit **email + téléchargement** automatiquement.
- Toi : tu vois la vente dans **Dashboard** (ventes, vues, taux de conversion, pays).
- L'argent s'accumule dans ton solde → **versé chaque vendredi** sur ton IBAN.
- Les clients peuvent laisser une **note/avis** → mets-les en avant, ça rassure les suivants.

---

## 8. Bonnes pratiques qui font vendre

- 🖼️ **Image d'aperçu soignée** sur chaque produit — c'est le n°1 du taux de clic.
- 💬 **Description orientée bénéfice** (« ton écran prend vie », pas « fichier mp4 1080p »).
- ⭐ **Demande un avis** après achat (email automatique de Gumroad).
- 🎁 Mets la **Collection à vie (49 €)** en avant : c'est ton meilleur panier moyen.
- 🔁 Ajoute régulièrement de **nouveaux packs** → tu peux ré-annoncer à tes anciens acheteurs.

---

## Récap express

1. Compte Gumroad + IBAN + identité → **pour être payé**.
2. Crée tes produits (Digital), **téléverse tes fonds**, publie.
3. Colle les liens dans `index.html`.
4. (Optionnel) code promo de lancement.
5. Envoie du trafic → Gumroad encaisse, livre et te vire l'argent chaque vendredi.
