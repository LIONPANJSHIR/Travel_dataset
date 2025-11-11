
# Analyse et Modélisation des Données de Voyage

Ce projet vise à analyser un ensemble de données lié aux voyages et à construire un modèle de classification pour prédire si un client prendra un produit de voyage (variable `ProdTaken`).

## Étapes du Projet

1.  **Importation des Bibliothèques :** Importation des bibliothèques nécessaires pour l'analyse des données, la visualisation et la modélisation (pandas, numpy, matplotlib, seaborn, sklearn).
2.  **Chargement des Données :** Chargement de l'ensemble de données "Travel.csv" dans un DataFrame pandas.
3.  **Analyse Exploratoire des Données (EDA) :**
    *   Affichage des premières lignes du DataFrame pour comprendre la structure des données.
    *   Visualisation des valeurs manquantes à l'aide de `missingno`.
    *   Calcul et affichage du pourcentage de valeurs manquantes pour chaque colonne.
    *   Affichage des informations sur les types de données et les valeurs non nulles (`data.info()`).
    *   Exploration des valeurs uniques dans les colonnes catégorielles.
    *   Correction des incohérences dans la colonne 'Gender' ('Fe Male' remplacé par 'Female').
    *   Remplacement de 'Unmarried' par 'Single' dans la colonne 'MaritalStatus'.
    *   Affichage de la distribution de la colonne 'Passport'.
    *   Identification et affichage des caractéristiques avec des valeurs manquantes.
4.  **Imputation des Valeurs Manquantes :**
    *   Imputation de la médiane pour les colonnes numériques ('Age', 'DurationOfPitch', 'NumberOfTrips', 'NumberOfChildrenVisiting', 'MonthlyIncome').
    *   Imputation du mode pour les colonnes catégorielles ('TypeofContact', 'NumberOfFollowups', 'PreferredPropertyStar').
    *   Vérification de l'absence de valeurs manquantes après imputation.
5.  **Ingénierie des Caractéristiques :**
    *   Création de nouvelles caractéristiques basées sur les données existantes, telles que 'Income_Per_Person', 'Income_Per_Child', 'Engagement_Score', 'Age_Group', et 'Total_visiting'.
    *   Suppression des colonnes originales utilisées pour créer les nouvelles caractéristiques pour éviter la multicolinéarité et simplifier le modèle.
6.  **Visualisation de la Corrélation :** Affichage d'une heatmap pour visualiser la matrice de corrélation entre les variables numériques afin d'identifier les relations.
7.  **Préparation du Modèle :**
    *   Séparation des caractéristiques (`X`) et de la variable cible (`y`).
    *   Analyse de la distribution de la variable cible (`ProdTaken`), révélant un déséquilibre de classe.
    *   Visualisation de la distribution de la variable cible à l'aide d'un countplot, mettant en évidence le déséquilibre.
8.  **Division des Données :** Division des données en ensembles d'entraînement et de test (80% entraînement, 20% test) en utilisant la stratification pour maintenir la proportion de la variable cible.
9.  **Prétraitement des Caractéristiques :**
    *   Application de `StandardScaler` pour normaliser les caractéristiques numériques.
    *   Application de `OneHotEncoder` pour gérer les caractéristiques catégorielles.
    *   Utilisation de `ColumnTransformer` pour appliquer les transformations appropriées aux différents types de colonnes.
10. **Entraînement et Évaluation des Modèles Initiaux :**
    *   Définition de plusieurs modèles de classification (Logistic Regression, SVC, Decision Tree, Random Forest, AdaBoost, Voting Classifier).
    *   Entraînement de chaque modèle sur l'ensemble d'entraînement.
    *   Évaluation des performances de chaque modèle sur l'ensemble de test en utilisant le F1-score (pondéré en raison du déséquilibre des classes), la matrice de confusion et le rapport de classification.
    *   Classement des modèles en fonction de leur F1-score sur l'ensemble de test.
11. **Tuning des Hyperparamètres :**
    *   Sélection des modèles les plus performants (Random Forest et Decision Tree) pour l'optimisation des hyperparamètres.
    *   Définition des grilles de paramètres pour `RandomizedSearchCV`.
    *   Exécution de `RandomizedSearchCV` avec validation croisée pour trouver les meilleurs hyperparamètres pour chaque modèle, en utilisant le F1-score comme métrique d'évaluation.
12. **Évaluation Finale des Modèles Optimisés :**
    *   Initialisation des modèles avec les meilleurs hyperparamètres trouvés.
    *   Entraînement final des modèles optimisés sur l'ensemble d'entraînement complet.
    *   Évaluation des performances finales sur l'ensemble de test en utilisant le F1-score et le rapport de classification.
    *   Classement final des modèles optimisés.

## Conclusion

Les modèles Random Forest et Decision Tree ont montré les meilleures performances initiales. Après l'optimisation des hyperparamètres, le modèle **Optimized Random Forest** a obtenu le meilleur F1-score sur l'ensemble de test, ce qui en fait le modèle le plus performant pour prédire si un client prendra un produit de voyage dans cet ensemble de données. Le déséquilibre des classes a été pris en compte en utilisant des métriques appropriées (F1-score pondéré) et des techniques (stratification).
