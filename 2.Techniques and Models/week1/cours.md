## Bayesian Statistics: Techniques and Models

Dessiner markov

http://steventhornton.ca/markov-chains-in-latex/

### 1. Introduction

#### 1.1 Modélisation statistique

Qu'est ce qu'un "modèle statistique" ?

#### 1.1.1 Objectifs

Ce cours a pour but la modélisation statistique ce qui fait partie de l'objectif d'analyse de données

On le définit comme (le model statistique)

> Une structure mathématiques qui cherche à imiter et approximer la génération des données, il décrit généralement les relations entres les variables tout en prenant en compte uncertainty et la variabilité des données

Considérons une expérience ou on souhaite révéler la cause à l'effet d'une relation. Si la relation entre les variables semble compliqué ou implique des variables qu'on ne peut pas mesurer, les données que nous avons collecté peuvent avoir un comportement aléatoire.

On peut le prendre en compte en utilisant la théorie des probabilités. 

Pour quels types de problèmes pourrions-nous utiliser la modélisation statistique ? On partira d'une étude où 57% des votants ont choisi le candidat A

1. Quantifier l'incertain

   Sur le pourcentage de votants, on veut déduire qu'avec une CI de 99% le vrais pourcentage de votants pour A est entre 51 et 63%

2. L'inférence:

   On va pouvoir inférer notre étude à toutes la population; on peut aussi chercher des informations démographiques.

3. Measuring the evidence in the data in support or against a hypothesis

   Supposons qu'un expert disent que le candidat est plus populaire avec les femmes que les hommes. Dans nos données de sondages, nous avons des informations supplémentaire qui disent que 55% des femmes sont pour A et 59% des hommes.

4. Prédiction

   Supposons qu'on ait des informations démographiques sur un votant mais on ne sait pas pour quel candidat il est en faveur; on va pouvoir utiliser la prédiction

#### 1.1.2 Modelling process

On appelle statistical modelling process; les différentes que compose une modélisation

1. Comprendre le problème

   Ca peut sembler évident mais un modèle mal utilisé sera inutile, comme si on calcule des moyennes de profits de différents magasins dans des unités monétaires différentes

2. Prévoir et collecter les données

   La qualité des données détermine la valeur des données. Si on lance un sondage sur nos collégues proches et qu'on souhaite le généraliser à toutes l'entreprise ce ne sera pas viable, car il y'a une forte diversités. C'est pour ça qu'il est conseillé de tirer des échantillons aléatoires parmi tous les employés

3. Explorer les données

   Permet de vérifier que les données collectés n'ont pas d'erreurs; on visualise les données etc.

4. Postuler un modèle

   On va choisir notre modèle, qui répond le mieux aux problèmes sous les contraintes de biais-variance ou autres.

5. FItter un modèle

   On estime les paramètres du modèles sur les données

6. Vérifier le modèle

   On vérifie que le modèle arrive à bien imiter le processus de génération des donneés

7. Itérer

   C'est-à-dire qu'on peut retourner aux étapes 4 à 8

8. Utiliser le modèle



#### 1.2 Bayesian modelling

#### 1.2.1 Composants des modèles bayésiens

Nous avons défini le modèle statistique comme une structure qui imite ou approxime le processus de génération des données, tout en incorporant l'incertitude et **la variabilité**.

Nous allons illustrer la notion de modèle statistique par des données sur la taille de 15 hommes en utilisant uniquement une seule variable

On prend un échantillon de $n=15$ , vu qu'il serait très coûteux de prendre un échantillon plus grand on peut considérer que **la variabilité** des données suit une loi normale
$$
y_i = \mu + \epsilon_i~~,~~ \epsilon_i \stackrel{i.i.d.}{\sim} \mathcal{N}(0, \sigma^2),i=1,\dots,n
$$
avec $\mu$ la moyenne de tous les hommess; $\epsilon_i$ la variable d'erreur individuel pour chaque individu i

On écrit:

On pourrait de façon équivalente écrire ce modèle directement de cette façon
$$
y_i \stackrel{i.i.d.}{\sim} \mathcal{N}(\mu, \sigma^2)
$$


