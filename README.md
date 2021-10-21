# iGEM Groningen 2021 - ART

Welcome to the github repoistory of iGEM Groningen 2021! Here you will find the code we used to incorporate the 
[Automated Recommendation Tool](https://sites.google.com/lbl.gov/art/home?authuser=0) into our project. The aim of using 
this tool was to make predictions on which combination of chassis, promoter, secretion peptide and alpha-amylase 
encoding gene would eventually result in a high alpha-amylase activity in the supernatant of the device in which all 
parts are combined. For an explanation on why there specific parts were chosen, please have a look at the 
[Engineering page](https://2021.igem.org/Team:Groningen/Engineering) of our [wiki](https://2021.igem.org/Team:Groningen). 

In order to run the code on this repository, a licence for the ART needs to be obtained first. Instructions on how to do 
this can be found [here](https://github.com/JBEI/ART#license). Once a licence has been obtained, follow the installation 
instructions and place the source code of art in the parent directory of this project. Have a look at the tutorials 
provided with the ART for an example of the correct project structure.

Once the ART has been properly installed, other dependencies can be installed using the 
following command:

`
pip install -r requirements.txt
`

The code is divided into three separate jupyter-notebooks, each representing one of the steps of the pipeline shown in figure 1

![test](https://2021.igem.org/wiki/images/4/43/T--Groningen--Model_pipeline_horizontal.png)
***Figure 1:*** *A description of the pipeline within this project. Between step 1 and 2, the actual measurements need 
to be taken. While python is great at automating a pipeline, this is unfortunately one of the few steps that cannot be 
automated*

## Step 1
Step 1 is covered in `Subsetting_combinatorial_library.ipynb`. In this notebook, a balanced subset is created from a 
combinatorial library. It produces a `sample_list.csv` where the measured activity is missing. Note that each part-variant
is assigned its own index. These indices need to be linked to the names of the actual parts using some sort of translation 
dictionary. `part_names.csv` is used for this purpose.

## Step 2
Step 2 is covered in `Preprocessing_v2.ipynb`. This file uses `sample_list.csv` and raw absorbance measurements from 
the Alpha-Amylase Assay to connect the samples with their activity measurement. The raw data used for this is located in
the `/training_data` folder. Each 96 well plate is given its own sub-folder where the name of the folder indicates the day at 
which the measurements were taken. On the 5th of October, experiments were conducted on 2 96-well plates and hence there are two folders
starting with `5-10`. More information about the raw measurements can be found in the `README.txt` located in each folder.
Note that the notebook needs to be executed once for each 96 well-plate.


In addition to extracting the activity, the natural logarithm of the activity is also determined and stored as 
"Corrected activity". This is a preprocessing step needed for the ART. Both the "Activity" and "Corrected activity" of 
the samples contained on the 96 well-plate are written into `sample_list.csv`. 

## Step 3
Step 3 is covered in `Performing_ART_analysis.ipynb`. All the Machine Learning used for our project is covered in this 
step. The produced model is thoroughly analysed to give some insights on how well the model will be able to generalise 
to new data. Furthermore, the predicted corrected activity of the tested samples is saved to `ART_out/filled_sample_list.csv`.
Finally, 30 exploitative recommendations are saved to `ART_out/exploit_reccomend.csv` and 30 explorative recommendations are 
saved to `ART_out/explor_reccomend.csv`.
