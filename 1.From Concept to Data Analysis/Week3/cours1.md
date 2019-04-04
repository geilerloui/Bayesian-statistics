# Statistique Bayésienne: Des concepts à l'analyse des données

## 1. Introduction

### 1.1 Paradigme des probabilités

Les statistiques sont l'étude de l'incertitude. Comment le mesurer ? Et comment prendre des décisions ?

Trois grands modèles définissent les probabilités:

1. Classique: les résultats qui sont équiprobable ont des probabilités égales

   > ex: Lors d'un lancer de dés, chaque face a une probabilité de $\frac{1}{6}$ de tomber si le dés n'est pas pipé. Parmi les lancer combien donneront une somme égale à quatre $P(X_1+X_2=4)$.

2. Fréquentiste: nous demande d'avoir une suite hypothétique infini d'évènements et on regarde à leurs fréquences

   >  ex: On lance un dés un nombre de fois infini. Dans certains cette approche peut s'avérer compliqué, par exemple calculé la $P(pluie)$ demain. Il faudrait imaginer un nombre de cas infini de pluie et de voir quelle fraction de tous ces scénario rendent l'hypothèse de pluie vraie. Dans le cas d'un dés on peut se demander si un dés est $P(non~ pipé)= \{0,1\}$ la probabilité est un ou zéro ce qui n'est pas une réponse très intuitive. Dans le cas de calcul de la probabilité que l'universe s'étende à l'infini on va avoir avoir une réponse binaire $P(Univers~s'étend)=\{0,1\}$ On peut voir que cette approche à quelques limitations philosophique

3. Bayésien: c'est une perspective personnel. Notre probabilité représente notre propre perspective, c'est notre mesure de l'incertitude, il prend en compte ce qu'on connait sur le problème

   >  ex: On va pouvoir prendre en compte notre connaissance du problème, par exemple que le dé est pipé. Si on a plus d'informations qu'une autre personne ceci peut impliauer plus d'in. 
   >
   >  Si il pleut demande on gagne 4 dollars si il ne pleut pas on perd 1\$; on a un odd de 4:1 . Ce qui signifie qu'on peut aussi le voir dans une autre direction i.e. on perd 4\$
   >
   >  Concept de cohérence: Les probabilités doivent suivre toutes les règles standard de probabilité si on ne suit pas ces règles on peut être incohérents; ce  qui peut amener à créer un jeux de pari ou on est sur de perdre c'est ce qu'on appelle Dutch book

### 1.2 Probabilité conditionnelles

Les probabilités conditionnelles apparaissent lorsqu'on essaye de considérer deux évènements qui sont liés ensembles. 
$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$
**exemple:**

> Considérons une classe de 30 étudiants, 9 sont des étudiantes; 12 ont choisi l'option informatique dont 4 sont étudiantes. 
>
> 1. Calculer les paramètres manquants
>
>    a = 8; b = 5; c = 13
>
>    |                      | Femme    | Homme     | Total     |
>    | -------------------- | -------- | --------- | --------- |
>    | **Informatique**     | 4 (2/15) | a (4/15)  | 12 (6/15) |
>    | **Non informatique** | b (1/6)  | c (13/30) | d (18/30) |
>    | **Total**            | 9 (3/10) | e (7/10)  | 30 (1)    |
>
> 2. Calculer $P(Femme)$
>    $$
>    P(Femme) = \frac{9}{30} = \frac{3}{10} \\
>    P(Informatique) = \frac{12}{30} = \frac{2}{5}\\
>    P(F \and Info)=\frac{4}{30}=\frac{2}{15}
>    $$
>
>
>
>
>
>
>
>
> 3. $Femme \perp Informatique$ ?
>
> $$
> P(F|Info) = \frac{P(F \cap Info)}{P(Info)} = \frac{2/15}{2/5} = \frac{1}{3}
> $$
>
> On peut aussi le résoudre en lisant énoncé de façon intuitive "Parmi les 12 étudiants en informatique 4 sont des étudiantes" ce qui revient à calculer $\frac{4}{12}=\frac{1}{3}$
>
> Dans l'autre sens on à:
>
> $P(F| Info^C)=  \frac{P(F \and Info^C)}{P(Info^C)}=\frac{5/30}{18/30}=\frac{5}{18}$
>
> 4. On a aussi la notion d'indépendence qui est que $P(A|B)=P(A)$ alors $P(A \and B)=P(A)P(B)$
>
> Or, $P(F|Info) \neq P(F)$ on en conclut que les évènements ne sont pas indépendants



### 1.3 La formule de Bayes discrète

La formule de Bayes permet d'inverser le sens du conditionnel
$$
P(A|B) = \frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^c)P(A^c)} = \frac{P(A\and B)}{P(B)}
$$

