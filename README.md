# HccDriverFinder
An integrated approach to uncover drivers for HBV-HCC

DriverFinder GUI:                                                
![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/gui1.png)

Visualize Reads Function Window: 
![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/visualize%20reads.png)

ViewSequence File (included in data summary folder):
![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/view%20sequence%20file.png)

Hepatocellular carcinoma (HCC) is the third leading cause of cancer deaths. HBV integration in the human genome is associated with the development of HCC. Statistically significant recurrent sites of HBV integration have been widely reported and are likely related to hepatocarcinogenesis. We believe that study of  HCC-related recurrent integration sites will identify driver genes that cause uncontrolled clonal expansion of cancerous hepatocytes. Our program is a novel NGS analysis software that facilitates i)identification of major junctions through integration detection in HCC, ii) mutational data analysis and iii) data mining to demonstrate driver identification for the construction of an HBV-HCC driver library for precision medicine. 

Our program is meant to be used in conjunction with ChimericSeq, a software for detecting and annotating viral integration events in Host DNA. After NGS reads with HBV integration sites through ChimericSeq, our program will analyze the output to identify potential HCC drivers through detection of major junctions and HBV mutations. 

We tested our program on the NGS data from 6 pairs of HBV-HCC tumor and adjacent nontumor tissue samples. 
Due to the GitHub file upload size limit, we uploaded these Fastq files to Google Drive at:              https://drive.google.com/drive/folders/0B_om_lBDmj3jcjZyRF9YNW1SS28?usp=sharing

The complete output files generated from 152 in-house HBV-HCC and non-HCC NGS datasets are shown below and saved in the folder 'Sample_Outputs' in the DriverFinder package.

## Prerequisites/dependencies:
Current system is for Mac only!

-ChimericSeq (download from: http://www.jbs-science.com/ChimericSeq.php)
  
  System memory: The minimum system memory requirement is 8G bytes. 
  Hard disk free space: 
  (a) 10G bytes for Human Reference genome and ChimericSeq application. 
  (b) 2 times of test data size space for holding original test data and alignment data. If you need to split test data into smaller files, it will need 3 times of test data size space for holding original test data, split files, & alignment data.

-Python (3.6.1 or later) (https://www.python.org/downloads/)

-BioPython (1.70) (http://biopython.org/wiki/Download)

-Pysam (0.11.2.2) (https://github.com/pysam-developers/pysam)

-Pandas/Numpy (0.20.1/1.13.1) (http://pandas.pydata.org/)

-OpenPyxl (2.4.6) (https://pypi.python.org/pypi/openpyxl)

-tkinter (8.5) (https://wiki.python.org/moin/TkInter)

-samtools (http://www.htslib.org/download/)

-cython (0.25.2) (http://cython.org/)

-xlrd (1.0.0) (https://pypi.python.org/pypi/xlrd)

We suggest using pip (package management system) to ease the installation of all the Python modules listed above (except samtools). Python 3.4 and later include pip by default. If you encounter difficulties, you may consider installing conda.
For example, to install xlrd simply issue the following command in your command prompt: "pip install xlrd" 

To install samtools, follow the link provided to download samtools 1.5, unzip and untar, enter samtools source directory, and follow instructions in the "INSTALL" file. You may need to remove dependencies on liblzma (./configure --disable-lzma) in the configuration step.

Use the script, 'test_modules.py', to make sure you have all the correct modules installed

NOTE: We have found that some Mac environments have problems with installing the python pysam module properly. After running test_modules.py script, you may still run the DriverFinder.py script if the pysam module is the only module not installed. If the pysam module is not installed, "Detect HBV Mutations" option will be disabled.

## Installing:
Install ChimericSeq according to instructions for first time setup on website. You will need to download the human and HBV reference .fa files, the gene information gtf file, and the prebuilt Bowtie2 Human and HBV reference genome files.

Download the file 'DriverFinder' and unzip

## Running Test Files:
1. Run the sample paired reads on ChimericSeq according to instructions on website. You will need to specify the settings, split the large paired fastq files, and load the reads as a directory. (OR use the sample ChimericSeq output files provided and skip this step)

After running ChimericSeq, our software will use the resulting csv, SAM, and log .txt files to identify major junctions, HBV mutations, and build a data summary excel sheet.

2. Move the 'final_Output'.csv and log .txt files into the folder named 'files'
    Move the viral Alignment SAM files to the folder named 'viralsamfiles'

3. Run the script, 'test_modules.py', to make sure you have all the correct modules installed for running HccDriverFinder
   - Open your computer's command prompt
   - 'cd' into the directory of the DriverFinder package
   - Use command: python test_modules.py

4. Open our python program through your command prompt with the command:
  -python DriverFinder.py

## To identify major junctions/drivers and build data summary:
5. Make sure all ChimericSeq output .csv and .txt files into a folder and drag the folder to the 'files' folder (or use sample folder)

6. Click on the button 'Build Summary/Identify Drivers'

7. The log window will update with timestamped documentation of events. Output files will be saved in the same folder with the ChimericSeq output files.
   - The file '_Sample_Summary.xlsx' contains the data summary and links to html generated graphic displays of reads
     - If you have trouble opening the hyperlinks in the excel summary, use your browser to open html files directly
   - The file 'DriverGeneDatabase.xlsx' will update with information from all potential driver genes found
   - The complete HCC driver gene database generated from our 152 in-house HBV-HCC NGS datasets is shown below and saved in the DriverFinder 'Sample_Outputs' folder.
    
## To identify HBV mutations:
8. Make sure all viral alignment SAM files in the folder 'viralsamfiles'
   - Access the viral alignment SAM files from our 12 samples at: https://drive.google.com/drive/folders/0B_om_lBDmj3jU3FaY2NybnJScVk?usp=sharing
   - OR, use the two smaller sample SAM files already saved in the HccDriverFinder package

9. Click on the button 'Detect HBV Mutations'

10. The mutation database file with information on all mutations found will be saved to a file named 'MutationDatabase.xlsx' in the DriverFinder folder. The program writes the results to two excel sheets, the first contains the positions of all the known mutations found and the second lists all other mutations sorted by frequency contains.
    - The list of HCC-linked HBV mutations that our program references is shown below and saved in the DriverFinder folder.
    - The complete mutation database generated from our 152 in-house HBV-HCC NGS datasets is shown below (both sheets) and saved in the DriverFinder 'Sample_Outputs' folder.

## To visualize chimeric (HBV junction) reads:
11. Click on the button 'Select Input File' and select any csv file in the ChimericSeq output format

12. Click on the button 'Visualize Reads' and the mapped reads will appear in the window

13. Use "F1", "F2", & "F3" to switch display, "F6" to increase font size, and "F5" to reduce font size.
F1 - Chimeric reads, F2 - HBV only, F3 - Major junction reads only




Complete Driver Gene Database:

![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/HCC%20Driver%20Gene%20Database.png) 

List of HCC-linked HBV mutations:
![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/HCC-linked%20HBV%20Mutations.png) 

Complete list of known HCC-linked HBV mutations found (sheet 1 of mutation database):
![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/Mutation%20Database%20Sheet%202.png) 

Complete list of all other HBV mutations found (sheet 2 of mutation database):
![alt text](https://github.com/Competition-Entrant-2017/DriverFinder/blob/master/Screenshots/Mutation%20Database%20Sheet%201.png) 



