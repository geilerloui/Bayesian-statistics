# Statistique Bayésienne: Des concepts à l'analyse des données

## 1. Introduction

### 1.1 Paradigme des probabilités

Les statistiques sont l'étude de l'incertitude. Comment la mesurer ? comment prendre des décisions ? Trois grand modèles permettent de répondre à ces interrogations

1. **<u>Classique</u>**:

   Par de l'hypothèse que des résultats qui sont équiprobables ont des probabilités égales.	*Exemple: Lors d'un lancer de dés, chaque face à une probabilité de $\frac{1}{6}$ de tomber si le dés n'est pas pipé. On pourra ensuite se demander parmi les lancer combien donneront une somme égale à quatre $P(X_1+X_2=4)$.*

2. **<u>Fréquentiste</u>**:

   Nous demande d'avoir une suite hypothétique infini d'évènements auxquels on va analyser leurs fréquences.

   *Exemple: On peut imaginer une situation ou on lance un nombre de fois infini un dés afin de voir si il est pipé, on obtient*; $P(non~ pipé)= \{0,1\}$ ; *on voit que la réponse est binaire soit il l'est soit il ne l'est pas.*

   *Si on voulait calculer la probabilité $P(pluie)$ il faudrait imaginer un nombre de cas infini de pluie et voir dans tous ces scénarios lesquels rendent l'hypothèse vrais.*

3. **<u>Bayésien</u>**:

   C'est une perspective personnel. Notre probabilité notre probabilité représente notre propre perspective, il prends en compte ce qu'on connait sur le problème

   Exemple: On revient sur le jeux du dés, si on sait qu'il est pipé on va pouvoir jouer la dessus. 

**Concept de cohérence:** 

Les probabilités doivent suivre toutes les règles standard de probabilité si on ne suit pas ces règles on peut être incohérents; ce  qui peut amener à créer un jeux de pari ou on est sur de perdre c'est ce qu'on appelle Dutch book

### 1.2 Probabilité conditionnelles

Les probabilités conditionnelles apparaissent lorsqu'on essaye de considérer deux évènements qui sont liés ensembles. 
$$
P(A|B) = \frac{P(A \cap B)}{P(B)}
$$
**Exemple:**

Considérons une classe de 30 étudiants, 9 sont des étudiantes; 12 ont choisi l'option informatique dont 4 sont étudiantes. 

1. Calculer les paramètres manquants

a = 8; b = 5; c = 13

|                      | Femme    | Homme     | Total     |
| -------------------- | -------- | --------- | --------- |
| **Informatique**     | 4 (2/15) | a (4/15)  | 12 (6/15) |
| **Non informatique** | b (1/6)  | c (13/30) | d (18/30) |
| **Total**            | 9 (3/10) | e (7/10)  | 30 (1)    |

2. Calculer $P(Femme)$

$$
\begin{aligned}
P(Femme) &= \frac{9}{30} = \frac{3}{10} \\
P(Informatique) &= \frac{12}{30} = \frac{2}{5}\\
P(F \cap Info)&=\frac{4}{30}=\frac{2}{15}
\end{aligned}
$$

3. $Femme \perp Informatique$ ?

$$
P(F|Info) = \frac{P(F \cap Info)}{P(Info)} = \frac{2/15}{2/5} = \frac{1}{3}
$$

On peut aussi le résoudre en lisant énoncé de façon intuitive "Parmi les 12 étudiants en informatique 4 sont des étudiantes" ce qui revient à calculer $\frac{4}{12}=\frac{1}{3}$

Dans l'autre sens on à:
$$
P(F| Info^C)=  \frac{P(F \cap Info^C)}{P(Info^C)}=\frac{5/30}{18/30}=\frac{5}{18}
$$


1. On a aussi la notion d'indépendence qui est que $P(A|B)=P(A)$ alors $P(A \cap B)=P(A)P(B)$

Or, $P(F|Info) \neq P(F)$ on en conclut que les évènements ne sont pas indépendants



### 1.3 La formule de Bayes discrète

La formule de Bayes permet d'inverser le sens du conditionnel
$$
P(A|B) = \frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^c)P(A^c)} = \frac{P(A\cap B)}{P(B)}
$$

**Exemple 1:**
$$
P(Info|F)=\frac{P(F|Info)P(Info)}{P(F|Info)P(Info)+ P(F|Info^CP(Info^C))}=\frac{4}{9} 
$$
Ou
$$
$P(Info|F)=\frac{P(Info|F)}{P(F)}=\frac{4}{9}
$$
**Exemple 2: **

Nous allons calculer la probabilité d'avoir le Sida sachant la positivité; on va se demander si on choisit quelqu'un de façon aléatoire en Amérique du Nord et on le teste et qu'il est positif qu'elle est la probabilité qu'ils ont le Sida sachant qu'ils sont positifs

$P(+|HIV) = 0.977 $
$P(-| not HIV) = 0.926 $
$ P(HIV) = 0.0026 $
$$
\begin{aligned}
P(HIV|+) &= \frac{P(+|HIV)P(HIV)}{P(+|HIV)P(HIV) + P(+|not~ HIV)P(not~ HIV)} \\
&= \frac{(0.977 \times 0.0026)}{(0.977 \times 0.00266)+(1-0.926)(1-0.0026)} \\
&= 0.033
\end{aligned}
$$
On a donc $0.33\%​$ de chance d'avoir le Sida sachant qu'on est positif. Le résultat peut paraitre surprenant mais c'est car c'est une maladie rare. Le nombre de faux positif dépasse largement les vrais positifs cars c'est une maladie rare. Si le test est très précis (0.977) on a plus de faux négatifs que de vrais positifs.  Il fait donc plus de sens que de faire des tests sur le Sida dans une population qui en a beaucoup

### 1.4 La formule généralisée

**En discret** :
$$
P(A|B) = \frac{P(B|A_1)P(A_1)}{\sum_{i=1}^{n}P(B|A_i)P(A_i)}
$$
On va appeler:

- Distribution *à priori* : $P(A_1)$
- Vraisemblance : $P(B|A_1)$
- Distribution *à posteriori* : $P(A|B)$

**En continue** : 

Quant-on a à faire avec une variable aléatoire continue $\theta$, on peut écrire la densité conditionnelle pour $\theta$ sachant $y$ comme:
$$
f(\theta|y) = \frac{f(y|\theta)f(\theta)}{\int f(y|\theta)f(\theta)d\theta}
$$

Cette expression fait la même chose que la version discrète, car $\theta$ est continue on intégrera sur toutes les valeurs possibles de $\theta$ plutôt que de prendre sa somme

### 1.5 Quelques distributions de probabilités continues

**La loi Gamma:**

Si $X_1,X_2,...,X_n$ sont indépendants (et identiquement distribués de loi $Exp(\lambda)$)le temps d'attente entre deux évènements successifs, alors le temps d'attente total pour les $n$ évènements qui se produisent est de $Y = \sum_{i=1}^{n}X_i$ suivra une loi gamma avec un shape parameter $\alpha=n$ et rate paramètre $\beta=\lambda$
$$
Y \sim Gamma(\alpha, \beta) \\
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

 
