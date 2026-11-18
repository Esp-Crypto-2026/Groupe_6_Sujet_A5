# Synthèse du rapporteur — A0 : Délivrance du diplôme de l'ESP par preuve à divulgation nulle

**Groupe rapporteur :** groupe 6 (Ndeye Mingue Ndiaye, Fatoumata Barro, Khadimou Rassoul Mbacké Mbaye)
**Groupe rapporté :** groupe 1 (Mouhamed Moustapha Niang, Thierno Abdoulaye Sall, Youssouph Gnaga Diatta, Mouhamed Dramé) — A0, séance [date à préciser]. Discutant du groupe 1 : [autre groupe].
**Note attribuée au groupe 1 : 16.** Version officielle : `rapport-rapporteur_G1_A0.pdf`.

---

## PARTIE A — Grille remplie pendant leur exposé

### Cadre commun (fiche, p.1)
- Question de recherche posée dès la 1re minute : prouver l'authenticité d'un diplôme de l'ESP et le seuil de moyenne sans rien révéler, à un coût tenable sur smartphone : [x]
- Une figure + un exemple chiffré : caverne d'Ali Baba, Schnorr sur petits nombres, exemple 15/20 ≥ 12 : [x]
- État de l'art ≥ 5 sources primaires : Goldwasser-Micali, Schnorr, Fiat-Shamir, BBS+, W3C Verifiable Credentials 2.0, Groth16 : [x]
- Démonstration en direct : engagement de Pedersen + preuve à OU de Schnorr liée par Fiat-Shamir : [x]
- Chaque membre prend la parole (les 4) : [x]
- Temps : début ___ fin ___ → durée ___ (cible 20 min + 5 de questions)

### Questions du bloc (posé par le groupe discuteur du groupe 1) — cœur de « points débattus »
- Q1 — Si l'ESP retire un diplôme, comment le vérificateur l'apprend-il sans pouvoir tracer le titulaire ? → liste de statut W3C signée, chacun vérifie chez soi ; piste : arbre de Merkle + preuve zk-SNARK pour cacher l'index ; coût : un petit délai de révocation.
- Q2 — Qui détecte, et comment, que la clé de l'ESP a été compromise ? → une clé compromise produit des signatures valides : indétectable par la cryptographie seule ; registre d'émission public (ajout seul), changement de clé dans le DID, seuls les diplômes antérieurs restent valables ; registre = piste, non implémenté.

---

## PARTIE B — Synthèse écrite d'une page

### 1. Question de recherche
Le groupe 1 demande si l'ESP peut délivrer un diplôme vérifiable **en preuve à divulgation nulle** : prouver qu'une moyenne dépasse un seuil (≥ 12/20) sans révéler ni les notes détaillées ni l'identité superflue, pour lutter contre les faux diplômes (saisies à Grand Yoff et Saint-Louis en 2026) tout en protégeant la vie privée des lauréats, à un coût tenable sur un smartphone d'entrée de gamme.

### 2. Mécanisme présenté
Les trois propriétés des ZKP (complétude, validité, divulgation nulle) illustrées par la caverne d'Ali Baba, puis l'identification de **Schnorr** sur de petits nombres (p = 23, g = 11) rendue non interactive par la transformation de **Fiat–Shamir**. État de l'art ancré : Goldwasser-Micali, Schnorr, Fiat–Shamir, signatures d'attributs **BBS+**, standards **W3C Verifiable Credentials 2.0** et **zk-SNARKs de Groth16**. Démonstration : un **engagement de Pedersen** combiné à une **preuve à OU de Schnorr** liée par Fiat–Shamir valide que la moyenne secrète (15/20) est ≥ 12 sans divulguer autre chose que la validité de l'attestation signée par l'ESP. Contribution : une architecture adaptée aux smartphones d'entrée de gamme en milieu ouest-africain.

### 3. Résultats montrés
Démonstration chiffrée : preuve « moyenne ≥ seuil » sur l'exemple 15/20, Schnorr reproductible à la main sur p = 23, g = 11 (nombres manipulables). Ancrage bibliographique conforme aux exigences du LITA (Katz-Lindell, Boneh-Shoup, Groth16, W3C v2.0). **Note obtenue : 16.**

### 4. Points débattus
- **Révocation** (Q1 du discuteur) : la liste de statut W3C fonctionne mais son index peut servir à tracer ; la piste Merkle + zk-SNARK cache l'index au prix d'un délai.
- **Clé compromise** (Q2) : indétectable par la crypto seule ; réponse : registre d'émission en ajout seul + rotation de clé dans le DID ; le registre reste une piste non implémentée.

### 5. Ce qui reste ouvert
- **Angle mort de la révocation** : mécanisme concret par l'ESP (litige, annulation) et son coût en confidentialité insuffisamment détaillés.
- **Métriques smartphone** : temps de génération d'une preuve zk-SNARK ou BBS+ sur un Android d'entrée de gamme non chiffré.
- **Trusted setup** : le rôle du « déchet toxique » (Groth16) a été survolé alors qu'il conditionne la souveraineté de l'ESP sur ses circuits.
- Le registre d'émission (détection de clé compromise) n'est qu'une piste d'architecture.

---

## PARTIE C — Mini-synthèse ORALE (dite juste après leur présentation, ~1 min)

> « Merci au groupe 1. **Résumé :** ils ont cherché comment l'ESP peut délivrer un diplôme vérifiable sans rien révéler d'autre que l'essentiel — prouver qu'une moyenne dépasse 12/20 grâce à une preuve à divulgation nulle, illustrée par la caverne d'Ali Baba, l'identification de Schnorr sur de petits nombres et une démonstration d'engagement de Pedersen avec preuve à OU liée par Fiat–Shamir.
>
> **Deux points forts :** l'ancrage local est percutant (faux diplômes de Grand Yoff et Saint-Louis) et la progression pédagogique de la théorie vers les chiffres manipulables rend l'exposé très accessible ; la bibliographie est rigoureuse et conforme aux exigences du LITA.
>
> **Ce qui reste à creuser** : trois points — la révocation concrète des diplômes et son coût en vie privée, les métriques chiffrées de génération de preuve sur un smartphone d'entrée de gamme, et le « déchet toxique » du trusted setup, enjeu de souveraineté si l'ESP déléguait la création de ses circuits. »

---
*Rappel : version officielle déposée dans `synthese/rapport-rapporteur_G1_A0.pdf`.*
