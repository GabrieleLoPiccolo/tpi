# TPI
## Introduction
This report analyzes the "TPI" algorithm described in the paper "Whom to Befriend to Influence People", written in 2016 by Gennaro Cordasco, Luisa Gargano, Manuel Lafond, Lata Narayanan, Adele A Rescigno, Ugo Vaccaro and Kangkang Wu. The pseudo-code exposed in the paper has been converted into Python (version 3.7) and uses the SNAP (Stanford Network Analysis Project) library. The dataset used is a reduced version of 60050 arches and 37873 nodes of the "YouTube social network and ground-truth communities" dataset, a dataset that analyzes the relationships between users of the popular video sharing site YouTube.
## Problem
Given a social network represented with a graph G = (V, E, t), with V nodes of the network, E edges which represent the connections between the nodes of the network and t activation threshold function for each node of the network, we want to find an "optimal pervasive link set", that is a set of nodes that is able to "activate" the entire network. This problem has application in viral marketing, in which a particular set of users of a social network (seed set) must be selected such as to be able to influence as many other users as possible in order to make them buy a new product or service. Users included in the seed set are provided with an incentive (partial, such as a discount coupon or total such as a free sample) in order to influence them and induce them to talk about the product to their contacts to take advantage of the word of mouth effect. Formally, given a social network G = (V, E, t), where t is the threshold function on V, and a set of external nodes U, it finds an optimal pervasive link set for (G, U).
## Algorithm
A step-by-step analysis of the algorithm is available in Section 3 of the document Relazione_Finale.odt
## Test execution
After loading the graph, the principle of "deferred decision" is applied: for each arc of the graph a pseudorandom number between 0 and 1 is generated. If the generated number is less than the probability present on the arc (ie the node infected with less likely than required), the arc is removed. This can be applied uniformly (the probability of the arc is chosen pseudo-randomly, if this value is greater than the probability of removal, also chosen pseudo-randomly, the arc is removed) or proportional ( the probability of the arc is 1 / the degree of the node, if this value is greater than the probability of removal, chosen in a pseudo-random way, the arc is removed). The Tresholds are instead calculated in 3 different methods: constant (equal to 2), random (a pseudo-random value between 1 and 5 is chosen) and proportional to the degree (if the degree is different from 0 the threshold is equal to ( 1 / (degree of the node + 5)) * (number of arcs / number of nodes), if this value is less than 1 or the degree is equal to 0 the threshold is 5). Six different combinations are performed in which the principle of deferred decision and the assignment of the threshold are varied. Each combination is repeated 10 times and the average of the number of nodes to be influenced and the average of the incentive to spend on these nodes is calculated.
## Results
The results are attached in the Excel document Test_Result.xlsx
## External Links
Whom to Befriend to Influence People: https://link.springer.com/chapter/10.1007/978-3-319-48314-6_22 <br>
SNAP: https://snap.stanford.edu/ <br>
YouTube social network and ground-truth communities: https://snap.stanford.edu/data/com-Youtube.html