Ce qui spécifie une distribution de probabilité et un modèle pour les données, ce qui nous permet aussi de générer de fausses donnéees qui se comporte de la même façon que notre dataset

Jusqu'à maintenant le modèle est similaire pour les fréquentistes et les bayésiens

<u>En fréquentiste</u>, on considérera  $\mu$ et $\sigma$ comme des constantes inconnus mais fixe et on les estimerait. Pour les estimer on répéterait le processus d'échantillonage avec un autre échantillon de quinze hommes

<u>En Bayésien</u> on considérera $\mu$ et $\sigma$ comme des probabilités, en les considérants comme des variables aléatoires avec leurs propres distribution de probabilité. Les trois composants primaires de ce modèle sont:

* *Vraisemblance:* il décrit comment, selon le paramètre inconu, nos données auront pu être généré. On dira ici que $\theta$ est le paramètre inconnu
  $$
  p(y|\theta)
  $$

* 


$$
p(\theta)
$$
* Une fois que nous avons la Distribution à priori et la Vraisemblance nous avons une probabilité jointe pour à la fois les connus, les données et les inconnus (le paramètre), on peut le voir en utilisant le chain rule des probabilités. 

* $$
  p(y, \theta) = p(\theta) p(y|\theta)
  $$

* *Distribution à posteriori:* Nous privilégerions cette distribution pour l'inférence c'est celle que nous avons besoin

$$
p(\theta | y) = \frac{p(y,\theta)}{p(y)}
 = \frac{p(\theta, y)}{\int p(\theta, y) d\theta} 
 = \frac{p(y|\theta)p(\theta)}{ \int p(y |\theta)p(\theta) d\theta}
$$

$p(y)$ est la distribution marginale qui est importante pour des modèles plus avancés bayésien. La Distributiion à posteriori est notre outils principale

------------------------------------------------------

Whereas non-Bayesian approaches consider a probability model for the data only, the hallmark characteristic of Bayesian models is that they specify a joint probability distribution for both data *and* parameters. How does the Bayesian paradigm leverage this additional assumption?

* This allows us to make probabilistic assessments about hypothetical data outcomes given particular parameter values.

* This allows us to use the laws of conditional probability to describe our updated information about parameters given the data.

* This allows us to select the most accurate prior distribution.

* This allows us to make probabilistic assessments about how likely our particular data outcome is under any parameter setting.

#### 1.2.2 Model specification

Avant de fitter le modèle on va devoir spécifier tous ses composants. Une façon pratique est d'écrire la **hierarchical form** du modèle. Ce qui signifie le modèle est défini en steps ou en couches.

On commence généralement; par modéliser les données directement, ou la vraisemblance. Par exemple, repartons du cas que nous avions vu.
$$
y_i| \mu \stackrel{i.i.d.}{\sim} \mathcal{N}(\mu, \sigma^2) ~~ i=1,...,n
$$
Le prochain level que nous aruons besoin est la Distribution à prior de $\mu $ et $\sigma^2$, nous dirons qu'ils sont indépendants:
$$
p(\mu, \sigma^2) = p(\mu)p(\sigma^2)
$$
Nous avions vu dans le cours précédent que La distribution à priori conjugué de $\mu$ suit une loi $\mathcal{N}(\mu_0, \sigma_0^2)$ et que pour $\sigma^2 $ le conjugué suit une loi gamma inverse $IG(\nu_0, \beta_0)
$$
\mu \sim \mathcal{N}(\mu_0, \sigma_0^2) \\
\sigma^2 \sim IG(\nu_0, \beta_0)
$$
On va pouvoir utiliser une représentation graphique on commence par le prior et on remonte.

Le cercle signifie aue cette V.A. à sa propre distribution, on trace les deux Distribution à priori. La seconde étape on va pouvoir générer les données qui sont les $y_i$ sont eux-mêmes des V.A. On va les encercler deux fois (ou en grisé) car on dit que **ces noeuds sont obesrvés** on les voit dans les données

Puis pour indiquer les dépendances entre les V.A. et leurs distributions, on va tracer des flèches. 

GRAPHE TO ADD

