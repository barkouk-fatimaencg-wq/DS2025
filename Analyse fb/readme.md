# COURS DE SCIENCE DES DONNÉES

# A.LARHLIMI

## BARKOUK Fatima 
## 22007237
<img src="m.jpg" style="height:540px;margin-right:393px"/>

## École Nationale de Commerce et de Gestion (ENCG) - 4ème Année

## Analyse des données relatives aux notes des étudiants aux examens
---
## À propos du jeu de données :
Le dataset "Student Exam Score Dataset Analysis" disponible sur Kaggle provient d'une école publique fictive selon les sources disponibles. Il contient des données démographiques, comportementales, et académiques des étudiants incluant leur genre, groupe ethnique, niveau d’éducation des parents, statut marital des parents, habitudes de préparation aux examens, temps d’étude hebdomadaire, activité sportive, structure familiale, moyen de transport pour l’école, et les scores aux mathématiques, lecture et écriture. Les données ont été collectées pour analyser les facteurs influençant la performance académique des étudiants et fournir des insights exploitables pour les éducateurs et décideurs.

Ainsi, bien que le dataset soit utilisé dans un contexte éducatif général, sa provenance exacte géographique n’est pas précisée précisément (il s'agit d'une école "fictional public school"), indiquant qu’il s’agit d’un jeu de données synthétique ou anonymisé pour des fins d’analyse pédagogique. Les variables démographiques incluent plusieurs groupes ethniques (groupes A à E), suggérant une population diverse mais non localisée géographiquement précise.
## Les objectifs principaux sont :
Le dataset "Student Exam Score Dataset Analysis" disponible sur Kaggle a pour objectifs principaux d'analyser et comprendre les performances des étudiants à leurs examens en relation avec leurs habitudes d'étude et leurs caractéristiques personnelles. Voici les informations et buts utiles à connaître sur ce dataset :

Il présente toutes les informations relatives à la performance des étudiants aux examens, mettant en relation les scores obtenus avec des facteurs comme le temps d'étude, les heures de sommeil, le taux d'assiduité, les scores précédents, et d'autres paramètres personnels. Cela facilite une analyse approfondie des déterminants du succès scolaire.
L'objectif est d'explorer les données pour identifier des tendances globales et des facteurs influents sur la réussite aux examens, par exemple comment les habitudes d'étude ou la présence en classe impactent les scores.

Ce dataset est souvent utilisé pour des analyses exploratoires, la visualisation des résultats, ainsi que pour la construction de modèles prédictifs de la performance scolaire (régression, classification).

Dans le contexte éducatif, ces analyses aident à détecter les étudiants à risque, guider des interventions ciblées, améliorer les stratégies d'enseignement, et optimiser les ressources pédagogiques.

On peut aussi utiliser ce jeu de données pour tester différents algorithmes de machine learning afin de prédire les résultats des examens en fonction des données fournies, ce qui constitue une application concrète de l'analyse basée sur ce dataset.
À propos du jeu de données
Cet ensemble de données présente toutes les informations relatives aux performances des étudiants aux examens. Les notes obtenues sont ainsi mises en relation avec les habitudes d'étude et le parcours de l'étudiant, facilitant l'analyse de ses résultats. Cet ensemble de données est utilisé dans les établissements d'enseignement supérieur (collèges, lycées, universités, etc.) pour déterminer si un étudiant a réussi ou échoué à un examen. Les colonnes de cet ensemble de données sont : identifiant de l'étudiant, heures d'étude, heures de sommeil, taux de présence, note précédente et note finale.
Contexte & objectif du dataset. 

Structure du dataset : colonnes & interprétations

D’après la description du dataset, les colonnes sont les suivantes 
Baselight
 :

Colonne	Type / Signification
student_id	Identifiant unique de l’étudiant (chaîne de caractères).
hours_studied	Nombre d’heures d’études (double / numérique). Indique combien d’heures l’étudiant a étudié — cela peut représenter une mesure d’effort.
sleep_hours	Nombre d’heures de sommeil (double / numérique). Cela peut mesurer le temps de repos / bien-être, potentiellement corrélé à la performance.
attendance_percent	Pourcentage de présence (double / numérique). Indique le taux de présence de l’étudiant (assiduité) — un facteur potentiellement influent pour la réussite.
previous_scores	Score(s) précédent(s) de l’étudiant — typiquement un entier (BIGINT). Cela peut représenter des notes antérieures, un indicateur d’historique académique.
exam_score	Score final de l’examen (double / numérique) — c’est la variable cible, l’“output” qu’on cherche à expliquer ou prédire.
---

# ⭐ **INTERPRÉTATION DE CHAQUE CODE DU NOTEBOOK**
1️⃣ student_id

Ce que c’est : un identifiant unique pour chaque étudiant.