>  Exemple:
>
>  $P(Info|F)=\frac{P(F|Info)P(Info)}{P(F|Info)P(Info)+ P(F|Info^CP(Info^C))}=\frac{4}{9}$
>
>  ou $P(Info|F)=\frac{P(Info|F)}{P(F)}=\frac{4}{9}$
>
>  Exemple: 
>
>  Nous allons calculer la probabilité d'avoir le Sida sachant la positivité; on va se demander si on choisit quelqu'un de façon aléatoire en Amérique du Nord et on le teste et qu'il est positif qu'elle est la probabilité qu'ils ont le Sida sachant qu'ils sont positifs
>
>  $P(+|HIV) = 0.977$
>
>  $P(-| not HIV) = 0.926
>
>  $P(HIV) = 0.0026$
>  $$
>  P(HIV|+) = \frac{P(+|HIV)P(HIV)}{P(+|HIV)P(HIV) + P(+|not~ HIV)P(not~ HIV)} \\
>  = \frac{(0.977*0.0026)}{(0.977*0.00266)+(1-0.926)(1-0.0026)} \\
>  = 0.033
>  $$
>  On a donc 0.33% de chance d'avoir le Sida sachant qu'on est positif. Le résultat peut paraitre surprenant mais c'est car c'est une maladie rare. Le nombre de faux positif dépasse largement les vrais positifs cars c'est une maladie rare. Si le test est très précis (0.977) on a plus de faux négatifs que de vrais positifs.  Il fait donc plus de sens que de faire des tests sur le Sida dans une population qui en a beaucoup
>

### 1.4 La formule généralisée

**En discret** :
$$
P(A|B) = \frac{P(B|A_1)P(A_1)}{\sum_{i=1}^{n}P(B|A_i)P(A_i)}
$$
On va appeler:

- Prior: $P(A_1)$
- Likelihood: $P(B|A_1)$
- Posterior: $P(A|B)$

**En continue** : Quant-on a à faire avec une variable aléatoire continue $\theta$, on peut écrire la densité conditionnelle pour $\theta$ sachant $y$ comme:
$$
f(\theta|y) = \frac{f(y|\theta)f(\theta)}{\int f(y|\theta)f(\theta)d\theta}
$$

Cette expression fait la même chose que la version discrète, car $\theta$ est continue on intégrera sur toutes les valeurs possibles de $\theta$ plutôt que de prendre sa somme

### 1.5 Quelques distributions de probabilités continues

**La loi Gamma:**

Si $X_1,X_2,...,X_n$ sont indépendents (et identiquement distributés de loi $Exp(\lambda)$)le temps d'attente entre deux évènements successifs, alors le temps d'attente total pour les $n$ évènements qui se produisent est de $Y = \sum_{i=1}^{n}X_i$ suivra une loi gamma avec un shape parameter $\alpha=n$ et rate parameter $\beta=\lambda$
$$
Y \approx Gamma(\alpha, \beta) \\
f(y|\alpha, \beta) = \frac{\beta^{\alpha}}{\Gamma(\alpha)}y^{\alpha-1}e^{-\beta y}\mathbb{I}_{\{ y \ge 0 \}}(y) \\
E[Y] = \frac{\alpha}{\beta} \\
Var[Y] = \frac{\alpha}{\beta^2}
$$
où $\Gamma()$ est la fonction gamma; une généralisation de la fonction factoriel qui peut accepter des arguments non-entiers. Si $n$ est un entier positif, alors $\Gamma(n)=(n-1)!$. On peut aussi noter que $\alpha \gt 0$ et $\beta  \gt 0$.

La loi exponentiel est un cas particulier de la loi Gamma avec $\alpha=1$. La loi Gamma apparait souvent dans les problèmes de statistique, comme nous le verrons dans le cours. Elle est utilisé pour modéliser des valeurs positive; quantité continue avec une distribution skewed à droite. Lorsque $\alpha​$ augmente, la loi Gamma se rapproche à une loi normale

**La loi Beta:**

La loi Beta est utilisé pour les variables aléatoires qui prennent des valeurs entre 0 et 1. Pour cette raison (et d'autres raisons que nous verrons plus tard), cette loi est généralement utilisé pour modélisé des probabilités
$$
X \sim Beta(\alpha, \beta) \\
f(x|\alpha, \beta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)}x^{\alpha - 1} (1-x)^{\beta - 1} \mathbb{I}_{0 \lt x \lt 1}(x) \\
E[X] = \frac{\alpha}{\alpha + \beta} \\
Var[X] = \frac{\alpha \beta}{(\alpha + \beta)^2(\alpha + \beta +1)}
$$
Où $Gamma()$ est la fonction gamma présenté avec la loi gamma. Noter aussi que $\alpha \gt 0$ et $\beta \gt 0$ . La loi standard $Uniforme(0,1)$ est un cas spécial de la loi normale lorsque $\alpha=\beta=1$

 

## 2. Inférence fréquentiste vs Bayésienne

### 2.1 Interval de confiance fréquentiste - rappel

Pour rappel dans le paradigme fréquentiste, les données sont vu comme un échantillon aléatoire d'une plus grande population hypothètique

On va avoir par exemple 10 groupes de personnes puis on va mesurer un estimateur pour chacun de ces groupes. Avec un interval de confiance a 95%, 95% des intervalles de confiances contiendront le vrais estimateur

Attention:

​	En fréquentiste, c'est soit l'estimateur appartient à l'intervalle de confiance soit pas. En bayésien on aura un cadre différent ou l'estimateur sera modélisé par une distribution de probabilité

