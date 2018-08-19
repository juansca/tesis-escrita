## Citas


Buen material de SVM: http://mcminis1.github.io/blog/2014/05/10/intuition-for-SVR/

@article{random_forest,
  title={Random forests},
  author={Breiman, Leo},
  journal={Machine learning},
  volume={45},
  number={1},
  pages={5--32},
  year={2001},
  publisher={Springer}
}


@article{scikit-learn,
 title={Scikit-learn: Machine Learning in {P}ython},
 author={Pedregosa, F. and Varoquaux, G. and Gramfort, A. and Michel, V.
         and Thirion, B. and Grisel, O. and Blondel, M. and Prettenhofer, P.
         and Weiss, R. and Dubourg, V. and Vanderplas, J. and Passos, A. and
         Cournapeau, D. and Brucher, M. and Perrot, M. and Duchesnay, E.},
 journal={Journal of Machine Learning Research},
 volume={12},
 pages={2825--2830},
 year={2011}
}



@inproceedings{sklearn_api,
  author    = {Lars Buitinck and Gilles Louppe and Mathieu Blondel and
               Fabian Pedregosa and Andreas Mueller and Olivier Grisel and
               Vlad Niculae and Peter Prettenhofer and Alexandre Gramfort
               and Jaques Grobler and Robert Layton and Jake VanderPlas and
               Arnaud Joly and Brian Holt and Ga{\"{e}}l Varoquaux},
  title     = {{API} design for machine learning software: experiences from the scikit-learn
               project},
  booktitle = {ECML PKDD Workshop: Languages for Data Mining and Machine Learning},
  year      = {2013},
  pages = {108--122},
}


@MISC{svm_tutorial,
    author = {Alex J. Smola and Bernhard Schölkopf},
    title = {A tutorial on support vector regression },
    year = {2004}
}


tag: least_square
Goldberger, Arthur S. (1964). "Classical Linear Regression". Econometric Theory. New York: John Wiley & Sons. pp. 156–212 [p. 158]. ISBN 0-471-31101-4.


tag: knnr
Altman, N. S. (1992). "An introduction to kernel and nearest-neighbor nonparametric regression". The American Statistician. 46 (3): 175–185. doi:10.1080/00031305.1992.10475879.

## Ideas

- Hablar del machine Learning en general, un poco de historia y
de tecnisismos  hasta la actualidad.
- Hablar un poco de machine learning en aplicaciones sociales.
- Hablar de machine learning en Geociencias
------------- parte técnica ----------
- Scikit learn ✓✓
- Desarrollar más en profundidad:
  - Regresión Lineal:
        - común ✓
        - ridge ✓
  - SVR ✓
  - Multilayer perceptron ✓
  - KNN ✓✓
  - DTR ✓✓
  - Random Forest ✓✓
- Irace



### SciKit learn

This project was started in 2007 as a Google Summer of Code project by David Cournapeau. Later that year, Matthieu
Brucher started work on this project as part of his thesis.
In 2010 Fabian Pedregosa, Gael Varoquaux, Alexandre Gramfort and Vincent Michel of INRIA took leadership of the
project and made the first public release, February the 1st 2010. Since then, several releases have appeared following
a ~3 month cycle, and a thriving international community has been leading the development

------


scikit-learn is a free-to-use machine learning module for Python built on SciPy. It is a straightforward and effective tool for data mining and data analysis. Because it is released with a BSD license, it can be used for both personal and commercial reasons.

With scikit-learn, users are able to conduct a variety of tasks under different categories like model selection, clustering, preprocessing, and more. The module provides the means to complete implementations.

Moreover, scikit-learn has an extensive use. It is being utilized by big companies in different industries like music streaming, hotel bookings, and more. This means that users can integrate algorithms in the platform to their own applications.


Free Platform

Because scikit-learn is released with a BSD license, it can be used for free by everyone. This license has minimal restrictions; therefore, users can utilize it to design their applications and platforms with little worry over limitations.

Industrial Use

scikit-learn is a helpful platform that can predict consumer behavior, identify abusive actions in the cloud, create neuroimages, and more. It is being used extensively by commercial and research organizations around the world, a testament to its ease of use and overall advantage.

Collaborative Library

scikit-learn began as a one-man mission but now it is being built by numerous authors from INRIA spearheaded by Fabian Pedregosa and individual contributors who are not attached to teams or organizations. This makes the module a well-updated one, releasing updates several times a year. Users can also look forward to assistance from an international community, in case they have queries or if they hit snags in development using the module.

Ease of Use

Commercial entities and research organizations alike have employed scikit-learn in their processes. They all agree that the module is easy-to-use, thereby allowing them to perform a multitude of processes with nary a problem.

API Documentation

scikit-learn ensures that users old and new alike get the assistance they need in integrating the machine learning module into their own platforms. That is why a documentation detailing the use of its API exists that users can access anytime on the website. This makes certain developers can implement machine learning algorithms offered by the tool seamlessly.

### Multilayer Perceptron
http://scikit-learn.org/stable/modules/neural_networks_supervised.html#mathematical-formulation

### Decision Tree
Decision Trees (DTs) are a non-parametric supervised learning method used for classification and regression. The goal is to create a model that predicts the value of a target variable by learning simple decision rules inferred from the data features.


Decision tree builds regression or classification models in the form of a tree structure. It breaks down a dataset into smaller and smaller subsets while at the same time an associated decision tree is incrementally developed. The final result is a tree with decision nodes and leaf nodes. A decision node (e.g., Outlook) has two or more branches (e.g., Sunny, Overcast and Rainy), each representing values for the attribute tested. Leaf node (e.g., Hours Played) represents a decision on the numerical target. The topmost decision node in a tree which corresponds to the best predictor called root node. Decision trees can handle both categorical and numerical data.

http://scikit-learn.org/stable/modules/tree.html#regression-criteria

ahí están las citas también



### Random Forest
http://www.jmlr.org/papers/volume13/biau12a/biau12a.pdf  Página 2

### KNN (Regression)
The principle behind nearest neighbor methods is to find a predefined number of training samples closest in distance to the new point, and predict the label from these. The number of samples can be a user-defined constant (k-nearest neighbor learning), or vary based on the local density of points (radius-based neighbor learning). The distance can, in general, be any metric measure: standard Euclidean distance is the most common choice.


Predictions are made for a new instance (x) by searching through the entire training set for the K most similar instances (the neighbors) and summarizing the output variable for those K instances. For regression this might be the mean output variable, in classification this might be the mode (or most common) class value.

When KNN is used for regression problems the prediction is based on the mean or the median of the K-most similar instances

poner ecuación

y^estimada(x) = 1/k * sumatoria(y_j tal que j \in knn(x))
y^estimada es la y con ~ arriba

### SVM
A support vector machine constructs a hyper-plane or set of hyper-planes in a high or infinite dimensional space, which can be used for classification, regression or other tasks. Intuitively, a good separation is achieved by the hyper-plane that has the largest distance to the nearest training data points of any class (so-called functional margin), since in general the larger the margin the lower the generalization error of the classifier.

svm_hiperplane.png

#### SVR
Support vector regression (SVR) is a fast and accurate way of interpolating data sets. It is useful when you have an expensive function you want to approximate over a known domain. It learns quickly and is systematically improvable. Variants of SVR are used throughout science including Krigging and Gaussian processes (GP).

Support vector regression is a generalization of the support vector machine to the regression problem. Technically, it can be labelled as a supervised learning algorithm. It requires a training set, \(\mathcal{T} = \{ \vec{X}, \vec{Y} \}\) which covers the domain of interest and is accompanied by solutions on that domain. The work of the SVM is to approximate the function we used to generate the training set, \[ F(\vec{X}) = \vec{Y}\]. In my mind, it's just an interpolation scheme.

In a classification problem, the vectors \(\vec{X}\) are used to define a hyperplane that seperates the two different classes in your solution. In SVR, these vectors are used to perform linear regression. The vectors closest to your test point, or decision boundary are the ones we refer to as support vectors. For regression, it turns out that all of the vectors are support vectors. We can evaluate our function anywhere, so any vectors could be closest to our test evaluation location.

http://scikit-learn.org/stable/modules/svm.html#svr



### Lineales

#### Ordinary least squares Linear Regression.
https://en.wikipedia.org/wiki/Ordinary_least_squares#Simple_linear_regression_model

#### Ridge
Ridge Regression
is a technique for analyzing multiple regression data that suffer from multicollinearity. When
multicollinearity occurs, least squares estimates are unbiased, but their variances are large so they may be far from
the true value. By adding a degree of bias to the regression estimates, ridge regression reduces the standard errors.
It is hoped that the net effect will be to give estimates that are more reliable. Another biased regression technique,
principal components regression, is also available in
NCSS
. Ri
dge regression is the more popular of the two
methods

https://ncss-wpengine.netdna-ssl.com/wp-content/themes/ncss/pdf/Procedures/NCSS/Ridge_Regression.pdf página 3
http://scikit-learn.org/stable/modules/linear_model.html#ridge-regression
