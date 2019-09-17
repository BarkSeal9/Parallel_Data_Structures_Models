# Parallel Data Structures Models

A set of *C* programs for probabilistic modeling of parallel data structures.

## Parallel FIFO Queues Models

"Custom Queuing" is one of the strategies for handling the traffic in the router. The scheme proposed in [Sedgewick R. Algorithms in C++, Parts 1-4, 1998] can be considered as a generalization of this queue management method, where insertions of elements in queues are performed on the odd step, deletions of elements from queues on the even step.

"One after another" is a theoretical method of data structure organization proposed in [Sokolov A.V. Mathematical Models and Algorithms of the Optimal Control of Dynamic Data Structures (RUS), 2002]. Here, two cyclic queues move one after another in the joint memory space.

Simulation models are based on the Monte Carlo method.  
Mathematical models based on the regular Markov chains.

Models parameters are:

* **m** -- size of the available memory;  
* **s** (in *Sedg_x2.c*) or **ox** (in *\*_OAA_x2.c*) -- the number of memory units allocated to the first queue;  
* **x** -- size of the first queue;  
* **m-s** (in *Sedg_x2.c*) or **oy** (in *\*_OAA_x2.c*) -- the number of memory units allocated to the second queue;  
* **y** -- size of the second queue;  
* **z** (in *\*_OAA_x2.c*) -- the distance between the end of the first queue and the beginning of the second;  
* **p1** -- probability of insertion in the first queue;  
* **p2** -- probability of insertion in the second queue;  
* **p12** -- probability of parallel insertion in both queues;  
* **q1** -- probability of deletion from the first queue;  
* **q2** -- probability of deletion from the second queue;  
* **q12** -- probability of parallel deletion from both queues;  
* **r1** (first queue) **r2** (second queue) -- probability of absence of operation.

Utilizing these models, you can solve the problem of finding the optimal partition of memory between two queues [Sokolov A.V., Barkovsky E.A. Some Problems of Optimal Control of Two Parallel FIFO-queues // AIP Proceedings of ICNAAM 2014, 2015, V. 1648, P. 520003]. The optimality criterion is the minimum average share of lost (by the overflow) elements of the queues.

### Queues_Sim_Models:

**Sim_Cust_OAA_x2.c**  
Simulation model of two custom queues, moving one after another in a circle.

**Sim_Sedg_x2.c**  
Simulation model of two queues based on the Sedgewick method.

**Sim_Sedg_OAA_x2.c**  
Simulation model of two queues based on the Sedgewick method, moving one after another in a circle.

### Queues_Math_Models:

The programs below describe the generation of the transition probability matrix for the Markov chain.

**Math_Cust_OAA_x2.c**  
Mathematical model of two custom queues, moving one after another in a circle.

**Math_Sedg_x2.c**  
Mathematical model of two queues based on the Sedgewick method.

**Math_Sedg_OAA_x2.c**  
Mathematical model of two queues based on the Sedgewick method, moving one after another in a circle.

## Work-Stealing Deques Models

"Work-stealing" is one of the methods of parallel task balancing. In this method, each processor (or core) has a buffer of its tasks -- a double ended queue called "deque" [Knuth D. The Art of Computer Programming, Vol. 1, 2001]. A processor (or core) uses one end of the deque to add or delete tasks from it. The second end of the deque is accessible by other processors (or cores) whose buffer is empty, so they can "steal" (delete from it) "work" (tasks).

Simulation models are based on the Monte Carlo method.

Models parameters are:

* **m** -- size of the available memory;  
* **s**  -- the number of memory units allocated to the first deque;  
* **x** -- size of the first deque;  
* **m-s** -- the number of memory units allocated to the second deque;  
* **y** -- size of the second deque;  
* **o** (in *\*_Redi.c*) -- the number of elements to redistribute;  
* **p1** -- probability of insertion in the first deque;  
* **p2** -- probability of insertion in the second deque;  
* **p12** -- probability of parallel insertion in both deques;  
* **q1** -- probability of deletion from the first deque;  
* **q2** -- probability of deletion from the second deque;  
* **q12** -- probability of parallel deletion from both deques;  
* **pq12** -- probability of insertion in the first deque and parallel deletion from the second;  
* **pq21** -- probability of insertion in the second deque and parallel deletion from the first;  
* **r** -- probability of absence of operation.

Utilizing these models, you can solve the problem of finding the optimal partition or redistribution of memory between two deques [Sokolov A.V., Barkovsky E.A. The Mathematical Model and the Problem of Optimal Partitioning of Shared Memory for Work-Stealing Deques // Proceedings of PaCT 2015, 2015, V. 9251, P. 102-106]. The optimality criterion is the maximum average time before the memory overflow.

### Deques_Sim_Models:

**Sim_WS_1_x2_Part.c**  
Simulation model of two deques (work-stealing of one element). Problem of memory partition.

**Sim_WS_0.5_x2_Part.c**  
Simulation model of two deques (work-stealing of half the elements). Problem of memory partition.

**Sim_WS_1_x2_Redi.c**  
Simulation model of two deques (work-stealing of one element). Problem of memory redistribution.

**Sim_WS_0.5_x2_Redi.c**  
Simulation model of two deques (work-stealing of half the elements). Problem of memory redistribution.

## Author

Eugene A. Barkovsky

## License

This project is licensed under the MIT License -- see the LICENSE.md file for details.
