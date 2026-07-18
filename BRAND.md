# FLUX — Identité de marque & stratégie

> Fait de A à Z pour le lancement : avatar client, positionnement, nom, palette, typographie, ton.

## 1. Avatar client (persona cible)

**« Nmaël », 22 ans — l'esthète du setup.**

| Dimension | Détail |
|---|---|
| **Profil** | Étudiant / jeune actif créatif. Gamer. Très présent sur TikTok & Instagram. |
| **Appareils** | Un téléphone récent + un PC (souvent un moniteur large / ultrawide). Il veut les deux assortis. |
| **Comportement** | Change de fond d'écran souvent, aime personnaliser, cherche l'unique et l'effet « waouh ». |
| **Budget** | Modéré, mais prêt à payer pour la qualité, l'exclusivité et la nouveauté régulière. |
| **Frustrations** | Fonds statiques ennuyeux · apps qui vident la batterie · résolutions moches sur grand écran · « le même fond que tout le monde ». |
| **Motivations** | Expression de soi · impressionner (screenshots, partages) · nouveauté continue · setup soigné. |
| **Déclencheur d'achat** | « Comment t'as fait bouger ton fond ?! » → preuve sociale + prévisualisation live. |

Le site est construit **autour de lui** : preuve visuelle immédiate (fonds rendus en direct),
langage tutoyé et jeune, mise en avant de la sync téléphone+PC, réponse anticipée à l'objection batterie.

## 2. Positionnement

**Nom :** FLUX — court, ownable, évoque le mouvement / le flux.
**Signature :** « Ton écran, en mouvement. »
**Promesse :** des fonds d'écran dynamiques 4K, vivants mais légers, pour téléphone ET PC,
avec de nouveaux drops chaque mois.

## 3. Palette

| Rôle | Sombre (défaut) | Clair |
|---|---|---|
| Fond | `#07080D` (near-black bleu-nuit / OLED) | `#F5F6FA` |
| Surface | `#12141F` | `#FFFFFF` |
| Texte | `#ECEDF4` | `#14161F` |
| Muted | `#868BA2` | `#676D82` |
| **Accent** | `#F5B841` (or chaud) | `#B9820F` |

Tension volontaire **chaud/froid** : sol bleu-nuit + accent or chaud. On évite le cliché violet→bleu.
La richesse chromatique vient des **canvas animés**, pas du chrome de l'interface (qui reste sobre).
Les « écrans » (héros, mockups, tuiles, CTA final) restent sombres dans les deux thèmes — ce sont des écrans.

## 4. Typographie

- **Titres** — grotesk système, très gras, tracking serré (`-0.03em`), grande échelle.
- **Corps** — même famille, poids régulier, largeur de lecture maîtrisée.
- **Libellés / specs** — **monospace** en majuscules espacées. Choix porteur de sens : le mono
  affiche les vraies specs d'écran (`4K · 120FPS · HDR`), l'univers technique du produit.

Aucun webfont CDN (bloqué par la CSP des artifacts) : on s'appuie sur des piles système robustes.

## 5. Ton éditorial

Tutoiement, phrases courtes, orienté bénéfice concret. On parle « écran », « setup », « drop »,
« waouh » — le vocabulaire de la cible. On répond aux objections (batterie, appareils, remboursement)
avant qu'elles ne bloquent l'achat.

## 6. Structure de la page

Héros live (le produit *est* la démo) → bandeau défilant → galerie filtrable (rendus en direct) →
pourquoi FLUX (4 atouts) → 3 étapes → tarifs (unité / mensuel / à vie) → avis → FAQ → CTA final → footer.

## 7. Technique

`index.html` autonome, zéro dépendance externe. Toutes les animations sont générées en **Canvas 2D**
(un moteur `WallpaperEngine` avec plusieurs modes : aurora, nebula, flow, waves, grid, rain, avatar).
Boucle d'animation unique + `IntersectionObserver` pour ne rendre que le visible, throttle ~40fps,
respect de `prefers-reduced-motion` → sobre côté batterie. Thème clair/sombre auto + bouton bascule.
