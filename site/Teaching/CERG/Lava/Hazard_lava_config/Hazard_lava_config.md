# Setting up QGIS

This section explains how to install [Q–LavHA](https://we.vub.ac.be/en/q-lavha), a model for the probabilistic hazard assessment of lava flows working as a `QGIS` plugin. 

## Objectives

- Install `Q–LavHA`.

## Installing Q-LavHA 


1. From the `Moodle` page of the class, download the `VolcanicRisk2024.zip` file and extract it somewhere **on your personal user drive.**
2. Make sure `QGIS` is closed.
3. In Windows, navigate to the following folder, where `$USER` is your ISIS username:

!!! tip "Alternative link"
    [Alternative dowload link](https://kdrive.infomaniak.com/app/share/250506/f6653aca-6802-4d55-b37f-1f3819057003) 

=== "Windows"

    ```
    C:\Users\$USER\AppData\Roaming\QGIS\QGIS3\profiles\default\python\plugins
    ```

=== "Mac OS"

    ```
    /Users/$USER/Library/Application Support/QGIS/QGIS3/profiles/default/python/plugins/
    ```

!!! warning
    - If the `plugins` folder doesn't exist, please create it.
    - The `Users\` folder might be named `Utilisateurs` in French

1. Copy the `Qlavha_v3` folder to the `plugins` folder.

!!! danger "Use your user disk!"

    If you are using the PC of the computer lab, make sure **your files are saved on your personal drive!** This is typically the `H:\` drive. Otherwise, your files **will be deleted every time you logout!**


## Starting QGIS

- Search for `QGIS 3.2x` and start it. Depending on the computer, the version might vary between `3.20` and `3.28`. Please take the most recent one. **Avoid QGIS 3.8!**

### Activate Q-LavHA

To activate `Q–LavHA` in `QGIS`:

1. Re-open `QGIS` as previously.
2. From the [Menu Bar](QGIS_Intro.md#the-qgis-interface), open the `Plugins` > `Manage and Install Plugins` window.
3. Following [Figure 1](#fig1), search for `lava` and activate the plugin.
4. There should now be a `Q-LavHA` icon in the [Toolbar](QGIS_Intro.md#the-qgis-interface).

<figure markdown>
  ![QGIS_plugin](img/qgis/qgis_plugin.png){#fig1}
  <figcaption>Figure 1: Activate the Q–LavHA plugin</figcaption>
</figure>

## Loading data

The `VolcanicRisk2024.zip` file downloaded from `Moodle` contains a `Lava flow exercise` folder that contains these files:

- `LaPalma_basemap.qgz`: Main `QGIS` file. 
- `Lava flow exercise/Data/`
    - `exercise.gpkg`: Geopackage containing some vector files for the exercise. 
    - `lapalma.gpkg`: Geopackage containing some vector files on previous eruptions at La Palma. 
    - `osm.gpkg`: Geopackage containing [openstreetmap](http://openstreetmap.org) files. 
    - `DEM/`: Folder containing some pre-processed DEM files. 
    - `Hydro`: Folder containing hydrological analyses.

Open the `LaPalma_basemap.qgz` file. 

!!! warning "Centering the map"

    If you don't see any data on the map, click the `Background` layer group in the [Layer panel](QGIS_Intro.md#the-qgis-interface) and click `Zoom to group`. 

    <figure markdown>
    ![zoom](img/qgis/zoom.png){width="450px"}
    <figcaption></figcaption>
    </figure>

You should now see something similar to this:

![data](img/qgis/qgis_data.png)

!!! danger "Save regularly!"

    `QGIS` is amazing, but it can be unstable at time. **Make sure you regularly save your project throughout the exercise!**

