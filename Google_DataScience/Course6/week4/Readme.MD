# Glossary terms from week 4

### Terms and definitions from Course 6, Week 4
 
 **%%time:** A magic command that provides the runtime of the cell it’s entered in	to											

**AdaBoost:** (Refer to adaptive boosting)

**Adaptive boosting:** A boosting methodology where each consecutive base learner assigns greater weight to the observations incorrectly predicted by the preceding learner											

**Bagging:** A technique used by certain kinds of models that use ensembles of base learners to make predictions; refers to the combination of bootstrapping and aggregating											

**Base learner:** Each individual model that comprises an ensemble												

**Black-box model:** Any model whose predictions cannot be precisely explained												

**Boosting:** A technique that builds an ensemble of weak learners sequentially, with each consecutive learner trying to correct the errors of the one that preceded it												

**Bootstrapping:** Refers to sampling with replacement												

**Child node:** A node that is pointed to from another node												

**Cross-validation:** A process that uses different portions of the data to test and train a model on different iterations												

**Decision node:** A node of the tree where decisions are made												

**Decision tree:** A flowchart-like structure that uses branching paths to predict the outcomes of events, or the probability of certain outcomes												

**Ensemble learning:** Refers to building multiple models and aggregating their predictions									

**Ensembling:** (Refer to ensemble learning)

**Extrapolation:** A model’s ability to predict new values that fall outside of the range of values in the training data												

**Gradient boosting:** A boosting methodology where each base learner in the sequence is built to predict the residual errors of the model that preceded it

**Gradient boosting machines (GBMs):** Model ensembles that use gradient boosting										

**GridSearch:** A tool to confirm that a model achieves its intended purpose by systematically checking every combination of hyperparameters to identify which set produces the best results, based on the selected metric																			

**Hyperparameter tuning:** Refers to changing parameters that directly affect how the model trains, before the learning process begins																				

**Hyperparameters:** Parameters that can be set by the modeler before the model is trained												

**Leaf node:** The nodes where a final prediction is made												

**learning_rate:** In XGBoost, a hyperparameter that specifies how much weight is given to each consecutive tree’s prediction in the final ensemble													

**Magic commands:** Commands that are built into IPython to simplify common tasks; always begin with either “%” or “%%”

**Magics:** (Refer to magic commands)																			

**max_depth:** In tree-based models, a hyperparameter that controls how deep each base learner tree will grow									

**max_features:** In decision tree and random forest models, a hyperparameter that specifies the number of features that each tree randomly selects during training called “colsample_bytree” in XGBoost					

**min_samples_leaf:** In decision tree and random forest models, a hyperparameter that defines the minimum number of samples for a leaf node called “min_child_weight” in XGBoost									

**min_samples_split:** In decision tree and random forest models, a hyperparameter that defines the minimum number of samples that a node must have to split into more nodes

**min_child_weight:** In XGBoost models, a hyperparameter indicating that a tree will not split a node if it results in any child node with less weight than this value called “min_samples_leaf” in decision tree and random forest models															

**min_samples:** In DBSCAN clustering models, a hyperparameter that specifies the number of samples in an ε-neighborhood for a point to be considered a core point (including itself)										

**Model selection:** The process of determining which model should be the final product and put into production												

**Model validation:** The set of processes and activities intended to verify that models are performing as expected																							

**n_estimators:** In random forest and XGBoost models, a hyperparameter that specifies the number of trees your model will build in its ensemble												

**Random forest:** An ensemble of decision trees trained on bootstrapped data with randomly selected features												

**Root node:** The first node of the tree, where the first decision is made												

**Shrinkage:** (Refer to learning_rate)

**Tree-based learning:** A type of supervised machine learning that performs classification and regression tasks												

**Weak learner:** A model that performs slightly better than randomly guessing												

**XGBoost (extreme gradient boosting):** An optimized GBM package			
