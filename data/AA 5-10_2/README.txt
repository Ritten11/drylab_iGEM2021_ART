---------------------------
Absorbance files
---------------------------

There are 15 .txt files that show absorbance at 15 different time-points. The files are named as hh.mm.txt where hh corresponds to the hour and m corresponds to the minute of the time-point at which the measurement was recoreded (e.g. the file 19.02.txt was recored at 19:02).

---------------------------
OD and plate arrangement
---------------------------

The "OD and Well Plate Arrangement.xlsx" file contains the OD values and shows the arrangement of the well plate.

The OD values are located int the "OD" sheet. The values in the column D ("OD (stadardized)") should be used. These measurement originate from two different well plates and thus there are two baseline OD values. Which baseline OD was substracted from which sample can de deduced from the "OD.xlsx" in the "Raw" folder.

The well plate arrangement is located in the "Well Plate Arrangement" sheet. Due to running out of measuring agents, sample #57 was only measured in dublicates. Samples #17, #40, #43 and #64 were treated slightly different than the other samples as there was a minor incident in the substracte extraction process.

Both sheets are also exported as .csv files for easy integration into the ART-pipeline as respectively "plate_arrangements.csv" and "OD_standerdized.csv". In these .csv files, all redundant information was manually removed
---------------------------

All raw data is located in the folder "Raw".

