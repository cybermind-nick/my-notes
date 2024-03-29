## 4 Feb, 2024
While learning the module on sample variance on Brilliant today, when I was calculating the estimator based off of the formular
$$\frac{1}{n}\sum_{i=1}^n(X_i - \bar{X})^2$$
and I noticed that I simply added the true values for the random variable $X(x = 1 \space else \space x = 0 \space otherwise)$  with the _popn mean_ $\mu$ being ___$\frac{3}{5}$ 

By simply adding
$$\frac{2}{5}+\frac{2}{5}+\frac{2}{5}$$ for the sample poll drawn where n=5, I got the actual answer $\frac{6}{5}$ 
The actual solution looks more like this
$$(1-\frac{3}{5})^2+(0-\frac{3}{5})^2+(0-\frac{3}{5})^2+(1-\frac{3}{5})^2+(1-\frac{3}{5})^2$$
for $X_1=1,X_2=0,X_3=0,X_4=1,X_5=1$
as a sample poll for pizza

Inspect why this is true and what is the underlying invariant property that makes this possible, or if this is just a fluke of this particular experiment

Use a dataset with $\mu = \frac{4}{9}$ and apply the standard approach and the shortcut. See, what happens