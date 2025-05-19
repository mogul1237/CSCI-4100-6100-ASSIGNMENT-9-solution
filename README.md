# CSCI-4100-6100-ASSIGNMENT-9-solution


Download Here: [CSCI 4100/6100 ASSIGNMENT 9 solution](https://jarviscodinghub.com/assignment/csci-4100-6100-assignment-9-solution/)

For Custom/Original Work email jarviscodinghub@gmail.com/whatsapp +1(541)423-7793

End to End Learning with Regularization and Validation
In this assignment, you will address the learning problem for predicting ‘Digit 1’ from ‘not Digit 1’.
Raw Data −→ Features −→ Learn −→ g −→ Estimate Eout(g)
You will use all the digits available on the class web site and your two features that you constructed in an earlier assignment. yn = +1 if the data point is ‘Digit 1’ and yn = −1 otherwise.
1. Combine the training and test data into a single data set.
2. Use your feature construction algorithm to create two features for each data point.
3. Normalize your features as follows. For each data point, shift the ﬁrst feature by a shift and then rescale the ﬁrst feature by a scale. You must determine the shift and scale so that the minimum feature value is −1 and the maximum feature value is +1. Repeat this for your second feature. So now you have a new pair of features where each feature (for every data point) is in the range [−1,1]. This process is an example of input normalization.
4. Randomly select 300 data points for your data set D. Put the remaining data into a test set Dtest.
5. Do not look at Dtest until you have created your ﬁnal hypothesis g and are ready to estimate Eout(g).
We will treat this problem as a regression problem with real valued targets ±1 until it is time to output our ﬁnal classiﬁcation hypothesis. At that point our ﬁnal classiﬁcation function will be sign(g). The polynomial feature transform is
(x1,x2) → (1,×1,x2,x2 1,x1x2,x2 2,×3 1,×2 1×2,x1x2 2,×3 2,×4 1,×3 1×2,…).
As discussed in class, this would create ‘non-orthogonal’ features, which can cause a problem for algorithms like the pseudo-inverse regression algorithm if the columns in the data matrix become too dependent. An ‘orthogonal’ polynomial transform is given by
(x1,x2) → (1,L1(x1),L1(x2),L2(x1),L1(x1)L1(x2),L2(x2),L3(x1),L2(x1)L1(x2),…),
where in each feature we replace xk i with Lk(xi) and Lk(·) is the kth order Legendre transform. See Problem 4.3 in LFD for a recursive expression that deﬁnes the Legendre polynomials from which you can develop a quick algorithm to compute the Lk(x) for any input x. We will use the pseudo-inverse linear regression algorithm with weight decay regularization for learning, which corresponds to minimizing Eaug(w) = Ein(w) + λwtw, and Ein(w) is the sum of squared errors. Recall that the learned linear regression weights are
wreg(λ) = (ZtZ + λI)−1Zty,
where Z ∈ RN× ˜ d is the matrix of transformed features and wreg ∈ R ˜ d is the regularized weight vector.
1
Do the following problems to end up with your ﬁnal hypothesis g.
1. (100) 8th order Feature Transform. Use the 8th order Legendre polynomial feature transform to compute Z. What are the dimensions of Z?
2. (100) Overﬁtting. Give a plot of the decision boundary for the resulting weights without any regularization (λ = 0). Do you think there is overﬁtting or underﬁtting?
3. (100) Regularization. Give a plot of the decision boundary for the resulting weights with λ = 2. Do you think there is overﬁtting or underﬁtting?
4. (200) Cross Validation. Use leave-one-out cross validation to estimate Ecv(λ) for
λ ∈ {0,0.01,0.02,…,2}.
The upper limit 2 is arbitrary – use your judgement to pick one that is reasonable (you may need to increase λmax, depending on your features). Ecv(λ) estimates Eout for regularization parameter λ, when learning with N −1 data points. You can use the formula in Equation (4.13) of LFD to eﬃciently compute Ecv(λ).
Plot Ecv(λ) versus λ, and on the same plot, Etest(wreg(λ)) (the regression error on the test set).
Comment on the behavior of Ecv in relation to Etest.
5. (100) Pick λ. Use the cross validation error to pick the best value of λ, call it λ∗. Give a plot of the decision boundary for the weights wreg(λ∗).
6. (100) Estimate Eout. Use the classiﬁcation error Etest(wreg(λ∗)) to estimate Eout for your ﬁnal hypothesis g. What is your estimate of Eout for separating ‘Digit 1’ from ‘Not Digit 1’?
7. (100) Is Ecv biased? Is Ecv(λ∗) and unbiased estimate of Etest(wreg(λ∗))? Explain.
8. (200) Data snooping. Is Etest(wreg(λ∗)) an unbiased estimate of Eout(wreg(λ∗))? Explain. If it is not an unbiased estimate, how can what you did be ﬁxed so that it is?
[Hint: Where has there been data snooping?. Data snooping occurs if the data used to estimate the performance of g in any way aﬀected the selection of g as the ﬁnal hypothesis. When you have ﬁgured this one out, you will have understood one of the most subtle forms of data snooping. ]