On peut retracer ce modèle en écrivant des exchangeable random variables avec ce qu'on appelle un plate. (Exchangeable = la distribution pour les ys ne change pas si on devait changer leurs index)

#### 1.2.3 Posterior derivation

JUsqu'à maintenant nous avons tracé des modèles à deux niveaux. Mais en réalité rien ne nous empêche d'en rajouter bien plus. Par exemple, au lieu de fixer les valeurs de hyper paramètres, nous aurions pu spécifié des nombres ou des distributions à priori . Une des raisons qui nous ferait faire ça et que ça permettrait que les données soient groupé ensemble, nous verrons ce cas plus tard.

Un exemple plus simple est celui que nous avions vu, sauf que cette fois ci nous ne considérerons pas l'hypothèse d'indépendance des Distribution à priori, 
$$
y_i| \mu, \sigma^2 \stackrel{i.i.d.}{\sim} \mathcal{N}(\mu, \sigma^2) ~~ i=1,...,n \\
\mu | \sigma^2 \sim \mathcal{N}(\mu_0, \frac{\sigma^2}{\omega_0}) \\
\sigma^2 \sim IG(\nu_0,\beta_0)
$$
On trace le modèle graphique en commençant par les variables qui ne dépendent de personnes puis on remonte.

TO ADD GRAPHE

Pour simuler des données hypothétique à partir de ce modèle, nous devrons en premier tirer un échantillon de la distribution à priori $ \sigma^2 $etc. 

