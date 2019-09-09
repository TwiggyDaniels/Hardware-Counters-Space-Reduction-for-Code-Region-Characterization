## About this repository

This repository contains the experimentation done for the paper "Hardware Counters’ Space Reduction for Code Region Characterization" published in Euro-Par 2019, which can be found in:

https://www.researchgate.net/publication/335232384_Hardware_Counters'_Space_Reduction_for_Code_Region_Characterization

https://link.springer.com/chapter/10.1007/978-3-030-29400-7_6

In this paper we introduce a methodology, based in Principal Component Analysis (PCA) and correlation analysis, for reducing the number of hardware performance counters needed for characterizing an OpenMP parallel region.

|**If you use these results, please, reference this paper as:**|
|-----------------------------------------------------------|
|Alcaraz J., Sikora A., César E. (2019) Hardware Counters’ Space Reduction for Code Region Characterization. In: Yahyapour R. (eds) Euro-Par 2019: Parallel Processing. Euro-Par 2019: 74-86. Lecture Notes in Computer Science, vol 11725. Springer, Cham|


## How to execute the examples

In order to run the examples you need to install:

[`Python 3.6`](https://www.python.org/downloads/)

[`R 3.6`](https://cran.r-project.org/)

[`Jupyter`](https://jupyter.org/)


## File description

* PCA and Correlation All Hardware Counters.ipynb :
	Script in jupyter notebook which uses R to make a PCA with the information obtained with the hardware performance counters for the four different patterns in STREAM benchmark.
	After the PCA is executed, a correlation analysis is performed and three correlation matrices are shown using different sorting of the columns.

* PCA and Correlation Reduced List.ipynb :
	This is the final evolution of the previous jupyter notebook. In this case we have reduced the number of available events to the limit we found without losing information.
	To reproduce the middle steps, the previous script (PCA and Correlation All Hardware Counters.ipynb) should be executed multiple times. In each execution, the user should look for correlated hardware performance counters and discard one if the correlation makes sense; i.e.: if L2 and branches are correlated, this correlation may appear because of the structure of the loops in this case. But L2 and branches don't have a direct relationship.
	
* Neural Network.ipynb :
	This is a jupyter notebook using Python. A simple neural network is used to verify that the resulting hardware performance counters can be used to identify the different parallel regions.
	We use a simple neural network with one hidden layer. The data used for training consists of the results of the executions for all data sizes but two sizes are removed. The removed sizes are used in the predictions to test if the characterization can be performed successfuly.

Sometimes github fails opening jupyter notebooks, if this problem appears, use nbviewer: https://nbviewer.jupyter.org/

## Database descriptopn

The database was compressed in zip format using winrar because of github's file size restrictions.

The columns of the database are:

* **id**. This field is used as an identifier of the row along with the next three columns.

* **size_vector**. This is the number of elements of each vector used in STREAM. The used sizes are:
	1K; 2K; 3K; 4K; 5K; 6K; 7K; 8K; 9K; 10K; 20K; 30K; 40K; 50K; 60K; 70K; 80K; 90K; 100K; 200K; 300K; 400K; 500K; 600K; 700K; 800K; 900K; 1M; 2M; 3M; 4M; 5M; 6M; 7M; 8M; 9M; 10M; 20M; 30M; 40M; 50M; 60M; 70M; 80M; 90M; 100M; 110M; 120M; 130M; 140M; 150M; 160M; 170M; 180M; 190M; 200M;

* **comp_opt**. This column describes the optimization flag used to compile STREAM. The used optimizations are: O0 and O2.

* **label**. STREAM has four patterns and each pattern has a different label: copy_e, add_e, scale_e and triad_e. 

* And one column for each of the hardware performance counters (57 were available in our test machine with Xeon E5645).

This database has 448001 rows (including the header) and 61 columns.

## LICENSE (GPL):

This program is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, version 3.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
 
You should have received a copy of the GNU General Public License along with this program. If not, see <http://www.gnu.org/licenses/>.
