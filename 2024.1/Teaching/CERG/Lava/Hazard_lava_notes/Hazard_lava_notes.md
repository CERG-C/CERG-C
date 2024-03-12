password: askja1875

<!-- ## Path of steepest descent  -->

## Q-LavHA


### Question 1: Single-vent simulations

1. > **In one sentence, describe what the color at any given pixel expresses.**
   
      - → Probability of inundation should a lava flow occur from the vent we identified.
   
2. > **How do modelled flows compare to the closest <a href="../../../files/GeologicalmapofLaPalma.pdf", target="_blank">historical lava flows</a> in terms of length and width?**
   
      - They capture the general direction, though branching can occur in different drainage basins
      - For the width, it is difficult to compare as most flows entered the ocean
      - They are typically narrower → Why? → Missing **time**
     
          - Flow fields are not single-event phenomena, they evolve in time and space as they resurface and alter existing topography 
          - Long-lasting hybrid eruptions - especially from fissures - typically result in the opening of multiple vents/cones that widen the flow field → ❗ important motivation for the next step

3. > **Analyse and discuss the spatial distribution of inundation probability. How do they compare to flow accumulation rasters and the path of steepest descent approach?**
   
      - Highest probabilities tend to occur over paths of steepest descents, which confirms the usefulness of hydrological modeling. However, this modelling approach allows to explore where **low-probability** inundation could occur.


--- 

### Question 2: Simulations with surface area


1. > **Compare the run with its single-vent counterpart. How do they differ and why?**
   
      - For well constrained basins (e.g., vent 3), the width is ± the same, but some channels have higher probabilities than before (e.g., the N channel becomes the most likely). 
      - In other cases (e.g., vents 1 and 2), the scenarios reveal new paths of inundation that tend to widen the predictions, but they have **low** probabilities of inundation &rarr; indicates the likelihood of low probability events &rarr; ❓ how do you account for these in risk planning?
      - Conversely, other vents (e.g., 4 and 5) show that vent opening uncertainty open access to entirely new drainage basins. This is due to larger-scale topographic constraints, either the ridge (vent 5) or previous lava channels (vent 4).

      - ❗ Outline how **ignoring uncertainties** can result in a **fragmented** vision of the hazard.

--- 

### Question 3: Forecasting the flows from the 2021 eruption


1. > **From what you know about both the 2021 eruption and the dynamics of lava flows, compare and discuss the hazard forecast and the actual deposit. What are `Q-LavHA`'s strengths and limitations?**
      - The predicted inundated area corresponds fairly well to what really happened
      - The highest-probability channel captures the first ocean entry 
      - **However** &rarr; is that just a coincidence?
          - `Q-LavHA` simulates only a single flow &rarr; which means that the low probability areas represent what **could have happened** with the first flow unit
          - It does not capture the **dynamic evolution** of a flow field
      - There is little to no physics in the model. This speeds up calculation, but it means that the model will fail to fully capture the complexity of lava flows
--- 



### Resources

#### Areas for surface simulations 

| Vent   | Easting (m) | Northing (m) | xL     | xR     | yD      | yU      |
|:-------|:------------|:-------------|:-------|:-------|:--------|:--------|
| Vent 1 | 222340      | 3169746      | 222090 | 222590 | 3169496 | 3169996 |
| Vent 2 | 219728      | 3168426      | 219478 | 219978 | 3168176 | 3168676 |
| Vent 3 | 221922      | 3165623      | 221672 | 222172 | 3165373 | 3165873 |
| Vent 4 | 224646      | 3167772      | 224396 | 224896 | 3167522 | 3168022 |
| Vent 5 | 221357      | 3155562      | 221107 | 221607 | 3155312 | 3155812 |

