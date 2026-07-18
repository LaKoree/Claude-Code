# 🚀 FLUX — Mettre le site en ligne et faire tes premières ventes

Ce guide te fait passer de « le site est prêt » à « je reçois de l'argent ».
Compte **~20 minutes**. Trois étapes : **1) mettre en ligne**, **2) encaisser**, **3) livrer**.

---

## Étape 1 — Mettre le site en ligne (gratuit, GitHub Pages)

Le site est un seul fichier `index.html`, donc l'hébergement est gratuit et instantané.

1. Va sur ton dépôt GitHub : **`LaKoree/Claude-Code`**.
2. Assure-toi que le dépôt est **public** (Settings → General → tout en bas → *Change visibility*).
   > GitHub Pages est gratuit sur les dépôts publics. (Sur un dépôt privé, il faut un plan payant.)
3. Ouvre **Settings → Pages**.
4. Sous **Build and deployment → Source**, choisis **« Deploy from a branch »**.
5. Branch : sélectionne **`claude/dynamic-wallpaper-sales-site-04nng6`** · Dossier : **`/ (root)`** · clique **Save**.
6. Attends ~1 minute, recharge la page : ton site est en ligne à l'adresse

   **`https://lakoree.github.io/Claude-Code/`**

> 💡 Quand tu voudras une adresse pro type `flux.com` : achète un domaine (Namecheap, OVH, ~10 €/an),
> puis renseigne-le dans **Settings → Pages → Custom domain**. Optionnel, à faire plus tard.

---

## Étape 2 — Encaisser les paiements (le plus important)

Tu n'as **pas besoin de coder** ni de serveur. Tu crées un « lien de paiement » chez un prestataire,
puis tu le colles dans `index.html`. Chaque bouton du site ouvre alors la vraie page de paiement.

### Quel prestataire choisir ?

| Prestataire | Idéal pour | Livraison du fichier | Gère la TVA (UE) | Frais indicatifs |
|---|---|---|---|---|
| **Gumroad** ⭐ | Débuter vite, produits numériques | ✅ automatique | ✅ oui | ~10 % + frais |
| **Lemon Squeezy** ⭐ | Vendeur UE, facturation propre | ✅ automatique | ✅ oui (merchant of record) | ~5 % + frais |
| **Stripe (Payment Links)** | Frais les plus bas, look pro | ❌ à gérer toi-même | ❌ à déclarer toi-même | ~1,5 % + 0,25 € |

> **Recommandation pour démarrer :** **Gumroad** ou **Lemon Squeezy**. Ils hébergent tes fichiers,
> les envoient automatiquement à l'acheteur, et gèrent la TVA européenne à ta place — parfait
> quand on vend depuis la France sans société montée.

### Exemple avec Gumroad (le plus rapide)

1. Crée un compte sur **gumroad.com** → *Start selling*.
2. **New product → Digital product**. Crée 3 produits qui correspondent aux offres du site :
   - « Fond d'écran FLUX (à l'unité) » — **3,99 €**
   - « Pass FLUX Mensuel » — **6,99 €** (abonnement / *membership*)
   - « Pass FLUX à vie » — **49 €**
3. Pour chaque produit, **téléverse le(s) fichier(s)** à livrer (voir Étape 3), publie, puis copie l'**URL du produit**
   (ex. `https://tonnom.gumroad.com/l/pass-mensuel`).
4. Ouvre **`index.html`** et colle ces URLs dans le bloc de config en haut du fichier :

   ```js
   window.FLUX_STORE = {
     checkout: {
       single:   "https://tonnom.gumroad.com/l/fond-unite",
       monthly:  "https://tonnom.gumroad.com/l/pass-mensuel",
       lifetime: "https://tonnom.gumroad.com/l/pass-a-vie"
     },
     items: {
       // Optionnel : un lien précis par fond, sinon "single" est utilisé
       // "Aurora Nord": "https://tonnom.gumroad.com/l/aurora-nord",
     },
     contactEmail: "ton-email@exemple.com"
   };
   ```

5. Enregistre, commit/push. **C'est tout** : les boutons « Démarrer le Pass », « Passer à vie »
   et « Acheter » sur chaque fond ouvrent désormais ta vraie page de paiement.

> Le même principe marche avec Stripe (crée des *Payment Links*) ou Lemon Squeezy :
> tu obtiens une URL par produit, tu la colles au même endroit.

> ℹ️ Tant qu'un lien est vide, le bouton affiche un petit message d'aide au lieu de planter —
> le site reste donc présentable même avant d'avoir branché le paiement.

---

## Étape 3 — Fabriquer et livrer les fonds d'écran (ton produit)

Le site montre des **aperçus animés** générés en direct. Pour la vente, il te faut les **vrais fichiers**
à livrer à l'acheteur. Deux formats par fond :

- **Téléphone** — vidéo verticale (ex. 1080×2340) ou Live Photo / vidéo `.mp4`.
- **PC** — vidéo large (ex. 3840×2160) `.mp4`, ou un fond animé pour **Wallpaper Engine** (Steam).

Comment les produire :
- Enregistre les animations du site (capture d'écran vidéo plein écran), ou
- Exporte depuis un outil de motion (After Effects, Canva, Motionleap pour mobile), ou
- Utilise des packs de fonds animés sous licence commerciale.

Téléverse ces fichiers dans chaque produit chez ton prestataire (Étape 2) → livraison automatique après paiement.

> ⚠️ Vends uniquement des visuels que tu as le droit de vendre (tes créations ou une licence commerciale).

---

## Étape 4 — Déclencher les premières ventes

1. **Partage le lien** `https://lakoree.github.io/Claude-Code/` en story Instagram / TikTok avec
   une capture de ton propre écran animé (« swipe pour le tien »).
2. Publie une **vidéo « avant/après »** de ton écran figé → écran vivant. C'est le format qui convertit.
3. Mets un **code promo de lancement** (ex. −30 % les 48 h) directement dans Gumroad.
4. Réponds à chaque « t'as fait comment ?! » avec le lien. C'est ta meilleure pub (cf. persona dans `BRAND.md`).

---

## Récapitulatif

| Fait pour toi ✅ | À faire par toi (obligatoire) |
|---|---|
| Site complet et responsive | Rendre le dépôt public + activer Pages (Étape 1) |
| Boutons d'achat câblés partout | Créer ton compte vendeur + coller les liens (Étape 2) |
| Config paiement centralisée, sans code | Préparer les fichiers de fonds à livrer (Étape 3) |
| Guide de vente et persona | Publier et partager (Étape 4) |

Je ne peux pas créer ton compte de paiement à ta place (il est lié à ton identité et à ton compte
bancaire — KYC obligatoire). Tout le reste est prêt. Une fois tes liens collés, tu peux vendre. 💸
