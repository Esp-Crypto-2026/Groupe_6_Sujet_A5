# Groupe 6 — Livrables A5

Le projet porte sur les nonces faibles d'ECDSA (réutilisation, prévisibilité, biais) dans les registres Bitcoin et Ethereum.

## Reproduction

Depuis la racine du dépôt :

```
code/reproduire.sh
```

À venir : le script régénère la recherche de `r` répétés sur les deux chaînes et l'attaque par réseaux euclidiens (fpylll) sur des nonces à biais contrôlé.

## Organisation

- `animation/` : source des diapositives (A5, séance S3) ;
- `article/` : article et bibliographie ;
- `code/` : expériences (statistiques de `r` répétés, attaque LLL/BKZ) ;
- `donnees/` : jeu de données (signatures ECDSA Bitcoin et Ethereum : `r`, `s`, `h`, clé publique) ;
- `resultats/` : résultats vérifiés ;
- `discussion/` : questions posées au groupe 4 (A11) et réponses ;
- `synthese/` : synthèse du groupe 1, rapporteur = groupe 6 ;
- `quiz/` : trois QCM avec réponses.

Les commits, tags et push sont réalisés par chaque membre sous son propre compte GitHub.
