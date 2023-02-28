# SimSVC
SimSVC is a live interaction simulator for modeling changes in chromatin interactions induced by strcutural variations (SVs), 
which is versatile enough to simulate both simple and complex genomic rearrangements.
## Installation
First, install following python packages through conda:
```
$ conda config --add channels defaults
$ conda config --add channels bioconda
$ conda config --add channels conda-forge
$ conda create -n SimSVC python=3.7 numpy pyqt5 matplotlib scipy scikit-learn sortedcontainers
```
**Note**


`scipy `, `scikit-learn` and `sortedcontainers` are required if the user needs to run the FitHiC2 module.

## Usage
### The interface for SimSVC
First, run the following command to open the user interface for SimSVC.
 ```
 $ python mainPlatform.py
 ```
 ### Input of reference Hi-C data
Click the ```BED``` and ```MATRIX``` buttons to pop up the file dialog to obtain the interaction interval file and the interaction matrix file respectively.
 After selecting the file, the path to the file is displayed in the edit line to the left of the button. After the user clicks the ```Load``` button, the software 
 checks to see if files exist. If files are valid, the above buttons are locked. The user can click the ```Chromosome``` drop-down box to select the chromosome 
 to be simulated, and the number of chromosomes is extracted from the BED file. After clicking the ```Confirm``` button, the drop-down box will not be modified, and the input of reference Hi-C data is completed.
 **Note**
 Here, we provide the test data, which is  a 20M segment of chromosome 10 from GM12878 cell line. Users can use the test data to verify that the software is running.
 ### Input of SV events
 Different types of SV require different input information.
 
 
 For deletion, duplication and inversion, the user needs to enter the start and end position of the SV event.
 
 
 For intra-chromosomal translocation, the user needs to provide the start and end positions of the fragment where the translocation occurs and where to translocate.
 
 
 For inter-chromosomal translocation, the user needs to provides the breakpoint of one chromosome and the breakpoint of another chromosome.  
 
 
 The user can add a new structural variation event by clicking the ```Add``` button. The three buttons on the interface can be used to adjust the order of multiple structural variations, with the functions of moving up, moving down and deleting respectively.
 ### Running the fithic2 module
 When the user is simulating structural variation for the first time, the user need to click the ```FitHiC2``` button to generate the background model. 
 Since this process takes some time,  the result of FitHiC2 will be saved in the directory  ```../result```. 
 
 
 If users need to simulate the current chromosome region again, they can click the button ```Use Local File```to upload the file to improve the operation efficiency.
 ### Output
 The simulation results for each sample are visualized in the panel as square heatmaps. The display of the simulated Hi-C maps focuses on SV regions rather than the whole chromosome, 
 and the visualization range is determined based on the leftmost and rightmost loci of all SV events. 
 
 
 Furthermore, SimSVC provides the parameters to control the visual properties of the maps. Users can adjust the maximum and minimum values of the matrix to reduce the background signals and make the interactions of SV regions more visible. 
 Here, these values cannot be less than the minimum value of the contact interaction and cannot be greater than the maximum value of the contact interaction. 
 
 
 These heatmaps can be exported as ‘.pdf’ image files (click ```Save Heatmap```)and simulated Hi-C data can be saved as a matrix (click ```Export HiC Map```) or a BED file (click ```Export Matrix File```) in TXT format.
 
 
 
 




