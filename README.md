# Brain-tissue-segmentation
Classical  and deep learning approaches for segmenting of different tissue types in MRI scans of the Brain

Segmentation of different tissues from MRI scans of the brain is an important step for further downstream applications such as disease prediction, classification or brain age estimation.

The goal of the project is to implement classical and deep learning approaches for segmentation of different tissue types in MRI scans of the brain, i.e., background, cerebrospinal fluid (CSF), white matter (WM), and gray matter (GM). We provide data from a total of 652 healthy subjects, that is split into different development sets and a hold-out test set.

## 1 Unsupervised Segmentation

I chose the k-mean algorithm as our first unsupervised method. Selecting the appropriate number of clusters (K) at first. In our case, it is 4 for grey matter, white matter, CSF, and background. Then it calculates the distance between each date point and the closest centroid in the feature space. After this step, it will update the centroid. The algorithm iterates these steps until the result converges.

I chose the Gaussian Mixture as our second unsupervised method. The Gaussian Mixture Model assumes that the data is generated from a mixture of several Gaussian distributions, each characterized by its mean, covariance matrix, and weight. It computes the probability of 
each data point belonging to each Gaussian based on the current model parameters. Then it updates the model parameters by maximizing the likelihood of the data given the responsibilities

## 2 Deep Supervised Segmentation

