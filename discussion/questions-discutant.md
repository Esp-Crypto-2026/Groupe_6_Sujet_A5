# Questions du discutant — A11 : Outils d'analyse de contrats Solidity

**Groupe discutant :** groupe 6 (Ndeye Mingue Ndiaye, Fatoumata Barro, Khadimou Rassoul Mbacké Mbaye)
**Groupe discuté :** groupe 4 (Mohamed LO, Ahmadoul Khadim TOURE, Amadou Tidiane KANE) — séance S5, vendredi 13 novembre 2026, bloc 3. Rapporteurs : groupe 7.
**Documents lus :** diapositives A11, fiche A11, réponses préparées du groupe 4 (`A11_G4_Questions_Reponses.pdf`), attentes de l'enseignant pour A11.

Le sujet est bien motivé (The DAO 2016, taxonomie d'Atzei), la démonstration de réentrance sur Hardhat est un bon cas d'école, et les limites annoncées sont honnêtes. Comme le demande la consigne, la première question porte sur la **méthode**, la seconde sur une **hypothèse**.

---

## Question 1 (méthode) — Vingt contrats suffisent-ils, et qui garantit l'objectivité de la vérité terrain ?

**Constat.**
- L'étude annoncée porte sur **au moins 20 contrats annotés**, face aux **47 500 contrats** de Durieux et al.
- Le taux de détection de 42 % chez Durieux ne vient pas des 47 500 contrats (qui servent à compter les alertes, 97 % signalées), mais de **69 contrats annotés** : les 20 contrats annoncés sont du même ordre de grandeur, mais l'échantillon reste faible.
- L'annotation est **manuelle** : une faille rattachée à une catégorie d'Atzei, des désaccords possibles entre annotateurs, donc la matrice de confusion dépend directement de la qualité de cette vérité terrain.
- Aucun critère d'annotation écrit avant l'exercice n'est présenté dans l'exposé.

**Question.** Comment votre échantillon de 20 contrats peut-il suffire pour conclure, et selon quelles règles écrites la vérité terrain est-elle établie pour que votre matrice de confusion soit objective ?

**Ce qu'une bonne réponse devrait contenir.**
- Une **reconnaissance explicite** : 20 contrats = étude pilote, pas de généralisation ; comparaison à armes égales avec les 69 contrats annotés de Durieux (pas avec les 47 500).
- Des **effectifs bruts par catégorie** de faille, avec intervalle de confiance, et l'aveu de l'échantillon trop petit pour conclure.
- Des **règles d'annotation écrites avant** d'annoter, rattachées à la taxonomie d'Atzei ; **deux annotateurs indépendants** et publication de leur taux d'accord ; une **preuve plutôt qu'un avis** (une réentrance n'est vraie que si l'attaque fonctionne sur Hardhat).
- Publication des annotations, scripts, versions d'outils et sorties brutes dans le dépôt.

---

## Question 2 (hypothèse) — En Solidity 0.8, où vont les faux positifs ?

**Constat.**
- Depuis Solidity 0.8, l'arithmétique est **vérifiée par défaut** : un dépassement interrompt l'exécution, sauf en bloc `unchecked`.
- Or les outils annoncés (Slither, Mythril, Echidna) datent pour partie d'avant la 0.8, et le corpus de référence (Durieux et al.) est ancien.
- Votre démo ne porte que sur **un** contrat (la réentrance) et **un** outil (Slither) : la question posée — où vont les faux positifs sur des contrats récents — n'est pas encore tranchée.

**Question.** Votre hypothèse est-elle que les faux positifs **arithmétiques** disparaissent et se déplacent vers la **logique métier** (contrôle d'accès, appels externes, ordre des instructions) ? Comment votre corpus la testera-t-il, et un outil conçu avant la 0.8 peut-il signaler un dépassement que le compilateur bloque déjà ?

**Ce qu'une bonne réponse devrait contenir.**
- Une **hypothèse testable** : faux positifs arithmétiques → presque nuls hors `unchecked` ; déplacement vers appels externes, ordre des instructions, contrôle d'accès.
- Une **procédure de tranchage** : chaque alerte classée vraie/fausse puis rangée par catégorie ; confirmation si les FP arithmétiques tombent et que ceux du contrôle d'accès montent ; comparaison avec les catégories de Durieux.
- La reconnaissance que, avec 20 contrats, on parlera de **tendance, pas de loi**.

---

## Relances et questions de réserve
- **Si Q1 reçoit la réponse « c'est une limite, on l'a écrit » :** « Pourquoi pas plus de contrats ? D'où viennent-ils — SmartBugs Curated et autres failles déjà documentées, et en priorité en Solidity 0.8 ? »
- **Si Q2 reçoit la réponse « on verra » :** « Et Echidna — n'écrit-il que les propriétés qu'on lui donne, c'est-à-dire surtout des failles manquées plutôt que de fausses alertes ? »
- **Réserve, angle mort des outils :** les failles de **logique métier** (contrôle d'accès, gestion de l'état) sont-elles détectées par les trois outils, ou est-ce précisément là que votre matrice de confusion montrera des faux négatifs ?

---

## Remarques de forme (pour la version corrigée à J+2)
- [ ] À relever pendant l'exposé : nombre de diapos et pied de page, sigles développés à la 1re utilisation, chiffres de la démo (valeurs du coffre, nombre de réentrées, alertes Slither), durée début/fin.

---

**Preuve conservée :** `A11_G4_Questions_Reponses.pdf` — réponses préparées du groupe 4 à ces questions (séance S5 du 13/11/2026).
