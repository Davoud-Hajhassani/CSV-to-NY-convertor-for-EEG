# MOABB-to-NY-format

## NY format:
This format has been conceived for easily sharing EEG data in Python and Julia. Each file is understood as a separate recording. Data consist of two files and They have the same name and extensions `npz` and `yml` as you can see below.

![image](https://user-images.githubusercontent.com/95529379/174257112-5c1e8d80-b0dc-4c47-b1bc-9288a7e83c82.png)


### YML
The `yml` file holds all meta-data info of the recording in `yml` format which includes various information about the Acquisition, Documentation, Id, Stim, and Subjects.
For more details see the ' yml ' examples. 

### NPZ 
The `npz` file typically holds the EEG data matrix, a real matrix of dimension num. of samples x num. of electrodes and a vector of integer with the tags for stimulations, with as many entries as number of samples. The tags are 0 (zero) for no stimulation and then employs the natural numbers (1, 2,...) for different stimulation classes. 

## Converting procedure

### Data set in `csv` format
First you need to download or create the dataset in `.csv` format . In our case we are working on https://zenodo.org/record/3266930. This dataset contains electroencephalographic (EEG) recordings of 43 subjects playing to a visual P300 Brain-Computer Interface (BCI) videogame named Brain Invaders. EEG data were recorded using 32 active wet electrodes. The experiment took place at GIPSA-lab, Grenoble, France, in 2015.The full ID of this dataset is bi2015a.

### Structure of the Data set
The EEG recording of the 43 subjects for the three sessions, resting state and eyes closed are provided in `mat` and `csv` formats. Each file is a 2D-matrix where the rows contain the observations at each time sample. The first column of the matrix represents the timestamp of each observation. Columns 2 to 33 contain the recordings on each of the 32 EEG electrodes. In the recording of the sessions, column 34 (Trigger) is filled with zero except at the timestamp corresponding to the onset of a stimulation where it gets the value of one. We also provide columns 35 (Target) which is filled with zeros, except at the timestamp corresponding to the onset of a Target flash where it gets the value of one.

### `yml`creating 

The `yml` file should be provided for all the files within the data set. in this case we need 129 `yml` file (# of subjects x # of sessions x # of runs). In order To create them you simply need to address all the variables and parameters in the `yml` section of the `CSV_to_NY.ipynb`

### `npz` creating 
As mentioned it above, The 'npz' file holds the EEG data including data and stim. `npz` contains data matrix and stim vector (['data','stim']). The data matrix contains columns 2 to 33 except the reference or ground columns (the fourth column in this data set).Furthermore, the stim vector contains the sum of the Trigger and Target columns (34 and 35 in this data set).

## Note
currenly this code only accept the data sets in the format of `csv` with the same data structure in bi2015a. For more details, please check the documentaion of the Data set in https://hal.archives-ouvertes.fr/hal-02172347.  




