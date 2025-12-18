# 📚 Assistant de Cours RAG (Retrieval-Augmented Generation)

Ce projet implémente une application de **Génération Augmentée par Récupération (RAG)** conçue pour interroger intelligemment des supports de cours.  
L'outil permet d'extraire des connaissances précises à partir de documents locaux tout en **citant systématiquement ses sources** afin de garantir la fiabilité des réponses.

---

## 🌟 Fonctionnalités Clés

- **Support Multi-format** : Chargement et extraction de texte à partir de fichiers **PDF, TXT et DOCX**.
- **Recherche Sémantique** : Utilisation d'une base de données vectorielle pour identifier les passages les plus pertinents par rapport à une question.
- **Citations Précises** : Chaque réponse inclut le nom du fichier source et, pour les PDF, le numéro de page exact.
- **Prévention des Hallucinations** : Le système est configuré avec des règles strictes pour répondre uniquement à partir du contexte fourni.

---

## 🛠️ Pile Technique (Stack)

- **LLM (Modèles de Langage)**    
  - `Mistral-7B-Instruct-v0.2`
- **Orchestration** : LangChain
- **Base de Données Vectorielle** : ChromaDB (persistante localement)
- **Embeddings** : `sentence-transformers/all-MiniLM-L6-v2`
- **Traitement de Documents** : PyPDF, python-docx
- **NLP / LLM** : Transformers, Accelerate

---

## ⚙️ Configuration du Pipeline

Le pipeline RAG utilise les paramètres optimisés suivants :

- **Découpage du texte (Chunking)** :
  - Taille des chunks : **900 caractères**
  - Chevauchement : **150 caractères**
- **Récupération (Retrieval)** :
  - Top-**5** segments les plus pertinents par requête
- **Persistance** :
  - Index vectoriels stockés dans `./chroma_db_project2`
  - Évite le recalcul des embeddings à chaque exécution

---

## 🚀 Installation

Assurez-vous d’avoir **Python** installé, puis installez les dépendances :

```bash
pip install -U langchain langchain-community langchain-huggingface \
chromadb sentence-transformers transformers accelerate pypdf python-docx
