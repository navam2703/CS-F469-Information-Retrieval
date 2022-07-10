# Group Members
* Navam Shrivastav 2019A7PS0092H
* Sukrit Kumar 2019AAPS0231H
* Shrikrishna Lolla 2019AAPS0345H

# Running the code
1. If adjacency matrix for a given graph is already known skip to step 2. Otherwise call the `getAdjacencyMatrix()` function to get the adjacency matrix for given nodes and edges as given in the pdf.
2. We will then transform the adjacency matrix to a probability translation matrix using the `convert_adj_to_prob()`, providing the adjacency matrix as the first argument and alpha value as the second argument. If P matrix is already known skip to step 3.
3. If we want to calculate the values using numpy call the `getLeftEigenVector()` on the computed P matrix
4. If we want to compute the values using the power iteration method we can call the `power_iteration()` method on the P matrix
5. To get the indices of the top 3 values, use `np.argsort()` on the result and get last n elements by indexing `[-n:]`. 