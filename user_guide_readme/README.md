

**Introduction**

• **G TA (GIS-To-AERMOD) is an off-line tool that enables automatic conversion from**

**roadway GIS shape files to AERMOD sources, include:**

o Generating geometry of RLINE, RLINEXT, AREA, or VOLUME defined sources

o Generating near-road receptors and gridded receptors

o Converting emission rates from per link or per mile units to AERMOD units

o Compiling AERMOD ‘.inp’ file

o Running AERMOD

o Organizing results and visualization

• **The document represents step-by-step manual on how to use GTA for near-**

**road dispersion modeling**

**1**





**Software Str ucture**

Data Tab

Road Tab

Receptors Tab

Emissions Tab

Compilation Tab

Results Tab

**2**





**Data Ta b**

**Input**

**Process**

**Output**

**Projected GIS w/**

**new Cartesian**

**Road GIS**

**Shape File**

**Data Ta b**

Road Tab

**coordinate (m) &**

**reference location**

**Data Tab takes GIS as input, and project into**

**Cartesian coordinated (meter) Geo-dataframe with**

**user-defined study boundary (spatial range where**

**concentration profile will be modeled) and reference**

**location (0, 0) as required by AERMOD**

Receptors Tab

Emissions Tab

Compilation Tab

Results Tab

**3**





**Data Ta b**

**4**





**Data Ta b**

**Upload GIS shape file**

**Here we uploaded “DC\_DupontCircle.shp” as**

**tutorial example.**

**5**





**Dupont Circle at Washington D.C .**

GIS Source: [https://opendata.dc.gov/datasets/23246020d6894453bdfcee00956df818_4](https://opendata.dc.gov/datasets/23246020d6894453bdfcee00956df818_41)[1](https://opendata.dc.gov/datasets/23246020d6894453bdfcee00956df818_41)

**6**





**Data Ta b**

**Identify GIS features**

**Columns required from GIS:**

• **Road Unique ID**: column that refers to unique ID

of each GIS link

• **Road Type:** column that represent road type ID

o In this example: 1-freeway; 2-arterial; 3-local

streets

• **Number of Lanes:** column that represent number

of lanes for each link (for calculating road width)

• **Lane Width:** column that represent lane width for

each link (for calculating road width)

• **Shoulder (m):** type float number (m) as shoulder

width

**Road width =**

**number of lanes × lane width + shoulder**

• **Geometry:** column that stores node coordinates of

each link (by default, this column name should be

‘geometry’)

**7**





**Data Ta b**

**Input the original and destination EPSG code**

**Available at: [https://spatialreference.org/ref/epsg/**](https://spatialreference.org/ref/epsg/)**

**8**





**Data Ta b**

**Origin EPSG: EPSG code for**

**the uploaded GIS file**

**This is the 4-digit code representing coordinate**

**projection type of uploaded GIS:**

• **In this example, GIS geometry is in GPS longitude**

**and latitude**

**(<https://spatialreference.org/ref/epsg/4326/>)**

**used by the GPS satellite navigation system**

• **Coordinate info from ArcMap**

**9**





**Data Ta b**

**Origin EPSG: EPSG code for**

**the uploaded GIS file**

**This is the 4-digit code representing coordinate**

**projection type of uploaded GIS:**

• **In this example, GIS geometry is in GPS longitude**

**and latitude**

**(<https://spatialreference.org/ref/epsg/4326/>)**

**used by the GPS satellite navigation system**

• **EPSG 4-digits code: 4326**

**10**





**Data Ta b**

**This is the 4-digit code representing local**

**Cartesian coordinate system that you want**

**convert GIS to:**

**Origin EPSG: EPSG code and**

**unit for the local projected**

**coordinate system**

• **In this example, we choose to convert to GIS**

**geometry into “NAD83 / Maryland (ftUS)” that**

**covers the GIS area in unit of “ft”**

**(<https://spatialreference.org/ref/epsg/2248/>)**

• **EPSG 4-digits code: 2248**

• **You may search state (e.g., Maryland, Georgia,**

**New Mexico, etc) at the website for the EPSG**

**code of local destination coordinates**

**Make sure your GIS was within the**

**bounds of the reference to qualify**

**for this destination EPSG**

**11**





**Data Ta b**

**Locate study boundary and**

**reference point from the map**

**12**





**Data Ta b**

**Click “Draw boundary”, then use mouse to draw**

**a red square in map as the study boundary**

• **You can re-click the button and re-draw the**

**boundary**

• **Only concentration within the square will be**

**modeled. Receptor will also be generated**

**within the square**

**13**





**Data Ta b**

**Click “Draw reference point”, then use mouse to**

**click a point within the map as reference location**

• **You can re-click the button and re-locate the**

**reference**

• **All the x- y- coordinates will be adjusted by**

**setting coordinate of reference as (0, 0)**

• **Reference does not have to be within the**

**square**

**14**





**Data Ta b**

**After the boundary and reference point are**

**determined, click “Confirm & close” to get back**

**to Data Tab**

**15**





**Data Ta b**

**Coordinates for boundaries and reference point are listed in**

**textbox. These numbers can be directly modified if users want to**

**type the information direct ly.**

**Y high**

**Reference x & y**

**Y low**

**X right**

**16**

**X left**





**Data Ta b**

**Click this button to verify all the input in the Data Ta b, and project**

**GIS into new Cartesian system (in unit of meters) with specified**

**reference point**

**17**





**Example: Original GIS to Projected GIS**

**Original GIS**

**Projected GIS**

**Longitude**

**X (meter)**

**18**





**Road Tab**

**Input**

**Process**

**Output**

**Projected GIS w/**

**new Cartesian**

Data Tab

**Road Ta b**

**coordinate (m) &**

**reference location**

**Geometry for**

**Line, AREA,**

**and/or**

**VOLUME source**

**Road Tab takes projected GIS and generate geometry**

**for AERMOD source of interest. The geometry**

**information will be stored as .CSV**

Receptors Tab

Emissions Tab

Compilation Tab

Results Tab

**19**





**Road Tab**

**20**





**Road Tab**

**Line**

**AREA**

**VOLUME**

**Users can choose to generate the AERMOD**

**source type they are interested:**

• Line (LINE, RLINE, RLINEXT) – ‘Line.csv’

• AREA – ‘AREA.csv’

• VOLUME – ‘VOLUME\_XX.csv’, XX refers to

maximum parcel size

**21**





**Road Tab – Line Source**

**Description of Line source**

**A graphic description of Line source**

**22**





**Road Tab – Line Source**

**Click this button to generate Line source**

**geometry and store as “Line.csv”**

**Columns of Line geometry “Line.csv”**

**\DC\_DupontCircle\results\Line.csv**

**23**





**Road Tab – Line Source**

**Click this button to view geometry of**

**roadways in Line geometry**

**24**





**Road Tab – AREA Source**

**Description of AREA source**

**A graphic description of AREA source**

**25**





**Road Tab – AREA Source**

**Click this button to generate AREA source**

**geometry and store as “AREA.csv”**

**Columns of AREA geometry “AREA.csv”**

**\DC\_DupontCircle\results\AREA.csv**

**26**





**Road Tab – AREA Source**

**Click this button to view geometry of**

**roadways in AREA geometry**

**27**





**Road Tab – VOLUME Source**

**Description of VOLUME source**

**A graphic description of**

**VOLUME source**

**Maximum volume parcel size**

**(d <=8 m recommended)**

**28**





**Road Tab – VOLUME Source**

**Click this button to generate VOLUME source**

**geometry and store as “VOLUME\_XX.csv”**

**Columns of VOLUME geometry “VOLUME\_XX.csv”**

**\DC\_DupontCircle\results\VOLUME\_8.0.csv**

**29**





**Road Tab – VOLUME Source**

**Click this button to view geometry of roadways in VOLUME**

**geometry (usually takes very long to generate VOLUME graph)**

**Max size = 8 m**

**30**





**Road Tab – VOLUME Source**

**Click this button to view geometry of roadways in VOLUME**

**geometry (usually takes very long to generate VOLUME graph)**

**Max size = 20 m**

**31**





**Receptors Tab**

**Input**

**Process**

**Output**

**Projected GIS w/**

**new Cartesian**

Data Tab

Road Tab

**coordinate (m) &**

**reference location**

**Near-road**

**receptors &**

**gridded receptors**

**Receptors Tab**

Emissions Tab

Compilation Tab

Results Tab

**Receptors**

**configuration**

**Receptors Tab takes projected GIS, generate near-**

**road receptors and gridded receptors with user**

**specified layers and/or intervals**

**32**





**Receptors Tab**

**33**





**Receptors Tab**

**A description on how to prepare for**

**receptors in this Tab**

**A graphic description of receptors**

**34**





**Receptors Tab – Near Road Receptors**

**Users may choose to either upload csv of receptors configuration**

**(1.1), or directly type in box chart (1.2). In this example, we uploaded**

**‘receptor\_layers.csv’**

For road type 1 (freeway in example),

generate 4 layers of receptors at 5, 15,

50, and 100 meters away from road

edge, with receptors interval of 20, 30,

50 and 100 meters within each layer

Configuration for near

road receptors

For road type 2 (arterial in example),

generate 3 layers of receptors at 5, 15,

and 50 meters away from road edge,

with receptors interval of 20, 30 and 50

meters within each layer

**35**





**Receptors Tab – Gridded Receptors**

• **Enter intervals of gridded**

**receptors (meters)**

• **200 meters was entered in the**

**example**

**36**





**Receptors Tab – Receptors Elevation**

**Enter elevation of receptors from ground**

**(1.5 to 1.6 meters recommended)**

**37**





**Receptors Tab**

**Then, click this button to view distribution of generated receptors**

**Click this button to generate receptors.**

**Receptors coordinates will be stored at:**

**‘\DC\_DupontCircle\results\receptors\_list.csv’**

**38**





**Receptors Tab – ‘receptors\_list.csv’**

**‘X Y Z’ in AERMOD format**

**Receptor ID**

**39**





**Emissions Tab**

**Input**

**Process**

**Output**

**Projected GIS w/**

**new Cartesian**

Data Tab

**coordinate (m) &**

**reference location**

**Geometry for**

**Line, AREA,**

**and/or**

**VOLUME source**

Road Tab

Receptors Tab

**Emissions Tab**

Compilation Tab

Results Tab

**Emissions Tab takes emission rate from**

**GIS file and generate AERMOD emission**

**rates for various AERMOD sources**

**AERMOD**

**Emission rates**

**40**





**Emissions Tab**

**41**





**Emissions Tab**

**A description on how to generate emission files in this Ta b.**

**All the generated emission files will be stored in**

**‘\DC\_DupontCircle\results\emission\\*’**

**42**





**Emissions Tab**

**If emission rate is not available, select ‘skip’**

**and users can just create AERMOD input file**

**without emission rate**

**If emission rate is available, locate emission**

**rate column in GIS, and identify the emission**

**unit of this column**

**43**





**Emissions Tab**

**Select source(s) to generate emission rate. For VOLUMN**

**source, the road ‘VOLUME\_XX.csv’ file needs to be uploaded.**

**Click this button to generate emission rate.**

**Store the emission rate (‘em\_AREA.csv’,**

**‘em\_LINE.csv’, ‘em\_RLINEXT.csv’, and**

**‘em\_VOLUME\_XX.csv’) into**

**“\DC\_DupontCircle\results\emission\\*”**

**44**





**Emissions Tab**

**The generated emission rate csv files (‘em\_AREA.csv’, ‘em\_LINE.csv’, ‘em\_RLINEXT.csv’, and**

**‘em\_VOLUME\_XX.csv’) contain one column ‘em\_aer’ – AERMOD emission rate.**

**AERMOD Emission**

**AERMOD Source**

**Rate Unit**

푔Τ푠Τ푚2

푔Τ푠Τ푚

푔Τ푠Τ푚2

푔Τ푠

LINE or RLINE

RLINEXT

AREA

VOLUME

**45**





**Compilation Tab**

**Input**

**Process**

**Output**

Data Tab

**Compilation Tab takes generated geometry csv (from**

**Road Tab) , receptors csv (from Receptors Tab) , and**

**emissions csv (from Emission Tab) , compile to**

**AERMOD input file, and conduct AERMOD runs (if**

**emissions are available)**

**Geometry for**

**Line, AREA,**

**and/or**

Road Tab

Receptors Tab

Emissions Tab

**Compilation Ta b**

Results Tab

**VOLUME source**

**Near-road**

**receptors &**

**gridded receptors**

**AERMOD**

**Emission rates**

**AERMOD ‘.inp’**

**& ‘.out’ file**

**46**





**Compilation Tab**

**47**





**Compilation Tab**

**If you have emission csv files available from Emission Ta b, select ‘Run AERMOD’ and the tool will generate ‘.inp’**

**file, run AERMOD, and generate ‘.out’ file from AERMOD. If emissions are not available ( e.g., skipped the**

**Emission Tab), select ‘Emission unavailable’, and the tool can still compile a ‘.inp’ file without emission information**

**48**





**Compilation Tab**

**Select pollutant type and modeling period.**

**Depending on POLLUTID, the values of**

**AVERTIME is consistent with NAAQS**

**POLLUTID**

**AVERTIME**

1

CO

8

1

NO2

ANNUAL

24

PM2.5

PM10

ANNUAL

24

1

8

24

Others

ANNUAL

**49**





**Compilation Tab**

**Other information needed for AERMOD**

**Click buttons to locate surface meteorology**

**(.SFC) and upper profile meteorology (.PFL) file.**

**1hr CO concentration is modeled in the example**

**with meteorology file ‘test\_1h.SFC’ and**

**‘test\_1h.PFL’ uploaded**

**50**





**Compilation Tab – Running AREA**

**Compile and run AERMOD for various sources. Users can**

**choose to run one or more sources as needed**

**51**





**Compilation Tab – Running AREA**

**Compile and run AERMOD for AREA Source**

**52**





**Compilation Tab – Running AREA**

**Upload ‘AREA.csv’ generated from Road Tab**

**‘\DC\_DupontCircle\results\AREA.csv’**

**Upload ‘receptors\_list.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\receptors\_list.csv’**

**Upload ‘em\_AREA.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\emission\em\_AREA.csv’**

**53**





**Compilation Tab – Running AREA**

**Compile ‘.inp’, run AERMOD, and generate ‘.out’.**

**Files stored in ‘\DC\_DupontCircle\results\\*’**

**For this example running CO concentration in 1**

**hour, the files are named as:**

• **‘AREA\_CO\_1.inp’**

• **‘AREA\_CO\_1.out’**

• **‘[Source]\_[Pollutant]\_[Period]’**

**54**





**Compilation Tab – Running VOLUME**

**Compile and run AERMOD for VOLUME Source**

**55**





**Compilation Tab – Running VOLUME**

**Upload ‘VOLUME\_XX.csv’ generated from Road Tab Upload ‘receptors\_list.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\VOLUME\_XX.csv’**

**‘\DC\_DupontCircle\results\receptors\_list.csv’**

**Upload ‘em\_VOLUME\_XX.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\emission\em\_VOLUME\_XX.csv’**

**56**





**Compilation Tab – Running VOLUME**

**Compile ‘.inp’, run AERMOD, and generate ‘.out’.**

**Files stored in ‘\DC\_DupontCircle\results\\*’**

**For this example running CO concentration in 1**

**hour, the files are named as:**

• **‘VOLUME\_CO\_1.inp’**

• **‘VOLUME\_CO\_1.out’**

• **‘[Source]\_[Pollutant]\_[Period]’**

**57**





**Compilation Tab – Running LINE**

**Compile and run AERMOD for LINE Source**

**58**





**Compilation Tab – Running LINE**

**Upload ‘Line.csv’ generated from Road Tab**

**‘\DC\_DupontCircle\results\Line.csv’**

**Upload ‘receptors\_list.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\receptors\_list.csv’**

**Upload ‘em\_LINE.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\emission\em\_LINE.csv’**

**59**





**Compilation Tab – Running LINE**

**Compile ‘.inp’, run AERMOD, and generate ‘.out’.**

**Files stored in ‘\DC\_DupontCircle\results\\*’**

**For this example running CO concentration in 1**

**hour, the files are named as:**

• **‘LINE\_CO\_1.inp’**

• **‘LINE\_CO\_1.out’**

• **‘[Source]\_[Pollutant]\_[Period]’**

**60**





**Compilation Tab – Running RLINE**

**Compile and run AERMOD for RLINE Source**

**61**





**Compilation Tab – Running RLINE**

**Upload ‘Line.csv’ generated from Road Tab**

**‘\DC\_DupontCircle\results\Line.csv’**

**Upload ‘receptors\_list.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\receptors\_list.csv’**

**Upload ‘em\_LINE.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\emission\em\_LINE.csv’**

**62**





**Compilation Tab – Running RLINE**

**Compile ‘.inp’, run AERMOD, and generate ‘.out’.**

**Files stored in ‘\DC\_DupontCircle\results\\*’**

**For this example running CO concentration in 1**

**hour, the files are named as:**

• **‘RLINE\_CO\_1.inp’**

• **‘RLINE\_CO\_1.out’**

• **‘[Source]\_[Pollutant]\_[Period]’**

**63**





**Compilation Tab – Running RLINEXT**

**Compile and run AERMOD for RLINEXT Source**

**64**





**Compilation Tab – Running RLINEXT**

**Upload ‘Line.csv’ generated from Road Tab**

**‘\DC\_DupontCircle\results\Line.csv’**

**Upload ‘receptors\_list.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\receptors\_list.csv’**

**Upload ‘em\_RLINEXT.csv’ generated from Receptors Tab**

**‘\DC\_DupontCircle\results\emission\em\_RLINEXT.csv’**

**65**





**Compilation Tab – Running RLINEXT**

**Compile ‘.inp’, run AERMOD, and generate ‘.out’.**

**Files stored in ‘\DC\_DupontCircle\results\\*’**

**For this example running CO concentration in 1**

**hour, the files are named as:**

• **‘RLINEXT\_CO\_1.inp’**

• **‘RLINEXT\_CO\_1.out’**

• **‘[Source]\_[Pollutant]\_[Period]’**

**66**





**Compilation Tab – Running AERMOD**

**Reminder: running AERMOD may take**

**seconds, minutes, hours, or even days,**

**depending on the size of network, number of**

**receptors, and modeling time period**

**67**





**Results Ta b**

**Input**

**Process**

**Output**

Data Tab

Road Tab

**Results Tab takes AERMOD output files ‘.out’,**

**organize concentration results into csv files, and**

**visualize concentration profile in heat map**

Receptors Tab

Emissions Tab

Compilation Tab

**Results Ta b**

**AERMOD ‘.inp’**

**& ‘.out’ file**

**Concentration**

**csv and profile**

**68**





**Results Ta b**

**69**





**Results Ta b**

**Click to upload AERMOD ‘.out’ and organize concentration into ‘.csv’ file.**

**Takes seconds to minutes, depending on the number of receptor results.**

**In the example, ‘RLINEXT\_Line\_CO\_1.out’ was uploaded**

**‘RLINEXT\_Line\_CO\_1.out’ in text format**

**‘RLINEXT\_Line\_CO\_1.csv’**

**70**





**Results Ta b**

**Users can type the concentration range to visualize**

**(default as from 0 to maximum concentration value in the file)**

**Then click the button to visualize concentration (range 0 - 2)**

**71**





**Results Ta b**

**Users can type the concentration range to visualize**

**(default as from 0 to maximum concentration value in the file)**

**Then click the button to visualize concentration (range 0 - 3)**

**72**





**Questions?**

**Questions?**

**Haobing Liu**

Assistant Professor

Department of Civil, Construction and

Environmental Engineering

University of New Mexico

[~~hliu332@unm.edu~~](mailto:hliu332@unm.edu)

[~~Haobing.liu2012@gmail.com~~](mailto:Haobing.liu2012@gmail.com)

**73**





**Appendix – EPSG Input for ‘Atlanta\_SMALLSITE.shp’**

**epsg projection 2240 - nad83 /**

**georgia west (ftus)**

[**https://www.spatialreference.org/**](https://www.spatialreference.org/ref/epsg/2240/)

[**ref/epsg/2240/**](https://www.spatialreference.org/ref/epsg/2240/)

**Same applies to**

**“Atlanta\_RURAL.shp” and**

**“Atlanta\_URBAN.shp”**

**74**





**Appendix – Albuquerque – I40 & I25 Interchange**

GIS Source: <https://www.cabq.gov/gis/geographic-information-systems-data>

**75**





**Appendix – EPSG Input for ‘ABQ\_I40I25.shp’**

**epsg projection 2903 - nad83(harn)**

**/ new mexico central (ftus)**

[**https://www.spatialreference.org/**](https://www.spatialreference.org/ref/epsg/2903/)

[**ref/epsg/2903/**](https://www.spatialreference.org/ref/epsg/2903/)

**76**

