# Toronto Rental Analysis

## Overview

I created an interactive dashboard using Toronto real estate data, including [Toronto Census Data](https://github.com/sarahm44/rental-analysis/blob/main/toronto_neighbourhoods_census_data.csv) and [Toronto Neighbourhood Coordinates](https://github.com/sarahm44/rental-analysis/blob/main/toronto_neighbourhoods_coordinates.csv), with the help of the [Mapbox API](https://www.mapbox.com/).

This dashboard's goal is to provide charts, maps, and interactive visualizations that help customers explore the data and determine if they want to invest in rental properties in Toronto.

## Rental Analysis

The code for the rental analysis is contained in [rental_analysis.ipynb](https://github.com/sarahm44/rental-analysis/blob/main/rental_analysis.ipynb).

### Dwelling Types Per Year
This section calculates the number of dwelling types per year and visualizes the results as a bar chart using the Pandas plot function.

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dwelling_types01.png)
![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dwelling_types02.png)
![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dwelling_types03.png)
![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dwelling_types04.png)

### Average Monthly Shelter Costs in Toronto Per Year

This section visualizes the average monthly shelter costs per year to better understand the rental income trends over time. See below the average (mean) shelter cost for owned and rented dwellings per year:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/shelter_costs.png)

### Average House Value per Year

This section determines the average house value per year. An investor may want to better understand the sales price of the rental property over time. For example, a customer will want to know if they should expect an increase or decrease in the property value over time so they can determine how long to hold the rental property.

See below the average house value in Toronto per year:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/house_value.png)

### Average House Value by Neighbourhood

This section compares the house value by neighbourhood. By using `hvplot`, the graph includes an interactive dropdown selector for the neighbourhood. See in the image below:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/value_by_neighbourhood.png)

### Number of Dwelling Types per Year

This section visualizes the number of dwelling types per year in each neighbourhood. This provides investors with a tool to understand the evolution of dwelling types over the years.

By using `hvplot`, the graph includes an interactive visualization of the average number of dwelling types per year with a dropdown selector for the neighbourhood. See in the image below

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dt_per_year.png)

### Top 10 Most Expensive Neighbourhoods

In order to ascertain which neighbourhoods are the most expensive, I calculated the mean house value for each neighbourhood and then sorted the values to obtain the top 10 most expensive neighbourhoods on average. 

The results are plotted as a bar chart:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/10_most_expensive.png)

### Neighbourhood Map

In this final section I read in neighbourhood location data and built an interactive map with the average prices per neighbourhood. A scatter Mapbox object from Plotly express was used to create the visualization.

See the visualisation below:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/map.png)

### Cost Analysis

See below a bar chart row facet created to plot the average house values for all Toronto neighbourhoods per year:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/value_neighbourhood.png)

See below a sunburst chart to conduct a cost analysis of the most expensive neighbourhoods in Toronto per year:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/sunburst.png)

## Dashboard

The [dashboard.ipynb](https://github.com/sarahm44/rental-analysis/blob/main/dashboard.ipynb) notebook contains the dashboard code. 

See the dashboard below:

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dashboard.png)

## Environment

This repo utilises PyViz. It is recommended the following are installed in a new environment.

### New Environment

Create a new environment using:

```shell
conda update anaconda
conda create -n pyvizenv python=3.7 anaconda -y
conda activate pyvizenv
```

### Before You Install PyViz Dependencies

Before installing the PyViz dependencies, you need to install a couple of libraries. First, install the `python-dotenv` library using `pip` to work with environment variables.

```shell
pip install python-dotenv
```

Next, install the `nb_conda` package that will allow you to switch between virtual environments in Jupyter lab.

```shell
conda install -c anaconda nb_conda -y
```

### PyViz and its Dependencies

Follow the next steps to install PyViz and all its dependencies in your Python virtual environment.

1. Download the PyViz dependencies **nodejs** and **npm** (included in nodejs).

    ```shell
    conda install -c conda-forge nodejs=12 -y
    ```