> **Exemple:**
>
> On jette une pièce 100 fois on a:
>
> 44 face et 56 piles
>
> On dira que cette variable aléatoire suit une loi:
> $$
> X_i \sim B(n, p)
> $$
> Avec n grand, on peut dire que par le théorème de Moivre Laplace
> $$
> \sum_{i=1}^{100} X_i \sim N(100p, 100p(1-p))
> $$
> D'où on peut écrire (avec une intervalle de confiance a 95%, d'où le 1.96)
> $$
> 100p - 1.96 \sqrt{100p(1-p)} \\
> 100p + 1.96 \sqrt{100p(1-p)}
> $$
> Pour notre estimateur
> $$
> \sum X_i = 44, \hat{p}= \frac{44}{100}=4.4
> $$
> L'intervalle de confiance est de 
> $$
> 44 \pm 1.96 \sqrt{44*(0.56)}=44 \pm9.7
> $$
> Donc nous sommes confiant à 95% que 
> $$
> \hat{p} \in [0.343; 0.537]
> $$
>

### 2.2 Interval de confiance - bonus

### 2.3 Maximum de vraisemblance

C'est ce qu'on appelle de l'estimation ponctuelle (où on cherche à estimer une valeur) par rapport à l'estimation par intervalle de confiance

> **Exemple:**
> $$
> Y_i \sim B(\theta) \\
> P(Y_i = 1) = \theta \\
> $$
>
> $$
> = P(Y_1=y_1|\theta) ... P(Y_n=y_n| \theta) \\
> = \Pi_{i=1}^{n}P(Y_i=y_i|\theta) \\
> = \Pi_{i=1}^{n}{\theta^{y_i}}(1- \theta)^{1 - y_i}
> $$
> Likelihood:
> $$
> L(\theta|y)= \Pi_{i=1}^{n} \theta^{y_i}(1 - \theta)^{1-y_i}
> $$
> MLE:
> $$
> \hat{ \theta} = argmax L(\theta|y) \\
> l( \theta) = log[L(\theta | y)] \\
> = log[\pi \theta^{y_i}(1 - \theta)^{1-y_i}] \\
> = \sum log [ \theta^{y_i}(1 - \theta)^{1 - y_i}] \\
> = \sum [y_i log\theta + (1-y_i)log(1 - \theta)] \\
> = (\sum y_i) log\theta + (\sum(1-y_i)log(1- \theta))
> $$
>
> $$
> l'(\theta)= \frac{1}{ \theta} \sum y_i - \frac{1}{1 - \theta}\sum (1 - y_i)=0 \\
> => \frac{ \sum y_i}{\hat{\theta}}= \frac{\sum(1-y_i)}{1- \hat{\theta}} \\
> => \hat{\theta} = \frac{1}{n}\sum y_i \\
> = \hat{p} = \frac{72}{400} = 0.18
> $$
>
> On peut approximer par TCL pour avoir un interval de confiance
> $$
> \hat{\theta } \pm 1.96 \sqrt{\frac{\hat{\theta}(1-\hat{\theta})}{n}}
> $$
>

Méthode par simulation:

``` 1
likelihood = fct(n, y, theta){
    return (theta^y)(1-theta)^(n-y)
}
theta = seq(from=0.01, to=0.99, by=0.01)

plot(theta, likelihood(400,72,theta))
```

### 2.3 L'approche fréquentiste vs l'approche bayésienne

**Approche fréquentiste:**

On va chercher a calculer la vraisemblance qu'on note $\mathbb{L}$ en fréquentiste mais en bayésien on préfère $f$

Note frére vient avec une pièce truqué qui donne face 70% du temps; il vient avec une pièce, mais on n'est pas sur de quel type, et il souhaite faire un pari avec nous, que ça va tomber. Il nous donne une chance de lancer la pièce 5x pour savoir si elle est truqué, après l'avoir lancé on obtient 3 faces et deux piles. La question est quelle est la probabilité que la pièce est truqué
$$
\theta = \{fair, loaded\} \\
X \sim B(5, ?) \\
f(x| \theta) = \begin{cases} \binom{5}{x} (\frac{1}{2})^5
, & \mbox{si } \theta \mbox{=fair} \\ \binom{5}{x} (0.7)^x(0.3)^{5-x}, & \mbox{si } \theta \mbox{=loaded} \end{cases} \\
= \binom{5}{x}(0.5)^5   \mathbb{1}_{\{\theta=fair\} } + \binom{5}{x}(0.7)^x(0.3)^{5-x} \mathbb{1}_{ \{ \theta=loaded \}}
$$


on suppose que  X=2, on observe deux head, en bayésien le L du likelihood est remplacé par f; le MLE est le $\theta$ (soit fair soit loaded) pour lequel on obtient deux head
$$
X=2:f(\theta|X=2) = \begin{cases} 0.3125
, & \mbox{si } \theta \mbox{=fair} \\  0.1323, & \mbox{si } \theta \mbox{=loaded} \end{cases} 
$$
On voit que ayant observé deux faces la vraisemblance est plus forte pour le dé non truqué, on peut donc dire que le MLEstimate $\hat{ \theta}=non~truqué$. Une fois; qu'on a ce résultat on peut vouloir savoir si on en est vraiment sur, ce qui n'est pas facile dans le paradigme fréquentielle.

On pourrait vouloir savoir ausssi que:
$$
P(\theta=fair|X=2) = P(\theta=fair) \in \{0,1\}
$$
En fréquentiste, nous n'avons que une valeur binaire pour ce résultat, ce qui n'est pas satisfaisant

**Approche Bayésienne:**

Cette approche permet de prendre en compte ce qu'on connait; dans le cas du jeux avec notre frère nous le connaissons depuis longtemps, on connait

Prior: $P(truqué)=0.6$ 


