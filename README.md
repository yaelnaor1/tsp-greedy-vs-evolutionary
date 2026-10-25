# Traveling Salesman – Greedy vs. Evolutionary Algorithm

Lab 2 of the **Computational Intelligence** course (2024, Politecnico di Torino, Prof. Giovanni Squillero).

## The problem
The Traveling Salesman Problem (TSP): find the shortest route that visits every city in a country exactly once and returns to the start. Distances are real geographic distances (geodesic, in km) between cities.

## My approach
I implemented and compared three solvers:

1. **Greedy – Nearest Neighbor:** start from a city and always go to the closest unvisited one.
2. **Greedy – Shortest Segments:** sort all city pairs by distance and add the shortest edges that don't create a city with more than two connections or close a loop too early (a Kruskal-like approach).
3. **Evolutionary Algorithm (EA):**
   - Population of random routes
   - Tournament selection
   - **Inver-Over crossover**
   - **Scramble** and **inversion** mutations
   - Elitism, plus injecting new random routes every 100 generations to keep diversity

## Results (total route length, km)
| Country | Cities | Nearest Neighbor | Segments | EA |
|---------|--------|------------------|----------|-----|
| Vanuatu | 8 | 1,475.5 | 1,475.5 | **1,396.3** |
| Italy | 46 | 4,436.0 | 4,730.1 | **4,291.1** |
| Russia | 167 | 42,334.2 | 39,758.5 | **34,803.2** |
| USA | 326 | 48,050.0 | 45,845.9 | **41,850.2** |

The EA beats both greedy methods in every case, and the gap grows with the number of cities. China is also included in the notebook.

## How to run
Open `tsp.ipynb` in Jupyter or Google Colab.
Requirements: `numpy`, `pandas`, `geopy`, `icecream`.
The notebook reads the course's city files (`vanuatu.csv`, `italy.csv`, `russia.csv`, `us.csv`, `china.csv`), available in the [course repository](https://github.com/squillero/computational-intelligence).
