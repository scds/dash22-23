---
layout: default
title: Jupyter
nav_order: 2
parent: Copying ArcGIS Online Content
---

# Jupyter Notebook 

The second method to copy content between ArcGIS accounts is using a Jupyter notebook.

Click on the binder badge below or use [this link](https://mybinder.org/v2/gh/scds/dash-webinars/main?labpath=%2Fcopy_arcgis_content.ipynb) to start the interactive tutorial in your own Jupyter Notebook.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/scds/dash-webinars/main?labpath=%2Fcopy_arcgis_content.ipynb)

You can also choose to [download the notebook](https://github.com/scds/dash-webinars/blob/main/copy_arcgis_content.ipynb) or copy the following code snippets if you prefer to work in another environment.

## Imports 

Import the arcpy, GIS, and getpass python libraries. 

``` 
import arcpy 
from arcgis.gis import GIS
import getpass
``` 

## Login parameters – source 

Login to the ArcGIS portal that contains the Hamilton Zoning map (or other content being copied). 

``` 
print("Please enter your credentials for the SOURCE ArcGIS portal.")  
print("==========")  
print("")  

source_url = input(prompt='URL: ')  
source_user = input(prompt='Username: ')  
source_pass = getpass.getpass(prompt='Password: ')  
print("")  

gis_source = GIS(source_url, source_user, source_pass) 
``` 

## Login parameters – destination 

Login to the target ArcGIS portal where the content is being copied to. 

``` 
print("")  
print("Please enter your credentials for the DESTINATION ArcGIS portal.") 
print("==========")  
print("")  

target_url = input(prompt='URL: ')  
target_user = input(prompt='Username: ')  
target_pass = getpass.getpass(prompt='Password: ')  
print("")  

gis_destination = GIS(target_url, target_user, target_pass) 
``` 

## Search and display contents 

Search for the Hamilton Zoning map by title and item type. Using the parameter _outside_org=False_ restricts the search to only items within your organization.

The content can be filtered by owner and displayed to include the ID of the item, which will be used in the next step.

``` 
print('')  
print('Portal contents:')  
print('================')  

search_my_contents = gis_source.content.search(query='title: Hamilton Zoning', item_type='Web Map', outside_org=False)  

from IPython.display import display  

for item in search_my_contents: display(item,item.id) 
``` 

## Clone web application 

Locate the ID number from the sample web map in the list produced above, and clone the map to the target portal. 

``` 
print('================')  
print("")  
web_app_id = input(prompt='Copy and paste the ID number from the above list for the application to be cloned: ')  

print("Cloning application...")  
item = gis_source.content.get(web_app_id)  
cloned_items = gis_destination.content.clone_items(items=[item], copy_data=True) 

print("Completed!") 
``` 