$$
f(\theta |x) = \frac{f(x|\theta)f(\theta)}{\sum_{\theta}f(x|\theta)f(\theta)} \\
= \frac{\binom{5}{x}[(\frac{1}{2})^5(0.4)\mathbb{1}_{ \{ \theta=fair \} }+(0.7)^x(0.3)^{5-x}(0.6) \mathbb{1}_{ \{ \theta=loaded \} }]}{\binom{5}{x}[(\frac{1}{2})^5(0.4)+(0.7)^x(0.3)^{5-x}(0.6) ]}\\
$$
Si on rentre nos données, on peut remarquer que avec le dénominateur on a une normalizing constant; ce qui fait que nos résultats donne un.
$$
f( \theta | x)= \frac{0.0125 \mathbb{1}_{ \{ \theta=fair \}} + 0.0079  \mathbb{1}_{ \{ \theta=truqué \}}   }{ 0.0125 +0.0079} \\

f(\theta | X=2) = 0.612 \mathbb{1}_{ \{ \theta=fair \} } + 0.388 \mathbb{1}_{\{ \theta=loaded \} }
$$
Dans ce paradigme:
$$
P(\theta=loaded | X=2) = 0.388
$$
On appelle le résultat Posterior probabilité; on a cette fois-ci une probabilité que la pièce soit truqué après deux faces.

On peut vouloir changer le prior, $p(\theta=truqué)=\frac{1}{2}  \rightarrow P(\theta=truqué|X=2)=0.297$ ou si on connait notre frère et qu'il triche souvent :

$p(\theta=truqué)=0.9  \rightarrow P(\theta=truqué|X=2)=0.792$

Dans le paradigme fréquentiste il y'a aussi des informations subjective enfoui dans le modèle, le choix de la population, quelle est note vraisemblance

### 2.5 Version continue de Bayes

On rappelle la formule; avec une "normalizing constant" qui permet d'obtenir 1 au dénominateur et donc qu'on a bien une densité de probabilité; la raison pour laquel on peut ignorer le dénominateur est que le posterior est un PDF de $\theta$ , mais $\theta$ n'apparait pas dans $f(y)$ car on intègre par rapport à lui
$$
f(\theta|y) = \frac{f(y|\theta)f(\theta)}{f(y)} \\
= \frac{f(y | \theta)f(\theta)}{\int f(y | \theta)f(\theta) d\theta} \\
= \frac{ lihelihood \times prior}{normalizing~ constant} \\
\approx likelihood \times prior
$$
exemple:

On lance une pièce, il a une probabilité $\theta$ d'avoir une face

$\theta \sim U_{[0;1])}$ ; $f(\theta) = \mathbb{1}_{  \{ 0 \le \theta \le 1 \} }$on dit qu'on à observer un flip de la pièce quel est notre posterior distribution de $\theta $
$$
f(\theta| y = 1) = \frac{\theta^1 (1 - \theta)^0 \mathbb{1}_{   \{0 \le \theta \le 1 \}   }}{\int_{- \infty}^{+ \infty} \theta^1 (1-\theta)^0 \mathbb{1}_{ \{ 0 \le \theta \le 1 \} } d\theta} \\
= \frac{\theta \mathbb{1}_{   \{0 \le \theta \le 1 \}   }}{ \int_{0}^{1} \theta d\theta} \\
= 2 \theta \mathbb{1}_{   \{0 \le \theta \le 1 \}  }
$$
On pourrait aussi le calculer par proportionnalité
$$
f(\theta | y) \approx f(y|\theta) f(\theta) \\
\approx \theta \mathbb{1}_{\{ 0 \le \theta \le 1 \}}
$$
il ne nous reste plus qu'à normaliser pour que ce soit une probabilité pour avoir la valeur exacte
$$
f(\theta | y=1) = 2 \theta \mathbb{1}_{ \{0 \le \theta \le 1 \}}
$$

### 2.6 Posterior Intervals

Aussi appelé, Bayesian posterior intervals ou Credible interval

Il est important de noter que chaque paramètre suit une loi de probabilité dans le paradigme bayésien. On leur définit un interval

On reprends l'exemple qu'on à vu juste avant, où nous allons tracer le prior et le posterior

Ce qu'on peut voir c'est qu'il est bien plus probable que $\theta$ soit proche de 1 dans le posterior que dans le prior; car nous avons vu une face $f(\theta | Y=1)$

![im1](im1.png)

Et pour $f(\theta|Y=0)=2 (1 - \theta) \mathbb{I}_{ \{ 0 \le \theta \le 1 \} }$

![im2](im2.png)

> Exemple:
>
> On peut calculer des Prior interval estimates
>
> $P(0.025 < \theta < 0.975) = 0.95$
>
> $P(\theta > 0.05) = 0.95$
>
> Graphiquement on peut imaginer ça comme intégrer dans la région sous la densité, car c'est uniforme c'est très simple à calculer
>
> Et le posterior interval estimates, sous la posterior density 
> $$
> P(0.025 < \theta < 0.975) = \int_{0.025}^{0.975}2 \theta d\theta = 0.975^2 - 0.025^2 = 0.95 \\
> $$
> Cette probabilité s'avère être la même que avec le Prior; ce qu'on peut voir avec la photo, si on déplace les deux extrémités on a toujours les mêmes valeurs au centre
> $$
> P(\theta > 0.05) = 1 -0.05^2 = 0.9975
> $$
> Il y'a donc maintenant très peu de chance que theta soit inférieur à 0.05 après avoir observé un face, ce qui est un gros changement par rapport au prior.
>
> On peut maintenant se poser la question: quel est l'interval qui contient 95% de la posterior probability. Ce qui serait équivalent à un interval de confiance fréquentiste. On peut faire ça de plusieurs façons:
>
> * Avec les Posterior intervals ou credible intervals ce sont des equal-tailed intervals
> * Highest posterior density intervals
>
> La question que nous avons répondu sont: la probabilité que le $\theta$ du posterior soit plus grand que 0.05 est de $99\%$

