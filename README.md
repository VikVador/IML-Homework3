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

Objective and data
The goal of the competition is to design a model to predict wind power 24h ahead in 10 zones, corresponding to 10 wind farms located in Australia (exact location is unknown). The data to train and test your model is given in the form of two files per zone (X_Zone_i.csv and Y_Zone_i.csv) that contain both different variables measured every hour from 1/01/2012 at 1am until 1/01/2014 at 0am (ie., 24 months, 17544 measurements).
The files X_Zone_i.csv, contain the following columns:
ZONEID: the zone number (from 1 to 10)
U10, V10, U100, V100: wind forecasts at two heigths, 10m and 100m, above the ground level at the exact location of the wind farm. The wind forecast is given as the zonal and meridional wind components (denoted u and v). They correspond to the projection of the wind vector on the west-east and south-north axes respectively. To match the objective of 24h ahead wind power prediction, these forecasts have been computed every day at midnight for next 24 hours.
Day, Month, Year, Hour: indicating the exact moment of the measurement.
The files Y_Zone_i.csv contain the same ZONEID, Day, Month, Year, and Hour columns as in the X_Zone_i.csv file, with the addition of a column TARGETVAR, containing the wind power measurements. All power measurements were normalized by the nominal capacity of the corresponding wind farm so that these values can be compared between zones.
Starting on 6/10/2013, wind power values are missing in the file (they are replaced by -1 values) for one full week every three weeks. These missing values are the values you are expected to predict for all 10 zones. More precisely, you are expected to predict (normalized) wind power for the following weeks:
From 6/10/2012 1am to 13/10/2012 0am
From 3/11/2012 1am to 10/11/2012 0am
From 1/12/2012 1am to 8/12/2012 0am
From 29/12/2012 1am to 5/01/2013 0am
From 26/01/2013 1am to 2/02/2013 0am
From 23/02/2013 1am to 2/03/2013 0am
From 23/03/2013 1am to 30/03/2013 0am
From 20/04/2013 1am to 27/04/2013 0am
From 18/05/2013 1am to 25/05/2013 0am
From 15/06/2013 1am to 22/06/2013 0am
From 13/07/2013 1am to 20/07/2013 0am
From 10/08/2013 1am to 17/08/2013 0am
From 7/09/2013 1am to 14/09/2013 0am
From 5/10/2013 1am to 12/10/2013 0am
From 2/11/2013 1am to 9/11/2013 0am
From 30/11/2013 1am to 7/12/2013 0am
From 28/12/2013 1am to 1/01/2014 0am (this week is incomplete)
In terms of time points, this means you have a training set of size 14760 and a test set of size 2784, for each zone.
Challenge and metric

To participate to the challenge, you will have to submit on gradescope 10 files, one per zone, containing each your predictions for the missing values in the corresponding Y_Zone_i.csv file. The files to be submitted need to be named Y_pred_Zone_i.csv (with i the zone number) and contain a single column with the predicted values ordered chronologically (i.e. 2784 values), with TARGETVAR as the column header. The file submission.py provided with the data loads the data and produce prediction files in the right format (corresponding to constant predictions). Feel free to submit these prediction files to familiarize yourself with the platform.
To rank your predictions, we will use the absolute error, i.e. the absolute difference between your prediction and the true value averaged over all zones and time points.
During the challenge period, the leaderboard on Gradescope (Assigment: Project 3 - Challenge) will show two scores:
- MAE_glob: the mean absolute error averaged over all zones.
- MAE_Z1: the mean absolute error on zone 1 predictions only
These two scores will be based only on a subset of the days you need to fill in. This subset will not be disclosed. MAE_Z1 is provided as well so that you can make experiments only on zone 1 during some preliminary exploratory phase and still get a feedback from Gradescope. Only this score will be computed if you provide a file Y_pred_Zone_1.csv and some or all other prediction files are missing in your submission.
When the challenge will be over, your MAE scores averaged over all zones and over all days that were not used to compute the scores during the challenge period will be used to produce the final ranking of your submissions.
Report
By December 11th, you should have submitted your code and a written report on the Gradescope platform (Assignement: Project 3 - Report). Your report should describe the different steps of your approach and your (main) results.
In particular, the report must contain:
A detailed description of all the approaches you have investigated
A detailed description of your approach to select and assess your model
A table summarising the results of your different approaches
All tables, figures and results should be analysed in-depth while avoiding unnecessary redundancies
Any complementary information that you want to analyse
Deadlines
9/12/2022 at 23h59: end of the challenge and release of the final ranking
11/12/2022 at 23h59: submission of your report and code
14/12/2022 at 9h00: debriefing of the challenge (usual lecture room)

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