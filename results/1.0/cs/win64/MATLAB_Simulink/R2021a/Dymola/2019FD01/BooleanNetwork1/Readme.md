-------------------------------------------------------------------------------------------------------
FMU Tested: BooleanNetwork1.fmu
From Software: Dymola Version: 2019FD01
Test done with: MATLAB 9.10.0.1602886 (R2021a)
On platform: Microsoft Windows [Version 10.0.19043.1052]
Solver used: ode1 (Euler)
StepTime used: 0.07 s
StopTime used: 10 s
-------------------------------------------------------------------------------------------------------

Import process : 

1) Create a new empty Simulink model and set the model solver and stoptime with the same configuration described previously using the following command lines:
   new_system(YourSimulationName);
   set_param(YourSimulationName,'Solver','ode1');
   set_param(YourSimulationName,'FixedStep','0.07');
   set_param(YourSimulationName,'StopTime','10');

2) Import the FMU inside Simulink using the FMU import block. You can add it using the following command line:
   add_block('simulink_extras/FMU Import/FMU' ,[YourSimulationName '/' 'NameForFMUBlock']);

3) Optional. By default Simulink used structure format (if available) for inputs/outputs. You can force the FMU to display scalars inputs/outputs by using the following command lines :
   set_param('FMU block Path','FMUInputMapping','flat');
   set_param('FMU block Path','FMUOutputMapping','flat');

4) Add Inputs and Outputs blocks to match the number of I/Os of the FMU. You can add them using the following command lines:
   add_block('simulink/Commonly Used Blocks/In1',InputPortName)
   add_block('simulink/Commonly Used Blocks/Out1',OutputPortName)

5) Optional. Import the Stimuli CSV file (if available) using the following command line:
   readtable('CSV full path name','PreserveVariableNames',true);

6) Optional. Connect Variables created by importing Stimuli CSV file to input ports using the following command line:
   set_param(YourSimulationName,'LoadExternalInput','on');
   set_param(YourSimulationName,'ExternalInput',[YourTimeVariable, YourVariableForInputOne, YourVariableForInputTwo,...])

7) Run the simulation using the following command line:
   SimOut = sim(YourSimulationName);

8) Explore the SimOut object using the Simulink Data Inspector to validate the results using the following command line:
   plot(SimOut);