### 2.6.1 Equal tailed intervals - cas 1

Nous matterons la même quantité de probabilité dans chaque queue. Donc pour faire du 95% d'interval, nous mettrons 0.025 dans chaque queue. 

Pour faire ça nous allons devoir savoir quels sont les quantiles

> Exemple:
>
> $P(\theta < q | Y=1) = \int_{0}^{q} 2 \theta d\theta = q^2$ (formule des quantiles)
> $$
> P(\sqrt{0.025} < \theta < \sqrt{0.975}) \\
> = P(0.158 < \theta < 0.987)\\
> = 0.95
> $$
> Il y'a donc 95% de chance que $\theta \in [ 0.158; 0.987 ]$

![im3](im3.PNG)

### 2.6.2 Highest Posterior Probability (HPD)

On se demande, ou la densité est la plus forte ? Théorèquiement parlant ce sera l'interval le plus court qui contient la probabilité de 0.95, une probabilité de 95% 

![im4](im4.png)

exemple, il faut re regarder la formule des quantiles en haut
$$
(HPD): P(\theta > \sqrt{0.05} | Y = 1) = P(\theta > 0.224| Y=1) = 0.95
$$
C'est le plus court interval sous le posterior a une probabilité de 0.95.

La distribution de probabilité décrit notre compréhension de notre incertainty combinant nos connaissance prior et nos données. Nous avons une densité de probabilité ce qui rend possible de faire des intervalles et parler de probabilité de theta appartenant à cet interval

On a une approche plus satisfaisante qu'en fréquentiste, on peut dire que le paramètre $\theta$ est plus grand que 0.05 avec une probabilité de 95%

La pièce est une quantité physique il peut avoir une valeur de theta qui peut être fixé; on représente notre uncertainty avec une distribution car on ne sait pas ce que c'est.

### Supplementary material for Lesson 5

Normalizing constants and proportionality







## 3. Comment définir un Prior ?

On choisit généralement un prior à partir d'une famille. Si des données sont forte, le prior peut avoir peu d'effet sur le posterior

On peut définir un interval de calibration prédictif, i.e. que par exemple 95% des données futures y seront dedans

> Exemple:
>
> Prior predictive distribution
>
> On lance une pièce 10x, on compte le nombre de face, combien de face prédit-on ?
> $$
> X = \sum_{i=1}^{n} Y_i
> $$
>
>
> Rappel:
> $$
> n! = \Gamma(n+1) \\
> z \sim \beta( \alpha, \beta) \\
> f(z) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} z^{\alpha - 1} (1-z)^{\beta - 1}
> $$
>
>
>
>
> Prior:
> $$
> f(\theta) = \mathbb{1}_{ \{ 0 \le \theta \le 1 \}} \\
> f(x) = \int f(x|\theta) f(\theta) d\theta \\
> = \int_{0}^{1} \frac{10!}{x!(10-x)!} \theta^x (1-\theta)^{10-x}(1)d\theta \\
> = \int_{0}^{1} \frac{\Gamma(11)}{\Gamma(x+1)\Gamma(11-x)}\theta^{(x+1)-1}(1-\theta)^{(11-x)-1} d\theta \\
> = \frac{ \Gamma(11)}{\Gamma(12)} \int_{0}^{1} \frac{12}{\Gamma(x+1)\Gamma(11-x)}\theta^{(x+1)-1} (1-\theta)^{(11-x)-1} d\theta \\
> = \frac{\Gamma(11)}{\Gamma(12)}(1) \\ =   \frac{10!}{11!} \\ =  \frac{1}{11} \forall x \in \{ 0,1,...,10 \}
> $$
> On voit que avec un prior uniforme, on finit une prédiction de type uniforme. Tous les résultats ont même probabilité

### 3.1 Bernouilli / Binomiale distribution avec prior uniforme



> Exemple:
>
> Likelihood: $f(y| \theta) = \theta^{\sum y_i} (1-\theta)^{n- \sum y_i}$
>
> Prior: $f(\tilde{\theta}) = \mathbb{1}_{0 \le \theta \le 1}$
>
> Posterior:
> $$
> f(\theta | y) = \frac{ f(y| \theta)f(\theta)}{\int f(y|\theta) f(\theta) d\theta}\\
> = \frac{\theta^{\sum y_i}(1-\theta)^{n- \sum y_i} \mathbb{1}_{ \{ 0 \le \theta \le 1 \}}}{\int_0^1 \theta^{\sum y_i}(1-\theta)^{n- \sum y_i} \mathbb{1}_{ \{ 0 \le \theta \le 1 \}}} \\
> = \frac{ \theta^{\sum y_i}(1-\theta)^{n- \sum y_i} \mathbb{1}_{ \{ 0 \le \theta \le 1 \} }}{ \frac{ \Gamma(\sum y_{i+1}) \Gamma(n - \sum y_{i+1})}{\Gamma(n+2)} \int_0^1 \frac{\Gamma(n+2)}{\Gamma(\sum y_{i+1}) \Gamma(n \sum y_i +1)}} \times \theta^{\sum y_i}(1 - \theta)^{n - \sum y_i} d\theta \\
> = \frac{\Gamma(n+2)}{\Gamma(\sum y_i + 1 ) \Gamma(n - \sum y_i +1)} \\
> \theta | y \sim Beta(\sum y_i + 1, n - \sum y_i +1)
> $$
>

