# Quantifying eruption source parameters from tephra fallout deposits

> **Physical volcanology course**

> Sébastien Biass, Riccardo Simionato, Corin Jorgenson, Tom Sheldrake

> April 24 2023

---

The aim of this lab is to apply techniques to quantify eruption source parameters (ESP) from tephra fall deposits. This includes:

- From field measurements at the outcrop level, producing **isopach** and **isopleth maps**;
- Calculating critical ESP such as plume height, tephra volume and mass and mass eruption rate;
- Estimating the *magnitude* and the *intensity* of an eruption;

![](img/deposit/field_characterisation.png)

Compute all parameters and discuss all points that are `highlighted` in the text. The lab uses the tephra fall deposit *Layer 5* of Cotopaxi volcano in Ecuador, which is a black scoriaceous lapilli fallout with an age of 1,180±80 years B.P. and a whole-rock silica content of 58 wt.% [@Barberi1995; @Biass2011]. *Thickness* and *maximum clast* measurements at each outcrop are provided. It is time consuming to estimate the areas of isopach and isopleth, so use the data provided separately.

You are provided with the following files:

- <a href="../files/deposit/isopach.csv", target="_blank">Isopach data</a>
- <a href="../files/deposit/ML.pdf", target="_blank">A map of maximum lithics measurements</a>
- <a href="../files/deposit/template.xlsx", target="_blank">A template for your answers</a>

 <!-- (Tables
[1](#isopach){reference-type="ref" reference="isopach"} and
[2](#isopleth){reference-type="ref" reference="isopleth"}). Use Excel
for calculations. -->

---

## Volume of the tephra fallout deposit 

Estimate the volume of Layer 5 using the 1-exponential segment method of Fierstein & Nathenson (1992)[@Fierstein1992] using the isopach map shown in Figure [1](#layer5):

- In Excel, import the <a href="../files/deposit/isopach.csv", target="_blank">isopach data</a> provided in Table 1 and plot the thickness ($cm$) versus the **square-root** of the area ($km$) and change the y-axis to a logarithmic scale

- Fit an exponential segment and display its equation to estimate the intersect ($T_0$) and the thinning rate ($k$). Note that $T_0$ is now in centimetres, so you need to convert it to a unit consistent with the x-axis in order to calculate the volume

- Calculate the `volume` of the tephra fallout deposit using the following formula:

$$ 
V = \frac{2T_0}{k^2} \ [m^3]
$$

- Estimate the corresponding `VEI` using the diagram in Fig. [2](#vei) from Newhall and Self (1982)[@newhall82]

- Convert the volume to a mass using a bulk density of 1000 $kg/m^3$ and calculate the associated `magnitude` following Pyle (2000)[@pyle2000]

$$
M = log_{10}(mass\ [kg]) - 7
$$

<figure markdown>
  ![](img/deposit/isopach.png){#layer5 width="500"}
  <figcaption>Figure 1: Isopach map of Layer 5.</figcaption>
</figure>

<figure markdown>
  ![](img/deposit/vei.jpg){#vei}
  <figcaption>Figure 2: VEI scale according to Newhall and Self (1982).</figcaption>
</figure>

---

!!! note "Table 1: Isopach data for Layer 5 of Cotopaxi volcano" 

    | Isopach area (km$^2$)   | Thickness (cm) |
    | --------------- | ---------------- |
    | 46              | 100 |
    | 85              | 50 |
    | 130             | 30 |
    | 330             | 20 |
    | 387             | 10 |
    | 685             | 5 |


## Plume height

Calculate the plume height ($km$ above vent) with the method of Rossi et al. (2019)[@Rossi2019] (Fig. [3](#rossi1)). The <a href="../files/deposit/ML.pdf", target="_blank">provided map</a> contains measurements of *maximum lithics* (density of $2500\ kg/m^3$). This method works with isopleth contour values of 1.6 and 3.2 $cm$, so **make sure to contour isopleth accordingly**. Assume a mean sampling elevation of 2500 $m\ asl$. Cotopaxi has an elevation of 5700 $m\ asl$.

- Contour isopleths on the <a href="../files/deposit/ML.pdf", target="_blank">provided map</a>. Make sure you contour values that are presented in Figure [3].
- Measure the *downwind* and *crosswind* ranges of the deposit and report them on Figure [3](#rossi1) to estimate a plume height **above mean sampling elevation**.
- Calculate the `plume height` and the `wind speed` as an average value of the results obtained from the different plots considered. Please also indicate the associated variation (i.e. ±(max-min)/2). Make sure to subtract the average height of sampling from the height obtained with the nomograms in order to derive the height above the vent.

=== "Figure 3a"
    <figure markdown>
        ![](img/deposit/rossi1.png){#rossi1}
        <figcaption>Figure 3a: Graphical method to estimate the plume height (km above the mean sampling elevation) and the wind speed for an isopleth of maximum lithics with a diameter of 1.6 cm.</figcaption>
    </figure>


=== "Figure 3b"
    <figure markdown>
        ![](img/deposit/rossi2.png){#rossi2}
        <figcaption>Figure 3b: Graphical method to estimate the plume height (km above the mean sampling elevation) and the wind speed for an isopleth of maximum lithics with a diameter of 3.2 cm.</figcaption>
    </figure>


--- 

## Mass eruption rate 


- Estimate the **peak** `mass eruption rate` (`MER`; $kg s^{-1}$) using the method of Degruyter and Bonadonna (2012)[@Degruyter2012]:

$$
MER = \pi\frac{\rho_{a0}}{g'}\left(\frac{\alpha^2\bar{N}}{10.9}H^4 + \frac{\beta^2\bar{N}^2\bar{v}}{6}H^3\right)
$$

- Use the following values:
  
    - $\rho_{a0}$: reference density of the surrounding atmosphere (use 1.2259 kg m$^{-3}$) 
    - $g'$: reduced gravity at the source (use 45.6525 m s$^{-2}$)
    - $\alpha$: radial entrainment coefficient (use 0.1)
    - $\bar{N}$: average buoyancy frequency across the plume height (use 0.0156 s$^{-1}$) 
    - $H$: plume height (m above the vent) 
    - $\beta$: wind entrainment coefficient (use 0.5)
    - $\bar{v}$ average wind velocity across the plume height (use 8.7 m s$^{-1}$). Note that the average wind speed along the plume should be smaller than the wind speed that you have derived with the method of Rossi et al. (2019), which is the maximum wind speed at tropopause

- Use the MER to calculate the associated `intensity` following Pyle (2000)[@pyle2000]

$$
I = log_{10}(MER [kg s^{-1}]) + 3
$$


## Further reading 

This list contains some references for the characterisation of tephra deposits.

### Characterization of tephra-fall deposits

- Thorarinsson (1954)[@Thorarinsson1954]
- Wilson (1972)[@Wilson1972]      
- Walker (1973)[@Walker1973]
- Wright et al (1980)[@Wright1980]      
- Walker (1980)[@Walker1980]      
- Carey and Sparks (1986)[@Carey1986]
- Sparks (1986)[@Sparks1986]      
- Wilson and Walker (1987)[@Wilson1987]      
- Cas and Wright (1988)[@Cas1988]
- Houghton and Carey (2015)[@HoughtonB.F.2000]

### Volume calculation

- Pyle (1989)[@Pyle1989]      
- Fierstein and Nathenson (1992)[@Fierstein1992] 
- Legros (2000)[@Legros2000]
- Sulpizio (2005)[@Sulpizio2005]  
- Bonadonna and Houghton (2005)[@Bonadonna2005] 
- Bonadonna and Costa (2013)[@Bonadonna2013a]
- Burden et al (2013)[@Burden2013]    
- Daggitt et al (2014)[@Daggitt2014]   
- Engwell et al (2015)[@Engwell2015]
- Yang and Bursik (2016)[@Yang2016]      
- Nathenson (2017)[@Nathenson2017] 

### Mass eruption rate

- Wilson and Walker (1987)[@Wilson1987]                                  
- Degruyter and Bonadonna (2012)[@Degruyter2012]   
- Woodhouse et al (2013)[@Woodhouse2013]
- Mastin et al (2009)[@Mastin2009]     

### Uncertainty assessment

- Biass and Bonadonna (2011)[@Biass2011]        
- Cioni et al (2011)[@Cioni2011]       
- Engwell et al (2013)[@Engwell2013]
- Biass et al (2014)[@Biass2014b]       
- Klawonn et al (2014a)[@Klawonn2014]     
- Klawonn et al (2014b)[@Klawonn2014a]
- Bonadonna et al (2015)[@Bonadonna2015a]   

