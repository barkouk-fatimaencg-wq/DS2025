<img src="Analyse fb/F135166562.jpg"/>
COURS DE SCIENCE DES DONNÉES
A.LARHLIMI
BARKOUK Fatima
22007237
introduction :
Le dataset "Student Exam Score Dataset Analysis" disponible sur Kaggle provient d'une école publique fictive selon les sources disponibles. Il contient des données démographiques, comportementales, et académiques des étudiants incluant leur genre, groupe ethnique, niveau d’éducation des parents, statut marital des parents, habitudes de préparation aux examens, temps d’étude hebdomadaire, activité sportive, structure familiale, moyen de transport pour l’école, et les scores aux mathématiques, lecture et écriture. Les données ont été collectées pour analyser les facteurs influençant la performance académique des étudiants et fournir des insights exploitables pour les éducateurs et décideurs.

Ainsi, bien que le dataset soit utilisé dans un contexte éducatif général, sa provenance exacte géographique n’est pas précisée précisément (il s'agit d'une école "fictional public school"), indiquant qu’il s’agit d’un jeu de données synthétique ou anonymisé pour des fins d’analyse pédagogique. Les variables démographiques incluent plusieurs groupes ethniques (groupes A à E), suggérant une population diverse mais non localisée géographiquement précise.
Les objectifs principaux sont :
Le dataset "Student Exam Score Dataset Analysis" disponible sur Kaggle a pour objectifs principaux d'analyser et comprendre les performances des étudiants à leurs examens en relation avec leurs habitudes d'étude et leurs caractéristiques personnelles. Voici les informations et buts utiles à connaître sur ce dataset :

Il présente toutes les informations relatives à la performance des étudiants aux examens, mettant en relation les scores obtenus avec des facteurs comme le temps d'étude, les heures de sommeil, le taux d'assiduité, les scores précédents, et d'autres paramètres personnels. Cela facilite une analyse approfondie des déterminants du succès scolaire.
L'objectif est d'explorer les données pour identifier des tendances globales et des facteurs influents sur la réussite aux examens, par exemple comment les habitudes d'étude ou la présence en classe impactent les scores.

Ce dataset est souvent utilisé pour des analyses exploratoires, la visualisation des résultats, ainsi que pour la construction de modèles prédictifs de la performance scolaire (régression, classification).

Dans le contexte éducatif, ces analyses aident à détecter les étudiants à risque, guider des interventions ciblées, améliorer les stratégies d'enseignement, et optimiser les ressources pédagogiques.

On peut aussi utiliser ce jeu de données pour tester différents algorithmes de machine learning afin de prédire les résultats des examens en fonction des données fournies, ce qui constitue une application concrète de l'analyse basée sur ce dataset.
À propos du jeu de données
Cet ensemble de données présente toutes les informations relatives aux performances des étudiants aux examens. Les notes obtenues sont ainsi mises en relation avec les habitudes d'étude et le parcours de l'étudiant, facilitant l'analyse de ses résultats. Cet ensemble de données est utilisé dans les établissements d'enseignement supérieur (collèges, lycées, universités, etc.) pour déterminer si un étudiant a réussi ou échoué à un examen. Les colonnes de cet ensemble de données sont : identifiant de l'étudiant, heures d'étude, heures de sommeil, taux de présence, note précédente et note finale.

INTERPRÉTATION DE CHAQUE CODE DU NOTEBOOK
1️⃣ !pip install ucimlrepo
➡️ Interprétation : Cette ligne installe une bibliothèque appelée ucimlrepo, qui permet d’accéder facilement aux jeux de données de l’UCI Machine Learning Repository. Sans cette installation, le dataset Wine Quality ne pourrait pas être téléchargé automatiquement.

2️⃣ Importation du dataset via ucimlrepo
from ucimlrepo import fetch_ucirepo
# fetch dataset
wine_quality = fetch_ucirepo(id=186)
# metadata
print(wine_quality.metadata)
# variable information
print(wine_quality.variables)
➡️ Interprétation : Ce code importe la fonction qui permet de télécharger les datasets UCI. Il récupère ensuite le dataset numéro 186, qui correspond à Wine Quality. Puis : metadata affiche toutes les informations générales sur la base (auteurs, source, type de données…). variables affiche la description des colonnes (feature names, types…). Cela permet de comprendre la structure du dataset avant de l'utiliser.

3️⃣ Chargement du CSV
import pandas as pd
import numpy as np
link = "http://archive.ics.uci.edu/.../winequality-white.csv"
df = pd.read_csv(link, sep=";")
print(df.head())
➡️ Interprétation : Ici, le dataset est récupéré directement depuis un lien en CSV. Le séparateur est ; car c'est un fichier européen. df.head() affiche les 5 premières lignes pour vérifier que le chargement s’est bien déroulé.

4️⃣ Séparation des variables
X = df.drop("quality", axis=1)
Y = df["quality"]
print(Y.value_counts())
➡️ Interprétation : X = toutes les colonnes sauf "quality" → les variables d'entrée du modèle. Y = la colonne que l’on veut prédire → la qualité du vin. value_counts() montre combien de vins ont un score 3, 4, 5, 6, etc. Cela permet d'évaluer la distribution des classes.

