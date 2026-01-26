# Projet principal — Plateforme Data Marketing

Ce projet peut être lu selon **deux angles complémentaires**, en fonction du rôle ciblé :

- **Data Engineer** : conception de la plateforme, ingestion, orchestration et robustesse opérationnelle  
- **Analytics Engineer** : modélisation analytique, fiabilité des KPIs et usages métier

---

## TL;DR — Analytics Engineering View
<a id="analytics-engineering-view"></a>

**Transformation de données marketing hétérogènes en KPIs fiables et exploitables par les équipes métier.**

- Modélisation analytique SQL-first avec dbt (Raw → Staging → Intermediate → Marts)
- Harmonisation des KPIs marketing (CTR, CPA, ROAS)
- Tests automatisés, documentation et traçabilité des modèles
- Production de data marts BI-ready pour le reporting et l’analyse

---

## TL;DR — Data Engineering View
<a id="data-engineering-view"></a>

**Construction d’une data platform cloud robuste et scalable pour l’ingestion multi-sources.**

- Pipelines d’ingestion incrémentaux et idempotents
- Orchestration centralisée avec Airflow
- Architecture modulaire et extensible
- CI/CD, monitoring et contrôles de qualité intégrés

---

## Contexte et objectifs

**Une plateforme data marketing moderne, modulaire et cloud-ready**, conçue pour unifier, fiabiliser et valoriser
les données issues de multiples régies publicitaires.

### Problème
Les données marketing proviennent de plateformes multiples (Google Ads, Meta Ads, TikTok, LinkedIn, etc.) avec :
- Schémas hétérogènes et définitions KPI non harmonisées
- Ingestions peu industrialisées et fragiles
- Couplage fort entre reporting et systèmes sources
- Absence de garanties de qualité des données

### Solution
- Architecture cloud-ready, modulaire et extensible
- Ajout de nouveaux connecteurs via interface standardisée
- Pipelines d’ingestion incrémentaux et testés (Airflow, dbt, CI/CD)
- Séparation stricte des couches analytiques
- Monitoring, tests automatisés et documentation intégrée

### Impact
- Ajout de nouvelles sources en moins d’un jour (vs. plusieurs semaines)
- Données fiables en production grâce aux tests automatisés
- Centralisation des données pour accélérer la prise de décision et les usages analytiques

---

## Fonctionnalités clés

- Ingestion multi-sources incrémentale et idempotente
- Orchestration et transformations analytiques industrialisées
- Tests, monitoring et CI/CD intégrés
- Déploiement cloud-ready (BigQuery, Snowflake)

---

## Aperçu de la plateforme

### Orchestration
![DAG Airflow — orchestration des pipelines](../img/airflow_dag_detail.png)

*DAGs Airflow orchestrant l’ingestion multi-sources et les transformations analytiques.*

### Données brutes — Raw layer
![Tables raw Google Ads et Meta Ads](../img/data_quality_monitoring.png)

*Tables brutes issues de Google Ads et Meta Ads.*

### Transformations analytiques
![Transformations dbt — modèles et dépendances](../img/dbt_transformations_sql.png)

*Modèles dbt structurés en couches staging, intermediate et marts.*

### Exposition métier
![Tables marts — datasets métier](../img/marts.png)

*Datasets analytiques orientés métier pour la BI, le reporting et l’analyse.*

---

## Accès au projet
L’ensemble du code source, de la documentation technique et des choix d’architecture est disponible sur GitHub :  
[Consulter le dépôt GitHub](https://github.com/y-ikli/media-data-platform)


---

