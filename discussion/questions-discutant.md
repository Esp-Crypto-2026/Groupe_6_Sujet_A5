# Questions du discutant — A11 : Outils d'analyse de contrats Solidity

**Groupe discutant :** groupe 6 (Ndeye Mingue Ndiaye, Fatoumata Barro, Khadimou Rassoul Mbacké Mbaye)
**Groupe discuté :** groupe 4 (Mohamed LO, Ahmadoul Khadim TOURE, Amadou Tidiane KANE) — séance S5, vendredi 13 novembre 2026, bloc 3. Rapporteurs : groupe 7.
**Documents lus :** diapositives A11, fiche A11, attentes de l'enseignant pour A11, réponses préparées du groupe 4 (`A11_G4_Questions_Reponses.pdf`).
**Version officielle :** `rapport-discutant_G4_A11.pdf`.

Le sujet est bien motivé (The DAO 2016, taxonomie d'Atzei) et la démonstration de réentrance sur Hardhat est un bon cas d'école. Les deux questions ci-dessous sont celles posées en séance ; elles portent sur une **hypothèse** puis sur la **méthode**.

---

## Question 1 (hypothèse) — L'impact de Solidity 0.8 sur la nature et la répartition des faux positifs

**Contexte.** Le groupe 4 s'appuie sur Durieux et al. (2020) : environ 42 % de détection des failles réelles et un taux élevé d'alertes, mais sur un corpus développé **avant Solidity 0.8**, à une époque où les dépassements arithmétiques (overflows/underflows) généraient la majeure partie des alertes automatiques.

**Question formulée.** « Sur vos contrats récents en Solidity 0.8, version où l'arithmétique est désormais protégée par défaut par le compilateur, est-ce que les faux positifs signalés par des outils comme Slither ou Mythril proviennent encore de résidus arithmétiques obsolètes, ou constate-t-on un déplacement des faux positifs vers des failles de logique métier plus complexes (telles que le contrôle d'accès ou la gestion des états) ? »

**Réponses reçues (groupe 4).**
- **Hypothèse de départ :** le compilateur 0.8 protégeant nativement contre les dépassements (sauf bloc `unchecked`), les fausses alertes arithmétiques doivent chuter.
- **Déplacement attendu :** vers la logique métier (contrôle d'accès, gestion d'état, appels externes), c'est-à-dire là où les outils signalent des risques sans prouver l'exploitabilité.
- **Méthode de vérification :** chaque alerte classée vraie/fausse, mesure statistique de l'évolution, comparaison avec les résultats d'avant 0.8, avec prudence (tendance sur 20 contrats).

---

## Question 2 (méthode) — Représentativité du corpus et subjectivité de la vérité terrain

**Contexte.** Le groupe 4 annonce un corpus d'**au moins 20 contrats annotés** en Solidity 0.8, dont la « vérité terrain » est validée manuellement par deux membres de l'équipe, face aux **47 500 contrats** de Durieux et al.

**Question formulée.** « Un échantillon de 20 contrats est-il statistiquement suffisant pour formuler des conclusions robustes, comparé aux dizaines de milliers de contrats analysés dans la littérature de référence (comme les 47 500 contrats de Durieux et al.) ? De plus, sachant que l'annotation humaine repose sur une relecture manuelle, comment garantissez-vous l'objectivité de votre vérité terrain pour éviter que l'interprétation subjective du code ne vicie l'ensemble de votre matrice de confusion ? »

**Réponses reçues (groupe 4).**
- **Taille :** pas de généralisation massive — étude pilote ciblée sur les contrats récents 0.8 ; volume comparable aux **69 contrats annotés** de l'étude originale.
- **Objectivité, trois piliers :** règles d'annotation écrites à l'avance (taxonomie d'Atzei) ; double annotation indépendante avec taux d'accord mesuré et publié ; remplacement des avis par des preuves techniques (validation d'une réentrance par attaque réelle sur Hardhat).

---

## Conclusion du discutant

Le travail du groupe 4 pose de solides bases pour actualiser l'état de l'art face aux standards modernes d'Ethereum. Les réponses reçues transforment habilement les faiblesses apparentes (échantillon réduit, hypothèses à vérifier) en forces méthodologiques : transparence totale, critères de validation solides (double annotation, Hardhat), vision technique précise de Solidity 0.8.

**Limite à garder en tête — angle mort des failles systémiques :** 20 contrats, même parfaitement annotés, restent restreints ; l'échantillon valide une méthode pilote et dégage des tendances, mais risque de passer à côté de vulnérabilités rares ou de logiques complexes n'apparaissant qu'à grande échelle ou au sein d'architectures DeFi multi-contrats enchevêtrées.

---

**Preuves conservées :** `A11_G4_Questions_Reponses.pdf` (réponses préparées du groupe 4) et `rapport-discutant_G4_A11.pdf` (rapport officiel du groupe 6).
