# G.L.U.T.E.N — Pizza Intelligence Engine (Local AI)

G.L.U.T.E.N est un système expert local capable de transformer des contraintes réelles (température, farine, matériel, temps) en protocoles de pizza cohérents, reproductibles et expliqués.

Projet de recherche et développement combinant science alimentaire, expertise métier pizzaiolo et intelligence artificielle.

Application utilisée pour explorer une approche systémique et reproductible de la fabrication de la pâte.

---

## Contexte

La majorité des approches autour de la pizza reposent sur des recettes fixes.

G.L.U.T.E.N adopte une approche différente :

- comprendre les phénomènes physiques (gluten, fermentation, hydratation)
- intégrer les contraintes réelles (température, farine, matériel)
- produire des protocoles adaptatifs et cohérents

Objectif : obtenir des résultats fiables dans n’importe quel environnement.

---

## Vision

Construire un système capable de raisonner sur la pâte à pizza comme un expert :

- analyser une situation
- comprendre les contraintes
- proposer plusieurs solutions (sécurisée / équilibrée / optimisée)

---

## Exemple rapide

Entrée :

- four domestique (450°C)
- farine W300
- température ambiante 22°C
- 24h disponibles

Sortie :

- style recommandé : pizza contemporaine
- hydratation : 63–65%
- température eau : ~16°C
- fermentation : longue maîtrisée
- niveau de risque : modéré
  
## Aperçu

![Interface](screenshots/screen-gluten.jpg)

---

## Architecture du système

Le système est structuré en plusieurs modules :

- **Floor Kernel**  
  Lois physiques : fermentation, hydratation, structure du gluten

- **Pizzatron**  
  Moteur de calcul et de décision

- **Thermal Engine**  
  Gestion de la cuisson et dynamique thermique

- **Pizza Codex**  
  Base de connaissances documentaire (RAG)

---

## Decision Engine (Pizzatron)

Le cœur du système repose sur un moteur de décision capable de transformer des contraintes réelles en protocoles cohérents.

Le moteur fonctionne dans deux sens :

- **Forward mode** : contraintes réelles → protocole recommandé
- **Reverse mode** : pizza cible → conditions nécessaires et protocole cohérent

---

### Entrées techniques

Le moteur peut prendre en compte plusieurs familles de paramètres :

#### Environnement
- température ambiante
- humidité ambiante
- saison
- température de la farine
- température de l’eau
- température finale de pâte cible

#### Farine
- type de farine
- force boulangère (W)
- P/L
- protéines
- cendres
- absorption

#### Formulation
- hydratation
- taux de sel
- matière grasse
- type de levure
- type de préferment (direct, biga, poolish, levain)

#### Temps
- temps total disponible
- temps de pointage
- temps d’apprêt
- durée de maturation visée

#### Mise en forme
- poids du pâton
- diamètre final
- épaisseur souhaitée
- type de corniche

#### Cuisson
- type de four
- température maximale
- sole / pierre / acier
- inertie thermique
- durée de cuisson cible

#### Objectif produit
- style de pizza visé
- texture recherchée
- niveau d’alvéolage
- croustillant / moelleux
- digestibilité
- priorité (sécurité / équilibre / performance)

---

### Traitement

Le moteur combine :

- récupération documentaire via RAG
- règles métier
- contraintes physiques
- heuristiques de cohérence
- pondération du risque

Le traitement suit plusieurs étapes :

1. validation des entrées
2. détection des incohérences
3. filtrage des styles de pizza compatibles
4. calcul des plages plausibles
5. génération de protocoles candidats
6. classement des solutions par niveau de risque

Un facteur de tolérance (**k**) permet de moduler la prise de risque et le niveau d’ambition des recommandations.

---


### Sorties techniques

Le moteur peut produire :

#### Recommandations produit
- styles de pizza compatibles
- style recommandé
- styles déconseillés

#### Paramètres de protocole
- hydratation cible
- température de l’eau
- température finale de pâte visée
- type de fermentation recommandé
- durée de pointage
- durée d’apprêt
- fenêtre optimale d’utilisation

#### Paramètres de cuisson
- température de cuisson cible
- durée de cuisson attendue
- compatibilité avec le four déclaré
- ajustements liés au matériel

#### Qualité / risque
- niveau de risque
- points de vigilance
- incohérences détectées
- marges de tolérance

#### Explication
- justification des choix
- alternatives possibles
- compromis proposés

---

### Objectif

Fournir une aide à la décision plutôt qu’une recette.

Le système vise à :

- expliquer les choix
- proposer des alternatives
- s’adapter aux contraintes réelles

---

### Exemple 1 — Forward mode

**Entrée**

