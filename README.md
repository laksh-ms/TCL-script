# TCL Script
Introduction to Advanced Scripting Techniques in VLSI Design and Synthesis 

Author: Lakshmi M S

Acknowledgements: TCL Workshop by Mr. Kunal Ghosh, VLSI System Design

# Introduction
Tcl (pronounced "tickle") is a high-level, general-purpose, interpreted, dynamic scripting language commonly used in various domains, including software development, system administration, and electronic design automation (EDA). 


# Day-1: 
How to use VSDSYNTH tool box and to create command (Laksh) and pass .csv from UNIX shell to Tcl script.

- Create a tcsh shell excutable file Laksh, create logo and give it excute permission.
 
   ```#!/bin/tcsh -f```
  
  ```chmod -R 777 laksh ```
  
  Note : Make sure the file is executable by using the above command 

- Scenario 1: User doesn't provide an input CSV file
  
    ![NoCSVFile](https://github.com/laksh-ms/TCL-script/assets/109785515/01328f05-939b-4a4e-812a-ee35af3e6343)
  
- Scenario 2: User providing incorrect CSV
  
    ![FileNotFound](https://github.com/laksh-ms/TCL-script/assets/109785515/c45506bf-613a-4fd5-a2bb-b49f4a72b54b)

- Scenario 3 : User typing "-help"
  
    ![HelpOutput](https://github.com/laksh-ms/TCL-script/assets/109785515/aeabda10-8328-4f2f-b090-cda315b6aeba)

- Scenario 4: Source the Unix shell to the Tcl script by passing the required csv file 

```tclsh lakshscript.tcl $argv[1] ```


# Day-2:

