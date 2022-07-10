# Group Members
* Navam Shrivastav 2019A7PS0092H
* Sukrit Kumar 2019AAPS0231H
* Shrikrishna Lolla 2019AAPS0345H


# `HITS` function
This is the main function where the hubs and authorities scores are calculated for a given graph, computation is done using numpy for eigen vector calculation. Then the result is returned in form of a dictionary

# Running the code
1. Load the web graph initially using nx
2. Preprocess the graph if we want to run a complex query else move to step 3
3. Enter a query to find the root set
4. If the root set is not empty find the base set using the `getBaseSet()` function
5. Get a subgraph from the initially web graph using the subgraph function in nx
6. Call the HITS function on the subgraph (`HITS(subgraph)`) to get hub and authority scores for the given subgraph.
7. Optional: If required we can call the sorting cells, to get the top 3 hubs and authorities respectively