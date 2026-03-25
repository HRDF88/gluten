# Pipeline de données

Le pipeline de G.L.U.T.E.N transforme des sources brutes en base de connaissances exploitable.

## Étapes

1. Acquisition des sources
2. Conversion PDF / scan
3. OCR
4. Nettoyage du texte
5. Structuration
6. Chunking
7. Embeddings
8. Indexation vectorielle
9. Interrogation via RAG

## Détail

### Acquisition
Les sources proviennent de livres, ebooks et formations spécialisées.

### OCR
Les documents scannés sont convertis en texte exploitable.

### Nettoyage
Le texte est corrigé, normalisé et débarrassé des artefacts les plus gênants.

### Structuration
Les contenus sont regroupés par axe :
- science
- métier
- folklore
- réel

### Chunking
Les documents sont découpés en morceaux exploitables pour l’indexation.

### Embeddings
Chaque chunk est vectorisé afin de permettre la recherche sémantique.

### Indexation
Les vecteurs sont stockés dans FAISS pour l’interrogation rapide.

## Objectif

Obtenir une base documentaire cohérente, fiable et interrogeable localement.
