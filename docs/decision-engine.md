# Decision Engine — Pizzatron

Le Decision Engine (Pizzatron) est le cœur logique de G.L.U.T.E.N.

Il transforme des contraintes réelles et des objectifs produit en protocoles cohérents, reproductibles et expliqués.

---

## Objectif

Fournir une aide à la décision plutôt qu’une simple recette.

Le moteur vise à :

- analyser une situation complète
- détecter les incohérences
- proposer plusieurs solutions adaptées
- expliquer les choix et compromis

---

## Modes de fonctionnement

### Forward mode

Contraintes → protocole

Le moteur part des conditions réelles pour proposer un protocole adapté.

Exemples :

- environnement
- farine disponible
- matériel
- temps disponible

---

### Reverse mode

Objectif → contraintes + protocole

Le moteur part d’un résultat souhaité pour définir :

- les conditions nécessaires
- les paramètres cohérents
- les limites éventuelles

---

## Modèle d’entrée

Le moteur s’appuie sur un objet global (ex : `PizzaScenario`) structuré en plusieurs blocs.

### Environnement

- température ambiante
- humidité
- saison
- température de la farine
- température de l’eau
- température finale de pâte cible

---

### Farine

- type
- W
- P/L
- protéines
- cendres
- absorption

---

### Formulation

- hydratation
- sel
- matière grasse
- levure
- type de fermentation (directe, biga, poolish, levain)

---

### Temps

- temps total disponible
- pointage
- apprêt
- durée de maturation

---

### Mise en forme

- poids du pâton
- diamètre
- épaisseur
- corniche

---

### Cuisson

- type de four
- température maximale
- surface de cuisson (pierre, acier)
- inertie thermique
- durée de cuisson cible

---

### Objectif produit

- type de pizza
- texture
- alvéolage
- croustillant / moelleux
- digestibilité
- priorité (sécurité / équilibre / performance)

---

## Traitement

Le moteur combine plusieurs couches :

### 1. Récupération documentaire (RAG)

- interrogation du corpus
- récupération de contextes pertinents

---

### 2. Règles métier

- compatibilité farine / temps
- compatibilité four / style de pizza
- cohérence hydratation / cuisson
- contraintes fermentation

---

### 3. Contraintes physiques

- température finale de pâte
- activité enzymatique
- comportement du gluten
- dynamique thermique

---

### 4. Heuristiques

- estimation des temps
- plages de validité
- tolérances

---

### 5. Gestion du risque

Un facteur de tolérance (**k**) permet de moduler :

- sécurité
- performance
- expérimentation

---

## Pipeline de décision

1. validation des entrées  
2. détection des incohérences  
3. filtrage des styles compatibles  
4. calcul des plages plausibles  
5. génération de protocoles candidats  
6. classement des solutions  

---

## Modèle de sortie

Le moteur produit une réponse structurée :

### Recommandations

- styles compatibles
- style recommandé
- styles déconseillés

---

### Paramètres de pâte

- hydratation cible
- température de l’eau
- température finale de pâte
- fermentation recommandée
- durée pointage / apprêt

---

### Paramètres de cuisson

- température cible
- durée
- compatibilité four
- ajustements nécessaires

---

### Analyse

- niveau de risque
- incohérences détectées
- points critiques

---

### Explication

- justification des choix
- alternatives
- compromis

---

## Exemple (Forward)

Entrée :

- four domestique 450°C
- farine W300
- 24h disponibles
- température ambiante 22°C

Sortie :

- styles compatibles
- protocole recommandé
- hydratation ajustée
- température eau calculée
- niveau de risque

---

## Exemple (Reverse)

Entrée :

- pizza napolitaine contemporaine
- texture légère et alvéolée

Sortie :

- contraintes nécessaires
- type de four recommandé
- plage de W
- hydratation cohérente
- protocole adapté

---

## Vision

Le Decision Engine est conçu comme un système évolutif :

- ajout de règles métier
- amélioration du dataset
- intégration de modèles plus précis
- raffinement des heuristiques

---

## Limites actuelles

- dépendance à la qualité des sources
- heuristiques encore empiriques
- modélisation thermique partielle

---

## Évolution

- formalisation mathématique des règles
- calibration sur données réelles
- amélioration du scoring des solutions
- intégration de retours terrain
