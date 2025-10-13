# Sentinel 2 data

This repo contains the presentation and resources for a lecture about Sentinel 2 as part of TEK4710 at ITS, UiO.

The presentation includes a demo of how to download Sentinel 2 data using the Copernicus Browser, visualise the data and calculate the NDVI index. 

If you are a participant in that course, as a pre-homework, I would like you to read this README.md before the class. 


## How to create a Copernicus Data Space account

[Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/) is the platform that distributes the data from European Space Agency's satellites. 

In order to download data from Copernicus, you have to create a user account. To do this, you click on the Register button here: [Sign in to Copernicus Data Space Ecosystem](https://identity.dataspace.copernicus.eu/auth/realms/CDSE/protocol/openid-connect/auth?client_id=cdse-public&response_type=code&scope=openid&redirect_uri=https%3A//dataspace.copernicus.eu/account/confirmed/1), fill out the form and hit Register. (If anyone has used the old Open Access Hub and had an account there, this is not the same platform, so you will need to register here.) 

## What you need to install in order to run this notebook

Please, try to get this conda environment ready before the class.

### 1. First of all you need [Anaconda](https://www.anaconda.com/download) 

Anaconda is the easiest way to get coding with Python, so go ahead and install if you don't have it yet.
Installing Anaconda should provide all you need, including the jupyter notebooks. 
### 2. Create a new environment with the right packages

Most projects will require you to install a bunch of Python packages. It can get messy fast, because many 
packages depend on each other. It's good practice to make a new virtual environment, called conda environment
in this case, for any new projects. 
These are the packages used in this project:  
* jupyter (for jupyter notebook)
* ipykernel (jupyter) 
* ipywidgets (jupyter)
* rasterio (to work with geotiffs in Python)
* matplotlib (for plotting)
* shapely (working with geometries)
* pyproj (working with projections)  

Note: In Jupyter notebook you will need to pick the right environment. 
You have two options for creating the env and istalling packages: 

#### a) Install it yourself   

To do this, you go to Anaconda Powershell Prompt and type:   

```conda create --name <your_env_name>``` where <your_env_name> can be something like sentinel2 or whatever you want.

Then type ```conda activate <your_env_name>``` and you can start using it.  

You install packages with ```conda install -c conda-forge <package_name>```, so you can do `conda install -c conda-forge jupyter ipykernel ipywidgets rasterio matplotlib shapely pyproj` in one go. 

#### b) Install from the environment.yml file

Download the `environment.yml` file from this repo, then go to Anaconda Powershell Prompt, navigate to the folder where you store the file and run:  
`conda env create -f environment.yml`.  
This will create the environment, give it the name that I called mine, i.e. `Sent2Intro24` and install the necessary packages. You can then activate the environment by typing ```conda activate Sent2Intro24```.

## Side-note about Copernicus Open Access Hub vs Copernicus Data Space Ecosystem

The [Copernicus Open Access Hub](https://scihub.copernicus.eu/), which was previously distributing esa’s data, has closed at the end of October 2023. The new service is called [Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/) and it provides a simple [Browser](https://browser.dataspace.copernicus.eu/?zoom=5&lat=50.16282&lng=20.78613&themeId=DEFAULT-THEME&visualizationUrl=U2FsdGVkX189mCFCYnDD3UnASaMbX0sftnlKaN3uO6insQGa7BZae5N4qzS8XaMSkDRUDKafY42Hj90c5dZ%2F2RTG0v7Bn8WHkn9b6DBcb4hPVVHLGwPtC3fq3FPlMZac&datasetId=S2_L2A_CDAS&demSource3D=%22MAPZEN%22&cloudCoverage=30&dateMode=SINGLE) that you can use to download data. 

In this class we will be using the Browser, but apart from the Browser, the new Copernicus Data Space provides a number of APIs to download data. 

If you search around for APIs to download Sentinel data, you will surely run into many of them. Particularly the Python library called sentinelsat used to be very popular, and you will find it used in a lot of older code examples. However, it was based on the old Open Access Hub, which isn’t up anymore, so the sentinelsat package doesn’t work. There are probably other third-party libraries that also got broken because of this (just so you know if you try something and it doesn’t work). 

Some of the APIs that work with the new Copernicus Data Space Ecosystem are listed here: [APIs | Copernicus Data Space Ecosystem](https://dataspace.copernicus.eu/analyse/apis).