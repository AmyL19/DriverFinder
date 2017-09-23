# DriverFinder
An integrated approach to uncover drivers for HBV-HCC

Hepatocellular carcinoma (HCC) is the third leading cause of cancer deaths. HBV integration in the human genome is associated with the development of HCC. Statistically significant recurrent sites of HBV integration have been widely reported and are likely related to hepatocarcinogenesis. We believe that study of  HCC-related recurrent integration sites will identify driver genes that cause uncontrolled clonal expansion of cancerous hepatocytes. Our program is a novel NGS analysis software that facilitates i)identification of major junctions through integration detection in HCC, ii) mutational data analysis and iii) data mining to demonstrate driver identification for the construction of an HBV-HCC driver library for precision medicine. 

Our program is meant to be used in conjunction with ChimericSeq, a software for detecting and annotating viral integration events in Host DNA. After NGS reads with HBV integration sites through ChimericSeq, our program will analyze the output to identify potential HCC drivers through detection of major junctions and HBV mutations. 

We tested our program on the NGS data from 6 pairs of HBV-HCC tumor and adjacent nontumor tissue samples. 
Due to the GitHub file upload size limit, we uploaded these Fastq files to Google Drive at: https://drive.google.com/drive/folders/0B_om_lBDmj3jU1VlM0E5RTlUU1E?usp=sharing
You can run these files in ChimericSeq by following the instructions on the ChimericSeq website: http://www.jbs-science.com/ChimericSeq.php
OR, you can use the sample ChimericSeq output files provided to test DriverFinder (already in DriverFinder package folder)

Sample output files are located in the folder 'Sample_Outputs' 
The HCC driver database in this folder is built from 140 in-house NGS HBV-HCC datasets in addition to our 12 datasets (data not provided)

# Prerequisites/dependencies:
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

# Installing:
Install ChimericSeq according to instructions for first time setup on website. You will need to download the human and HBV reference .fa files, the gene information gtf file, and the prebuilt Bowtie2 Human and HBV reference genome files.

Download the file 'DriverFinder' and unzip

# Running Test Files:
1.) Run the sample paired reads on ChimericSeq according to instructions on website. You will need to specify the settings, split the large paired fastq files, and load the reads as a directory. (OR use the sample ChimericSeq output files provided and skip to step 5)

After running ChimericSeq, our software will use the resulting csv, SAM, and log .txt files to identify major junctions, HBV mutations, and build a data summary excel sheet.

2.) Move the 'final_Output'.csv and log .txt files into the folder named 'files'
    Move the viral Alignment SAM files to the folder named 'viralsamfiles'

3.) Open our python program through your command prompt with the command:
      python "script".py

# To identify major junctions/drivers and build data summary:
4.) Make sure all ChimericSeq output .csv and .txt files into a folder and drag the folder to the 'files' folder

5.) Click on the button 'Build Summary/Identify Drivers'

6.) The log window will update with timestamped documentation of events. Output files will be saved in the same folder with the ChimericSeq output files.
    
# To identify HBV mutations (Mac only!):
7.) Make sure all viral alignment SAM files in the folder 'viralsamfiles'

8.) Click on the button 'Detect HBV Mutations'

9.) The mutation database file with information on all mutations found will be saved in the input folder. The program writes the results to two excel sheets, the first contains the positions of all the known mutations found and the second lists all other mutations sorted by frequency contains.

# To visualize chimeric (HBV junction) reads:
10.) Click on the button 'Select Input File' and select any csv file in the ChimericSeq output format

11.) Click on the button 'Visualize Reads' and the mapped reads will appear in the window
     Use "F1", "F2", & "F3" to switch display, "F6" to increase font size, and "F5" to reduce font size.
     
12.) To align reads, click on the button 'Align Reads'
     
13.) To visualize HBV breakpoints, click on the button 'Align Viral Reads'