### 3.2 Les conjugates prior

On le définit comme une "family distribution" si on a un membre de la famille comme prior on connait son posterior.

Exemple:

*  $\beta$ est conjugate a Bernouilli
* La loi normale est conjugate a la loi normale 

demonstration: $\beta -> \beta$
$$
\beta prior: f(\theta) = \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha)\Gamma(\beta)}\theta^{\alpha}(1-\theta)^{\beta - 1} \mathbb{1}_{0 \le \theta \le 1}\\
f(\theta | y) \approx f(y|\theta) f(\theta) \\
= \theta^{\sum y_i} (1 - \theta)^{n - \sum y_i} \frac{\Gamma(\alpha + \beta)}{\Gamma(\alpha) \Gamma(\beta)} \theta^{\alpha - 1 } (1 - \theta)^{ \beta - 1} \mathbb{1}_{0 \le \theta \le 1} \\
\approx \theta^{\alpha + \sum y_i - 1} (1 - \theta)^{\beta -1} \mathbb{1}_{0 \le \theta \le 1} \\
\approx \theta^{\alpha + \sum y_i - 1}(1 - \theta)^{\beta +n} \mathbb{1}_{0 \le \theta \le 1} \\
\theta | y \sim Beta(\alpha + \sum y_i, \beta + n - \sum y_i)
$$
On retient que $U \sim \beta(1,1)$, un $\beta$ prior donne un $\beta$ posterior

### 3.3 Posterior mean and effective sample size

En partant de $\theta | y \sim Beta(\alpha + \sum y_i, \beta + n - \sum y_i)$ Prior $Beta(\alpha, \beta)$

* On peut déterminer:
  * Effective sample size of the prior = $\alpha + \beta$
* L'espérance de Beta comme:
  * $\frac{\alpha}{\alpha + \beta}$
* On peut avoir la moyenne du posterior

$$
\frac{\alpha + \sum y_i}{\alpha + \sum y_i + \beta + n - \sum y_i} = \frac{\alpha + \sum y_i}{\alpha + \beta + n} \\
= \frac{\alpha + \beta}{\alpha + \beta + n} \times \frac{\alpha}{\alpha + \beta} + \frac{n}{\alpha + \beta + n} \times \frac{\sum y_i}{n}
$$

On en déduit la formule suivante:

Posterior mean = Poid du prior $\times$ moyenne du prior + poids des données $\times$ moyenne des données

Remarque:

1. Le poid de prior + donnée = 1
2. La moyenne Posterior est une weighted moyenne de deux moyenne
3. si $\alpha + \beta < n$ le posterior dépend des données
4. si $\alpha + \beta > n$ il dépend du prior

Méthodologie pour un "credible interval" avec posterior distribution de Beta:

Analyse séquentielle:

1. On commence avec un prior $f(\theta)$, on a un n points de nos données
2. Avec $f(\theta)$ on observe $y_1,...,y_n$ de données on met à jours le prior pour avoir un posterior $\theta | y_1,...,y_n$
3. Le prochain jours on observe plus de points $y_{n+1}...y_{n+m}$
4. On obtient un nouveau Posterior etc.

> Remarque:
>
> * On obtient le même résultat que si la mise à jours était en batch; alors qu'ici elle est séquentielle.
>
> Exemple: dans le cas médicale ils rajoutent les données au fur et à mesure
>
> * Fréquentiste ne peuvent pas ajouter de sous-suite

Exercice:

Supposons que nous faisons une analyse de donnée Binomiale avec un Conjugate Prior $Beta$. Notre prior a moyenne de 0.4 et "effective size de 5".

On observe ensuite 10 lancer avec 6 succès, donc la moyenne des données est de 0.6. Posons $\theta^*$ la moyenne du posterior de $\theta$, la probabilité de succès.

Qu'est ce qui est vrais sur $\theta^*$:

