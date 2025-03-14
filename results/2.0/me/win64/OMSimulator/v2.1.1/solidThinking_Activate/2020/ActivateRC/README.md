The following command and script was used to simulate `ActivateRC.fmu`:
```bash
> .omsimulator/OMSimulator-mingw64-v2.1.1/bin/OMSimulator.exe --workingDir=results/2.0/me/win64/OMSimulator/v2.1.1/solidThinking_Activate/2020/ActivateRC --stripRoot=true --skipCSVHeader=true --addParametersToCSV=true --suppressPath=true --timeout=60 ActivateRC.lua
```

ActivateRC.lua:
```lua
-- lua file for ActivateRC.fmu
oms_setTempDirectory('C:/Temp/cross-check')
oms_newModel('model')
oms_addSystem('model.root', oms_system_sc)

-- instantiate FMU
oms_addSubModel('model.root.fmu', '../../../../../../../../../fmus/2.0/me/win64/solidThinking_Activate/2020/ActivateRC/ActivateRC.fmu')
oms_addSubModel('model.root.input', '../../../../../../../../../fmus/2.0/me/win64/solidThinking_Activate/2020/ActivateRC/ActivateRC_in.csv')

-- connect inputs to FMU
oms_addConnection('model.root.input.Signal_in', 'model.root.fmu.Signal_in')

-- simulation settings
oms_setResultFile('model', 'ActivateRC_out.csv')
oms_setLoggingInterval('model', 0.1)
oms_setStartTime('model', 0.0)
oms_setStopTime('model', 10.0)
oms_setTolerance('model', 1e-06, 0.0001)
oms_setVariableStepSize('model', 1e-12, 1e-12, 0.1)

-- instantiate, initialize and simulate
oms_instantiate('model')
oms_initialize('model')
oms_simulate('model')
oms_terminate('model')
oms_delete('model')
```
See the [OMSimulator documentation](https://openmodelica.org/doc/OMSimulator/master/html/index.html) for more information.

