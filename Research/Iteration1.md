## Iteration 1: Improve on Distance

**Goal**: Investigate distance improvement posibility in SA path finding through AI

### Result 1
SA global distance minimization is *equivalent to TSP*: 
- It can be transformed to a TSP by adding an origin city with distance 0 to every other city.
  - Ref: https://cs.stackexchange.com/questions/43549/what-tsp-variant-doesnt-return-to-start-point
  
### Result 2
A *very low cost aproximation* must be used to pah finding.
- As TSP is NP-hard, it can only be solved for many nodes with approximate
algorithms. Thus for practical purposes, some kind of formula must be used
to mesure the performance, instead of a comparison to the actual optimal
distance. This formula is the lower bound given by the Held-Karp algorithm,
which is O(n*2^n)).
  - Ref: http://dimacs.rutgers.edu/Challenges/TSP/papers/HKsoda.pdf
- Approximate algorithms for TSP can be classified in 3:
  - Costly good approximations: Are the ones that strive for
  the lowest distance, but keeping tractability. One of them
  is Christofides with time complexity of O(n^3) and 
  distance at most 1.5 the optimum, but with average over randome
  euclidean instances of 1.1 Held-Karps lower bound.
    These algorithms are used for graphs of nearly 100 nodes,
  not reaching 1000 node cases. Google has recently published
  one of this kind, beating Christofides and others, but not
  getting much faster.
    - https://arxiv.org/pdf/1611.09940.pdf
  - Medium approximations: These strive for a complexity of
  nearly O(n^2), with theoretically at most 2 times the optimum 
  distance, and do not get very far from 10000 nodes examples.
    - https://web.tuke.sk/fei-cit/butka/hop/htsp.pdf
  - Fast approximations: They have nearly linear time, but with
  no constant theorical bound on the distance (log(N) times the optimum).
  Fortunately,their average is nearly 1.25 Held-Karps lower bound.
  And they can face problems with 10000000 nodes in less than an hour.
  One of them is Nearest Neighbor search using a tree for spatial partition.
    - http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.92.1635&rep=rep1&type=pdf
- Only the last kind of these algorithms is suitable for SA within its 
current performance standards.

### Result 3
Performance improvement should be centered in the *trade-off between optimization parameters*.
- SA distance improvement with AI would require partial observability treatment techniques to
address current time cost standards. Moreover, training over one particular example would
be practically inexistent, therefore global considerations would be strongly limited. So
improvement warranties are very poor.
- As can be seen, distance used by algorithms used are quite stable, making earnings in distance
of only 3 percent very optimistic.
- Trade-off between the different optimization parameters still presents appealing features due to
their reduced quantity at a specific node and due to the current rather ad-hoc treatment.
    
    