Interprétation :

Sert uniquement à distinguer les étudiants.

N’a aucune valeur statistique ou explicative.

On ne l’utilise jamais dans une analyse ou dans un modèle.

2️⃣ hours_studied

Ce que c’est : nombre d'heures d'étude.

Interprétation :

Plus ce nombre est élevé, plus l’étudiant a travaillé.

Hypothèse courante : plus d’heures d’étude → meilleur score.

On l’utilise pour vérifier si l’effort (temps passé) a un impact sur le résultat de l’examen.

Exemple d’interprétation :
Si la corrélation est forte, cela signifie que l’étude explique une partie importante de la réussite.

3️⃣ sleep_hours

Ce que c’est : nombre d'heures de sommeil.

Interprétation :

Mesure le niveau de repos de l’étudiant.

Trop peu de sommeil peut réduire les performances.

Trop de sommeil peut aussi être un signe de désorganisation.

On vérifie souvent s’il existe un niveau optimal de sommeil.

Exemple :
Si les étudiants avec 6–8 heures dorment mieux et ont les meilleurs scores → effet positif du manque ou surplus de sommeil.

4️⃣ attendance_percent

Ce que c’est : le pourcentage de présence en cours.

Interprétation :

Mesure l’assiduité et l’implication.

Plus le pourcentage est élevé, plus l’étudiant assiste aux cours.

Souvent, la présence est un excellent prédicteur du score final.

Exemple d’analyse :
Si un étudiant a 30% de présence mais 90% d’examen, c’est atypique.
Si 90% de présence = bons résultats, cela confirme l’importance de l’assiduité.

5️⃣ previous_scores

Ce que c’est : score(s) obtenus précédemment.

Interprétation :

Mesure le niveau académique historique de l’étudiant.

Les étudiants avec de bons résultats dans le passé ont statistiquement plus de chances de réussir encore.

C’est une variable très utile pour prédire le score final.

Exemple :
Un étudiant avec 95 de moyenne avant a plus de chances d’avoir un bon score à l’examen final.

6️⃣ exam_score (variable cible)

Ce que c’est : score final de l’examen.

Interprétation :

C’est le résultat final, la variable que l’on cherche à expliquer.

On va analyser comment les autres variables (étude, sommeil, présence, scores précédents) influencent ce score.

Exemple :
Si hours_studied explique 40% de la variation du score → bonne prédiction.
Si sleep_hours n’a aucun effet → variable non déterminante.
---
7️⃣Interprétation du graphique
plt.figure(figsize=(8, 6))
sns.histplot(data['exam_score'], kde=True, bins=10, color='skyblue')
plt.title("Target Distribution")
plt.xlabel("exam_score")
plt.ylabel("Count")
plt.show()

Ce graphique représente la distribution de la variable exam_score, c’est-à-dire la répartition des notes finales des étudiants.
<img src="téléchargement (1).png" style="height:540px;margin-right:393px"/>

Voici ce que l’on observe :

✅ 1) Forme générale : distribution quasi-normale

La courbe bleue ressemble à une courbe en cloche (distribution normale).

Cela signifie que :

La majorité des étudiants ont des scores proches de la moyenne.

Peu d’étudiants ont des scores très bas ou très élevés.

👉 Interprétation :
La performance des étudiants est centrée autour d’un score moyen et varie normalement — c’est un bon signe pour utiliser des méthodes statistiques classiques (corrélations, régression linéaire…).

✅ 2) Score moyen autour de 32–35

Le “pic” du histogramme est autour de 30–35.

Donc, la plupart des étudiants obtiennent une note dans cette zone.

👉 Interprétation :
Le niveau général est moyen à légèrement bon.

✅ 3) Symétrie

La distribution semble assez symétrique, mais peut-être légèrement plus étalée vers la droite (scores plus élevés).

👉 Interprétation :
Pas de forte asymétrie → pas de biais important dans les scores.

✅ 4) Pas de valeurs extrêmes évidentes

On voit très peu de notes < 20 ou > 50.

Cela signifie que le dataset est propre et ne contient pas d’outliers problématiques.

<img src="téléchargement (1).png" style="height:540px;margin-right:393px"/>
8️⃣Interprétation complète de la matrice
plt.figure(figsize=(12, 10))
corr = data.corr()

sns.heatmap(
    corr,
    annot=True,
    cmap="coolwarm",
    vmin=-1,
    vmax=1,
    linewidths=0.5
)

plt.title("Correlation Matrix of Student Exam Scores Data")
plt.show()
Voici ce que signifie chaque corrélation importante :
<img src="téléchargement (1).png" style="height:540px;margin-right:393px"/>
🔥 1. La corrélation la plus forte : hours_studied → exam_score (0.78)

Valeur : +0.78, très forte corrélation positive.

