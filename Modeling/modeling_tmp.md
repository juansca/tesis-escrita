


in a interinstitutional framework between the Argentinean
National Space Agency (CONAE) and the Health Minister of Argentine,
there have been initiatives to model the temporal evolution of mosquito pop-
ulations using environmental variables obtained from remote sensors. These
works used series of a few years and are based on a small number of satellite
variables [36, 37]. In an effort to improve this, (author?) [38] constructed
models based on a large number of variables from various sensors for four
years. All these works assumed multivariate linear models.


This work represent an improvement of that scenario. We compare Sup-
port Vector Machines, Artificial Neural Networks, K-nearest neighbors and
Decision Tree Regressor in addition to two linear approaches. With this,
we obtain an operational methodology which contributes to the Argentinean
Dengue risk system currently in operation [31, 39].
We explore, in contrast to previous ones, the ability of modeling and
predicting oviposition with out of the shelf ML algorithms, i.e., with min-
imum parameter tuning, as provided by FLOSS – Free/Libre Open Source
Software. This promotes the assimilation of these techniques for the whole
community that deals with similar problems.




The study here presented was developed on Tartagal city (79,900 inhab-
itants) on the Northwest of Argentina (22 ◦ 32 0 S, 63 ◦ 49 0 W, 450 m above the
sea level), in Salta Province. The site is between 50 and 100 km from the
Argentinean-Bolivian border (Figure 1). Tartagal is in a subtropical native
forest environment surrounded by crops.


The site has an average annual temperature of about 23 ◦ C (summer aver-
age maximum of 39 ◦ C and winter average minimum of 9 ◦ C). It has an annual
precipitation of 1100 mm, with a dry season (June to October). Tartagal, like
several north-west Argentinean cities, has a cultural diversity based on the
presence of autochthonous ethnic groups and immigrant population in ad-
dition to a migration movement from the bordering country Bolivia. These
characteristics lead to peculiar cultural, social and economic profile behavior.



The vector population is measured using the monitoring of oviposition
activity. It is measured using ovitraps placed at randomly selected houses in
the urban area of the City. The period of monitoring used in this study was
from August 2012 until July 2016 over 50 houses. Two ovitraps were placed
in each house: one inside and other outside in a shaded site at ground level in the backyard, following the WHO guidelines [17]. The ovitraps are 1000 cm 3
of black plastic cups containing 250 mL of water without attracting infusion.
We used only the external ovitraps data in this study because they correlate
more with the satellite-derived environmental variables. The ovitraps are
replaced weekly and eggs are counted on a laboratory according to the Egg
Density Index [40]. Then the weekly Aedes ægypti oviposition activity is
estimated by the sum of egg-catches on the external traps of the city.






Following the idea to build predictive models of vector population based
on environmental variables derived from satellite, but with an operational
perspective and based on previous studies, we obtain proxies of the vegetation, moisture, temperature and rain operationally available from MODIS
and TRMM/GPM products.
Global vegetation indexes provide consistent spatial and temporal prod-
ucts of vegetation canopy greenness, property of leaf area, chlorophyll and canopy structure. These indexes are derived from atmospherically-corrected
reflectance in the red and near-infrared bands. In our case, we use the NDVI
from the MODIS MOD13Q1 satellite product (composed of 16 days) with
a 250 m spatial resolution. The vegetation conditions are included because
it is related also with the temperature, humidity and precipitation [36, 41],
relevant variables for the mosquito population evolution.





In addition, we include the Normalized Difference Water Index (NDWI),
which is related to the liquid water and humidity content in both soil and
vegetation. It is calculated from the same MODIS product using Gao’s def-
inition [42] of NDWI from the bands provided by the MOD13Q1 product,
corresponding to MIR and NIR reflectance N DW I = (ρ N IR −ρ M IR )/(ρ N IR +
ρ M IR )10 4 . MODIS products require the 10 4 factor since they are stored, for
computational economy, as integer numbers.




We also used Land Surface Temperature (LST) from MODIS because it
is an approximation of the environmental temperature [33, 43, 44]. For this,
the MOD11A2 satellite product was chosen. It has 1 km spatial resolution
and is an average of clear-sky LST’s values during an 8-day period. This
product includes daytime and nighttime LST’s representing, in some sense,
the maximum and minimum temperatures [45]


