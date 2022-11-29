<img src="assets/background.gif" />
<hr>
<p align="center">
<b style="font-size:30vw;">Introduction to machine learning - Homework 3</b>
</p>
<hr>

The goal of this third assignment is to predict the power produced by a wind farm with the use of different machine learning models !

*Note:*

- Don't forget to code on **your branch** !
```
git checkout -b yourname
```

- Don't forget our good friend:
https://github.com/meurissemax/elen0062-1

<hr>
<p  style="font-size:20px; font-weight:bold;" align="center">
More informations
</p>
<hr>

More practical information to come. By December 11th, you should have submitted your code and a written report on the Gradescope platform. Your report should describe the different steps of your approach and your (main) results.
In particular, the report must contain:

- A detailed description of all the approaches you have investigated
- A detailed description of your approach to select and assess your model
- A table summarising the results of your different approaches
- All tables, figures and results should be analysed in-depth while avoiding unnecessary redundancies
- Any complementary information that you want to analyse

<hr>
<p  style="font-size:20px; font-weight:bold;" align="center">
Notes from the professor
</p>
<hr>

Le but est de faire une prédiction sur la production d’une ferme à éoliennes sur base de la connaissance du vent, hauteur de l’éolienne … Nous avons donc un problème à dépendance temporelle ! Le but sera de prédire la production pour 10 éoliennes différentes.

RAPPORT

- Première partie: traitement/amélioration du dataset
- Seconde partie: exploration de différentes méthodes

METHODOLOGIE

- En première approximation, on ne considère pas la dépendance temporelle. On prend le sujet comme un simple problème de régression.

- Pour aller plus loin, on prend en compte la dépendance temporelle.

TIPS

- Au lieu d’entrainer le modèle sur les données séparées entre les éoliennes, sachant que celles-ci se trouvent sur le même terrain, on pourrait essayer de combiner les données de plusieurs éoliennes pour « généraliser » un peu nos data. C’est une piste à explorer.

- Quand on prendre en compte la dépendance temporelle, on peut essayer de l’inclure en faisant un input vector contenant les valeurs des attributs en t ET t -1 voir même t - 2, t - 3, …

- Quand on fait la partie 2 du rapport, le mieux est qu’on se répartisse les différentes méthodes à explorer et qu’on écrive en même temps le rapport afin d’avoir quelque chose de complet (EX: l’année passée, des gens dans le top 1 de la complétion ont obtenu des points de merde parce que leur rapport était éclaté)

- (Victor) on va donc devoir explorer les méthodes qu’on a vues au cours, dont les réseaux de neurones. Une chose que je n’aime pas trop dans ce qu’il a dit c’est qu’on va essayer d’introduire nous-mêmes la dépendance temporelle en incluant des variables à des temps antérieurs. Le truc c’est que la plupart des méthodes qu’on a vues ne sont pas explicitement désignées pour être à l’aise avec des dépendances temporelles ! CEPENDANT, dans les réseaux de neurones, on a les réseaux LSTM qui sont spécialisés là-dedans et on a passé tout le quadrimestre passé à faire notre projet de deep learning avec. Donc, on peut explorer un maximum de trucs qu’on a vu au cours et si j’ai le temps à la fin, je suis chaud tenter un « bonus » en reprenant ce qu’on a fait le quadrimestre passé !

NOTE

- Je suis vraiment très curieux de commencer par la partie 1 ce projet ! Dans le livre que je vous ai envoyé, le type montrait quelques techniques pour reformuler/améliorer son dataset ainsi que des méthodes pour voir si nos nouvelles variables contiennent plus d’informations utiles pour l’entraînement précédemment !

- J’arrête d’écrire la parce que ça devient sacrément long ahahah !

- On va devoir utiliser google colab pour faire nos petits entrainements tranquillement ! Si vous avez jamais utilisé, je vous montrerai !