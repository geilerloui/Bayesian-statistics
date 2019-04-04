## Bayesian Statistics: Techniques and Models

### 1. Introduction

#### 1.1 Qu'est ce que la modélisation en statistique ?

On le définit comme

> Une structure mathématiques qui cherche à imiter et approximer la génération des données

Comme on peut avoir des variables compliqués ou non mesurable ou des comportements aléatoires, les statistiques aideront à ces problèmes

On définit quatre objectifs:

1. Quantifier l'incertain

   On prédit que 57% des votes pour un candidat seront dans l'interval de confiance: [51;62]

2. L'inférence:

   On étend le modèle; en se demandant quel pourcentage des gens supportent le candidats

3. Mesurer le support pour des hypothèses

   On voit que 59% des hommes et 55% des femmes votent pour B. A quel point en ait on sur ?

4. Prédiction

   Algorithme de machine learning

Les étapes d'un traitement statisitques sont les suivantes:

1. Comprendre le problème
2. Prévoir et collecter les données
3. Explorer les données
4. Postulrer un modèle
5. FItter un modèle
6. Vérifier le modèle
7. Itérer
8. Utiliser le modèle



#### 1.2 Rappels de probabilité Bayésienne:

Prennons un exemple sur la taille des hommes

On prend un échantillon de $n=15$ On suppose que leurs tailles suit une loi normale et on pose le modèle
$$
y_i = \mu + \epsilon_i
$$
avec $\mu$ la moyenne de tous les hommess; $\epsilon_i$ la variable individuel pour chaque homme

On écrit:

* $\epsilon \sim N(0, \sigma^2),i=1,...,n$
* $y_i \sim N(\mu, \sigma^2)$

Remarque: pour l'instant notre modèle est similaire à un fréquentiste

<u>En fréquentiste</u>, on se seriat demandé comment $\mu$ et $\sigma$ changeraient si on repéter le processus d'échantillonage sur un autre groupe de n=15 hommes

<u>En Bayésien</u> on définit directement
$$
Likelihood: p(y|\theta) \\
prior: p(\theta) \\
posterior:  p(\theta | y) = \frac{p(y,\theta)}{p(y)}\\
 = \frac{p(\theta, y)}{\int p(\theta, y) d\theta} \\
 = \frac{p(y|\theta)p(\theta)}{ \int p(y |\theta)p(\theta) d\theta}
$$
ajouter une flèche entre les textes

http://www.sascha-frank.com/Arrow/latex-arrows.html