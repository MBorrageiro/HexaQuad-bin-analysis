# HexaQuad Bin Analysis

This repo house the bin analysis tools and results from a MAVlogdump batch process.

Currently, the quad and hex flight house csv files with extracted data from the flight bin log files. The csvs make it easier to graph specific data for paper writing and comparison.
Included are the bin files for the moment, it is likely that these files will be moved to an alternative location.

**Original .bin files:**

[Quad bins](https://drive.google.com/drive/folders/1blnslVVIkTeMw01TvXwdlLu9-NemGIcE?usp=sharing)

[Hex bins](https://drive.google.com/drive/folders/1p-Np6uSYCnqMlToL2rfl4IctGXj7VmPZ?usp=sharing)

# logBatchProcess
The `logBatchProcess.bat` makes use of the tool from MAVlogdump to extract certain parameters from ardupilot bin files.

## How to use:

- Takes 2 arguments:
  1. Bin file name
  2. Parameter to extract
  
E.g: `> logBatchProcess.bat fQ_18-10-2022_#1.bin BAT`
- It will then create a folder for the created CSV files `/fQ_18-10` as well as name the CSV file according to the file name and parameters entered. `fQ_18-10_#1_BAT.csv`
- If a folder exists it will use it however files with the same name will be overwritten.

## File Naming Convention:

The batch file requires a specific file name to create the folder and file names correctly. This helps automate it, I have not dived too deep into batch commands to make it more complex.

**Convention:**

`f$_dd-mm-yyyy_#%.bin`

Where `$` is replaced with either `H` or `Q` for Hex and Quad respectively.
The `%` is used to identify the flight number on a specific day, i.e. "1, 2, 3...".

# Installing and using MAVlogdump files:

Mavlogdump.py is a tool part of the pymavlink package found [here](https://github.com/ArduPilot/pymavlink). This tool can be used to extract certain parameters from the log bin files and exported to CSV files. The logs are stored in bin files to save space.

**Installation:**
1. I used miniconda, to organise my python environments:
2. Installed Miniconda.
3. Created an environment to separate files
4. Installed, python3.9, which included a number of other packages
5. Pip3 installed the pymavlink package.
6. I had to download the package from git too as some folders did not install from the pip install.

## Example Code:
Run the command from the folder containing the mavlogdump.py script.

`path> python mavlogdump.py  -- types ATT --format csv filepath.bin > filepath.csv`

Replace ATT above with the set of parameters you wish to extract from the bin file.