Une fois que nous avons le modele specification, on va pouvoir écrire la Distribution à posteriori pour tout les paramètres sachant les données. Pour rappelle le numérateur de bayes est une probabilité jointe de tous les paramètres on écrira: (qu'on calcule avec le chain rule des probabilités)
$$
\begin{align}
p(y_1,...,y_n,\mu,\sigma^2)&=p(y_1,...,y_n|\mu, \sigma^2) p(\mu | \sigma^2) p(\sigma^2) \\
&= \Pi_{i=1}^{n} [\mathcal{N}(y_i|\mu,\sigma^2)]  \mathcal{N}(\mu|\mu_0,\frac{\sigma^2}{\omega_0})IG(\sigma^2_0|\nu_0,\beta_0) \\
&\approx p(\mu, \sigma^2 |y_1,...,y_n)
\end{align}
$$
La seule chose qui va nous manquer est une constante qui va permettre l'expression d'intégrer à un. Si on peut reconnaitre cette expression comme étant proportionnelle a à une distribution connue; alors nous connaissance la Distribution à posteriori. Ce qui était le cas pour tous les modèles du cours précédent avec les conjugate prior.

-----------------------

When viewed as a function of some real number $\theta$, the function $f(\theta) = \frac{\sigma}{\theta^2 + 1} e^{-\sigma \theta}$ is proportional to which of the following?

**Hint**: To be proportional to the original function $f(\theta)$, the new function must be equal to $f(\theta)$ times a constant that does not involve $\theta$, and this must be true for all possible values of $\thetaθ$.

$\frac{1}{\theta^2 + 1} e^{-\sigma \theta}$                    $\frac{1}{\theta^2 + 1} e^{-\theta}$

$\frac{1}{\theta^2} e^{-\theta}$                        $\frac{\sigma}{\theta^2} e^{-\sigma \theta}$



#### 1.2.4 Non-conjugate models

Nous allons voir plusieurs modèles qui n'ont pas de Distribution à posteriori très propre.

Premièremenent, nous verrons un cas avec un paramètre qui n'est pas conjugué.

Supposons que nous avons des valeurs qui représentent un pourcentage change in total personnel from last year to this year pour 10 entreprises. Ces entreprises viennent d'un secteur particulier. Nous allons ensuite supposer que ces mesures viennent d'une distribution normale avec variance connue mais moyenne inconnue.

La moyenne inconnue pourrait représenter la croissance pour une industrie spécifique, c'est la croissante moyenne pour toutes les entreprises. La faible variance entre les entreprises et le pourcentage de croissante peu être approprié si le secteur est stable.
$$
n=10 \\
y_i| \mu \stackrel{i.i.d.}{\sim} \mathcal{N}(\mu,1) \\
\mu \sim t(0,1,1) 
$$
L'expression que nous obtenue est presque proportionnel a à une loi normal sauf que nous avons au dénominateur un $1 + \mu^2$, nous n'aurons pas donc de Distribution à posteriori intéressante car nous ne reconnaissons pas une loi standard (qui nous permettrait d'intégrer ou simuler), nous devrons faire quelque chose d'autre
$$
\begin{align}
p(\mu | y_1,...,y_n) &\approx \prod_{i=1}^{n}\Big[\frac{1}{\sqrt{2\pi}}exp\Big(-\frac{1}{2}(y_i- \mu)^2\Big)\Big] \frac{1}{\pi (1 + \mu)^2} \\
&\approx exp \Big[- \frac{1}{2} \sum_{i=1}^{n}(y_i-\mu^2)\Big]\frac{1}{1 + \mu^2}\\
& \approx exp \Big[- \frac{1}{2}\Big( \sum_{i=1}^{n}(y_i^2-2\mu\sum_{i=1}^{n}y_i+ n \mu^2\Big)\Big]\frac{1}{1 + \mu^2}\\
&\approx \frac{exp \Big[n \Big( \bar{y}\mu- \frac{\mu^2}{2}\Big)\Big]}{1 + \mu^2}
\end{align}
$$
Example 2:

Pour deux paramètres, on va estimer $\mu$ et $\sigma^2$ qui sont tout les deux inconnus; on a écrit ci-dessous leurs Distribution à priori conjugué, si celle de sigma était connu on aurait celle de mu ; et inversement. Nous avions vu que 
$$
y_i| \mu, \sigma^2 \stackrel{i.i.d.}{\sim} \mathcal{N}(\mu, \sigma^2) ~~ i=1,...,n \\
\mu \sim \mathcal{N}(\mu_0, \sigma^2_0) \\
\sigma^2 \sim IG(\nu_0,\beta_0)
$$
Nous avions vu que si on inclut le sigma au carré comme Distribution à priori de mu, et on utiliser le modèle hiérarchique; ce modèle serait conjugué et on aurait une forme bien défini. Cependant, dans le cas le plus général, que nous avons ici, la Distribution à posteriori n'apparait pas comme pouvant être simulé ou intégré

Synthèse:

Ce genre de problème que nous avons vu sont une des raisons principales qui ont fait que  les statistiques bayésienne ont pris beaucoup de temps avant de devenir mainstream, car seule les problèmes simple étaient résolvables.

--------------------

What major challenge do we face with both of the models introduced in this segment?

* We have the posterior distribution up to a normalizing constant, but we are unable to integrate it to obtain important quantities, such as the posterior mean or probability intervals.

* The expression derived is only an approximation to the posterior.

* We have the full posterior distribution, no methods exist for computing important quantities, such as the posterior mean or probability intervals.

* The posterior distribution derived is not a proper probability distribution with a finite integral.

#### 1.2 Estimation de Monte Carlo

L'estimation de Monte carlo signifie simuler des tirages hypothétique d'une distribution de probabilité, afin de calculer d'importantes quantités de cette distribution. La plupart de ces opérations nécéessitent l'intégration qui peut dans certains cas s'avérer très complexe.

Supposons que nous avons une variable aléatoire $\theta$ , 
$$
\theta \sim \Gamma(a,b) \\
a = 2 ~~~~ b = \frac{1}{3} \\
E(\theta) = \int_{0}^{\infty}\theta p(\theta) d\theta = \frac{a}{b}
$$
On peut calculer ici la valeur de l'espérance; mais on pourrait aussi vérifier le résultat avec Monte-Carlo, posons ici $\theta^*$
$$
\theta_i^* ~~~~~i=1,...,m
$$
On peut ensuite calculer 
$$
\bar{\theta}^* = \frac{1}{m} \sum_{i=1}^{m}\theta_i^*
$$
Si on prend une autre fonction $h(\theta)$ on pourrait aussi calculer son espérance avec
$$
\int h(\theta) p(\theta)d\theta = E[h(\theta)] \approx \frac{1}{m} \sum_{i=1}^{m}h(\theta_i^*)
$$
Exemple:
$$
h(\theta) = I_{\theta \lt 5}(\theta) \\
\begin{align}
E(h(\theta)) &= \int_0^{\infty}I_{\theta \lt 5}(\theta)p(\theta)d\theta\\
&= \int_{0}^{5} 1 \cdot p(\theta) d\theta + \int_{5}^{\infty}0 \cdotp(\theta)d\theta\\
&= Pr[0 \lt \theta \lt 5]
\end{align}
$$
Ce qui signifie qu'on peut approximer cette intégrale en prennant un ensemble d'échantillons:
$$
\approx \frac{1}{m} \sum_{i=1}^{m} I_{\theta^* \lt 5}(\theta^*_i)
$$
De la même façon on peut calculer les quantiles d'une distribution; si on regarde une valeur $z$ et qu'on veut la probabilité que $z$ est moins que $0.9$. On va ranger les échantillons $\theta_i^*$ par ordre ascendant et on trouverait la plus petite valeur des $\theta^*$ qui est plus grande que $90\%$ des autres. En d'autres mots on prendrait le 90th percentile des $\theta^*$ qui approximent le 0.9 quantile de la distribution.

-------------------

Quizz:

Forecasters often use simulations (usually based on a probability model) to approximate the probability of something they are trying to predict (for example, see <https://fivethirtyeight.com/>). How do they use the simulations to obtain the forecast probability?

* They calculate the probability directly within each simulation by integrating the probabilistic model. They then average these probabilities across many simulations.

* They calculate the probability directly by integrating the probabilistic model. They then run one simulation, inputting the calculated probability. If the event occurs in the simulation, they forecast that it will occur.

* They simulate the system under study many times and count the fraction of times the event of interest occurs.

* They simulate the system under study once. If the event of interest occurs in that simulation, they forecast that it will occur.

-------------------------



#### 1.3 Erreurs de Monte-Carlo et marginalisation

Pour estimer la qualité d'un échantillonage de Monte-Carlo on pourra une fois de plus utiliser le théorème centrale limlite qui nous dit que la variance de notre estimateur est contrôlé en partie par $m$ notre taille d'échantillon. Si nous voulons un meilleur estimateur nous devons choisir une plus grande valeur pour m.
$$
\bar{ \theta}^* \sim \mathcal{N} \Big ( E(\theta), \frac{Var(\theta)}{m} \Big) \\
\hat{Var(\theta)} = \frac{1}{m} \sum_{i=1}^{m}(\theta_i^* - \bar{ \theta}^*)^2
$$
L'écart type de notre estimation de Monte-Carlo est la racine carré de ça, si m est large on pourra supposer que la vrais valeur sera probablement dans deux std de notre estimateur de Monte-Carlo
$$
\sqrt{ \frac{\hat{Var(\theta)}}{m}} = standard~~error
$$
On peut aussi obtenir les échantillons de Monte-Carlo avec des modèles hiérarchiques:
$$
y | \phi \sim Bin(10, \phi) \\
\phi \sim Beta(2,2)
$$
En utilisant le chain rule des probabilités on peut écrire, afin d'obtenir une probabilité jointe
$$
p(y, \phi) = p(\theta)p(y | \theta)
$$
On suivra les étapes suivante pour simuler:

1. $\phi_i^*$ de Beta
2. Selon $\phi_i^*$ tirer $y_i^* \sim Bin(10, \phi_i^*)$

Si on répète ce processus pour plusieurs échantillons; nous allons produire $m$ paires indépendantes $(y_i^*, \phi_i^*)$ces pairs sont tirés à partir de leurs probabilités jointes.

Un des avantages majeurs de la simulation Monte-Carlo est que marginaliser ces distributions est facile. Si on a des tirages de la loi jointe; on peut juste jeter les $\phi_i^*$ et utiliser les échantillons des $y_i^*$ comme échantillons de leurs distributions marginale. C'est aussi appelé le **Prior Predictive Distributions** qui a été introduit dans le cours précédent.









