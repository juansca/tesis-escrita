


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
