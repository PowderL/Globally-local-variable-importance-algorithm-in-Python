glvi
============

**glvi** is a Python module for machine learning built on top of **scikit-learn** and is distributed under the MIT license.

**glvi** was developed by Mr. Li for evaluating sptiotemporal heterogeneity of variable imporance through a global model 

built on a large time-space scope.

**glvi** inherits from the RandomForestRegressor in **scikit-learn**. If you want to use **glvi** to estimate local variable importance, 

model fitting is necessary. But at present, using a fitted random forest model from RandomForestRegressor is not supported. To 

accelerate the process, parallel is provided which is same with the parallel in **scikit-learn**. The parallel process can be 

implemented by the parameter of ``n_jobs`` which just is consistent with the **scikit-learn**.

**glvi 0.1.5 and later was not supporting Python 2.7 and Python 3.4.**
glvi 0.1.5 and later require Python 3.5 or newer.

glvi requires:

- Python (>= 3.5)
- NumPy (>= 1.11.0)
- SciPy (>= 0.17.0)
- Pandas (>= 0.24.0)
- Joblib (>= 0.11.0)
- Scikit-learn (>= 0.20.0)
User installation
~~~~~~~~~~~~~~~~~

Install from github is available but is not recommended. If you already have a working installation of numpy, scipy, pandas and scikit-learn, the easiest way to install glvi is using ``pip``   ::
	
	pip install -U glvi

Or build from source for Windows ::

	python setup.py install

For Linux ::
	
	pip install --verbose

User guide
~~~~~~~~~~~~~~~~~

Compute local variable importance based on decrease in node impurity ::

	from glvi import todi
	r_t = todi.lovim(500, max_features=0.3, n_jobs=-1)
	r_t.fit(train_x, train_y)
	local_variable_importance = r_t.compute_feature_importance(X,Y,partition_feature = partition_feature, norm=True,n_jobs=-1)
	
or compute local variable importance based on decrease in accuracy ::

	from glvi import meda
	r_m = meda.lovim(500, max_features=0.3, n_jobs=-1)
	r_m.fit(train_x, train_y)
	local_variable_importance = r_m.compute_feature_importance(X,Y,partition_feature = partition_feature, norm=True,n_jobs=-1)
	
Development
~~~~~~~~~~~~~~~~~

To acquire lower computation cost, we also developed a another package called **forest-gis** using **Cython** to accelerate the process.
Please refer to : https://github.com/PowderL/Tree-based-machine-learning-for-gis.
