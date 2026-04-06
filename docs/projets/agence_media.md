# Projet : Marketing Data Platform

> **Projet en cours de refactoring.**
> Ce projet est actuellement en cours de refonte afin d'intégrer une vraie API Meta Ads connectée à une campagne publicitaire réelle.
> La documentation et les captures d'écran seront mises à jour une fois les changements finalisés.

---


**L'objectif :** Construire une infrastructure robuste capable d'unifier les données de Google Ads et Meta Ads pour fournir une vision business transverse, fiable et automatisée.

> **Stack :** Python, Airflow, dbt, BigQuery, Docker, GitHub Actions.

---

## Architecture Technique

Cette plateforme repose sur un découplage strict entre le transport de la donnée et sa valorisation :

1.  **Ingestion (Python + Airflow) :** Extraction via des connecteurs modulaires, gestion de l'idempotence et chargement dans le `RAW Layer` de BigQuery.
2.  **Transformation (dbt) :** Passage par 4 couches de modélisation (Staging, Intermediate, Marts) pour garantir la qualité et la réutilisabilité.
3.  **Orchestration :** Un DAG Airflow centralise le cycle de vie, avec des Task Groups pour paralléliser l'ingestion.

---

## Aperçu de la plateforme

### 1. Orchestration & Monitoring (Airflow)
![DAG Airflow — orchestration des pipelines](../images_projets/agence_media/airflow_dag_detail.png
)
*Vue du DAG orchestrant l'ingestion parallélisée et le déclenchement des transformations dbt. Chaque étape inclut une logique de retry et un logging détaillé.*



### 2. Qualité & Exposition (BigQuery)
![Tables marts — datasets métier](../images_projets/agence_media/marts.png)
*Exposition des Data Marts finaux dans BigQuery. Les données sont nettoyées, typées et prêtes pour être consommées par un outil de BI (Looker, Tableau).*

---
