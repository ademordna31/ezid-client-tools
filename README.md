# EZID Client Tools


**UPDATE 31 July 2019**


Helpful client scripts for use with [EZID](https://ezid.cdlib.org/).

This software is copyrighted by the Regents of the University of
California and released under the
[BSD License](http://creativecommons.org/licenses/BSD/).

_Note: This iteration requires Anaconda virtual environment (https://www.anaconda.com/distribution/#download-section) to execute. A virtual environment is used in order to standardize the process across multiple operating systems. This first section assumes you do you not have Anaconda installed on your machine.

0. Open the Anaconda prompt.

1. Determine the latest version of Python on your machine:
`conda search "^python$"`

2. Create a new Anaconda environment, called ark, with the latest version of Python 2 (2.7.x):
`conda create --name ark python=2.7.16`

3. Enter into the new Anaconda environment created in the previous step. The environment indicator to the left of the directory should change from (base) to (ark):
`conda activate ark`

4. Install git:
`conda install git`


_At this point, Anaconda is set to run the batch mint ARKs script. The following instructions assume the above steps are completed. Subsequent uses of the script can begin here._

0. Open the Anaconda prompt. Ensure that you are using the correct virtual environment:
`conda activate ark`

1. Download this GitHub repository with the script to batch mint ARKs:
`git clone https://github.com/CDLUC3/ezid-client-tools`

2. Move to the newly created directory:
`cd ezid-client-tools`

3. Create a csv file (e.g. metadata.csv) that contains the metadata for the ARK. Note that headings are not included. The batch-register.py script gives each item an ARK, so each row should correspond to an item. 

4. Create a text file (e.g. mapping.txt) to map columns from the metadata CSV to the EZID metadata required to mint an ARK (https://ezid.cdlib.org/). Map the What field to the title of the object e.g. erc.what = $6 (read: the title of the object is found in the sixth column of the metadata csv).

5. Run batch-register.py in order to mint the ARKs. Note the following:
- ark:/21198/z1 is the UCLA Digital Library ARK
- The -o argument indicates what the output file should be called and what column contains manuscript title. In this case, it is in column 3
- Use the names of the mapping and metadata files created previously.

`python batch-register.py -c ucla-library -s ark:/21198/z1 mint mapping.txt metadata.csv -o _id,3 > output.csv`

