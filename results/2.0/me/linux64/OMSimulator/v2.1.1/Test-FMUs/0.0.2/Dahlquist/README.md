The following command and script was used to simulate `Dahlquist.fmu`:
```bash
> .omsimulator/OMSimulator-linux-amd64-v2.1.1/bin/OMSimulator --workingDir=results/2.0/me/linux64/OMSimulator/v2.1.1/Test-FMUs/0.0.2/Dahlquist --stripRoot=true --skipCSVHeader=true --addParametersToCSV=true --suppressPath=true --timeout=60 Dahlquist.lua
```

Dahlquist.lua:
```lua
-- lua file for Dahlquist.fmu
oms_setTempDirectory('/tmp/cross-check')
oms_newModel('model')
oms_addSystem('model.root', oms_system_sc)

-- instantiate FMU
oms_addSubModel('model.root.fmu', '../../../../../../../../../fmus/2.0/me/linux64/Test-FMUs/0.0.2/Dahlquist/Dahlquist.fmu')

-- simulation settings
oms_setResultFile('model', 'Dahlquist_out.csv')
oms_setLoggingInterval('model', 0.02)
oms_setStartTime('model', 0.0)
oms_setStopTime('model', 10.0)
oms_setTolerance('model', 1e-06, 1e-05)
oms_setVariableStepSize('model', 1e-12, 1e-12, 0.02)

-- instantiate, initialize and simulate
oms_instantiate('model')
oms_initialize('model')
oms_simulate('model')
oms_terminate('model')
oms_delete('model')
```
See the [OMSimulator documentation](https://openmodelica.org/doc/OMSimulator/master/html/index.html) for more information.

