


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
