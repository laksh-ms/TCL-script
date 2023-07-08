# TCL Scripting: Introduction to Advanced Scripting Techniques in VLSI Design and Synthesis.


_Author: Lakshmi M S_

_Acknowledgements: A TCL-Workshop by [Kunal Ghosh](https://github.com/kunalg123), VLSI System Design Corp. Pvt. Ltd._

# TCL Workshop Agenda
The agenda for the workshop is to automate User Interface(uI) by using TCL script, which will take RTL netlist & SDC constraints as inputs and will generate synthesized netlist & pre-layout timing report as output. It uses Yosys, a Open source tool for synthesis and Opentimer to generate pre-layout timing reports.

It was achieved as below:

[Day-1](#day-1) : Creating a TCL command and pass .csv file from UNIX shell to tcl script

[Day-2](#day-2) : Variable Creation and Processing Constraints from CSV

[Day-3](#day-3) : Processing Clock and Input Constraints

[Day-4](#day-4) : Complete Scripting and Yosys Synthesis

[Day-5](#day-5) : Advanced Scripting Techniques and Quality of Results Generation


# Introduction
Tcl, stands for Tool Command Language (pronounced "tickle") is a high-level, general-purpose, interpreted, dynamic scripting language commonly used in various domains, including software development, system administration, and electronic design automation (EDA). TCL scripting plays a crucial role in the field of VLSI design and verification, making it an indispensable tool for semiconductor engineers. VLSI projects involve complex tasks such as chip design, simulation, verification, and manufacturing, and TCL scripting provides an efficient and flexible way to automate these processes. 


# Day-1: 
Using VSDSYNTH tool box, create a shell command (laksh) and pass .csv from UNIX shell to Tcl script(lakshscript.tcl)

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
Convert .csv file content into Yosys readable format and .csv file to SDC format using Tcl scripting

- Data in csv file passed 
  ![csv_details](https://github.com/laksh-ms/TCL-script/assets/109785515/d8bd7171-7cf1-4891-bf8f-55e2643d6848)

- Creating variables fron csv file
  ![VariablesFromCSV](https://github.com/laksh-ms/TCL-script/assets/109785515/86225b53-6a40-4e0c-9d44-a31933733d73)

- Checking if all flies and directories are present in the path
  ![AllFilesFoundInPath](https://github.com/laksh-ms/TCL-script/assets/109785515/b47736ce-0fff-45d1-846a-d1c9eb324202)

- Throw error if a file or directory is not present in the path
  ![FileNotInPath](https://github.com/laksh-ms/TCL-script/assets/109785515/a7001764-6c45-4c85-8b39-1294cd0f392e)

- Converting constraints csv to SDC format
  ![CSVRowColumnIndex](https://github.com/laksh-ms/TCL-script/assets/109785515/f067c9c7-c59c-4212-a368-278b96063e8e)
  

# Day-3:

Creating Constraints and dumping them to a .sdc file

- Creating complete clock constraints
  
- Creating complete input constraints (also diffentiating between bits and bus)
  
- Creating complete output constraints (also diffentiating between bits and bus)
  

# Day-4:
Yosys synthesis : Create a tcl script that can Parsing the RTL netlists in a Yosys Synthesis Tool readable format .ys after performing  the hierarchy check to verify if all RTL modules are correctly present, if not that print an error. 

- Checking hierarchy
  
- Error in hierarchy checks
  
- Parsing the RTL netlists in a Yosys readable format .ys
  
- Feed .ys file to Yosys tool generate the below top level Netlist
  

# Day-5:
Report generation

- 

