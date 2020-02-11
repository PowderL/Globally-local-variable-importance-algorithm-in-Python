## Globally-local-variable-importance-algoritm-in-python
- Two methods to calculate local variable importance with global models. It means that calcuate variable importance for subset of global data set using global model trained by global data set. I provide two files including 'todi.py' and 'meda.py' to realise these two methods. Both file include a class called 'gim' inheriting from 'RandomForestRegressor' in 'scikit-learn'.
- For example:
- l = lovim(500, max_features=0.3, n_jobs=-1))# just be same with the class 'RandomForestRegressor' in 'scikit-learn'.
- l.fit(X,Y)# fitting the model.
- local_variable importance = l.compute_feature_importance(X,Y,group_by = group_by, std='Y',n_jobs=-1) # calculate local variable importance.
