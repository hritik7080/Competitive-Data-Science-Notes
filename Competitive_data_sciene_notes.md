# Data Science Competition winning techniques

## Platforms:
- Kaggle
- Driven Data
- CrowdAnalityx
- CodaLab
- DataScienceChallenge.net
- DataScience.net
- Single-comptetion sites(like KDD, VizDooM)

## Facts:
- Linear Model splits space into 2 subspaces with a hyperplane.
- Tree-based methods splits spaces into boxes and use constant the predictions in every box.
- KNN methods heavily rely in how to measure points "closeness". The assusmption is close objects are likely to have same labels. It heavilyrelies in how to measure point closeness.
- Feed forward NNs produce smooth non-linear decision boundary. 
- The most powerful methods are GBDT and NNs. but not always.

## Difference between RandomForest and ExtraTrees models
ExtraTrees classifier always tests random splits over fraction of features(in contrast to Random Forest, which tests all possible splits over fraction of features.) That's why they are called extra/randomized trees.

Random Forest :-
https://www.datasciencecentral.com/profiles/blogs/random-forests-explained-intuitively

Gradient Boosting :-
http://arogozhnikov.github.io/2016/06/24/gradient_boosting_explained.html

KNN :-
https://www.analyticsvidhya.com/blog/2018/03/introduction-k-neighbours-algorithm-clustering/

## Imp. points regarding trees
- In random forest, if we drop first and last tree, the model we average 100 similar performing trees, trained independently. So the order of trees does not matter in RandomForest and performance drop will be very similar on average.
- In GBDT if we drop first and last tree, the  model we have sequence of trees, each improve predictions of all previous. So, if we drop first tree — sum of all the rest trees will be biased and overall performance should drop. If we drop the last tree -- sum of all previous tree won't be affected, so performance will change insignificantly (in case we have enough trees). case1 performance will drop more than in the case2.
- In a Random forest, each tree in forest is independent from the others, so two RF with 500 trees is essentially the same as single RF model with 1000 trees.

## ML Workflow
![image][https://raw.githubusercontent.com/hritik7080/Competitive-Data-Science-Notes/master/images/ml_map.png]

## Numeric Feature

### Feature Processing
- Regularization impact turns out to be proportional to feature scale.
- Gradient Desent method can go crazy without proper saling.

Different feature scaling ruslt in different models quality. 

Also we can use rank transformation, linear models, KNN, neural networks can benefit from this kind of transformation.

Rank can be imported as a random data function from scipy. 

scipy.stats.rankdata

One more important note about the rank transformation is that to apply to the test data,
you need to store the creative mapping from features values to their rank values.
Or alternatively, you can concatenate,
train, and test data before applying the rank transformation.

Some more transformation for non tree based models specially neural networks :
- Log transfom
np.log(1+x)
- Raising to the power < 1:
np.sqrt(x + 2/3)

Another important moment which holds true for all preprocessings is that sometimes,
it is beneficial to train a model on
concatenated data frames produced by different preprocessings,
or to mix models training differently-preprocessed data. Again, linear models, KNN,
and neural networks can benefit hugely from this. 

### Feature Generation

Ways to proceed:
- prior knowledge
- EDA

Sometimes, if we have prices of products as a feature,
we can add new feature indicating fractional part of these prices.
For example, if some product costs 2.49,
the fractional part of its price is 0.49.
This feature can help the model utilize
the differences in people's perception of these prices. 
