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

###  Project Structure

```bash
├── balance_model.py        # Monte Carlo simulation
├── order_parameters.py     # q_func() and mean_of_links()
├── triangle_analysis.py    # Triangle-based balance classification
├── main_simulation.py      # Example script to run all components
├── README.md               # You are here!