Interprétation : Plus un étudiant étudie, plus son score augmente.
👉 C’est le facteur le plus déterminant de la réussite.

➡ C’est une corrélation presque “linéaire” : les heures d’étude expliquent beaucoup la note.

⭐ 2. previous_scores → exam_score (0.43)

Corrélation modérée à forte.

Interprétation :
Les étudiants qui avaient de bonnes notes avant ont tendance à réussir encore.

➡ Cela montre une continuité du niveau académique.

👍 3. attendance_percent → exam_score (0.23)

Corrélation faible mais positive.

Interprétation :
Être présent en cours aide un peu, mais pas autant que les heures d’étude.

➡ La présence est utile, mais moins déterminante que le travail personnel.

😴 4. sleep_hours → exam_score (0.19)

Corrélation faible positive.

Interprétation :
Dormir un peu plus semble aider, mais l’effet est limité.

➡ Peut refléter un meilleur état mental → meilleure concentration.

💤 5. previous_scores ↔ sleep_hours (-0.19)

Corrélation négative faible.

Interprétation :
Les étudiants qui dormaient moins avaient parfois de meilleurs scores précédents.
(Peut être dû à des étudiants stressés / très travailleurs.)

➡ Rien de sérieux : faible corrélation.

❌ Variables inutiles dans l’analyse : student_id

Corrélations d’environ 0, donc non interprétables.

C’est normal : l’identifiant est juste un numéro.
9️⃣Interprétation du graphe
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Exemple de DataFrame selon les variables visibles dans le graphique
df = pd.DataFrame({
    "student_id": [...],
    "hours_studied": [...],
    "sleep_hours": [...],
    "attendance_percent": [...],
    "previous_scores": [...],
    "exam_score": [...]
})

# Calcul de la matrice de corrélation
corr_matrix = df.corr()

# Taille du graphe
plt.figure(figsize=(10, 8))

# Heatmap
sns.heatmap(
    corr_matrix,
    annot=True,
    cmap="Blues",
    linewidths=0.5,
    fmt=".2f"
)

plt.title("Matrice de corrélations")
plt.show()
heatmap montre les corrélations entre :

hours_studied

sleep_hours

attendance_percent

previous_scores

exam_score
<img src="téléchargement (1).png" style="height:540px;margin-right:393px"/>
et on voit plusieurs choses importantes :

🔵 1. hours_studied → exam_score (corrélation positive forte)

Dans ton graphique, la corrélation entre hours_studied et exam_score est élevée (environ ~0.75).

➡️ Plus un étudiant étudie, meilleur est son score d’examen.
C’est la relation la plus forte du graphe.

🔵 2. previous_scores → exam_score (corrélation faiblement positive)

La corrélation est faible (autour de 0.40).

➡️ Les étudiants ayant eu de bons résultats auparavant ont une légère tendance à réussir aussi l’examen.
Mais ce n’est pas un facteur très dominant.

🔵 3. sleep_hours → exam_score (corrélation faible)

Dans le graphe, cette corrélation est proche de zéro.

➡️ Le sommeil ne prédit presque pas le score dans ton dataset.
Cela veut dire que dormir plus n'influence pas directement la note.

🔵 4. attendance_percent → other variables

attendance_percent ne montre pas de corrélation forte avec exam_score ni avec les autres variables.

➡️ La présence n’est pas un facteur déterminant dans ce dataset.
Elle ne prédit pas les performances de l’étudiant.

🔵 5. student_id est non pertinent

La diagonale montre 1.0 (normal), mais toutes les autres corrélations sont très proches de 0.

➡️ student_id n’a aucun lien avec les variables académiques, ce qui est normal (simple identifiant).
---

## Conclusion

L’analyse globale du dataset des performances étudiantes met en évidence une structure cohérente et des relations logiques entre les variables. La distribution des scores d’examen suit une forme quasi-normale, indiquant un système d’évaluation équilibré où la majorité des étudiants obtiennent des résultats proches de la moyenne. Les visualisations et la matrice de corrélation montrent que la variable la plus influente sur la performance finale est le nombre d’heures d’étude, révélant l’impact majeur du travail personnel sur la réussite académique. Les scores antérieurs contribuent également de manière significative, soulignant l’existence d’un niveau académique stable et progressif chez les étudiants. En revanche, la présence en cours et les heures de sommeil n’exercent qu’un effet modéré, suggérant qu’ils favorisent la performance sans en être des déterminants principaux. L’ensemble de ces résultats montre que la réussite dépend principalement de l’effort individuel et du parcours académique antérieur, tandis que les facteurs comportementaux ou contextuels jouent un rôle d’appoint. Cette analyse fournit ainsi une vision claire des leviers de performance et permet d’orienter des actions pédagogiques ciblées pour améliorer les résultats étudiants.