- four domestique 450°C
- farine W300
- 24h disponibles
- température ambiante 22°C
- poids pâton 280 g
- objectif : pizza légère et bien développée

**Sortie**

- styles compatibles : contemporaine, teglia légère, hybride
- style déconseillé : napolitaine extrême à très haute température
- hydratation recommandée : 63–65%
- température de l’eau calculée : 16°C
- protocole conseillé : biga ou direct long maîtrisé
- niveau de risque : modéré

---

### Exemple 2 — Reverse mode

**Entrée**

- objectif : pizza napolitaine contemporaine à corniche développée
- texture : légère, alvéolée, cuisson rapide

**Sortie**

- four recommandé : > 450°C avec forte inertie
- farine recommandée : W280–340
- hydratation plausible : 65–70%
- fermentation adaptée : directe longue ou biga
- température finale de pâte cible : à définir selon environnement
- contraintes critiques : gestion de la chaleur, maturité de la pâte, cohérence cuisson / protocole

## Exemple de fonctionnement du moteur

### Scénario

- Four : domestique (450°C)
- Farine : W300
- Hydratation cible : 65%
- Température ambiante : 22°C
- Temps disponible : 24h
- Objectif : pizza légère avec bon développement de corniche

---

### Analyse du moteur

- Four limité → pénalisation des styles napolitains extrêmes
- Hydratation élevée → cohérence avec objectif d’alvéolage
- Temps disponible → compatible avec fermentation longue
- Farine W300 → adaptée à fermentation intermédiaire / longue

---

### Recommandations

**Styles compatibles**
- Pizza contemporaine
- Pizza hybride
- Teglia légère

**Style déconseillé**
- Napolitaine cuisson très haute température

---

### Paramètres proposés

- Hydratation : 63–65%
- Température de l’eau : ~16°C (pour contrôler la température finale de pâte)
- Fermentation : biga ou direct long maîtrisé
- Maturation : ~24h

---

### Cuisson

- Température cible : ~450°C
- Surveillance : coloration rapide et développement de corniche

---

### Niveau de risque

- Modéré

---

### Points de vigilance

- éviter la sur-fermentation
- contrôler la température finale de pâte
- adapter l’hydratation si la farine absorbe moins

## Règles métier (exemples)

Le moteur repose sur un ensemble de règles permettant de filtrer et pondérer les décisions.

### Compatibilité four / style

- Si température four < 430°C  
  → pénaliser les styles napolitains extrêmes  
  → privilégier les styles contemporains ou hybrides  

### Compatibilité farine / fermentation

- Si W < 220  
  → limiter les fermentations longues  
  → privilégier des protocoles courts ou adaptés  

### Hydratation / cuisson

- Si hydratation élevée + four domestique  
  → ajuster pour éviter une pâte difficile à cuire

## Logique simplifiée

Le moteur suit une logique en plusieurs étapes :

1. normalisation des entrées  
2. validation des contraintes  
3. filtrage des styles compatibles  
4. calcul des plages de paramètres  
5. génération de protocoles  
6. scoring des solutions  
7. sélection selon le niveau de risque (k)
  
## Pipeline de données

1. Scan des livres  
2. Conversion PDF  
3. OCR  
4. Nettoyage  
5. Structuration  
6. Chunking (400–800 tokens + overlap)  
7. Embeddings  
8. Indexation FAISS  
9. Interrogation via RAG  

---

## Dataset

Corpus structuré :

- +40 sources (livres, ebooks, formations)
- multilingue : italien, anglais, français, espagnol
- données nettoyées et normalisées

### Axes

- Science (gluten, enzymes, fermentation, céréales)
- Métier (techniques professionnelles)
- Folklore (culture pizza)
- Réel (contraintes terrain)

---

## Structure du dépôt

- `docs/architecture.md`
- `docs/pipeline.md`
- `docs/dataset.md`
- `docs/decision-engine.md`
- `data/sources_sample.csv`
- `screenshots/`

---

## État actuel

- pipeline RAG local fonctionnel  
- index FAISS opérationnel  
- ingestion documentaire en cours  
- interface Streamlit active  

---

## Philosophie

- privilégier la justesse plutôt que l’approximation  
- confronter théorie et terrain  
- modéliser les phénomènes plutôt que suivre des recettes  

---

## Roadmap

- finalisation de l’ingestion documentaire  
- structuration avancée des données  
- développement du backend FastAPI  
- application Android  
- orchestration avancée (LangGraph)  

---

## Particularités

- IA 100% locale  
- respect de la confidentialité  
- système orienté compréhension et aide à la décision  

---

## Note

Projet personnel de recherche et développement.

Objectif : construire un système capable de produire des recommandations fiables basées sur des données réelles et une modélisation cohérente.

---

À suivre.
