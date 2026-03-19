Entre vie, greffe et décès : Analyse prédictive appliquée à une cohorte hépatique
<img width="1792" height="1024" alt="image" src="https://github.com/user-attachments/assets/dc83077b-3cfd-45cb-bf95-e091e9ae615e" />


Introduction
La prédiction du pronostic vital chez les patients atteints de maladies hépatiques représente un enjeu majeur en santé publique, tant pour optimiser la prise en charge médicale que pour anticiper les évolutions cliniques. Dans ce contexte, ce projet a pour objectif de développer un modèle de classification permettant d’estimer, pour chaque patient, la probabilité d’appartenir à l’une des trois catégories suivantes : Status_C (patient vivant), Status_CL (patient vivant ayant bénéficié d’une transplantation hépatique) et Status_D (patient décédé).

Les performances des modèles sont évaluées à l’aide du log loss, une métrique qui mesure la qualité des probabilités prédites et pénalise fortement les erreurs de calibration. L’objectif final est donc de minimiser cette valeur afin d’obtenir des prédictions fiables et précises des probabilités associées à chaque issue possible.

Pour mener à bien ce travail, nous suivrons une démarche structurée. Nous commencerons par une analyse exploratoire approfondie des données afin de mieux comprendre les caractéristiques de la cohorte et d’identifier les éventuelles anomalies. Nous procéderons ensuite à la gestion des valeurs manquantes et des valeurs aberrantes, étapes essentielles pour garantir la qualité et la robustesse des données utilisées.

Dans un premier temps, nous mettrons en œuvre une régression logistique multinomiale, choisie pour sa simplicité et sa capacité à modéliser des sorties multiclasses probabilistes. Enfin, afin d’améliorer la performance du modèle initial, nous expérimenterons des approches plus complexes, notamment l’algorithme XGBoost, reconnu pour son efficacité sur des problématiques de classification multiclasses et sa capacité à gérer des données hétérogènes et bruitées.

À travers cette approche progressive, nous chercherons à identifier le modèle le plus performant et le mieux calibré pour prédire le statut vital des patients, en veillant à assurer la robustesse des résultats aussi bien sur nos jeux de données internes que sur le dataset d’évaluation externe fourni par Kaggle.
