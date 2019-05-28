fract Parameter Descriptions
============================

 Fractl calculates U, V, and W wind components from 2 or more Doppler 

DEBUGGIN
--------


debug
~~~~~


 Debug option.

 If set, debug messages will be printed appropriately.


 Type: enum

Options:

+      DEBUG_OFF

+      DEBUG_NORM

+      DEBUG_VERBOSE

+      DEBUG_EXTRA


**debug = DEBUG_OFF**

detailSpec
~~~~~~~~~~


 detail spec used for debugging only.
 Example: "5,20,30,0.1".


 Type: string


**detailSpec = "not_set"**

MINIMUM VALUE
-------------


minDbz
~~~~~~


 Minimum dBZ value for valid data.

 Any value below that will be tossed out.
 Example: -20.


 Type: double


**minDbz = -20**

minNcp
~~~~~~


 Minimum NCP value for valid data.

 Any value below that will be tossed out.
 Example: 0.3.


 Type: double


**minNcp = 0**

TEST MOD
--------


testMode
~~~~~~~~


 Test mode.

      MODE_ALPHA:
        Use simple synthetic wind data.
        Skip the redar files.
        Must specify synWinds: W,V,U
        Obs are located at the verif cell centers.

      MODE_BETA:
        Use simple synthetic wind data.
        Read swp files and use swp obs locations,
        but replace radial vel with synthetic.
        Must specify synWinds: W,V,U
        radFiles beg,lim
        Use radar files i: beg <= i < lim.
        If beg == lim == 0, read all files

      MODE_ZETA:
        Operational: use specified radar data.
        Specify synWinds: 0,0,0
        radFiles beg,lim
        Use radar files i: beg <= i < lim.
        If beg == lim == 0, read all files

      MODE_ZETA_BELTRAMI:
        Like zeta, but compare the results with
        the test Beltrami flow and print statistics.
        Specify synWinds: 0,0,0
        This is only useful for swp files generated
        by Michael Bell's Beltrami flow simulation.
      MODE_GAMMA:
        Like zeta, but compare the results with
        the constant flow and print statistics.
        Specify synWinds: 0,0,0.


 Type: enum

Options:

+      MODE_NONE

+      MODE_ALPHA

+      MODE_BETA

+      MODE_ZETA

+      MODE_ZETA_BELTRAMI

+      MODE_GAMMA


**testMode = MODE_ZETA**

radFiles
~~~~~~~~


 Use radar files i: start <= i < limit.
 Read all files if start == limit == 0.


 Type: string


**radFiles = "0,0"**

SYN WIN
-------


synWinds
~~~~~~~~


       Specify a comma sep triplet: W,V,U
       If a wind spec is numeric,
         use that constant uniform value.
       Else the wind spec is the name for
         one of SYNFUNC_* values:
         "sinx": wind component = sin(locx)
         "siny": wind component = sin(locy)
         "sinz": wind component = sin(locz)
       Example:
         -synWinds 3,sinx,sinx
         Means uniform Z wind at 3 m/s.
         Both V and U winds = sin(locx),
           so the wind would be from the SW
           to the NW, varying as sin(locx).


 Type: string


**synWinds = "0,0,0"**

GRID SPE
--------


zGrid
~~~~~


 "min,max,incr"
    To get min and max from the data, specify only the increment.


 Type: string


**zGrid = "0.0,16.0,0.5"**

yGrid
~~~~~


 "min,max,incr" or "incr".


 Type: string


**yGrid = "-150.0,250.0,1"**

xGrid
~~~~~


 "min,max,incr" or "incr".


 Type: string


**xGrid = "-200.0,100.0,1"**

GRID_TYP
--------


gridType
~~~~~~~~


 Mesh for stand-alone. Mish for Samurai input.


 Type: enum

Options:

+      GRID_MESH

+      GRID_MISH


**gridType = GRID_MESH**

PROJECTIO
---------


projName
~~~~~~~~


 Must be transverseMercador.


 Type: string


**projName = "transverseMercator"**

projLat0
~~~~~~~~


 For example: 16.5.


 Type: double


**projLat0 = 34.675063013242**

projLon0
~~~~~~~~


 For example: 148.0.


 Type: double


**projLon0 = -99.8960354021649**

