# TPS-Oct-2021

The dataset this month is huge with millions rows and over two hundreds features, hence only 5-folds is adopted with 5-seeds aggregation for each model.

Level 0: Base tree models of LGB, XGB. XGB is built with leafwise and depthwise growth policies. Several different parameters from other Kagglers are also used to diversify. Several CatB and HGB models are added for diversity.

Level 1: Stacking on level 0 predictions with metamodels of LGB, XGB, GNB, NN, Ridge and RF. RF is implemented by XGB with special hyperparameters chosen. Each of them are fitted on different inputs based on performance. There are four possible combinations of inputs based on best/all models with raw/average inputs.

Level 2: Stacking on level 1 and level 0 predictions by Logistic and LGB. The final outputs is re-input to the same model for training, the loop is iterated until no further improvement in the CV. Power averaging on the two final models to further boost performance.
