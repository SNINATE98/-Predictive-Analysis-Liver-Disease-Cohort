#  Entre vie, greffe et décès : Analyse prédictive appliquée à une cohorte hépatique

<img width="1792" height="1024" alt="image" src="https://github.com/user-attachments/assets/dc83077b-3cfd-45cb-bf95-e091e9ae615e" />

##  Objectif

Ce projet vise à prédire le statut vital de patients atteints de maladies hépatiques à partir de données cliniques et biologiques.

Trois classes sont considérées :
- **Status_C** : patient vivant  
- **Status_CL** : patient vivant avec transplantation  
- **Status_D** : patient décédé  

L’objectif est de produire des **probabilités fiables et bien calibrées** pour chaque classe.

---

##  Métrique d’évaluation

Le modèle est évalué avec la **log loss**, une métrique adaptée à la classification probabiliste :

- pénalise fortement les mauvaises prédictions
- sensible à la **calibration des probabilités**
- favorise les modèles bien ajustés

 Objectif : **minimiser le log loss**

---

## Approche méthodologique

### 1. Analyse exploratoire (EDA)
- Analyse des distributions et des asymétries
- Détection des valeurs aberrantes (outliers)
- Étude des corrélations (heatmap)
- Analyse univariée et bivariée

### 2. Gestion des valeurs manquantes
- Variables numériques :
  - imputation par **médiane conditionnelle (par classe)**
  - médiane globale si faible taux de NA
- Variables catégorielles :
  - nettoyage des anomalies
  - imputation par **mode conditionnel**
- Validation statistique :
  - **Kolmogorov-Smirnov** (normalité)
  - **Kruskal-Wallis** (variables informatives)
  - **Chi²** (indépendance catégorielle)

 Objectif : limiter le biais et préserver l’information

---

### 3. Préprocessing
- **One-Hot Encoding** pour variables catégorielles
- **RobustScaler** (robuste aux outliers)
- Split train / validation (**stratifié**)

---

##  Modélisation

###  Régression logistique multinomiale
- Modèle de base probabiliste
- Optimisation via **GridSearchCV**
- Validation croisée **Stratified K-Fold (k=10)**

**Résultat :**
- Log loss CV ≈ **0.328**
- Bon compromis biais / variance

---

###  Calibration des probabilités
- Méthode : **Platt Scaling (sigmoid)**
- Évaluation :
  - courbes de calibration
  - comparaison log loss avant/après

**Conclusion :**
- Modèle déjà bien calibré
- calibration inutile → légère dégradation du log loss

---

###  XGBoost
- Modèle de **gradient boosting**
- Gestion des non-linéarités et interactions

**Résultats :**
- Log loss train ≈ 0.355  
- Log loss Kaggle ≈ **0.3479**  (meilleure généralisation)

---

###  Réseau de neurones (MLP)
- Implémentation avec **PyTorch**
- Architecture simple (2 couches cachées)

**Résultat :**
- Mauvaise généralisation (log loss ≈ 0.84)

 Modèle non retenu

---

##  Résultats clés

-  Modèle logistique performant et **bien calibré**
-  XGBoost améliore la **généralisation externe**
-  Réseau de neurones non adapté
-  Difficulté sur la classe minoritaire (déséquilibre)

---

##  Points techniques clés

- Classification **multiclasse probabiliste**
- **Calibration des probabilités**
- **Log loss optimization**
- Validation croisée (CV)
- Feature engineering & preprocessing
- Gestion avancée des valeurs manquantes
- Analyse statistique (KS, Kruskal, Chi²)

---

##  Perspectives

- Gestion du déséquilibre de classes
- Feature engineering avancé
- Calibration multiclasses plus robuste
- Modèles hybrides / ensembles

---

##  Stack technique

- Python (Pandas, NumPy)
- Scikit-learn
- XGBoost
- PyTorch
- Matplotlib / Seaborn

---

##  Conclusion

Ce projet met en évidence l’importance de la **calibration des probabilités**, de la **qualité des données** et du **choix du modèle** dans un problème de classification médicale.

Les modèles linéaires et les méthodes de boosting apparaissent comme les plus adaptés pour produire des prédictions fiables et interprétables dans ce contexte.
