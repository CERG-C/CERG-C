# Estimer l'aléas et l'impact des retombées de balistiques

> **Module risques volcaniques**

> Sébastien Biass, Simon Thivet, Allan Fries

> 13 Mars 2023

---

## :material-format-list-checks:{ .icn } Introduction

Depuis quelques jours, une augmentation du niveau sismique laisse penser qu'une nouvelle éruption est imminente sur l'île de La Palma. Ce matin, le bruit sismique à migré de façon inattendue vers la localité d'El Remo. Un tremblement de terre a endommagé la seule route liant El Remo à la route principale permettant l'évacuation. Depuis, l'éruption a commencé, créant un cone d'une hauteur d'environ 20 mètres situé à environ 1 km du village, situé à la hauteur de la mer. La mer étant mauvaise, une évacuation par bateau ou hélicoptère est pour l'instant impossible et les habitants et touristes ont reçu la recommendation de s'abriter à l'intérieur.

Une étude rapide de l'évolution de l'éruption révèle que:

1. Du à la morphologie du cone, la lave s'écoule vers le nord-ouest et ne devrait pas atteindre El Remo. La coulée devrait entrer en contact avec l'océan d'ici à demain
2. Les vents viennent du nord-est
3. Le principal aléa en ce moment est l'éjection de blocks suivant une trajectoire parabolique (balistique)

Vous faites partie du conseil scientifique assemblé pour conseiller PEVOLCA (*Plan Especial de Protección Civil y Atención de Emergencias por riesgo volcánico en la Comunidad Autónoma de Canarias*) sur l'aléas et les impacts possible durant la gestion de crise. 

---

## Tâches

### 1. Estimer l'intensité de l'aléa lié aux retombées de blocks

Basé sur des modèles disponibles, il est estimé que la masse la plus probables des blocks pouvant atteindre El Remo est de **0.4 kg**. Les équations ci-dessous permettent **d'estimer l'énergie cinétique au moment de l'impact** d'un bloc de cette masse: 


#### Equation 1

L'équation 1 décrit la hauteur du bloc $z$ (m) en fonction du temps $t$ (s):
  > $z = z_0+\frac{v_0}{\sqrt{2}}t-\frac{1}{2}gt^2$, où $g=9.81\ m/s^2$

#### Equation 2

L'équation 2 décrit la distance horizontale $d$ (m) en fonction du temps $t$ (s):
  > $d = \frac{v_0}{\sqrt{2}}$

#### Equation 3

L'équation 3 décrit la vitesse du bloc $v$ (m/s) en fonction du temps $t$ (s):
  > $v = \sqrt{v_{x}^2+v_{z}^2}$

L'équation 3.1 décrit la composante horizontale de la vitesse:
  > $v_x = \frac{v_0}{\sqrt{2}}$   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Eq. 3.1)

L'équation 3.2 décrit la composante verticale de la vitesse:
  > $v_z = \frac{v_0}{\sqrt{2}}-gt$   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Eq. 3.2)

#### Equation 4

L'équation 4 décrit l'énergie cinétique $E_k$ (J) au moment de l'impact:
  > $E_k = \frac{1}{2}mv^2$













The volume of tephra deposits is estimated from isopach maps by integrating the area below a curve plotting the **logarithm of the thickness of isopach contours** (y-axis) against the **square-root of the isopach area** (x-axis). On such plots, the exponential segment method of Fierstein & Nathenson (1992)[@Fierstein1992] states that a thickness $T$ at any $x$ value can be expressed as:

###### Equation 1

$$
T(x) = T_{0}e^{-k\sqrt{A}}
$$ 

with $T_0$  being the maximum deposit thickness, $k$ the slope of the exponential segment and $\sqrt{A}$ the square root of the isopach area. Based on the assumption of ellipsoidal shapes of isopachs Fierstein & Nathenson (1992)[@Fierstein1992] estimate the volume as:


###### Equation 2

$$ 
V = \frac{2T_0}{k^2}
$$

### Exercise 

