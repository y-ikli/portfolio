# MonCapitain

**Système RAG 100% local** pour interroger un corpus documentaire scientifique en langage naturel — conçu pour les équipes biotech, aucune donnée ne quitte la machine.

> **Stack :** Python · FastAPI · Ollama · Qdrant · RDKit

---

## Contexte

Dans les équipes biotech, les documents internes (rapports, articles, fiches techniques, données de criblage) s'accumulent et deviennent difficiles à interroger. Les solutions cloud posent des problèmes de confidentialité sur des données sensibles — brevets, molécules, résultats d'essais.

**Problème :** trouver une information précise dans un corpus de centaines de documents prend du temps, et envoyer ces données à une API externe n'est pas envisageable.

**Solution :** un moteur RAG local — l'utilisateur pose une question en langage naturel, le système retrouve les passages pertinents et génère une réponse ancrée dans les sources, sans connexion externe.

---

## Architecture

```
  Documents Internes
        │
        ▼
  Extraction + Chunking
  (overlap, métadonnées par chunk)
        │
        ▼
  Embeddings → Vectorstore local
        │
        ▼
  Retrieval sémantique
        │
        ▼
  LLM local
  (réponse + citation des sources)
        │
        ▼
  Interface desktop
```

---

## Fonctionnalités

- Extraction de documents internes.
- Chunking avec overlap et métadonnées.
- Recherche vectorielle par similarité sémantique.
- Génération de réponses avec citation des sources.
- Choix du modèle LLM via Ollama.
- Module chimio-informatique : similarité moléculaire, visualisation SMILES — via RDKit.
- Architecture modulaire — nouveaux modules ajoutables sans refonte.

---

## Aperçu

### Interface principale

![Lancement MonCapitain](../images_projets/moncapitain/premier_apercu.png)
*Interface principale de MonCapitain.*

### Import de document

![Ajout document](../images_projets/moncapitain/ajout_doc.png)
*Import et indexation d'un document.*

### Sélection du modèle LLM

![Choix du LLM](../images_projets/moncapitain/choisir_model.png)
*Sélection du modèle Ollama.*

### Interrogation du corpus

![Poser Question](../images_projets/moncapitain/poser_question.png)
*Question posée sur le document — réponse générée localement.*

### Module RDKit — similarité moléculaire

![Modules cheminformatique](../images_projets/moncapitain/cheminfo.png)
*Deux structures SMILES comparées, score de similarité de Tanimoto affiché.*

---

## État du projet

Projet en cours de réflexion et d'adaptation — architecture et fonctionnalités encore en évolution.
