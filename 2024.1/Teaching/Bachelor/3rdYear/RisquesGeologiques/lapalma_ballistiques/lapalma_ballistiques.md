# Estimer l'aléas et l'impact des retombées de balistiques

> **Module risques volcaniques**

> Sébastien Biass, Simon Thivet, Allan Fries

> 13 Mars 2023

---

!!! warning "Cet exercise est fictif!"

    Les conditions d'aléas et de vulnérabilité physique présentés dans cet exercise sont 100% fictifs!

## :material-format-list-checks:{ .icn } Introduction

Depuis quelques jours, une augmentation du niveau sismique a laissé penser qu'une nouvelle éruption était imminente sur l'île de La Palma (Figure 1). Ce matin, le bruit sismique à migré de façon inattendue vers la localité d'El Remo. Un tremblement de terre a endommagé la seule route liant El Remo à la route principale permettant l'évacuation. Depuis, l'éruption a commencé, créant un cone d'une hauteur d'environ 100 mètres situé à environ 1 km du village, situé à la hauteur de la mer. La mer étant mauvaise, une évacuation par bateau ou hélicoptère est pour l'instant impossible et les habitants et touristes ont reçu la recommendation de s'abriter à l'intérieur.

Une étude rapide de l'évolution de l'éruption révèle que:

1. Du à la morphologie du cone, la lave s'écoule vers le nord-ouest et ne devrait pas atteindre El Remo. La coulée devrait entrer en contact avec l'océan d'ici à demain
2. Les vents viennent du nord-est
3. Le principal aléa en ce moment est l'éjection de blocks suivant une trajectoire parabolique (balistique)

Vous faites partie du conseil scientifique assemblé pour conseiller PEVOLCA (*Plan Especial de Protección Civil y Atención de Emergencias por riesgo volcánico en la Comunidad Autónoma de Canarias*) sur l'aléas et les impacts possible durant la gestion de crise. 

### Objectifs

Dans ces modules, vous avez gagné une compréhension des tenants et aboutissants autour des concepts d'impact et de risque. Ici, le but est d'illustrer le soutient que des **analyses d'impact rapides** peuvent apporter à une situation de **gestion de crise**. Nous nous focaliserons principalement sur la **vulnérabilité physique** du bâti.

<figure markdown>
![map](img/map.png)
    <figcaption>Figure 1: Cas d'étude. En haut à gauche: La Palma. En haut à droite: Village d'El Remo. En bas à droite: Zoom sur les habitations. Le cercle rouge montre une distance de 1000 m. </figcaption>
</figure>

---

## :fontawesome-solid-gears:{ .icn } Tâches

### 1. Estimer l'intensité de l'aléa lié aux retombées de blocks

Basé sur des modèles disponibles, il est estimé que la masse la plus probables des blocks pouvant atteindre El Remo est de **0.4 kg**. Les équations ci-dessous permettent **d'estimer l'énergie cinétique au moment de l'impact** d'un bloc de cette masse. Notez que ce système d'équation est basé sur quelques hypothèse:

1. Les blocks sont éjectés à un angle de 45 degrés (→ on considère la distance maximale atteinte par un objet balistique)
2. Les blocks sont des sphères et on considère une trajectoire parabolique dans le vide (→ on néglige les forces de drag)

!!! question "Question 1"

    Réorganiser les **équations 1-4** pour estimer **l'énergie cinétique** qu'on des blocs de 0.4 kg au moment de l'impact.

#### Equations

<figure markdown>
![map](img/sketch.png)
    <figcaption>Figure 2: Sketch du cas d'étude. </figcaption>
</figure>

##### Equation 1

- L'équation 1 décrit la hauteur du bloc $z$ (m) en fonction du temps $t$ (s), de l'élévation initiale $z_0$ (m), de la vitesse d'éjection $v_0$ (m/s):
  > $z = z_0+\frac{v_0}{\sqrt{2}}t-\frac{1}{2}gt^2$, où $g=9.81\ m/s^2$

##### Equation 2

- L'équation 2 décrit la distance horizontale $d$ (m) en fonction du temps $t$ (s):
  > $d = \frac{v_0}{\sqrt{2}}t$

##### Equation 3

- L'équation 3 décrit la vitesse du bloc $v$ (m/s) en fonction du temps $t$ (s):
  > $v = \sqrt{v_{x}^2+v_{z}^2}$

- L'équation 3.1 décrit la composante horizontale de la vitesse:
  > $v_x = \frac{v_0}{\sqrt{2}}$   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Eq. 3.1)

- L'équation 3.2 décrit la composante verticale de la vitesse:
  > $v_z = \frac{v_0}{\sqrt{2}}-gt$   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(Eq. 3.2)

##### Equation 4

- L'équation 4 décrit l'énergie cinétique $E_k$ (J) au moment de l'impact en fonction de la masse $m$ (kg) et de la vitesse à l'impact $v$ (m/s):
  > $E_k = \frac{1}{2}mv^2$

??? tip "Réorganiser les équations?"

    1. La quantité qui nous intéresse est l'énergie cinétique $E_k$. Pour cela nous avons besoin de **l'équation 4**, mais il nous manque la valeur de vitesse $v$.
    2. Il faut donc réorganiser **l'équation 3**, mais elle requiert les valeurs de vitesse initiale $v_0$ ainsi que le temps total $t$ jusqu'à l'impact.
    3. $t$ peut être obtenu de **l'équation 2**, mais nous avons besoin de $v_0$ pour cela.
    4. $v_0$ peut être obtenu de **l'équation 1**!

--- 

### 2. Estimer l'impact potentiel sur les habitations 

La figure 3 ci-dessous présente des valeurs d'énergie cinétique limites pour la perforation de toits constitués de matériaux différents. La localité d'El Remo contient principalement des habitations faites de toits en métal.

!!! question "Question 2"

    Les habitations typiques d'El Remo constituent-elles un abris suffisant contre des impacts causés par des blocks de 0.4 kg?

<figure markdown>
![map](img/energies.png)
    <figcaption>Figure 3: En haut: Classification du types de toits; En bas: fourchette d'énergies pouvant causer une perforation en fonction du type de toit. </figcaption>
</figure>


### 3. Identifier des abris possibles 

!!! question "Question 3.1"

    Il existe un bâtiment avec un toit en béton armé (=reinforced concrete) où tous les résidents pourraient s'abriter quelques temps. Quelle est la taille minimum d'un bloc pouvant causer une perforation?


!!! question "Question 3.2"

    Les modèles estiment que la probabilité d'occurrence d'un bloc de cette taille est de $10^{-3}$ (soit 1 chance sur 1000). Réfléchissez à ces différents aspects:

    - Pensez-vous que cette probabilité soit haute/faible?
    - Pensez-vous que cette probabilité soit acceptable?
    - Feriez-vous une recommendation à PEVOLCA? Comment répondriez-vous si ils vous le demandaient?

### 4. Autres impacts possibles 

!!! question "Question 4"

    PEVOLCA vous demande à quels autres aléas les habitants peuvent être exposés. En se basant sur vos connaissances incomensurables en matière d'aléas volcaniques et de la situation, que répondez-vous? 


