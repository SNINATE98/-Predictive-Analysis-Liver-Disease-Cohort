Entre vie, greffe et décès : Analyse prédictive appliquée à une cohorte hépatique
<img width="1792" height="1024" alt="image" src="https://github.com/user-attachments/assets/dc83077b-3cfd-45cb-bf95-e091e9ae615e" />


##  Introduction

La prédiction du pronostic vital chez les patients atteints de maladies hépatiques constitue un enjeu majeur en santé publique. Elle permet non seulement d’optimiser la prise en charge clinique, mais aussi d’anticiper l’évolution de la maladie et d’adapter les stratégies thérapeutiques.

Dans ce projet, nous cherchons à développer un modèle de classification capable d’estimer, pour chaque patient, la probabilité d’appartenir à l’une des trois catégories suivantes :  
- **Status_C** : patient vivant  
- **Status_CL** : patient vivant ayant bénéficié d’une transplantation hépatique  
- **Status_D** : patient décédé  

La performance des modèles est évaluée à l’aide du **log loss**, une métrique adaptée aux problèmes de classification probabiliste, qui pénalise fortement les prédictions mal calibrées. L’objectif est donc de minimiser cette valeur afin d’obtenir des probabilités fiables et bien ajustées.

Le projet suit une démarche méthodologique structurée :

### 🔍 1. Analyse exploratoire des données (EDA)
Une étude approfondie des données est réalisée afin de comprendre les caractéristiques de la cohorte et de détecter d’éventuelles anomalies.

### 🧹 2. Prétraitement des données
Cette étape inclut la gestion des valeurs manquantes et des valeurs aberrantes, indispensables pour garantir la qualité et la robustesse des modèles.

### 📊 3. Modélisation initiale
Une régression logistique multinomiale est utilisée comme modèle de base, en raison de sa simplicité d’interprétation et de sa capacité à produire des probabilités pour des classes multiples.

### 🚀 4. Amélioration des performances
Des modèles plus avancés, notamment **XGBoost**, sont ensuite testés afin d’améliorer la performance prédictive, en particulier dans un contexte de données complexes et potentiellement bruitées.

---

À travers cette approche progressive, l’objectif est d’identifier le modèle le plus performant et le mieux calibré pour prédire le statut vital des patients. Une attention particulière est portée à la robustesse des résultats, évalués à la fois sur des données internes et sur un jeu de test externe fourni par Kaggle.
