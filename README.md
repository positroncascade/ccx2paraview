© Ihor Mirzov, UJV Rez, May 2019.  
Distributed under GNU General Public License, version 2.

<br/><br/>



# Calculix to Paraview converter (frd to vtk/vtu)

The main script is *ccx2paraview.py*. Together with *VTKWriter.py*, *VTUWriter.py* and *FRDParser.py* it converts [CalculiX](http://www.dhondt.de/) .frd-file to view and postprocess calculation results in [Paraview](https://www.paraview.org/). For each output interval generates separate file - it makes possible to animate time history. You'll need *python3* with *numpy* to use this converter.

It is recommended to convert .frd to modern XML .vtu format:

    python3 ccx2paraview.py -frd jobname

To convert .frd to legacy ASCII .vtk format, use command:

    python3 ccx2paraview.py -frd jobname -fmt vtk

By default script will skip ERROR fields generated by CalculiX. If you'd like to leave them, run commands with '-skip 0' argument:

    python3 ccx2paraview.py -frd jobname -fmt vtk -skip 0
    python3 ccx2paraview.py -frd jobname -fmt vtu -skip 0

Unfortunately, VTK format doesn't support names for field components. So, for stress and strain tensors components will be numbered as:

    0. xx
    1. yy
    2. zz
    3. xy
    4. yz
    5. zx
    6. Mises
    7. Min Principal
    8. Mid Principal
    9. Max Principal

Tested in ccx_2.15 and Paraview 5.6.0 for:

- element types: S3, S6, S4, S8, CPE3, CPE4, CPS3, CPS4, C3D15, C3D20
- output variables: U, NT, S, E, RF, PEEQ, SDV
- analysis type: static, coupled temperature-displacement, visco, frequency

<br/><br/>



# Your help

Please, you may:

- simply use this converter
- ask questions
- post issues here, on the GitHub
- attach your models and screenshots
- follow discussion in the [Yahoo CalculiX Group](https://groups.yahoo.com/neo/groups/CALCULIX/conversations/topics/13712)

Current TODO-list:

- Test converter for all the Calculix examples.

<br/><br/>



# dev

Folder with tests and development version of the converter. Users may not need it.