radarAlt
~~~~~~~~


 only needed for pre gridded mode.


 Type: double


**radarAlt = -1**

MIS
---


baseW
~~~~~



 Type: double


**baseW = 0**

epsilon
~~~~~~~



 Type: double


**epsilon = 1e-06**

LIMIT
-----


maxDeltaAltKm
~~~~~~~~~~~~~


 in km. Default 0.


 Type: double


**maxDeltaAltKm = 0**

maxAbsElevDeg
~~~~~~~~~~~~~


 in degree.


 Type: double


**maxAbsElevDeg = 0**

minRadialDistKm
~~~~~~~~~~~~~~~


 in km.


 Type: double


**minRadialDistKm = 0**

numNbrMax
~~~~~~~~~



 Type: int


**numNbrMax = 100**

maxDistBase
~~~~~~~~~~~


 max point distance = base + factor * aircraftDist.


 Type: double


**maxDistBase = 1**

maxDistFactor
~~~~~~~~~~~~~


 max point distance = base + factor * aircraftDist.


 Type: double


**maxDistFactor = 0.016666**

FLAG
----


forceOk
~~~~~~~


 y/n.


 Type: string


**forceOk = "n"**

useEigen
~~~~~~~~


 y: use Eigen, n: use Cramer.


 Type: string


**useEigen = "y"**

preGridded
~~~~~~~~~~


 (NOT WORKING YET) Data is pre-gridded.


 Type: string


**preGridded = "n"**

FILES AND DIRECTORIE
--------------------


inDir
~~~~~


 Any radx supported format, or output of Radx2Grid.


 Type: string


**inDir = "/bell-scratch/tcha/APAR/Test_Data/hurricane/20190322/fractl/lhsandrhs/"**

fileRegex
~~~~~~~~~


 for example '^swp'.


 Type: string


**fileRegex = "^cfrad"**

fileList
~~~~~~~~


 One entry per line
 fileName altKmMsl latDeg lonDeg
 # in the first column is a comment.


 Type: string


**fileList = "not_set"**

outTxt
~~~~~~


 Has verification of grid results.


 Type: string


**outTxt = "/bell-scratch/tcha/APAR/Test_Data/hurricane/fractl/res.raw.txt"**

outNc
~~~~~


 If outNc ends in a slash we make a subdir and write to 
   yyyymmdd/ncf_yyyymmdd_hhmmss.nc.


 Type: string


**outNc = "./20190322_lhsandrhs.nc"**

FIELD
-----


radialName
~~~~~~~~~~


 VEL for NEXRAD, VG for Eldora, VE for CSU-CHILL.


 Type: string


**radialName = "VELTRU"**

dbzName
~~~~~~~


 REF for NEXRAD, DBZ for Eldora, DZ for CSU-CHILL.


 Type: string


**dbzName = "Zhh"**

ncpName
~~~~~~~


 Not available for NEXRAD, NCP for Eldora, NC for CSU-CHILL.


 Type: string


**ncpName = "VELUNF"**

FILTER
------


uvFilter
~~~~~~~~



 Type: enum

Options:

+      FILTER_NONE

+      FILTER_LEISE


**uvFilter = FILTER_NONE**

wFilter
~~~~~~~



 Type: enum

Options:

+      FILTER_NONE

+      FILTER_LEISE


**wFilter = FILTER_NONE**

uvSteps
~~~~~~~


 Applies to all dimensions. Use uvMultiSteps for dimension specific 
   steps.


 Type: int


**uvSteps = 1**

uvMultiStep
~~~~~~~~~~~


 Comma separated steps.
 Example: "1,2,1".


 Type: string


**uvMultiStep = "not_set"**

wSteps
~~~~~~


 Applies to all dimensions. Use wMultiStep for dimension specific 
   steps.


 Type: int


**wSteps = 1**

wMultiStep
~~~~~~~~~~


 Comma separated steps.
 Example: "1,2,1".


 Type: string


**wMultiStep = "not_set"**

INTERPOLATIO
------------


uvInterp
~~~~~~~~


 Applied before calculating W.


 Type: enum

Options:

+      INTERP_NONE

+      INTERP_LEISE

+      INTERP_RADAR_WIND


**uvInterp = INTERP_NONE**

