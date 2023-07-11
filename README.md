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
  ![Clock_constraints](https://github.com/laksh-ms/TCL-script/assets/109785515/d7adad02-cdca-49f3-9b15-95a2fe9f0aeb)

- Creating complete input constraints (also diffentiating between bits and bus)
  ![inoutConstraints](https://github.com/laksh-ms/TCL-script/assets/109785515/650dc87b-8da2-405f-a90c-22581dd33846)
  ![InputPorts](https://github.com/laksh-ms/TCL-script/assets/109785515/de0f0fdc-ac04-4195-8f29-a8eb03e02cd0)

- Creating complete output constraints (also diffentiating between bits and bus)
  ![OutputPorts](https://github.com/laksh-ms/TCL-script/assets/109785515/77a49592-7469-4f59-b103-71ed26044d12)


# Day-4:
Yosys synthesis : Create a tcl script that can parse the RTL netlists in to a Yosys Synthesis Tool readable format (.ys) and perform the hierarchy check to verify if all RTL modules are correctly present, if not that print an error. 

- Parsing all RTL netlists in a Yosys readable format (.hier.ys) to perform hierarchy check
  ![YosysFormat](https://github.com/laksh-ms/TCL-script/assets/109785515/50c9e79d-f460-44d4-9c5c-74d821365c7f)

- Checking hierarchy
  ![CheckingHierarchy](https://github.com/laksh-ms/TCL-script/assets/109785515/8c61f38d-2052-44b7-a305-3d57fcf79e30)

- Example of Error in hierarchy checks
  ![hierarchyError](https://github.com/laksh-ms/TCL-script/assets/109785515/12f17e5e-6b1b-41f6-968e-c995087a9170)

- Understanding the Error from hierarchy log file
  ![hierarchyCheck_ErrorLOG](https://github.com/laksh-ms/TCL-script/assets/109785515/800fe49c-3ad8-4835-bef0-906ec02706c2)

- Hierarchy pass After correcting the error
  ![HierarchyCheckPASS](https://github.com/laksh-ms/TCL-script/assets/109785515/b5dc805d-5b09-4974-be4c-73f92fa8a930)
  

# Day-5:
Creating final format for Yosys to synthesize the gate level netlist and to create a final timing format for OpenTimer for STA.

- Creating yosys format(.ys) netlist for synthesis
  ![Yosysformat4synthesis](https://github.com/laksh-ms/TCL-script/assets/109785515/2ace3e7e-f575-4961-a253-45f980c4a771)

  ![runningYosysSynthesis](https://github.com/laksh-ms/TCL-script/assets/109785515/47c8c8b0-dea3-46c7-bcd3-df8c02255a51)
  

- Feed the above .ys file to Yosys tool generate the below synthesized gate level Netlist
  ![SynthesizedNetlistFromYosys](https://github.com/laksh-ms/TCL-script/assets/109785515/805ade27-6ec6-468c-9a72-30988bca418e)

- Formating the above Synthesized netlist for OpenTimer, STA or PNR i.e. (removing all asterisk(*) symbols and replacing backslash(\) symbols with a null character(""))
  ![FormattingSynthesizedNetlist](https://github.com/laksh-ms/TCL-script/assets/109785515/1f9f577b-4fff-4a49-91de-9ecad6c6c17a)
  ![FormattedNetlist](https://github.com/laksh-ms/TCL-script/assets/109785515/a59c41f8-6a41-4e61-a810-f356c9000974)

- Creating Opentimer readable format using procs for setting num of threads, early lib, late lib, reading verilog in .conf file
  

- Creating Opentimer readable format(.timing) using read sdc proc (Formatting Opentimer readable format for clocks, input, output and load constraints  and of course the buses )
  
  
- Since routing is not yet done, enable the prelayout timing variable so that the wire load parasitics is omitted i.e. set load parasitic value to 0.
  
-  openMSP430.conf and openMSP430.timing files are fed to OpenTimer tool for STA
-  Final Results

# Conclusion
Successful TCL scripting was used to Automate the process of pre-layout Synthesis and Static Timing analysis.

