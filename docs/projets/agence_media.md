# Media Data Platform

**Pipeline ELT publicitaire** — Meta Ads (API réelle) et Google Ads — vers des tables analytiques dans BigQuery, avec transformations dbt et contrôles qualité automatiques.

> **Stack :** Python · BigQuery · dbt · GitHub Actions

**Repo :** [github.com/y-ikli/media-data-platform](https://github.com/y-ikli/media-data-platform)

---

## Contexte

Une agence marketing gère des campagnes sur Meta et Google en même temps. Chaque plateforme livre ses données dans son propre format : noms différents, métriques incohérentes, exports manuels.

**Problème concret :** le CTR n'est pas calculé de la même façon selon la source. Comparer Meta et Google sur les mêmes campagnes et les mêmes dates devient impossible.

**Solution :** un pipeline qui réunit les deux sources dans une seule table analytique, avec une définition unique de chaque indicateur.

---

## Architecture

```
Meta Ads API (réelle)          Google Ads (simulé)
        │                              │
        ▼                              ▼
  Connecteur Python            Connecteur Python
        │        (même interface)      │
        └──────────────┬───────────────┘
                       ▼
              BigQuery — données brutes
              partitionnées par date, rejouables sans doublon
                       │
                       ▼
              dbt — 3 couches
              ├─► Staging       — nettoyage et typage par source
              ├─► Intermediate  — union des deux sources
              └─► Marts         — indicateurs prêts pour la BI
```

---

## Résultats

| Source | Lignes | Campagnes | Période |
|--------|--------|-----------|---------|
| Meta Ads (réelle) | 447 | 46 | 2023-04 → 2025-08 |
| Google Ads (simulé) | 4 280 | 5 | même période |

**Table finale :** 4 727 lignes · 1 ligne = 1 campagne × 1 date × 1 plateforme · 57 tests dbt au vert

Indicateurs calculés : CTR, CPC, CPA, taux de conversion, ROAS (valeur des conversions / dépense).

---

## Aperçu

![BigQuery mart_campaign_daily](../images_projets/agence_media/bigquery_mart.png)
*Table finale : indicateurs Meta et Google unifiés.*

![Lineage dbt](../images_projets/agence_media/lineage.png)
*Lineage dbt : de la source brute aux indicateurs, chaque étape est traçable.*

![Documentation dbt](../images_projets/agence_media/dbt_serve.png)
*Documentation générée automatiquement : colonnes, descriptions, tests.*

---

## Ce qui rend le pipeline fiable

- **Rejouable sans doublon** : relancer un chargement ne duplique jamais les données.
- **Traçable** : chaque ligne est reliée à l'exécution qui l'a chargée.
- **Une seule définition par indicateur**, versionnée dans Git et documentée.
- **Testé à chaque modification** : tests dbt (clés, valeurs, cohérence des métriques) et CI GitHub Actions (lint, tests unitaires, compilation dbt).

Détail technique et choix d'architecture : voir le [dépôt GitHub](https://github.com/y-ikli/media-data-platform).