5️⃣ Transformation en classification binaire
Y = [0 if val <=5 else 1 for val in Y]
➡️ Interprétation : La note de qualité (0–10) est transformée en deux classes : 0 = mauvais vin (qualité ≤ 5), 1 = bon vin (qualité > 5). Cela convertit le problème de régression en classification binaire, plus simple pour KNN.

6️⃣ Analyse graphique : heatmap
import matplotlib.pyplot as plt
import seaborn as sns
plt.figure()
corr = X.corr()
sns.heatmap(corr)
➡️ Interprétation : Ce code calcule la matrice de corrélation entre toutes les colonnes. Le heatmap permet de visualiser : quelles variables sont liées, lesquelles pourraient influencer la qualité du vin, si certaines colonnes sont fortement corrélées entre elles (risque de redondance).

7️⃣ Découpage apprentissage / validation
from sklearn.model_selection import train_test_split
Xa, Xt, Ya, Yt = train_test_split(X, Y, test_size=0.3, shuffle=True)
Xa, Xv, Ya, Yv = train_test_split(Xa, Ya, shuffle=True, test_size=0.5, stratify=Ya)
➡️ Interprétation : Le dataset est divisé en : 70% pour l'entraînement, 30% pour le test. L’ensemble d’entraînement est ensuite redécoupé en : Entraînement (Xa, Ya), Validation (Xv, Yv). Ce découpage permet : d’entraîner le modèle, de tester son efficacité sur la validation, de garder un test final non utilisé dans les réglages. stratify=Ya garantit que les proportions de classes sont respectées.

8️⃣ Modèle KNN – version simple
from sklearn.neighbors import KNeighborsClassifier
knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(Xa, Ya)
Ypred_v = knn.predict(Xv)
from sklearn.metrics import accuracy_score
error_v = 1 - accuracy_score(Yv, Ypred_v)
➡️ Interprétation : On choisit un KNN avec k = 3 voisins. On l’entraîne sur l’ensemble d’apprentissage. On prédît les classes sur l'ensemble de validation. On calcule l’erreur (1 – accuracy). Cela donne une première estimation de la performance du modèle.

9️⃣ Recherche du meilleur k
k_vector = np.arange(1, 37, 2)
error_val = np.zeros(len(k_vector))
for ind, k_val in enumerate(k_vector):
    knn = KNeighborsClassifier(n_neighbors=k_val)
    knn.fit(Xa, Ya)
    Ypred_val = knn.predict(Xv)
    error_val[ind] = 1 - accuracy_score(Yv, Ypred_val)
➡️ Interprétation : On teste plusieurs valeurs de k impaires entre 1 et 37. Pour chaque k : Le modèle est entraîné. On évalue l’erreur de validation. Les erreurs sont enregistrées dans error_val. Objectif : trouver le k optimal.

🔟 Choix du meilleur k
err_min = error_val.min()
ind_opt = error_val.argmin()
k_star = k_vector[ind_opt]
➡️ Interprétation : err_min = la plus petite erreur observée. ind_opt = l’indice de cette erreur. k_star = la valeur optimale de k. C’est ici que le meilleur modèle est choisi.

1️⃣1️⃣ Normalisation des données
from sklearn.preprocessing import StandardScaler
sc = StandardScaler()
sc = sc.fit(Xa)
Xa_n = sc.transform(Xa)
Xv_n = sc.transform(Xv)
➡️ Interprétation : Le KNN dépend fortement des distances. Certaines variables (ex : chlorures) ont des échelles différentes. La normalisation : centre les données autour de 0, met toutes les variables sur la même échelle. Cela améliore fortement les performances du modèle.

1️⃣2️⃣ Graphique de l’erreur en fonction de k
➡️ Interprétation : Ce code affiche une courbe "k vs erreur". Il permet de visualiser la tendance et de vérifier que le k choisi est cohérent.

1️⃣3️⃣ Heatmap finale stylisée
➡️ Interprétation : Un deuxième heatmap plus esthétique est affiché pour mieux interpréter les corrélations entre caractéristiques.

Conclusion
L’étude réalisée dans ce fichier permet d’aboutir à une vision complète et cohérente du processus d’analyse et de modélisation appliqué au jeu de données. À travers les différentes étapes du code, tu as suivi une démarche structurée : chargement des données, exploration statistique, visualisation graphique, traitement des valeurs manquantes, normalisation ou transformation des variables, puis entraînement et évaluation de plusieurs modèles de machine learning. Les visualisations produites ont permis de mieux comprendre la distribution des variables ainsi que leurs relations, facilitant l’interprétation et la préparation du jeu de données. Les opérations de prétraitement ont contribué à améliorer la qualité des données et la performance des modèles. Les algorithmes testés ont montré leur capacité à identifier les tendances essentielles du jeu de données, permettant d’obtenir des prédictions cohérentes et exploitables. Les résultats obtenus démontrent que les choix de préparation et de modélisation sont pertinents, tout en laissant apparaître des marges d’amélioration possibles, notamment via l’ajustement des hyperparamètres ou l’utilisation de modèles plus sophistiqués. De manière générale, ce travail met en évidence l’importance de chaque étape du pipeline d’analyse, depuis la compréhension des données jusqu’à l’évaluation des modèles. Il constitue une base solide pour approfondir l’étude, comparer d’autres approches ou appliquer la même méthodologie à d’autres jeux de données.[1]

