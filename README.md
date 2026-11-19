# RAG multimodal agentique

Notebook de cours : recherche dans un PDF avec du texte et des images, puis réponse générée par un modèle, puis agent LangChain.

Le fichier est `rag_multimodal_agentique.ipynb`.

## Contenu

1. **CLIP** encode un texte et une image dans le même espace de vecteurs.
2. **Extraction** du PDF *Attention Is All You Need* : texte par page et images.
3. **ChromaDB** stocke les fragments de texte et les images, avec les embeddings CLIP.
4. **Recherche** à partir d'une question ou d'une image.
5. **Génération** : un modèle OpenAI répond en français en citant les sources `[S1]`, `[S2]`.
6. **Agent** : LangChain décide quand appeler l'outil `consulter_pdf`.

La section « Suite à compléter » du notebook demande encore une interface Streamlit et un serveur MCP. Ces deux parties ne sont pas dans les cellules.

## Installation

Python 3.11.

```powershell
cd "C:\Users\SOUMIA\Desktop\rag_multimodal_agentique"
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install -r requirements.txt
```

Dans le notebook, choisir le noyau de ce `.venv`.

## Avant de lancer les cellules

- Placer le PDF dans `pdfs/attention is all you need.pdf`.
- Placer l'image `architecture_transformer.png` à la racine du dossier. La première cellule CLIP l'ouvre.
- Renseigner la clé API dans la cellule d'initialisation, à la place de `"...."`, ou définir la variable d'environnement `OPENAI_API_KEY` avant de lancer Jupyter. Ne pas commiter cette clé.

Le premier lancement télécharge les poids CLIP `ViT-B-32` (`laion2b_s34b_b79k`).

## Fichiers produits, non versionnés

- `resultats_pdf/` : textes et images extraits du PDF
- `chroma_pdf/` : base vectorielle
- `pdfs/` et les images PNG locales
