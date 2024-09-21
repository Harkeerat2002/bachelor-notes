# Slides:

![Lecture 04 (Graph Clustering)](../Slides/Lecture%2004%20(Graph%20Clustering).pdf)
# What is a Graph?
- ![[../../../Attachments/Pasted image 20231025101607.png|625]]
- Graphs are very flexible **data structures** used for modeling in many different fields. whenever there are **entities** and **relations** between them.
- Used in fields such as:
	- Bioinformatics
	- Social Science
	- HPS in Physics
## Understanding Graphs: Analysis and Algorithms
- How to find the most important node in Graph: <mark style="background: #FFF3A3A6;">PageRank</mark>
- How to divide the Graph in two or more parts that are balanced: <mark style="background: #FFF3A3A6;">Graph Partitioning</mark>
- How to find possible clusters in the graph: <mark style="background: #FFF3A3A6;">Graph Clustering</mark>
# Graph partitioning (Bisection): Problem Setup

- You and your friends want to organize a soccer match (whichever team game). There are a total of 10 people, and you need to form two teams.

- Here is the rule: each individual can specify **one preferred teammate** for the match. However, since you are all friends, **you are open to playing with anyone who selects you** as their preference. If your preference is not taken into account when assembling the teams, you feel disappointed.

How can you create the two teams in a way that maximizes everyone's happiness?

- ![[../../../Attachments/Pasted image 20231025102616.png|600]]
- ![[../../../Attachments/Pasted image 20231025102943.png|600]]
## How to solve the Partitioning Problem?
- **Two Families of Algorithms:**
	- Partitioning **with** nodal coordinates each node has x, y, z coordinates (Partition Space)
		- Coordinate Bisection
		- Recursive Coordinate Bisection
		- Inertial Partitioning
	- Partitioning **without** Nodal Coordinates
		- Spectral Methods
# Coordinate Bisection
- Partition the graph along hyperplanes orthogonal to the coordinate system
	![[../../../Attachments/Pasted image 20231025103230.png|575]]
- Divide the graph into two equal parts using a cutting plane orthogonal to a coordinate axis (Coordinate Bisection)
- Consider each partition as a new graph and reapply the Coordinate Bisection to it. (Recursive Call)
	![[../../../Attachments/Pasted image 20231025103335.png|346]]
# Inertial Partitioning
- **Generalization of the coordinate partitioning:**

