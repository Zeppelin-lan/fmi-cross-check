The following command and script was used to simulate `ControlledTemperature.fmu`:
```bash
> .omsimulator/OMSimulator-linux-amd64-v2.1.1/bin/OMSimulator --workingDir=results/2.0/me/linux64/OMSimulator/v2.1.1/MapleSim/2019/ControlledTemperature --stripRoot=true --skipCSVHeader=true --addParametersToCSV=true --suppressPath=true --timeout=60 ControlledTemperature.lua
```

ControlledTemperature.lua:
```lua
-- lua file for ControlledTemperature.fmu
oms_setTempDirectory('/tmp/cross-check')
oms_newModel('model')
oms_addSystem('model.root', oms_system_sc)

-- instantiate FMU
oms_addSubModel('model.root.fmu', '../../../../../../../../../fmus/2.0/me/linux64/MapleSim/2019/ControlledTemperature/ControlledTemperature.fmu')

-- simulation settings
oms_setResultFile('model', 'ControlledTemperature_out.csv')
oms_setLoggingInterval('model', 0.02)
oms_setStartTime('model', 0.0)
oms_setStopTime('model', 10.0)
oms_setTolerance('model', 1e-05, 1e-05)
oms_setVariableStepSize('model', 1e-12, 1e-12, 0.02)

-- instantiate, initialize and simulate
oms_instantiate('model')
oms_initialize('model')
oms_simulate('model')
oms_terminate('model')
oms_delete('model')
```
See the [OMSimulator documentation](https://openmodelica.org/doc/OMSimulator/master/html/index.html) for more information.

