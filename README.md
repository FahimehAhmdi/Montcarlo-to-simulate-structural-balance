# Montcarlo-to-simulate-structural-balance


This project models how signed networks evolve toward structural balance using a Monte Carlo Metropolis algorithm. The simulation is applied to a collection of adjacency matrices representing signed interactions — such as those in social, biological, or brain networks.

---

###  Custom Order Parameters: `q` and `p`

To characterize the state of the network during simulation, we define two custom **statistical order parameters**:

####  `p` — Mean Link Strength
- Measures the average of all signed edges, normalized by the total magnitude of links.
- Indicates the **overall tendency** of the network:  
  - Positive `p`: cooperative or synchronized structure  
  - Negative `p`: conflictual or anti-correlated structure

####  `q` — Two-Star Structural Order Parameter
- Captures how aligned two-step paths are in the network (i.e., j → i → k).
- Reflects **structural balance** or **frustration** in indirect interactions:
  - High `q`: coherent indirect influence  
  - Low `q`: imbalance or noise in communication paths

These parameters help summarize the **macroscopic organization** of the network and are useful for detecting phase transitions or developmental changes.

---

###  Simulation Overview

The core function `balance_model()` performs the simulation:

- Applies the **Metropolis algorithm** to flip edges with probability based on local energy changes
- Runs across temperature steps `T = 0, 1, 2, 3` to explore different levels of randomness
- Repeats each step over multiple ensembles to ensure statistical reliability

At each temperature, the simulation tracks:
- `Energy`: Overall system energy
- `q`: Structural alignment
- `p`: Mean interaction value

---

###  Output

The function returns:

- `configuration`: Final networks for each temperature
- `Temp`: List of temperatures
- `E_mean`: Average energy at each temperature
- `q_mean`: Mean of structural order parameter
- `p_mean`: Mean link strength

---

###  Custom Statistical Order Parameters: q and p

This simulation framework defines two custom **order parameters** — `q` and `p` — to summarize the structural and statistical properties of signed networks.

####  `p` — Mean Link Strength
The `mean_of_links()` function calculates `p`, defined as:

> The sum of all signed edge values, normalized by the total edge magnitudes.

It captures the **average tendency of interactions**:
- Positive `p` → more cooperative or correlated network
- Negative `p` → more conflictual or anti-correlated network

####  `q` — Two-Star Structural Measure
The `q_func()` function defines `q` as:

> The normalized sum over all two-star motifs (`i ← j → k`), reflecting alignment of indirect paths.

This metric captures **global structural alignment** in the network and serves as an indicator of **imbalance or frustration**.

####  Why These Parameters?
Both `q` and `p` are treated as **statistical order parameters**, inspired by concepts in statistical mechanics and complex systems.
- each link is important ; p
- each link in a triangle depends on  the two other links so the q or two star parameter is important too! ;q
- Dynamical behavior during Monte Carlo simulations







