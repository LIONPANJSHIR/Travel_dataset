# 🚀 Projet d'Apprentissage Automatique : Prédiction de la Souscription de Produits de Voyage

## 🎯 Objectif du Projet
L'objectif principal de ce projet est d'analyser les données de clients potentiels pour un produit de voyage et de développer un modèle de classification robuste capable de prédire si un client est susceptible de **souscrire au produit** (`ProdTaken`). Le projet met l'accent sur la rigueur du pipeline MLOps et la gestion du déséquilibre de classe.

## 🛠️ Stack Technique et Bibliothèques
| Composant | Outil / Librairie |
| :--- | :--- |
| **Langage** | Python 3.x |
| **Analyse** | Pandas, NumPy |
| **Visualisation** | Matplotlib, Seaborn |
| **Modélisation** | Scikit-learn (SVC, RF, DT, AdaBoost) |
| **Optimisation** | RandomizedSearchCV, ColumnTransformer |

---

## 🗺️ Pipeline de Modélisation (Étapes Clés)

### 1. 🔍 Analyse Exploratoire et Préparation des Données

* **Nettoyage & Imputation :**
    * Correction des incohérences ('Fe Male' → 'Female', 'Unmarried' → 'Single').
    * Imputation stratégique : **Médiane** pour les variables numériques sensibles aux *outliers*, **Mode** pour les variables catégorielles.
* **Ingénierie des Caractéristiques :** Création de nouvelles variables clés pour améliorer la puissance prédictive : `Income_Per_Person`, `Engagement_Score`, `Total_visiting`, etc.
* **Corrélation :** Analyse par Heatmap pour identifier et gérer la multicolinéarité.

### 2. 🛡️ Gestion du Déséquilibre et Prétraitement

* **Déséquilibre :** La variable cible (`ProdTaken`) présente un déséquilibre important.
* **Division Stratifiée :** Les données ont été divisées en ensembles d'entraînement et de test (80/20) en utilisant la **stratification** pour maintenir la proportion des classes dans les deux ensembles.
* **Pipeline de Prétraitement :** Mise en place d'un `ColumnTransformer` pour garantir l'absence de *Data Leakage* :
    * **Numérique :** `StandardScaler` (Normalisation).
    * **Catégorielle :** `OneHotEncoder`.

### 3. ⚖️ Entraînement, Évaluation & Optimisation

* **Évaluation Initiale :** Plusieurs modèles de classification ont été évalués (Logistic Regression, SVC, RF, DT, AdaBoost).
    * **Métrique Clé :** Le **F1-score pondéré** a été choisi comme métrique principale en raison du déséquilibre des classes.
* **Tuning des Hyperparamètres :** Les meilleurs modèles (Random Forest et Decision Tree) ont été sélectionnés pour l'optimisation.
    * Utilisation de `RandomizedSearchCV` pour trouver les meilleurs hyperparamètres de manière **efficace en temps**.

### 4. 📈 Résultats et Analyse Finale

| Modèle Optimisé | Métrique d'Optimisation | **F1-Score Final (Test)** | **Classement** |
| :--- | :--- | :--- | :--- |
| **Optimized Random Forest** | F1-Score (CV) : ~0.78 | **[Score Final Obtenu]** | 🥇 Meilleur Modèle |
| Optimized Decision Tree | F1-Score (CV) : ~0.68 | [Score Final Obtenu] | 🥈 Second Meilleur |

---

## 💡 Interprétabilité et Conclusion

* **Meilleur Modèle :** Le **Random Forest Optimisé** a démontré la meilleure capacité de généralisation.
* **Analyse de l'Importance des Caractéristiques :**
    * Cette étape a permis d'identifier les variables qui ont le plus d'impact sur la décision de souscription (e.g., `MonthlyIncome`, `Passport`, `Engagement_Score`). Ces informations sont directement exploitables par l'équipe marketing.
* **Évaluation ROC/AUC :** Une analyse approfondie a été réalisée via la **Courbe ROC** et le **Score AUC** pour confirmer la robustesse du modèle indépendamment du seuil de classification.

> **Conclusion :** Le pipeline a produit un modèle robuste (Random Forest) capable de prédire la souscription avec une grande fiabilité, fournissant des leviers d'action clairs pour l'engagement client.
