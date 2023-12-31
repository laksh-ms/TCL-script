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
  ![NoCSVFile](https://github.com/laksh-ms/TCL-script/assets/109785515/2565c3a8-88b7-45b3-94ec-88e3257693c8)

- Scenario 2: User providing incorrect CSV
  ![FileNotFound](https://github.com/laksh-ms/TCL-script/assets/109785515/edefd9d4-ad9c-4ab2-83d0-9ff4e000371f)

- Scenario 3 : User typing "-help"
  ![HelpOutput](https://github.com/laksh-ms/TCL-script/assets/109785515/fb415999-e1b7-47b2-984c-063a7467f6ab)

- Scenario 4: Source the Unix shell to the Tcl script by passing the required csv file 

  ```tclsh lakshscript.tcl $argv[1] ```


# Day-2:
Convert .csv file content into Yosys readable format and .csv file to SDC format using Tcl scripting

- Data in csv file passed 
  ![csv_details](https://github.com/laksh-ms/TCL-script/assets/109785515/c6ae3b6e-634b-40ce-9e56-25f00ef16bf5)

- Creating variables fron csv file
  ![VariablesFromCSV](https://github.com/laksh-ms/TCL-script/assets/109785515/b49b9569-b67f-498d-ba32-b03f87e57ecb)

- Checking if all flies and directories are present in the path
  ![AllFilesFoundInPath](https://github.com/laksh-ms/TCL-script/assets/109785515/73360fba-2fba-4845-b412-bc475a513a58)

- Throw error if a file or directory is not present in the path
  ![FileNotInPath](https://github.com/laksh-ms/TCL-script/assets/109785515/6f04e87f-1dc5-4bdb-a1e5-ba12d8306696)

- Converting constraints csv to SDC format
  ![CSVRowColumnIndex](https://github.com/laksh-ms/TCL-script/assets/109785515/93028ec5-1432-4af4-badd-3dadf1378ce7)


# Day-3:

Creating Constraints and dumping them to a .sdc file

- Creating complete clock constraints
  ![Clock_constraints](https://github.com/laksh-ms/TCL-script/assets/109785515/79433520-fc6f-42ec-8b7e-b66058c55f69)

- Creating complete input constraints (also diffentiating between bits and bus)
  ![inoutConstraints](https://github.com/laksh-ms/TCL-script/assets/109785515/8c98f629-4f22-4e4f-98cf-56c6e1763259)
  ![InputPorts](https://github.com/laksh-ms/TCL-script/assets/109785515/a9af0fef-9f16-4a70-aeb3-5e516e7a4539)

- Creating complete output constraints (also diffentiating between bits and bus)
  ![OutputPorts](https://github.com/laksh-ms/TCL-script/assets/109785515/9ab5d409-2670-4b8b-b5ad-e57aa8a6e068)


# Day-4:
Yosys synthesis : Create a tcl script that can parse the RTL netlists in to a Yosys Synthesis Tool readable format (.ys) and perform the hierarchy check to verify if all RTL modules are correctly present, if not that print an error. 

- Parsing all RTL netlists in a Yosys readable format (.hier.ys) to perform hierarchy check
  ![YosysFormat](https://github.com/laksh-ms/TCL-script/assets/109785515/be5612a2-bab6-4f50-b120-0e36445d515e)

- Checking hierarchy
  ![CheckingHierarchy](https://github.com/laksh-ms/TCL-script/assets/109785515/0d14b35e-4ab3-4e97-aa20-af8f7f235de0)

- Example of Error in hierarchy checks
  ![hierarchyError](https://github.com/laksh-ms/TCL-script/assets/109785515/8721de37-464e-413e-9e40-2cf03fe25cdd)

- Understanding the Error from hierarchy log file
  ![hierarchyCheck_ErrorLOG](https://github.com/laksh-ms/TCL-script/assets/109785515/9997f032-0dcc-45bb-8e9c-b35c0989b0fe)

- Hierarchy pass After correcting the error
  ![HierarchyCheckPASS](https://github.com/laksh-ms/TCL-script/assets/109785515/fd7be03d-8679-44f2-821e-5a709555a7aa)


# Day-5:
Creating final format for Yosys to synthesize the gate level netlist and to create a final timing format for OpenTimer for STA.

- Creating yosys format(.ys) netlist for synthesis
  ![Yosysformat4synthesis](https://github.com/laksh-ms/TCL-script/assets/109785515/76cda526-eb0e-4e85-bcc0-03e7b5ebf07c)
  
  ![runningYosysSynthesis](https://github.com/laksh-ms/TCL-script/assets/109785515/5c797825-2027-411b-bd85-56583cdcbe5a)

- Feed the above .ys file to Yosys tool generate the below synthesized gate level Netlist
  ![SynthesizedNetlistFromYosys](https://github.com/laksh-ms/TCL-script/assets/109785515/49a33d2e-c713-44a3-84b2-66c498cabe55)

- Formating the above Synthesized netlist for OpenTimer, STA or PNR i.e. (removing all asterisk(*) symbols and replacing backslash(\) symbols with a null character(""))
  ![FormattingSynthesizedNetlist](https://github.com/laksh-ms/TCL-script/assets/109785515/10da4601-b792-4d4e-81fc-a70cb25a79d7)
  
  ![FormattedNetlist](https://github.com/laksh-ms/TCL-script/assets/109785515/37521989-6e88-4d56-9dd1-ec75cf777140)

- Creating Opentimer readable format using procs for setting num of threads, early lib, late lib, reading verilog in .conf file
  ![confFileafter4Proc](https://github.com/laksh-ms/TCL-script/assets/109785515/17172a31-a8e3-4a94-9012-c64cfc4cd609)

- Creating Opentimer readable format(.timing) using read sdc proc (Formatting Opentimer readable format for clocks, input, output and load constraints  and of course the buses )
  ![FormattedTimimgFile](https://github.com/laksh-ms/TCL-script/assets/109785515/0a604729-97e8-4cea-8a53-9caac8e4710e)

- Since routing is not yet done, enable the prelayout timing variable so that the wire load parasitics is not considered. Update the .spef file for OpenTimer
  ![spefFile](https://github.com/laksh-ms/TCL-script/assets/109785515/ba7167a1-5156-41f6-8c6a-c194385c58fc)

- QOR (Quality of Results)
  Results formatted in to a tabular form : openMSP430.conf and openMSP430.timing files were fed to OpenTimer tool for STA

  ![Pre-layout-TimingAnalysis](https://github.com/laksh-ms/TCL-script/assets/109785515/c62e4ab4-8069-46c9-a76f-5d0dd1f71005)


# Conclusion
TCL scripting was successfully used to Automate the process of pre-layout Synthesis and Static Timing analysis.

