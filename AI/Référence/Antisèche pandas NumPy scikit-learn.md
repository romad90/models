Retour : [[00 Accueil]] · Module : [[M1 Fondations Python et maths]] · Leçon : [[0001-entrainer-son-premier-modele|0001]]

# Antisèche : NumPy, pandas, scikit-learn

## NumPy
```python
import numpy as np
a = np.array([[1, 2], [3, 4]])     # tableau 2D
a.shape, a.dtype                    # (2, 2), int64
np.zeros((3, 4)); np.ones(5); np.arange(0, 10, 2); np.linspace(0, 1, 5)
a.T                                 # transposée
a @ a                               # produit matriciel
a * a                               # produit élément par élément
a.mean(axis=0)                      # moyenne par colonne (axis=1 : par ligne)
a[a > 2]                            # masque booléen
a.reshape(4, 1)                     # changer la forme
np.random.default_rng(42).normal(size=(3,))  # aléatoire reproductible
```

## pandas
```python
import pandas as pd
df = pd.read_csv("data.csv")        # aussi read_parquet, read_gbq (BigQuery)
df.head(); df.info(); df.describe() # premier coup d'œil
df["col"]; df[["a", "b"]]           # sélection de colonnes
df.loc[df["age"] > 30, ["nom"]]     # filtre par étiquette
df.iloc[0:5, 0:2]                   # filtre par position
df.isna().sum()                     # valeurs manquantes par colonne
df["col"].fillna(df["col"].median(), inplace=False)
df.groupby("ville")["prix"].agg(["mean", "count"])
df.merge(autre, on="id", how="left")
df["col"].value_counts(normalize=True)   # répartition des classes
pd.get_dummies(df, columns=["ville"])    # one-hot encoding
```

## scikit-learn : le schéma universel
```python
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import classification_report

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, stratify=y, random_state=42)   # stratify si classification

model = Pipeline([("scale", StandardScaler()),          # le prétraitement fait partie
                  ("clf", RandomForestClassifier())])   # du modèle : évite la fuite de données
model.fit(X_train, y_train)          # entraîner
y_pred = model.predict(X_test)       # prédire
print(classification_report(y_test, y_pred))
cross_val_score(model, X_train, y_train, cv=5, scoring="f1")
```

| Tâche | Estimateurs courants |
|---|---|
| Régression | `LinearRegression`, `Ridge`, `RandomForestRegressor`, `GradientBoostingRegressor` |
| Classification | `LogisticRegression`, `RandomForestClassifier`, `GradientBoostingClassifier`, `SVC` |
| Clustering | `KMeans`, `DBSCAN` |
| Réduction de dimension | `PCA` |
| Prétraitement | `StandardScaler`, `OneHotEncoder`, `SimpleImputer`, `ColumnTransformer` |
| Recherche d'hyperparamètres | `GridSearchCV`, `RandomizedSearchCV` |

> [!warning] Règle
> On fait `fit` **uniquement** sur le jeu d'entraînement, y compris pour le scaler. Sinon, c'est une fuite de données ([[Pièges classiques du ML]]).

> [!source] Source primaire
> [Guide utilisateur scikit-learn](https://scikit-learn.org/stable/user_guide.html) · [10 minutes to pandas](https://pandas.pydata.org/docs/user_guide/10min.html)
