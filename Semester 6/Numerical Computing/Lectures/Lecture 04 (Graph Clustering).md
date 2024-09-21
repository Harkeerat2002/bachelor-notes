![[Lecture 04 (Graph Clustering).pdf]]
# Clustering Algorithms
- ## Flat Algorithms
	- No explicit structure that would relate clusters to each other.
	- Usually start with a random partitioning
		- K-means clustering
		- Model Based Clustering
	- ### Spectral Clustering
- ## Hierarchical Algorithms
	- Bottom-up, agglomerative
	- Top-down, divisive

# Hierarchical Clustering 
- **Agglomerate**: To collect or gather into a cluster or mass.
- Treat each data entry as a singleton cluster, and then successively merge pairs of clusters until all clusters have been merged into a single one.
- Typically visualized as a dendogram:
	- *Horizontal Line:* cluster mere.
	- *Y-axis:* The similarity between clusters
- ![[../../../Attachments/Pasted image 20231101145610.png|423]]
- **Cut the Hierarchy at:**
	- Large gap between two successive similarities -> natural clusters.
	- Prespecified level of similarity.

# Graph Theory Introduction
- **Cliques:** Subsets of connected nodes, each pair of elements is connected
- **Clusters:** Highly connected groups of nodes
- **Centrality:** Important Nodes and hubs
- **Outliers:** Unimportant Nodes
- ## Graph Construction - Connectivity Matrix **G**
	- **Goal:** Model the local neighborhood relationships between the data points.
		- **ε-neighborhood Graph**
			- Identify a threshold value ε, and include edges if the distance between two nodes is smaller or equal to ε.
		- **k-nearest Neighbors (k-nn)**
			- Insert edges between a node and its k-nearest neighbors
			- Each node is connected to (at least) k nodes.
		- **Fully connected**
			- An edge between every pair of nodes
			- This is a full graph
- ## Graph Construction - Similarity Matrix **S**
	- **Goal:** Define a similarity function on the data. Ensure that the local neighborhoods promoted by this similarity function are "meaningful".
	- **Example:** In this notes check whether documents with ah high similarity score indeed belong to the same text category
	- **Common Case:** Data points in the Euclidean Space $\mathbb{R}^d$ -> default candidate the Gaussian similarity function
		- ![[../../../Attachments/Pasted image 20231101151510.png]]
- ## Graph Construction
	- **S ⊙ G = W**
	- ### Algorithm 1 ε-Connectivity Graph
