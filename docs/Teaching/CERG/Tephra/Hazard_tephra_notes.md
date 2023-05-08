password: askja1875

## Tephra hazard assessment exercise

### Question 1: Wind conditions

1. > **Visualize these wind patterns in the context of a hazard assessment. What is the main wind direction? How will that affect tephra dispersal?**
      - Below 1 km, most of the dispersal is towards SW, with a slightly more S component for the month of May 
  
2. > **Do you notice any seasonality? If yes, identify during what months it happens.**
      - Summer months have the lowest wind velocities below the tropopause

--- 

### Question 2: ESP


1. > **Analyse the distributions of sampled ESP. For each ESP, discuss:**
   > - **From what distribution have each ESP been sampled from?**
   > - **What *prior knowledge* do these distribution reflect?**

     - **Height:** logarithmic &rarr; small heights have more probability of occurrence 
     - **Mass:** gaussian &rarr; most likely mass ~4, but symmetric error 
     - Other: uniform, equal probabilities of occurrence


--- 

### Question 3: Probability calculation

1. > **The [previous module](Hazard_probabilistic2.md) has introduced how to compute *exceedence probability* for tephra accumulation. Based on the 10 simulations below for pixel $x,y$, what are the probabilities of this pixel to suffer tephra accumulations exceeding**:

    - 50 $kg/m^2$ → $10/10 = 100\%$
    - 100 $kg/m^2$ → $7/10 = 70\%$
    - 150 $kg/m^2$ → $2/10 = 20\%$

2. > **Similarly, we also learned how to estimate a **typical accumulation** associated with a given probability of occurrence. The figure below shows the [survivor function](Hazard_probabilistic2.md#hazard-outputs) for the data in the table above. Estimate the typical load associated with probability values of:**

    - 25% → ~122 $kg/m^2$
    - 75% → ~85 $kg/m^2$

--- 


### Question 4: Hazard curves

| Vent   | Load(P=25%) | Load(P=75%) | P(collapse)  25% | P(collapse)  75% |
|--------|-------------|-------------|------------------|------------------|
| Vent 1 | 125         | 48          | ~0               | ~0               |
| Vent 2 | 1500        | 972         | 100              | ~100             |
| Vent 3 | 256         | 120         | ~0.2             | ~0               |
| Vent 4 | 165         | 44          | ~0               | ~0               |
| Vent 5 | 3448        | 2500        | ~100             | ~100             |