Local precipitation is obtained from the Tropical Rainfall Measuring Mis-
sion (TRMM) [46]. This is a joint mission of NASA and the Japan Aerospace
Exploration Agency launched in 1997 to study rainfall for weather and climate research. The satellite uses several instruments including radar, microwave imaging, and lightning sensors, to detect rainfall. TRMM was out of fuel on 2014, even though it continued providing data until June 2015.
After that, other products were published to assure continuity in the information based in a new space mission called GPM (https://earthdata.
nasa.gov/trmm-to-gpm).



Two areas of 85 ha were defined around the city and then the mean values,
for all the satellite derived variables, were calculated . The first area is
located within the city (Urban Area) and the second one encompasses the
native vegetation surrounding the city (Rural Area) following the approach
from (author?) [47, 48, 38]. The choice was made under the hypothesis
that selecting a zone outside the city would represent well the environmental
conditions (NDWI, NDVI, LST). The same idea was used in previous studies
in several cities. These observations and the larval indexes are likely to be
closely related. In this way, the external or rural area should be randomly
selected from areas of native vegetation close enough to the city, representing
the natural environment conditions. In this specific case this rural region is
selected in the north-east of the city. It has a similar altitude to the city and
mostly native forest. It can be see in Figure 2.






The procedure to build the temporal series of remote sensed variables
is outlined in Figure 3. The images were downloaded from NASA (http:
//e4ftl01.cr.usgs.gov) and imported into GRASS 7.1. The mean for
each of the previously defined two areas was calculated for every date. All
these average values and their dates were exported to a table in the R soft-
ware, which is used to build the complete temporal series. The data were
interpolated in order to obtain values for all the sampling dates (a value for
every epidemiological week).




All the variables are considered with three weeks lags from the original
time series, to represent Non synchronous influences, corresponding to one,
two and three time lapses.





The first step consisted in analyzing the forty environmental variables and eggs collected in each week by means of a correlation matrix and the p-values that measure their significance. This led to discarding thirty-five variables. Lagged variables were preferred because of their potential ability
to forecast. The following variables were chosen: NDVI rural lag 1, NDWI
rural lag 1, LST day rural lag 3, LST night rural lag 1, and TRMM lag 3.
All the variables are then normalised using z-scores.





Figure 4 presents the environmental variables along with the oviposition data as a heatmap. This format promotes the visualization of the temporal
evolution, the correlation pattern between variables, and the lags effect.





With the data described in previous section, we implemented two linear
models (Simple and Ridge) and four non-linear models (Support Vector Ma-
chine, ANN multi-layer Perceptron, Decision Tree, K-Nearest Neighbor) to
model the oviposition in each week. All the models use the same set of 5
environmental variables



In all the cases we generated the models with 80 % of the dataset and
retained the remaining 20 % of the temporal series (almost one year) as an
independent set to corroborate the temporal prediction capacity of the tools
(we use the last 20 % from our dataset). This splitting selection is the most
used in the ML literature [49].



Cross validation [50, 49] was used in order to decrease the dependency of
the evaluation results on a particular selection of training set and validation
set pair. In particular, a time series split cross validation procedure was
used to evaluate the models http://scikit-learn.org/stable/modules/
cross_validation.html. Other cross validation techniques like K-folds are
not suitable for time series data, i.e., when the ordering of the data is relevant.




In the following we describe the techniques used to model the oviposition
z-score as a function of the remotely sensed environmental variables. All
the models were implemented using functions from the sklearn library, freely
available in Python.





Previous experiences on the modeling of epidemiological applications us-
ing remotely sensed environmental variables report good results with this
approach [51, 37, 52]. We used simple linear and ridge regressions, the latter
with Tikhonov regularization with cross-validation. Note that Ridge regres-
sion is often referred to as “weight decay” in the ML literature.





Nonlinear models are able to capture more complex functional relations
among the data, at the expense of computational complexity and some burden on the user that has to fine tune more parameters than in linear models.



Typically, machine learning regression includes three steps: architecture,
e.g. the number of layers and neurons in an artificial neural network or the number of neighbours in the K-Nearest Neighbor algorithm, the training-
validation (where the coefficients are adjusted and the performance is eval-
uated), and then the use of the model with new data. These steps were
implemented with functions available in the sklearn package already men-
tioned.



The configuration or selection of the optimal set of parameters in this
kind of nonlinear models is a complex issue and could be handcrafted or obtained using semi automatic tools.




We used the iRace (Iterated Racing for Automatic Algorithm Configura-
tion) package [53] for automatic parameter tuning. This tool is an iterative
procedure capable of automatically finding the most appropriate parameter
configurations given the input data instances of the optimization problem. It
is implemented in R and is freely available at http://iridia.ulb.ac.be/
irace/.


In order to avoid overfitting, a problem when dealing small data sets,
the tuning was performed automatically with data from a different city:
Clorinda.



Support Vector Machines are a class of supervised techniques that build
either linear or nonlinear decision rules and regression models. We used the
SVR from SVM module. This method implements Epsilon-Support Vector
Regression, with penalty C = 0.887453, and RBF kernel coefficient gamma
= 0.015561 as tuning parameters.





Neural Networks are built by a massive number of simple processing units
highly interconnected. They can be trained to provide universal function ap-
proximators. We used the MLPRegressor method from the neural_network
module. This method implements the Multilayer Perceptron regressor by
optimizing the squared loss by either LBFGS or stochastic gradient descent.
We tuned the following parameters: alpha (the regularization quadratic term,
set to 0.070921), three layers with three neurons each proved being a suitable
and parsimonious architecture for our problem. The activation is done by
the rectified linear unit function f (x) = max{0, x}






We used the K-NeighborsRegressor module. This method infers a re-
gression based on k-nearest neighbors. The target is predicted by local inter-
polation of the targets in the neighborhood in the training set. The original
data are decomposed with principal components, and only the first five are
used. The tuning parameters choices were four neighbors, uniform weight,
Chebyshev metric and brute force.






Decision Trees are classification rules built incrementally, from which a regression model can be learned. We used the DecisionTreeRegressor
method from the tree module. Again, we used PCA but retained only the
two first components. The other parameters were the splitting rule (“best”),
the maximum depth of the tree (three levels), and the minimum number of
samples required to split an internal node (five).


The choice of numbers of PCA components for the two last methods was
based on trial-and-error, seeking for the smallest subset that produced good
results.




Fig. 5 shows the results of the classical multivariate linear and Ridge
models. These results are in conformity with previous studies. Both
linear regressors produce very close results preventing, thus, the use of
the latter due to its higher computational cost.



Linear regressors do not follow the peaks of the observed data, and
tend to underestimate the smallest values




Fig. 6 shows the observed data and the result of the Support Vector
Regression (SVR) procedure. The latter fails to model the peaks of the former, but produces a relatively good fit in the bulk of the data.



Fig. 7 shows the results of fitting the observed data with the Mul-
tilayer Perceptron (MLP) technique. The fit is very good, although the
model overestimates the data around the 25th week of the study, and
underestimates them around the last peak.





Fig. 8 shows the results produced by the KNN procedure. Also, this
is a very good model although it fails to follow the two largest peaks.
The first, around the 125th week is underestimated, and the second,
which is close to the 180th week, is overestimated.

Fig. 9 shows the result of applying the Decision Tree Regressor. The structure of this technique produces flat outputs which, nevertheless, follow closely the observed data. It is important to remember that in all
previous figures the last 40 weeks are not used to build the models,
therefore they are completely predicted.



Table 1 presents a summary of the observed and fitted data: the
minimum (Min) and maximum (Max) values, the first (q 1/4 ) and third
(q 3/4 ) quartiles, the median (q 1/2 ) and the mean.



Table 1 reveals the following facts:

\item Linear and Ridge regressions exaggerate the minima, as they produce values which are approximately the double of the observed ones.
\item The Multilayer Perceptron exaggerates the maximum by about \SI{10}{\percent}, while the other models underestimate it. Notice that the Support Vector Regression flattens the maximum by a factor of about \num{3.6}.
\item The mean and median of the observed data differ noticeably, suggesting that they are significantly skewed to the left.
\item The closest median value to the observed one is produced by K-Nearest Neighbors, which also leads to a very close mean value.




Fig. 10 shows the observed and predicted data as a scatterplot. This
figure reveals that none of the models is able to follow the largest ob-
served values, and that the Linear, Ridge and Support Vector Regres-
sions are the least apt for this task, while the Multilayer Perceptron is
the closest one. We also notice that this last model is the most prone to
overestimating the data. Notice that underestimation is, from the ap-
plication viewpoint, more dangerous than overestimation, as the former leads to a false negative indicator that may lead to not firing preventive measures in cases when they are needed.




In the following we analyze the residuals. Fig. 11(a) and (b) show,
respectively, the histograms and boxplots of the errors produced by
each model. The errors produced by KNN are the most concentrated
around zero, followed by MLP. The two errors most spread are due to
the linear regressions. This is an indication that the models obtained
using simple linear techniques are the worst among the ones considered
here.



Table 2 presents quality measures of the models here considered:
Pearson correlation coefficients between the observed and fitted values,
using the complete data set (Corr11) and the 20% (CorrL20) left for
validation; and the Mean Square Error of the complete data set (MSE)
and of the validation data (MSEL20). Following Cramer et al. (2017),
we also include the mean Score obtained from the cross validation and
its standard deviation.





Requerimientos


This operative system is based on user requirements that were stated after several meetings between health decision makers at
both the national and provincial levels. It was agreed that the system should:
(i) be able to support both multiple diseases and multiple scales of risk;
(ii) estimate the risk stratification by applying a multifactor approach at the national level for all the localities;
(iii) also produce risk cartography at the urban level;
(iv) facilitate decision making;
(v) update environmental conditions based on remotely sensed data;
(vi) integrate information such as viral circulation, urbanization, entomological field data and population parameters;
(vii) be expandable in order to cover others regional countries without significant change;
(viii) make information and maps accessible via the Internet (SIG Web based user interface);
(ix) be developed at low cost (open-source preferable);
(x) be free of charge for all end users;
(xi) be operative (running) steadily by an expected life time of >5 years;
(xii) be user friendly in order to interact with non-informatic specalist staff in the provinces; and
(xiii) aim at eventually involve the whole country.











Taking into account all the goodness-of-fit parameters included in Tables 1
and 2, and the analysis of errors, we may consider that KNN stems as the
best method for this problem. It has a correlation near to 90 %, considerably
greater than 75 %, the typical values obtained with linear approaches.


The Mean Score value would lead to choose Support Vector Regressor as
the best technique [49]. It is noteworthy that the standard deviation of this
measure of quality is so high that is it unlikely that it is able to render a
good choice by itself. For this reason, we follow a holistic approach in the
forthcoming Conclusions.



In this kind of modeling, basically we have three large issues to consider.
The response variable that we want to represent, in this case number of eggs.
It is clear that, based in ovitraps measurements, we could consider others
alternatives like proportion positive traps for example. The second one is the
independent variables that we choose like predictors (Ndvi, ndwi, etc). And
finally the method that to use to generate the model (Linear, Generalized
linear, logistic, neural networks etc.). As we said this paper dont focus on the
two first issues and then those are based in previous results/publications. Of
course these are matters of discussion and could be improved. Here, in this
contribution, we prefer leave these points untouched and focus our attention
on the possibilities of the different machine learning tools to model those
variables. In that sense it should be clear that here we are not closing the general problem of modeling vector populations.




An interesting point that appears in the results of all the models here
presented, is that that models fit well the main pattern but not necessarily
the large peaks. One hypothesis is that the vector population may disengage
the macro-environmental/climatic variables when conditions are optimal and,
again, be restricted when the environmental conditions get poorer. In fact,
it would be clear that, we can not hope to fit exactly this urban vector
population only based in large scale macro-environmental variables




An interesting point that appears in the results of all the models here
presented, is that that models fit well the main pattern but not ne-
cessarily the large peaks. One hypothesis is that the vector population
may disengage the macro-environmental/climatic variables when
conditions are optimal and, again, be restricted when the environ-
mental conditions get poorer. In fact, it would be clear that, we can not hope to fit exactly this urban vector population only based in large scale macro-environmental variables.





We found that K-Nearest Neighbour Regression (KNNR), MLP and
SVM improve predictive models of vector population based on satellite
derived environmental variables. The performance of these algorithms
could be improved substantially using a larger dataset. Although the used period is large in comparison with similar works on vector po- pulation, at the same time the used dataset is very small from the machine learning point of view.




###################### para discusión general

\par En este tipo de modelado, básicamente se tiene tres grandes cuestiones
  a considerar. La variable objetivo que queremos representar, en este caso
  el número de huevos. Es claro que, basado en las mediciones de ovitrampas,
  podríamos considerar otras opciones como, por ejemplo, la proporción de
  trampas positivas. La segunda es el conjunto de variables independientes
  que se seleccionan como predictores (NDVI, NDWI, etc). Y, finalmente, el
  método que se utiliza para generar el modelo (Lineal, Logístico, ANN, etc).
  Como ya dijimos, en este trabajo no nos concentramos en las primeras dos
  cuestiones si no que éstas fueron basadas en trabajos previos. Por supuesto
  que existe camino a discusión en ese sentido y pueden ser muy mejorables.
  Aquí, en esta contribución, preferimos no tocar estos puntos y enfocar
  nuestra atención a la capacidad de modelado de estas variables,
  de diferentes herramientas de Aprendizaje Automático.
  En ese sentido debería quedar claro que en este trabajo no estamos dando como cerrado el problema de modelado de poblaciones de mosquitos.
