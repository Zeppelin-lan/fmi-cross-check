Model:
CoupledClutches

FMI Type:
CoSimulation

Generation Tool:
MWorks.Sysporer 2021

Available Platforms:
win64

Known Errors:
None

FMUChecker:
FMUChecker Version 2.0.4

run command for ComplianceChecker:
set FMUName=CoupledClutches
fmuCheck.win64.exe -k cs -o %FMUName%_ref.csv -i %FMUName%_in.csv -e %FMUName%_cc.log -h 1e-3 -s 1.5 "%FMUName%.fmu"

Contact email:
huangzc@tongyuan.cc