* $\theta^* \le 0.4$ 
* $\theta^* \le ]0.4;0.5[$
* $\theta^* = 0.5$ exactement
* $\theta^* \in ]0.5;0.6[$
* $\theta^* \ge 0.6$

Correction:

Post mean = prior weight $\times$ data weight + prior mean $\times$ data mean <=> $\theta^* = P_w \times 0.4 + D_w \times 0.6$

Effective sample size => $5= \alpha + \beta$ <=> $\alpha = 5 - \beta$

De plus;
$$
\frac{\alpha}{\alpha + \beta}=0.4 <=> \frac{5- \beta}{5 - \beta + \beta} =0.4 \\
<=> \beta = 0.3;\alpha = 2
$$
Pour 10 trials
$$
P_W = \frac{\alpha + \beta}{\alpha + \beta + n} =0.33 \\
D_W  = \frac{n}{\alpha + \beta + n} = 0.5
$$
On retient ici que les données ont plus de poids que le prior

### 3.4 Loi de Poisson

On va calculer les mêmes paramètres qu'au chapitre d'avant. On rappelle un cas d'usage de l'exemple:

> exemple:
>
> les cookies aux pépites; le nombre de pépites suit une loi de Poisson
> $$
> Y_i \sim Poisson(\lambda) \\
> f(y|\lambda) = \frac{\lambda^{\sum y_i} e^{-n \lambda}}{\Pi_{i=1}^{n}y_i!} \forall \lambda \gt 0
> $$
> Gamma prior:
> $$
> \lambda \sim \Gamma(\alpha, \beta) \\
> f(X) = \frac{\beta^{\alpha}}{\Gamma(\alpha)}\lambda^{\alpha - 1} e^{-\beta \lambda}
> $$
> Par la loi de Bayes:
> $$
> f(\lambda | y) \approx f(y|\lambda) \\
> \approx \lambda^{\sum y_i} e^{-n \lambda} \lambda^{\alpha -1} e^{-\beta \lambda} \\
> \approx \lambda^{(\alpha + \sum y_i)-1} e^{-(\beta+n)\lambda}
> $$
> On a Posterior
> $$
> \Gamma(\alpha + \sum y_i, \beta + n)
> $$
> Moyenne du gamma:
> $$
> \frac{\alpha}{\beta}
> $$
> D'où la moyenne du Posterior 
> $$
> \frac{\alpha + \sum y_i}{\beta + n} = \frac{\beta}{\beta+n} \times \frac{\alpha}{\beta} + \frac{n}{\beta + n} \times \frac{\sum y_i}{n} 
> $$
> Comment choisir les $\alpha,\beta$ pour les cookies ?
>
> Stratégie:
>
> 1. Moyenne du prior: $\frac{\alpha}{\beta}$ équivaut à dire que "Quel est le nombre de pépite que j'ai sur mes cookies en moyenne"
>    1. Prior standard deviation: $\frac{\sqrt{\alpha}}{\beta}$ qui donne le prior de Gamma
>    2. La "effective sample size": $\beta$
> 2. On peut représenter notre ignorance par un prior très vague: **petit $\epsilon \gt 0 $ **
>
> $\Gamma(\epsilon, \epsilon ) \approx$ moyenne $\frac{\epsilon}{\epsilon}=1$ et variance $\frac{1}{\epsilon}$ -> huge
>
> On a une posterior mean de 
> $$
> \frac{\epsilon + \sum y_i}{\epsilon +n} \approx \frac{\sum y_i}{n}
> $$
>

### 3.5 Exemple avec loi de Poisson

Exemple: On attend a un arrêt de bus qui arrive en moyenne toutes les 10 minutes selon notre connaissance passé
$$
Y \approx Exp(\lambda)\\
Prior~~~moyenne = \frac{1}{10} \\
\Gamma(100, 1000) \\
Prior ~~ sd = \frac{1}{100}
$$
Supposons que nous attendons 12 minutes pour le bus: $Y=12$. On va vouloir mettre à jours le Posteior $lambda$ sur les arrivés de bus
$$
f(\lambda | y) \approx f(y | \lambda) f(\lambda) \\
\approx \lambda e^{-\lambda y} \lambda^{\alpha - 1} e^{- \beta \lambda} \\
\approx \lambda^{(\alpha +1)-1} e^{-(\beta + y) \lambda} \\
=>n \lambda | y \approx \Gamma(\alpha +1, \beta + y) \\
=> \lambda | y \approx \Gamma(101, 102)
$$
On peut calculer la:

Posterior mean $$=\frac{101}{1012} = 0.0998$$

On se rend compte que cette information de retard de bus n'a pas apporté beaucoup d'informations sur le posterior

### 3.6 Loi normale avec variance connu

On va vouloir déterminer sa moyenne
$$
X_i \sim N(\mu, \sigma^2) \\
conjugate ~ prior:~~ \mu \sim N(m_0,s_0^2) \\
Par~Bayes: f(\mu |x) \approx f(x| \mu)f(\mu) \\
\mu |x \approx N(\frac{\frac{n \bar{x}}{\sigma_0^2} + \frac{m_0}{s_0^2}}{\frac{n}{\sigma_0^2} + \frac{1}{s_0^2}}, \frac{1}{ \frac{n}{\sigma_0^2} + \frac{1}{s_0^2}})
$$
On va calculer la posterior mean
$$
\frac{ \frac{n}{\sigma_0^2}}{\frac{n}{n + \sigma_0^2}} \bar{x} + \frac{\frac{\sigma_0^2}{s_0^2}}{n + \frac{\sigma_0^2}{s_0^2}} m 
$$
avec x bar la data mean; le m est la prior mean; en haut a droite on a la variance des données et la variance prior

=> On retient que la moyenne posterior est une fois de plus une weighted average du prior moyenne et des données

> Exercice:
>
> On pose $Y| \theta \sim N(\mu, \sigma^2)$ et$\theta \sim N(m_0, s_0^2)$
>
> La distribution marginale est:
>
> $$ \int f(y, \theta)d\theta,~donne~ N(m_0, s_0^2+\sigma^2)$$
>
> supposer que les données soient $N(theta, var=1)$ on a un prior $\sim N(\theta,2)$
>
> Trouver a 
>
> on q $m_0=0$, $s_0^2=2$, $\sigma^2=1$
>
>  donc:
> $$
> \sim N(0 ,2+1) \\
> \sim N(0,3) \\
> a = 3
> $$
>

### 3.7 Loi normale avec variance et moyenne inconnu

On peut poser 
$$
X_i | \mu, \sigma^2 \sim N(\mu, \sigma^2) \\
\mu | \sigma^2 \sim N(m, \frac{\sigma^2}{w}) \\
w = \frac{\sigma^2}{\sigma_{\mu}^2},l'effective~sample~size~du~prior \\
\sigma^2 \sim \Gamma^{-1} (\alpha,\beta)
$$
Calculons le posterior
$$
\sigma^2 | x \sim \Gamma(\alpha + \frac{n}{2}, \beta + \frac{1}{2} \sum(x_i - \bar{x})^2 + \frac{nw}{2(n+w)}(\bar{x}-m)^2 \\
\mu | \sigma^2, x \sim N(\frac{n \bar{x} + wm}{n+w}, \frac{\sigma^2}{n+w})
$$
On va pouvoir réecrire le posterior mean
$$
\frac{n \bar{x}+wn}{n+w} = \frac{w}{n+w}m + \frac{n}{n+w}\bar{x}
$$
On a de plus que :
$$
\mu | x \sim t-distribution
$$
Question:

Nous souhaitons faire de l'inférence sur $\mu$, mais $\sigma^2$ est inconnu trois solutions

s1) On fixe $\sigma^2$ a une valeur qu'on suppose

s2) On estime $\sigma^2$ des données