Estimate the volume of Layer 5 using the 1-exponential segment method of Fierstein & Nathenson (1992)[@Fierstein1992] using the isopach map shown in Figure [1](#layer5):

- In Excel, import the <a href="../../../../../files/deposit/isopach.csv", target="_blank">isopach data</a> provided in Table 1 and plot the thickness ($cm$) versus the **square-root** of the area ($km$) as a **scatter plot**. Change the y-axis to a **logarithmic** scale

- Fit an **exponential** trendline and display its equation to estimate the intersect ($T_0$) and the thinning rate ($k$) as in [Equation 1](#equation-1)
  
!!! tip "Note on units" 
    
    $T_0$ as expressed from the equation is now in the same unit as the y-axis. You need to convert it to a unit consistent with the x-axis in order to calculate the volume, which will have the same unit to the cube.

    For instance, if both $sqrt(A)$ and $T_0$ are in $km$, then the volume will be in $km^3$.

- Calculate the `volume` of the tephra fallout deposit using [Equation 2](#equation-2)

- Estimate the corresponding `VEI` using the diagram in Fig. [2](#vei) from Newhall and Self (1982)[@newhall82]

- Convert the volume to a mass using a bulk density of 1000 $kg/m^3$ and calculate the associated `magnitude` following Pyle (2000)[@pyle2000]:

###### Equation 3

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

    | Isopach area (km$^2$) | Thickness (cm) |
    |-----------------------|----------------|
    | 46                    | 100            |
    | 85                    | 50             |
    | 130                   | 30             |
    | 330                   | 20             |
    | 387                   | 10             |
    | 685                   | 5              |


## Plume height

The method of Carey & Sparks (1986)[@Carey1986] relies on the construction of theoretical envelopes within which the vertical velocity of the column and the terminal velocity of a clast of specified size and density are equal. Based on this, the crosswind and downwind ranges of isopleth maps can be used to estimate plume height and wind speed. This method method was further updated by Rossi et al. (2019)[@Rossi2019] to account for a better parametrisation of physical processes in the plume (e.g., plume rise, settling velocity of particles).


![](img/deposit/envelopes.png)


 
### Exercise 

Calculate the plume height ($km$ above vent) with the method of Rossi et al. (2019)[@Rossi2019] (Fig. [3](#rossi1)). The <a href="../../../../../files/deposit/ML.pdf", target="_blank">provided map</a> contains measurements of *maximum lithics* (density of $2500\ kg/m^3$). This method works with isopleth contour values of 1.6 and 3.2 $cm$, so **make sure to contour isopleth accordingly**. Assume a mean sampling elevation of 2500 $m\ asl$. Cotopaxi has an elevation of 5700 $m\ asl$.

- Contour isopleths on the <a href="../../../../../files/deposit/ML.pdf", target="_blank">provided map</a>. Make sure you contour values that are presented in Figure [3](#rossi1).
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

Based on early theoretical studies of plume dynamics, Wilson & Walker (1987)[@Wilson1987] relate the **height of a plume to the MER**, with the height $H$ being proportional to the fourth root of the MER ($kg\ s^{−1}$). More recently, Degruyter and Bonadonna (2012)[@Degruyter2012] have proposed a new analytical expressions relating height and MER that accounts for the variability of the plume parameters and atmospheric conditions: 

###### Equation 4

$$
MER = \pi\frac{\rho_{a0}}{g'}\left(\frac{\alpha^2\bar{N}^3}{10.9}H^4 + \frac{\beta^2\bar{N}^2\bar{v}}{6}H^3\right)
$$

- Use the following values:
  
    - $\rho_{a0}$: reference density of the surrounding atmosphere (use 1.2259 kg m$^{-3}$) 
    - $g'$: reduced gravity at the source (use 45.6525 m s$^{-2}$)
    - $\alpha$: radial entrainment coefficient (use 0.1)
    - $\bar{N}$: average buoyancy frequency across the plume height (use 0.0156 s$^{-1}$) 
    - $H$: plume height (m above the vent) 
    - $\beta$: wind entrainment coefficient (use 0.5)
    - $\bar{v}$ average wind velocity across the plume height (use 8.7 m s$^{-1}$). Note that the average wind speed along the plume should be smaller than the wind speed that you have derived with the method of Rossi et al. (2019), which is the maximum wind speed at tropopause


### Exercise 

- Estimate the `mass eruption rate` (`MER`; $kg\ s^{-1}$) using the method of Degruyter and Bonadonna (2012)[@Degruyter2012] and the height obtained from isopleth maps. Note that this technique provides the **peak MER** of the eruption. 

- Use the MER to calculate the associated `intensity` following Pyle (2000)[@pyle2000]

###### Equation 5

$$
I = log_{10}(MER [kg\ s^{-1}]) + 3
$$


## :material-check-bold:{ .icn } Summary

This exercise provided an introduction on the characterisation of eruption source parameters from tephra fallout deposits, which is a critical process to infer the eruptive histories of volcanic systems from their stratigraphy. Namely, we learned:

- [x] How to calculate the **volume** of tephra deposits from **isopach** maps;
- [x] How to estimate the maximum **plume height** and **wind speed** from **isopleth** maps;
- [x] How to compute the **peak mass eruption rate** from plume height and wind speed;
- [x] How to estimate **VEI**, **magnitude** and **intensity** of eruptions.

## :fontawesome-solid-book:{ .icn } Further reading 

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

