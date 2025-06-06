# Probabilistic tephra hazard modelling

Tephra describes all fragments of rocks of any size or composition that are injected into the atmosphere during explosive volcanic eruptions. Although tephra is not one of the main causes of casualties in the context of volcanic crisis (tephra are responsible for only 2% of all volcano-related deaths), it can cover wide areas and disrupt a broad range of socio-economic activities. Examples are health problems, collapse of roofs, death of vegetation, blockage of roads and disruption of airports and air traffic. Some hazardous tephra thresholds are shown in the table below. These ranges are wide due to the range of typologies of crops, vegetation, buildings that can be impacted, as well as external factors (e.g. time of the year for crops). Refer to the references provided in the [previous lesson](index.md) for more information on how to quantify physical vulnerability to tephra fallout.

<figure markdown>
| Element                          | Threshold ($kg/m^{2}$) |
|----------------------------------|------------------------|
| Airport closure                  | 1                      |
| Perturbation of the road network | 1-100                  |
| Impact on crops                  | 5-150                  |
| Impact on vegetation             | 5-1500                 |
| Roof collapse                    | 100-300                |
</figure>

## :material-format-list-checks:{ .icn } Objectives

The aim of this exercise is to compile a probabilistic hazard assessment for tephra accumulation for a future eruption at La Palma. Probabilistic modeling will be performed using the model [Tephra2](https://github.com/geoscience-community-codes/tephra2) [@Bonadonna2005] and the Matlab toolbox [TephraProb](https://github.com/e5k/TephraProb) [@Biass2016]. 

In this exercise, you will use the user-friendly Matlab toolbox called `TephraProb` to:

- Analyse the eruptive record and perform some basic frequency analyses.
- Analyse the wind patterns in a region and put this in the perspective of the hazard assessment. 

Running the full workflow for probabilistic hazard assessment in the computer lab is complicated by technical issues (e.g., computation time, compilation of source libraries). Therefore, we have already ran the scenario for you. You will nevertheless:

- Learn how to interpret the sampling of ESP.
- Analyse the hazard outputs.

!!! info "TephraProb"

    For more information about `TephraProb`, you can refer to the:

    - [Video tutorial](https://www.youtube.com/channel/UCP8gCjSeMoPVwgzMwKUnW3w).
    - Updates on the code's [website](https://e5k.github.io).


## Getting started

Due to the logistics of installing Matlab on PC's, we might encounter some issues. Throughout the exercise, you will see tabs similar to the one below. If you have access to Matlab and can use `TephraProb`, use the `With TephraProb` tab. Otherwise, we have extracted the figures required for the exercise in the `Without TephraProb` tab.

=== "With TephraProb"
    Make sure Matlab and `TephraProb` are setup according to [this guide](../Setup/matlab.md#step-3-install-tephraprob)

=== "Without TephraProb"
    Just sit tight for now!
<!-- 
The `VolcanicRisk2024.zip` located on `Moodle` contains folder named `TephraProb`, which we will use throughout the exercise. 

!!! tip "Alternative link"
    [Alternative dowload link](https://kdrive.infomaniak.com/app/share/250506/f6653aca-6802-4d55-b37f-1f3819057003) 

1. Start `Matlab`. If your computer has several versions, use the latest one.
2. Left of the address bar at the top of the main `Matlab` window, click on the icon `Browse for Folder` and navigate to the location of `TephraProb` (i.e. the location of the file `tephraProb.m`).
3. In the Matlab command line, type `TephraProb` and press enter to start `TephraProb`.

!!! danger "Use your user disk!"

    If you are using the PC of the computer lab, make sure **your files are saved on your personal drive!** This is typically the `H:\` drive. Otherwise, your files **will be deleted every time you logout!** -->

<!-- ### Get the eruption data 

1. Each one of you was assigned a different vent. From the `Moodle` page of the course, download the according folder `ventX` located in the `Tephra hazard assessment` folder. 
2. Place it in the `RUNS` folder located in your copy of `TephraProb`

!!! note "RUNS folder"

    If the `RUNS` folder does not exist at the root of `TephraProb`, please create it. -->


## :fontawesome-solid-gears:{ .icn } Hazard assessment 

This exercise is structured in 3 parts:

<!-- 1. Analysing the eruptive record of La Palma using the [GVP](https://volcano.si.edu) database. -->
2. Analysing wind patterns at la Palma using the [EMCWF ERA-5](https://www.ecmwf.int/en/forecasts/datasets/reanalysis-datasets/era5) database.
3. Defining an eruption scenario and associated ESP. 
4. Analysing the hazard output.

!!! warning "Exercise"

    Please answer the <a href="../../../../files/Exercise.docx", target="_blank">question sheet</a> and **submit it back to Moodle**.

<!-- 
### Eruption history

As already introduced, the [GVP](https://volcano.si.edu) database compiles the eruptive history of Holocene volcanoes based on their VEI. Each volcano is identified by an `id`, which is `383010` for La Palma. Let's have a look at the eruptive history of La Palma based on the GVP database. 

1. On the main `TephraProb` window, click `Input>GVP`.
2. Enter the `id`, click `Access` and wait a few seconds.
3. This first plot is a histogram showing the frequency of occurrence of each VEI. This is not super informative for La Palma, so change the `Plot type` to `Cumulative` and click the `Plot` button.
4. This new plot shows the cumulative number of eruption through time, colour-coded by the VEI. 

!!! info "Reading between the lines..."

    The GVP database is incredibly useful but, since based on the VEI, shares [similar strengths and weaknesses](index.md#why-are-tephra-deposits-important) previously discussed. Namely, the VEI works best for large, explosive eruptions, but not that well for eruption in the smaller spectrum of explosive styles such as those in La Palma. When thinking about the GVP data, bear in mind:

    1. The 2021 eruption is reported as `Undefined` VEI because no article reporting it has yet been published. However, we know it was a **VEI 3** eruption. 
    2. In the GVP, eruptions that have been identified as **having an explosive component** but for which **no tephra volume** are reported are assigned a default VEI of 2[^2]. This is probably why most eruptions for la Palma are reported as VEI 2.
    3. Conversely, eruptions for which no explosive component was identified in the field are reported with an `undefined` VEI. This might indicate that no tephra was produced or, more likely, that it was eroded.

!!! question "Question 1: Eruptive history"

    1. On the cumulative GVP plot, what does the slope of the plot (i.e., the ratio of `y` to `x`) represent?
    2. How does it vary in time, and how do you explain it?
    3. What is the **annual frequency of eruption** for the recent history? -->


### Wind data analysis

In order to take into account the aleatoric variability of atmospheric conditions in the hazard assessment, a large population of wind profiles is required from which a different wind profile is randomly sampled at each model run. The atmospheric database used here is the [EMCWF ERA-5](https://www.ecmwf.int/en/forecasts/datasets/reanalysis-datasets/era5) database.

Downloading atmospheric data takes time - we have therefore already prepared the dataset for you. The dataset contains 5 years of wind for the period 2017-2021, providing 4 wind profiles per day at a resolution of 0.25 degrees (e.g., ~28 km at the equator) above La Palma.

!!! info "Wind population"

    For the purpose of the exercise, we are using 5 years of wind data, which facilitates file transfer and speed up analyses. Keep in mind that we usually use larger populations for real applications (typically more than 10 years depending on the variability in a given region).

#### Analysing wind patterns

You can now display wind profiles. We use two formats to analyse wind conditions:

- **Wind profiles** show `wind velocity` and `wind direction` as a function of altitude. Wind profiles can be plotted either *separately* (e.g., one wind profile per year or per month) or *averaged* (e.g., mean ± standard deviation).
- **Wind roses** show the probability (concentric circles) of the wind blowing in each direction [0 - 360 degrees]. Colours indicate wind velocity. Wind roses are plotted for **a given elevation**, so explore a few. 

Keep your eyes opened for *seasonal trends* in both wind direction and speed.

=== "With TephraProb"
      1. On the main `TephraProb` window, click `Input>Wind>Analyze wind`
      2. Select the `wind.mat` file located in `WIND/CumbreVieja_1721/`
      3. A new panel opens, on which you can explore wind profiles either using `wind profiles` or `wind roses`. 

=== "Without TephraProb"
      
    ??? info "Wind profiles"

        <figure markdown>
        ![height](img/tephraprob/profile_average.png){width='450px'}
        <figcaption>Average wind profiles for the period 2017-2021.</figcaption>
        </figure>
        
        <figure markdown>
        ![height](img/tephraprob/profile_months.png){width='450px'}
        <figcaption>Monthly averaged profiles for the period 2017-2021.</figcaption>
        </figure>

    ??? info "Wind Roses"

        <figure markdown>
        ![height](img/tephraprob/rose_1.png){width='450px'}
        <figcaption>Wind rose at 1 km asl for the period 2017-2021.</figcaption>
        </figure>
        
        <figure markdown>
        ![height](img/tephraprob/rose_2.png){width='450px'}
        <figcaption>Wind rose at 2 km asl for the period 2017-2021.</figcaption>
        </figure>
        
        <figure markdown>
        ![height](img/tephraprob/rose_4.png){width='450px'}
        <figcaption>Wind rose at 4 km asl for the period 2017-2021.</figcaption>
        </figure>
        
        <figure markdown>
        ![height](img/tephraprob/rose_6.png){width='450px'}
        <figcaption>Wind rose at 6 km asl for the period 2017-2021.</figcaption>
        </figure>
        
        <figure markdown>
        ![height](img/tephraprob/rose_8.png){width='450px'}
        <figcaption>Wind rose at 8 km asl for the period 2017-2021.</figcaption>
        </figure>
<!--         
        <figure markdown>
        ![height](img/tephraprob/rose_10.png){width='450px'}
        </figure>
        <figcaption>Wind rose at 10 km asl for the period 2017-2021.</figcaption>
        
        <figure markdown>
        ![height](img/tephraprob/rose_15.png){width='450px'}
        </figure>
        <figcaption>Wind rose at 15 km asl for the period 2017-2021.</figcaption>
         -->




!!! question "Question 1: Wind conditions"

    1. Visualize these wind patterns in the context of a hazard assessment. What is the main wind direction **below 5 km**?
    2. Can you observe a **variability** in wind patterns as a function of the month? If yes, is it gradual or do you observe two distinct wind regimes?

    <!-- 2. How does the mean wind direction vary with height? How is that affecting eruptions of different sizes? (&rarr; refer to the note about *VEI and plume heights* above). -->
    <!-- 3. Do you notice any seasonality? If yes, identify during what months it happens. -->



### Eruption scenario 

Let's try and forget what we know about the 2021 eruption and put ourselves in this reasoning framework:

1. We need to assess the hazard associated with tephra accumulation for a future eruption along the Cumbre Vieja rift. 
2. From the historical record, most eruptions are **VEI 2**. However, since what we observed in the field deposits seems larger than VEI 2 eruptions, we decide to focus on a **VEI 3** eruption. 
3. However, the deposits we observed do not look like **short-lasting, subplinian VEI 3** eruptions. We suspect that these eruptions were less intense and longer-lasting. We therefore model an eruption lasting between **3 days to one week** with plume heights varying between **1-5** km.
4. We have **no information** regarding the **grain-size** distribution of the observed deposits, and therefore decide to use an **analogue eruption** to inform us. We chose the 2002 eruption of Etna volcano.


See what we just did? We just defined an **eruption scenario**! The table below summarises the **ESP** for our **low-intensity VEI 3** eruption.

| ESP           | Value                  | Description                                                                                                        |
|:--------------|:-----------------------|:-------------------------------------------------------------------------------------------------------------------|
| VEI           | 3                      | Similar to the 2021 eruption                                                                                       |
| Mass          | 10$^{10}$–10$^{11}$ kg | Using the volume ranges of a VEI 3 eruption and conversion to mass using a bulk deposit density of 1000 $kg/m^{3}$ |
| Height        | 1-5 km                 | Low intensity VEI 3 eruption occurring over a few days                                                             |
| Duration      | 3-7 days               | Paroxysmal phase of a longer eruptive sequence                                                                     |
| Md$_\Phi$     | 0-1 $\Phi$             | Center of the grain-size distribution, based on Etna 2002                                                          |
| $\sigma_\Phi$ | 1-2 $\Phi$             | Spread of the grain-size distribution, based on Etna 2002                                                          |


!!! tip "VEI and plume height"

    The VEI scale suggests *very approximative* indications of plume height for each VEI class. For instance, it suggests heights of 1-5 km for VEI 2 and 3-15 km for VEI 3 eruptions. However, the VEI scale does not include any information about **intensity** of the eruption (&rarr; **duration** over which the VEI volume was erupted). 

    The volume associated with the 2021 VEI 3 eruption was erupted over the course of **a few months**, but plume heights were in the 1-5 km range rather than the 3-15 km range. Therefore, let's consider here the following plume heights:

    - **VEI 2**: 1-5 km.
    - **VEI 3 - low intensity**: 1-5 km (→ long-lasting eruption lasting for days/weeks).
    - **VEI 3 - high intensity**: 3-15 km (&rarr; intense eruption lasting for hours).

??? info "Grain size distribution"

    For clarity, we haven't touched yet on the concept of **grain-size distribution** or GSD. This is an important ESP for tephra dispersal as it controls *how fine* (or *coarse*) the tephra generated at [fragmentation level](Hazard_tephra_modeling.md#model-parametrisation) will be, and therefore will control *how far particles will go*. 

    Grain size is expressed in $\Phi$ units, which is calculated as $-log_2(d)$, where $d$ is the particle diameter in $mm$. In $\Phi$ units:

    - A 1 mm-particle has $\Phi=0$. 
    - Particles **coarser** than 1 mm have **negative** $\Phi$ values. 
    - Particles **finer** than 1 mm have **positive** $\Phi$ values. 

    In `Tephra2` the GSD of the model deposit is considered to be a **Gaussian** distribution centered on $Md_\Phi$ (i.e., mean) and varying by $\sigma_\Phi$ (i.e., standard deviation). 


#### ESP sampling 

Now that we have defined the ranges of ESP, `TephraProb` applies the algorithm below to sample $n$ sets of ESP. For the sake of the exercise, $n$ is here set to **250 runs**. The figures below summarise the sampling of the ESP.

=== "Plume height"
    <figure markdown>
    ![height](img/tephraprob/plume_height.png){width='450px'}
    </figure>
=== "Mass"
    <figure markdown>
    ![mass](img/tephraprob/mass.png){width='450px'}
    </figure>
=== "Date"
    <figure markdown>
    ![date](img/tephraprob/date.png){width='450px'}
    </figure>
=== "Duration"
    <figure markdown>
    ![duration](img/tephraprob/duration.png){width='450px'}
    </figure>
=== "GSD"
    <figure markdown>
    ![mass](img/tephraprob/gsd.png){width='450px'}
    </figure>

=== "Sampling algorithm"


    ```mermaid 

    flowchart TD 

    subgraph sg0 ["Eruption scenario"]

    A1["HEIGHT [min, max]"]
    C1["DATE [min, max]"]
    B1["DURATION [min, max]"]
    D1["MASS [min, max]"] 

    end

    subgraph sg1 ["For each run"]

        subgraph sg2 [" "]
            A2["Sample Height"]
            C2["Sample Date"]
            B2["Sample Duration"]
        end



    C2 --> C3["Get wind velocity"]
    C3 --> E["Calculate MER"]
    A2 --> E
    E --> F["Calculate simulation Mass"]
    B2 --> F

    F --> G["Is Mass within MASS [min, max]"]
    D1 --> G

    end

    A1 --> A2 
    C1 --> C2 
    B1 --> B2

    G --> H1[Yes]
    G --> H2[No]

    H1 --> I1["Run is valid, move to next one"]
    H2 --> I2["Run is not valid, restart"]

    ```

!!! question "Question 2: ESP"

    Analyse the distributions of sampled ESP. For each ESP, discuss:

    1. From what distribution have ESPs for i) plume height, ii) erupted mass and iii) grain-size distribution been sampled from? (Hint: there are three types of distributions used here: *logarithmic*, *normal* and *uniform*).
    2. What *prior knowledge* do these three distributions reflect?



### Hazard output

!!! question "Question 3: Probability calculation"

    1. The [previous module](Hazard_probabilistic2.md) has introduced how to compute *exceedance probability* for tephra accumulation. Based on the 10 simulations below for pixel $x,y$, what are the probabilities of this pixel to suffer tephra accumulations exceeding:

        - 50 $kg/m^2$?
        - 100 $kg/m^2$?
        - 150 $kg/m^2$?
        
    <div class="grid" markdown>

    | Simulation | Tephra accumulation ($kg/m^2$) |
    |------------|--------------------------------|
    | 1          | 115                            |
    | 2          | 80                             |
    | 3          | 151                            |
    | 4          | 65                             |
    | 5          | 112                            |

    | Simulation | Tephra accumulation ($kg/m^2$) |
    |------------|--------------------------------|
    | 6          | 156                            |
    | 7          | 102                            |
    | 8          | 104                            |
    | 9          | 85                             |
    | 10         | 123                            |

    </div>

    2. Similarly, we also learned how to estimate a **typical accumulation** associated with a given probability of occurrence. The figure below shows the [survivor function](Hazard_probabilistic2.md#hazard-outputs) for the data in the table above. Estimate the approximative load associated with probability values of:

        - 30%
        - 70%

    <figure markdown>
    ![survivor](img/survivor.png){width='450px'}
    </figure>

!!! warning "Load runs"

    **One single vent** was assigned to each of you. For the rest of the exercise, **make sure you refer only this one**.

    **If you use TephraProb**, let's now load your assigned scenario, where `runName` goes from `vent1` to `vent5`:

    -  On the main `TephraProb` window, click `File>Open`
    -  Select the `.mat` file located in `RUNS/runName/1/`


#### Probability maps

!!! tip "Hazard outputs"
    You can always refer the previous lesson where we reviewed how the different [outputs](Hazard_probabilistic2.md#hazard-outputs) are compiled from probabilistic hazard assessments.

Probability maps fix a critical value of tephra accumulation ($kg/m^2$) to allow the contouring of the spatial probability of exceeding this critical threshold. These maps are useful to see the dispersion of probabilities across an area, but only for **one given tephra accumulation threshold at the time**. Let's now look at them.

=== "With TephraProb"
      1. Make sure the scenario for the vent that was attributed to you is loaded (`File > Load`). 
      2. From the main `TephraProb` window, click `Display > Probability Maps`. 
      3. A new window opens, from which you can select pre-defined accumulation threshold (you can select multiple using the ++cmd++ (Mac) or the ++ctrl++ (Windows) keyboard buttons). **Do not open all maps!** Select only the **1** **10**, **100** $kg/m^2$.
      4. Click `Ok` - `Google Earth should now open`. 

        ??? warning "Troubleshooting Google Earth" 

            **If Google Earth is in French**: 

            - `Google Earth` is in French by default. To change the language, go to `Outils/Options/General/Parametres de langue` and choose your language.

            **If Google Earth does not open:**

            - From the main `TephraProb` window, select `File > Preferences` and make sure the `Show Google Earth` option is selected.

=== "Without TephraProb"

    === "Vent 1"

        [Download KMZ file :fontawesome-solid-globe:](files/V1/V1%20-%20Probability%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V1/V1_prob_all_1_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V1/V1_prob_all_10_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V1/V1_prob_all_100_kg_m2.png)
        </figure>

        
    === "Vent 2"

        [Download KMZ file :fontawesome-solid-globe:](files/V2/V2%20-%20Probability%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V2/V2_prob_all_1_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V2/V2_prob_all_10_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V2/V2_prob_all_100_kg_m2.png)
        </figure>

    === "Vent 3"

        [Download KMZ file :fontawesome-solid-globe:](files/V3/V3%20-%20Probability%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V3/V3_prob_all_1_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V3/V3_prob_all_10_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V3/V3_prob_all_100_kg_m2.png)
        </figure>

    === "Vent 4"

        [Download KMZ file :fontawesome-solid-globe:](files/V4/V4%20-%20Probability%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V4/V4_prob_all_1_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V4/V4_prob_all_10_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V4/V4_prob_all_100_kg_m2.png)
        </figure>

    === "Vent 5"

        [Download KMZ file :fontawesome-solid-globe:](files/V5/V5%20-%20Probability%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V5/V5_prob_all_1_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V5/V5_prob_all_10_kg_m2.png)
        </figure>
        <figure markdown>
        ![height](files/V5/V5_prob_all_100_kg_m2.png)
        </figure>




!!! question "Probability maps"

    No question to answer here, but take a moment to think about:

    1. In which direction (i.e., downwind cardinal reference) is the hazard associated with tephra fallout most likely to occur?
    2. At each point of the map, can you express exactly the information that is presented?


#### Probabilistic isomass maps

Probabilistic isomass maps fix a probability threshold to represent a typical tephra accumulation given a probability of occurrence of the hazardous phenomenon. The choice of the probability threshold, which can be regarded as an acceptable level of hazard, is a critical aspect that is the resort of decision-makers. Scientists should therefore communicate results from probabilistic isomass maps with care. Plot a few probabilistic isomass maps and analyse them.

=== "With TephraProb"
    1. From the main `TephraProb` window, click `Display > Isomass Maps`. 
    2. A new window opens, from which you can select pre-defined probability thresholds. Choose the **25%** and **75%**.
    3. Click `Ok` - `Google Earth` should now open. 

=== "Without TephraProb"

    === "Vent 1"

        [Download KMZ file :fontawesome-solid-globe:](files/V1/V1%20-%20Probabilistic%20isomass%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V1/V1_IM_all_25_%25.png)
        </figure>
        <figure markdown>
        ![height](files/V1/V1_IM_all_75_%25.png)
        </figure>

    === "Vent 2"

        [Download KMZ file :fontawesome-solid-globe:](files/V2/V2%20-%20Probabilistic%20isomass%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V2/V2_IM_all_25_%25.png)
        </figure>
        <figure markdown>
        ![height](files/V2/V2_IM_all_75_%25.png)
        </figure>

    === "Vent 3"

        [Download KMZ file :fontawesome-solid-globe:](files/V3/V3%20-%20Probabilistic%20isomass%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V3/V3_IM_all_25_%25.png)
        </figure>
        <figure markdown>
        ![height](files/V3/V3_IM_all_75_%25.png)
        </figure>

    === "Vent 4"

        [Download KMZ file :fontawesome-solid-globe:](files/V4/V4%20-%20Probabilistic%20isomass%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V4/V4_IM_all_25_%25.png)
        </figure>
        <figure markdown>
        ![height](files/V4/V4_IM_all_75_%25.png)
        </figure>

    === "Vent 5"

        [Download KMZ file :fontawesome-solid-globe:](files/V5/V5%20-%20Probabilistic%20isomass%20map.kmz){ .md-button }

        <figure markdown>
        ![height](files/V5/V5_IM_all_25_%25.png)
        </figure>
        <figure markdown>
        ![height](files/V5/V5_IM_all_75_%25.png)
        </figure>


!!! question "Probabilistic isomass maps"

    Again, no question to answer, but reflect on:
    
    1. What are these maps showing?
    2. How do they differ from probability maps?

#### Hazard curves

Let's now look at hazard curves. Hazard curves fix a spatial locations (i.e., a single point) and continuously express the probability to exceed any threshold of hazard intensity. The table below shows the location of hazard curves extracted for each vent.


=== "Vent 1"

    | Location | Longitude | Latitude |
    | ----- | ------ | ------ | 
    | El Paso, houses | -17.85992 | 28.65247 |
    
    <!-- | Main highway | -17.84055 | 28.65027 |
    | El Paso, vineyard| -17.86370 | 28.64256 | -->

=== "Vent 2"

    | Location | Longitude | Latitude |
    | ----- | ------ | ------ | 
    | San Nicola, houses | -17.88052 | 28.60222 |

    <!-- | San Nicola, main road| -17.88763 | 28.60108 | -->
    <!-- | Crops | -17.90305 | 28.59933 | -->
    

=== "Vent 3"

    | Location | Longitude | Latitude |
    | ----- | ------ | ------ | 
    | Jedey, houses | -17.87995 | 28.58373 |

    <!-- | Jedey, vineyard | -17.87881 | 28.58865 | -->
    <!-- | Forest | -17.84751 | 28.57731 | -->
    

=== "Vent 4"

    | Location | Longitude | Latitude |
    | ----- | ------ | ------ | 
    | El Pueblo, houses  | -17.77892 | 28.60605 |

    <!-- | El Pilar, forest | -17.83002 | 28.61377 |
    | Crops  | -17.82077 | 28.62483 | -->
    

=== "Vent 5"

    | Location | Longitude | Latitude |
    | ----- | ------ | ------ | 
    | Los Canarios, houses | -17.84446 | 28.49251 |

    <!-- | Los Canarios, vineyard| -17.83749 | 28.47775 |
    | Road leading to Los Canarios from W | -17.82308 | 28.51489 | -->
    

Let's now visualise and analyse the information retained by hazard curves.


=== "With TephraProb"
    1. From the main `TephraProb` window, click `Display > Hazard curves`
    2. Choose the point for your own vent as named in the table above.  

=== "Without TephraProb"

    === "Vent 1"
        <figure markdown>
        ![height](files/V1/V1_curve.png)
        </figure>
    === "Vent 2"
        <figure markdown>
        ![height](files/V2/V2_curve.png)
        </figure>
    === "Vent 3"
        <figure markdown>
        ![height](files/V3/V3_curve.png)
        </figure>
    === "Vent 4"
        <figure markdown>
        ![height](files/V4/V4_curve.png)
        </figure>
    === "Vent 5"
        <figure markdown>
        ![height](files/V5/V5_curve.png)
        </figure>


[Figure 1](#fig1) represents fragility curves for various European roofs [@Spence2005], and estimate a median probability of roof collapse as a function of tephra accumulation. Use these curves to answer the following questions. 

<figure markdown>
![roofs](img/tephra/fragility.png){#fig1}
<figcaption>Figure 1: Fragility curves of Spence et al. (2005) expressing the median probability of roof collapse for various European roofs. The different curves represent various roof typologies: WE: Weak (e.g., Tiled roof, old or in poor condition); MW: Medium Weak (e.g., Tiled roof, average or good condition); MS: Medium Strong (e.g., Flat RC roof); ST: Strong (e.g., Flat RC roof designed for access, younger than 20 years). </figcaption>
</figure>

!!! question "Question 4: Hazard curves"

    For the point attributed to your vent, use the model of Spence et al. (2005)[^Spence2005] to estimate a probability of occurrence of roof collapse. To convert a mass per unit area ($M$, $kg/m^2$) to a load ($L$, $kPa$), use:

    $$
    L = M \times 9.81 \times 10^{-3} 
    $$
    
    1. Assuming that the considered buildings are of a **MS** fragility class, what are the probabilities of roof collapse for associated with mass loads for 25% and 75% probability of occurrence? 


    ??? tip "Accessing hazard curves with **data tips**"

        On the hazard curve figure, you can activate the `Data Tips` tool. This allows you to click on the curve and directly get the underlying data. It is hard to get exact probabilities, **so anything within a ± 5% range is ok**.

        <figure markdown>
        ![Data-tip](img/tephraprob/data-tip.png){width="300"}
        </figure>

    !!! tip "Estimating probability of roof collapse"

        Once you have estimated the load, you can read the corresponding probability of roof collapse from [Figure 1](#fig1). If you feel adventurous, you can also compute it directly from the Matlab command line (where $L$ is the load):

        ```matlab 
            P = normcdf(log(L), log(4.5), 0.2)
        ```

        Note that the MS class according to Spence et al. (2005)[^Spence2005] is characterised by:
        
         1. A normal cumulative density function 
         2. A mean value of 4.5 kPa
         3. A standard deviation of 20% 

        Refer to the original paper for more information.


## :material-thought-bubble:{ .icn } Food for thoughts 

Well done - you have successfully completed a **scenario-based probabilistic hazard assessment for tephra accumulation**! Keep in mind that:

- The **scenario-based** part implies that this hazard is **contitional** to the occurrence of the eruption scenario. This contrasts with a *fully* **probabilistic volcanic hazard assessment**, where the *spatio-temporal* probability of occurrence of given volcanic phenomena also need to be accounted for. 
- Having pretty maps is great... but knowing how to communicate the hazard output and the associated assumptions and uncertainties is often *equally important*. Keep that in mind for the rest of the exercises, both in the lab and in the field. 

<!-- ### Getting the hazard data 

As displayed in `Matlab`, you can save the maps displayed within `TephraProb` by simply typing `saveAllMaps('png')`, which will save all opened maps to `TephraProb/MAPS`. The raw output data for both *probability* and *isomass* maps are saved as `ascii` raster file with a UTM 28 N projection. Probability (`PROB`) and isomass (`IM`) data are located in:

```
TephraProb/RUNS/ventX/1/PROB/all/RASTER/*.txt
TephraProb/RUNS/ventX/1/IM/all/RASTER/*.txt
```

These are useful for use in external softwares (e.g., `QGIS`). Similarly, `kml` files are stored in the `KML` folder of your run.

Hazard curves must be saved from within `Matlab`. -->

## :material-check-bold:{ .icn } Summary

This module provided a practical application of the concepts introduced in the previous module, using La Palma as a case study and producing a scenario-based hazard assessment for tephra accumulation using `TephraProb`.

## :fontawesome-solid-book:{ .icn } References

<!-- [^1]: Bonadonna, C., Connor, C.B., Houghton, B.F., Connor, L., Byrne, M., Laing, A., Hincks, T.K., 2005. Probabilistic modeling of tephra dispersal: Hazard assessment of a multiphase rhyolitic eruption at Tarawera, New Zealand. J. Geophys. Res 110, 2156–2202.
[^2]: Biass, S., Bonadonna, C., Connor, L., Connor, C., 2016. TephraProb: a Matlab package for probabilistic hazard assessments of tephra fallout. Journal of Applied Volcanology 5, 1–16. 
[^3]: Simkin, T., Siebert, L., Simkin, T., Kimberly, P., 2010. Volcanoes of the World. University of California Press, Tucson, AZ.
[^4]: Jenkins, S.F., Wilson, T.M., Magill, C., Miller, V., Stewart, C., Blong, R., Marzocchi, W., Boulton, M., Bonadonna, C., Costa, A., 2015. Volcanic ash fall hazard and risk, in: Loughlin, S., Sparks, S., Brown, S., Jenkins, S., Vye-Brown, C. (Eds.), Global Volcanic Hazards and Risk. Cambridge University Press, pp. 173–222.
[^5]: Spence, R.J.S., Kelman, I., Baxter, P.J., Zuccaro, G., Petrazzuoli, S., 2005. Residential building and occupant vulnerability to tephra fall. Natural Hazards and Earth System Sciences 5, 477–494. -->

*[ESP]: Eruption source parameter &rarr; most important initial conditions to a model
*[TGSD]: Total grain-size distribution
*[MER]: Mass eruption rate
*[VEI]: Volcanic explosivity index
*[HIM]: Hazard impact metrics
*[GAR]: Global assessment report
*[DDS]: Damage-Disruption states &rarr; one way of characterising vulnerability
*[GVP]: Global volcanism program 
*[GSD]: Grain size distribution