2. Use the `conda install` command to install the following packages. Note: On some of these installs, you may get a message that says that the requested packages are already installed. That is fine. Conda is really good at installing all of the required dependencies between these tools.

    ```shell
    conda install -c pyviz holoviz -y
    conda install -c plotly plotly -y
    conda install -c conda-forge jupyterlab=2.2 -y
    ```

3. Use pip to install the correct versions of `matplotlib` and `numpy` using the following commands:

  ```shell
  pip install numpy==1.19
  pip install matplotlib==3.0.3
  ```

4. PyViz installation also requires the installation of Jupyter Lab extensions. These extensions are used to render PyViz plots in Jupyter Lab. Execute the below commands to install the necessary Jupyter Lab extensions for PyViz and Plotly Express. 

    * **IMPORTANT:** _In some installation cases you may encounter the following warning. If you do, **continue with the installations as indicated**, as this warning will **not** affect your code._

      ```
      Config option `kernel_spec_manager_class` not recognized by `EnableNBExtensionApp`
      ```

    * Set `NODE_OPTIONS` to prevent "JavaScript heap out of memory" errors during extension installation:

      ```shell
      # (OS X/Linux)
      export NODE_OPTIONS=--max-old-space-size=4096

      # (Windows)
      set NODE_OPTIONS=--max-old-space-size=4096
      ```

    * Install the Jupyter Lab extensions: 

      ```shell
      jupyter labextension install @jupyter-widgets/jupyterlab-manager --no-build

      jupyter labextension install jupyterlab-plotly --no-build

      jupyter labextension install plotlywidget --no-build

      jupyter labextension install @pyviz/jupyterlab_pyviz --no-build
      ```

    * Build the extensions (This may take a few minutes):

      ```shell
      jupyter lab build
      ```
    
    * Using the `build` and `--no-build` flags allows the machine to build all four extensions simultaneously, otherwise you will have to wait several minutes in between in each installation.
        
    * After the build, unset the node options that you used above:

      ```shell
      # Unset NODE_OPTIONS environment variable
      # (OS X/Linux)
      unset NODE_OPTIONS

      # (Windows)
      set NODE_OPTIONS=
      ```

5. Run the following commands to confirm installation of all PyViz packages. Look for version numbers with at least the following versions.  

      ```shell
      conda list nodejs
      conda list holoviz
      conda list hvplot
      conda list panel
      conda list plotly
      ```

      ```text
      nodejs                    12.0.0
      holoviz                   0.11.3
      hvplot                    0.7.1
      panel                     0.10.3
      plotly                    4.14.3
      numpy                     1.19
      matplotlib                3.0.3
      ```

6. You will also need to register for a public mapbox API key, which can be obtained via [this sign-up link](https://account.mapbox.com/auth/signup/). Detailed information on how Mapbox can be used to generate plots can be found on [Plotly's documentation page](https://plotly.com/python/scattermapbox/#mapbox-access-token-and-base-map-configuration).

## How to Run the Dashboard

![](https://github.com/sarahm44/rental-analysis/blob/main/Images/dashboard.png)

### Running the Dashboard
In order to run the Dashboard, run the code in **dashboard.ipynb** file.
At code block titled "Serve the Panel Dashboard", run the code "dashboard.servable()".
The output will be the Dashboard.

### Interacting with the Dashboard
You can navigate the data by clicking on each tab at the top of the Dashboard.
Some of the charts and graphs are interactive. See details to navigate each tab below.

| Tab           | Instructions | 
| ------------- |-------------| 
| Welcome      | You can zoom in and out on the map of Toronto, and navigate around the map. Hover your cursor over a dot on the map to view more data associated with that neighbourhood. | 
| Yearly Market Analysis     | These graphs are static, but you can scroll across or up and down to view. |  
| Shelter Cost vs House Value | These graphs are static, but you can scroll across or up and down to view. |  
| Neighbourhood Analysis | On each chart use the dropdown menu to view data for different neighbourhoods. You can also navigate around these graphs through tools such as zoom, pan etc.|
|Top Expensive Neighbourhoods | These charts are also interactive. Zoom or move around on the bar chart. On the sunburst chart you can hover your cursor to view more data.|
