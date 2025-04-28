Session 1 – Rappels mathématiques et approfondissement des méthodes de classification

Durée totale : 1 h 40 – 2 h

#	Thème	Durée
1	Rappels mathématiques fondamentaux	25 min
2	Régression logistique	25 min
3	K-Nearest Neighbors (KNN)	15 min
4	Forêt aléatoire (Random Forest)	25 min
5	Synthèse, recommandations et Q&A	10 min



⸻

1. Rappels mathématiques fondamentaux (25 min)

1.1 Algèbre linéaire
	•	Vecteurs et matrices : notation, dimensions, interprétation en ML
	•	Opérations clés :
	•	Produit scalaire v\cdot u = \sum_i v_i\,u_i et norme \|v\| = \sqrt{\sum_i v_i^2}
	•	Multiplication matrice–vecteur y = A\,x
	•	Exercice flash : implémenter en Python la rotation 2D ou une mise à l’échelle, et visualiser le résultat.

1.2 Probabilités et statistiques
	•	Variable aléatoire : discrète vs continue
	•	Espérance \mathbb{E}[X], variance \mathrm{Var}(X)
	•	Distributions : uniforme, normale (gaussienne)
	•	Exercice : simuler un lancer de dé (10 000 tirages), tracer l’histogramme, observer la loi des grands nombres.

1.3 Optimisation
	•	Fonction de coût : définition, convexité, minimum local vs global
	•	Gradient : vecteur de dérivées partielles
	•	Descente de gradient :
\theta \;\leftarrow\;\theta - \eta\,\nabla_\theta J(\theta)
où \eta est le learning rate
	•	Exemple : minimiser f(x)=(x-3)^2 ; tester \eta=0.01, \eta=0.1 et \eta=1.0.

⸻

2. Régression logistique (25 min)

2.1 Modèle et fonction de coût
	•	Modèle binaire :
\hat y = \sigma(w^T x + b),\quad
\sigma(z)=\frac{1}{1+e^{-z}}
	•	Log-loss (cross-entropy) :
J(w,b) = -\frac1N\sum_{i=1}^N\bigl[y^{(i)}\ln\hat y^{(i)} + (1-y^{(i)})\ln(1-\hat y^{(i)})\bigr].
	•	Extension multiclasses : softmax et categorical cross-entropy.

2.2 Dérivées et mise à jour
	•	Dérivée par rapport à w :
\nabla_w J = \frac1N\,X^T(\hat y - y)
	•	Dérivée par rapport à b :
\partial_b J = \frac1N\sum_{i=1}^N (\hat y^{(i)} - y^{(i)})

2.3 Exercice guidé
	•	Sur un mini-dataset 2×2, calculez manuellement \hat y et effectuez un pas de gradient pour w et b.
	•	Comparez l’impact d’un learning rate trop grand vs trop petit.

2.4 Bonnes pratiques
	•	Standardisation des features (moyenne 0, écart-type 1)
	•	Régularisation L_2 (ridge) pour contrôler le sur-apprentissage
	•	Choix de l’algorithme de minimisation (Newton, BFGS, SGD, mini-batch…)

⸻

3. K-Nearest Neighbors (15 min)

3.1 Principe
	•	Distance : Euclidienne \|x - x{\prime}\|, Manhattan, Minkowski…
	•	Vote majoritaire parmi les k plus proches voisins
	•	Option de vote pondéré par l’inverse de la distance

3.2 Atelier interactif
	•	Sur un jeu de données 2D toy, tracer les frontières de décision pour k=1, k=3 et k=5.
	•	Exercice manuel : attribuer la classe d’un point donné pour k=3.

3.3 Limitations et optimisations
	•	Malédiction de la dimension : diminution de la pertinence du voisinage
	•	Structures d’index accélérées : KD-Tree, Ball-Tree
	•	Importance du scaling des features et choix de k par validation croisée

⸻

4. Forêt aléatoire (Random Forest) (25 min)

4.1 Rappel Arbre de Décision
	•	Impuretés :
	•	Gini : G = 1 - \sum_c p_c^2
	•	Entropie : H = -\sum_c p_c \ln p_c
	•	Critère de split : amélioration de l’impureté

4.2 Bagging et construction de la forêt
	•	Bootstrap aggregating : échantillonnage avec remise
	•	Sous-ensemble aléatoire de features à chaque split
	•	Prédiction : vote majoritaire des arbres

4.3 Exercice mathématique
	•	Calculer l’impureté Gini d’un nœud avant et après un split proposé.

4.4 Paramètres et tuning
	•	Nombre d’arbres, profondeur maximale, taille minimale des feuilles
	•	OOB score (out-of-bag) pour validation interne
	•	Extraction de l’importance des features

⸻

5. Synthèse, recommandations & Q&A (10 min)
	•	Comparaison des méthodes :
	•	Régression logistique : baseline rapide, interprétable
	•	KNN : prototypage non paramétrique, coûteux en production
	•	Random Forest : robustesse, peu de prétraitement, calcul plus lourd
	•	Pipeline conseillé pour la détection de pneumonies sur radiographies :
	1.	Régression logistique (vérifier linéarité)
	2.	KNN pour explorer les non-linéarités légères
	3.	Random Forest pour la version robuste en production
	•	Ouverture : introduction aux CNN et au transfert d’apprentissage

⸻

Ce plan peut servir de support à un notebook ou à des slides, avec illustrations, formules et exercices intégrés.