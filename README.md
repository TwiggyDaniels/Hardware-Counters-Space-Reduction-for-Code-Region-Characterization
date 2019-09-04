## About this repository

This repository contains the experimentation of the paper Hardware Counters’ Space Reduction for Code Region Characterization, which can be found in:
https://www.researchgate.net/publication/335232384_Hardware_Counters'_Space_Reduction_for_Code_Region_Characterization
https://link.springer.com/chapter/10.1007/978-3-030-29400-7_6
In this paper we reduce the number of hardware performance counters needed in order to characterize a parallel region.


## How to execute the examples

In order to run the examples to need to install:

[`Python 3.6`](https://www.python.org/downloads/)

[`R 3.6`](https://cran.r-project.org/)

[`Jupyter`](https://jupyter.org/)


## File description

* PCA and Correlation All Hardware Counters.ipynb :
	Script in jupyter notebook which uses R to make a PCA with the information obtained with the hardware performance counters for the different patterns.
	After the PCA is executed, correlation analysis is performed and three correlation matrices are shown using different sorting of the columns.

* PCA and Correlation Reduced List.ipynb :
	This is the final evolution of the previous jupyter notebook. In this case we have reduced the number of available events to the limit we found without losing data.
	To reproduce the middle steps, the previous script should be executed multiple times reducing the number of events until this script is obtained.
	
* Neural Network.ipynb :
	This is a jupyter notebook using Python. A simple neural network is used to verify that the resulting hardware performance counters can be used to identify the different parallel regions.
	We use a simple neural network with only one hidden layer. THe data used for training is all the sizes except two, which are used in the predictions to test if the characterization can be performed.

Sometimes github fails opening jupyter notebooks, if this problem appears, use nbviewer: https://nbviewer.jupyter.org/

## LICENSE (GPL):

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, version 3.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
 
You should have received a copy of the GNU General Public License along with this program. If not, see <http://www.gnu.org/licenses/>.