s3) On spécifie un prior pour $\sigma^2$ et $\mu$

La s3 est la meilleur solution: elle permet de refléter l'aspect incertain de $\sigma^2$ et protége contre des intervalles de confiance beaucoup trop confiant



### 3.8 Les non-informatif prior

Fait partie de ce qu'on appelle "Objective Bayesian statistic". On va chercher à minimiser l'information apporté par le prior

> Exemple:
>
> Lancer de pièce
> $$
> Y_i \sim \beta(\theta)
> $$
> Prior: $\theta \sim U_{[0,1]}=\beta(1,1)$
>
> On va descendre encore plus le prior par $\beta(\frac{1}{2},\frac{1}{2})$ puis $\beta(0.001,0.001)$ ou encore plus bas pour le prior quasiment inexistant:
>
> $$ \beta(0,0) -> f(\theta) \approx \theta^{-1}(1 - \theta^{-1})$$
>
> On aappelle ces priors "improper prior" due aux propriétés de l'intégrale. Et surtout qu'elle n'a pas de densité propre. 
> note: on peut avoir un Prior improper tant que le posterior ne l'est pas
>
>
>
> Ensuite;
>
> $$f(\theta|y) \approx \theta^{y-1} (1- \theta)^{n-y-1} \sim \beta(y, n-y)$$
>
> La moyenne posterior:
>
> $$ \frac{y}{n} = \hat{\theta}$$ (MLE)
>
> Pour rappel, avec le MLE on va pouvoir lui donner un interval ce qui est impossible en fréquentielle



Exemple2:

$$
Y_i \sim N(\mu,\sigma^2)~\sigma^2~connu 
$$
On définit un Prior vague
$$
\mu \sim N(0,(1.10^6)^2)
$$
Si on pqsse la variance à l'$\infty$ on :
$$
f(\mu) \approx 1~qui~est~impropre
$$
Ensuite,
$$
f(\mu | y) \approx f(y | \mu) f(\mu) \\
\approx exp(\frac{-1}{2 \sigma^2}\sum(y_i - \mu)^2) \\
\approx exp(\frac{-1}{2 \frac{\sigma^2}{n}}(\mu - \bar{y})^2) \\
\mu | y \approx N(\bar{y}, \frac{\sigma^2}{n})
$$
On va déterminer le $\sigma^2$ inconnu
$$
f(\sigma^2) \approx \frac{1}{\sigma^2} \Gamma^{-1}(0,0) ~qui~est~impropre
$$
Finalement le posterior de $\sigma^2$ est:
$$
\sigma^2 | y \approx \Gamma^{-1} (\frac{n-1}{2}, \frac{1}{2} \sum (y_i - \bar{y})^2)
$$

### 3.9 Jeffreys prior:

Premier point: Les prior uniforme ne sont pas invariants aux transformations

exemple:
$$
Y_i \approx N(\mu, \sigma^2)
$$
On peut définir deux priors
$$
f(\sigma^2) \approx \frac{1}{\sigma^2} \\
f(\sigma^2) \approx 1
$$
note: si on compare leurs Posterior ils seront différents

**Jeffrey prior** est un "transformation invariant" contrairement à l'exemple précédent

On le définit comme:
$$
f(\theta) \approx \sqrt{I(\theta)}
$$
Dans la plupart des cas, ce sera un improper prior

Exemple:
$$
Y_i \approx N(\mu, \sigma^2): f(\mu) \approx 1 \\
							  f(\sigma^2) \approx \frac{1}{\sigma^2}
$$

$$
Y_i \sim \beta(\theta): f(\theta) \approx \theta^{-\frac{1}{2}}(1 - \theta)^{-\frac{1}{2}} \\
\sim \beta(\frac{1}{2}, \frac{1}{2})
$$

C'est un des rares cas ou ce n'est pas un improper

### 3.10 Autres approches

Dans les méthodes objectives Bayésienne:

- Prior par max entropy
- References prior



La méthode des Empirical Bayes: on utilisera les données pour trovuer le prior

exemple: On utilise les données pour trouver la moyenne

Attention: On peut finir avec des estimates impropres. On va utiliser les données 2x





