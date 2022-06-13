## MOABB-to-NY-format
# convert .csv format to NY which is easily readable in Julia.
This format has been conceived for easily sharing EEG data in Python and 
Julia. Each file is understood as a separate recording. Data consist of two
files. They have the same name and extensions `npz` and `yml` (this file).
The `npz` file typically holds the EEG data matrix, a real matrix of 
dimension num. of samples x num. of electrodes and a vector of integer with
the tags for stimulations, with as many entries as number of samples. The 
tags are 0 (zero) for no stimulation and then employs the natural numbers 
(1, 2,...) for different stimulation classes.

The `yml` file holds all meta-data info of the recording in `yml` format. 
