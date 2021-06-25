


**GTA (GIS-To-AERMOD) is an off-line tool that enables automatic conversion from roadway GIS shape files to AERMOD sources, which include:**


o Generating geometry of RLINE, RLINEXT, AREA, or VOLUME defined sources

o Generating near-road receptors and gridded receptors

o Converting emission rates from per link or per mile units to AERMOD units

o Compiling AERMOD ‘.inp’ file

o Running AERMOD

o Organizing results and visualization



***This document represents a step-by-step manual on how to use GTA for near-road dispersion modeling***





**Software Structure**

![GTA 1](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic1.PNG)







***Data Tab***

The Data Tab takes GIS as input, and project into a Cartesian coordinated (meter) Geo-dataframe with user-defined study boundary (spatial range where concentration profile will be modeled) and reference location (0, 0) as required by AERMOD

![GTA 3](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic3.png)

Pictured above is the interface for the data tab of GIS-to-AERMOD Tool


**1) Upload GIS shape file by clicking "open" and navigating to the file of your choosing** 


*This example will be of Dupont Circle at Washington D.C.*

![GTA 4](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic4.PNG)


GIS Source: [https://opendata.dc.gov/datasets/23246020d6894453bdfcee00956df818_4](https://opendata.dc.gov/datasets/23246020d6894453bdfcee00956df818_41)[1](https://opendata.dc.gov/datasets/23246020d6894453bdfcee00956df818_41)

**2) Identify GIS features**


Columns required from GIS:

• Road Unique ID: column that refers to unique ID of each GIS link

• Road Type: column that represent road type ID

    o In this example: 1-freeway; 2-arterial; 3-local streets

• Number of Lanes: column that represent number of lanes for each link (for calculating road width)

• Lane Width: column that represent lane width for each link (for calculating road width)

• Shoulder (m): type float number (m) as shoulder width

    Road width = number of lanes × lane width + shoulder

• Geometry: column that stores node coordinates of each link (by default, this column name should be ‘geometry’)




**3) Input the original and destination EPSG code**

  
    Available at: [https://spatialreference.org/ref/epsg/](https://spatialreference.org/ref/epsg/)



    Origin EPSG: the EPSG code for the uploaded GIS file:

    • This is the 4-digit code representing coordinate projection type of uploaded GIS

    • In this example, GIS geometry is in GPS longitude and latitude (<https://spatialreference.org/ref/epsg/4326/>) used by the GPS satellite navigation system

    • Coordinate info from ArcMap
  
    Destination EPSG: ESPG code and unit for the local projected coordinate system:

    • This is the 4-digit code representing local Cartesian coordan systems that you want convert the GIS data to

    • In this example, we choose to convert to GIS geometry into “NAD83 / Maryland (ftUS)” that covers the GIS area in unit of “ft”(<https://spatialreference.org/ref/epsg/2248/>)

    • EPSG 4-digits code: 2248

    • You may search state (e.g., Maryland, Georgia, New Mexico, etc) at the website for the EPSG code of local destination coordinates

    • Make sure your GIS was within the bounds of the reference to qualify for this destination EPSG




**4) Locate study boundary and reference point from the map by clicking "Locate from graph"**


![GTA 5](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic5.PNG)



    Click “Draw boundary”, then use mouse to draw a red square in map as the study boundary

    • You can re-click the button and re-draw the boundary

    • Only concentration within the square will be modeled. Receptor will also be generated within the square




    Click “Draw reference point”, then use mouse to click a point within the map as reference location

    • You can re-click the button and re-locate the reference

    • All the x- y- coordinates will be adjusted by setting coordinate of reference as (0, 0)

    • Reference does not have to be within the square



    After the boundary and reference point are determined, click “Confirm & close” to get back to Data Tab






    Coordinates for boundaries and reference point are listed in the textbox. These numbers can be directly modified if users want to type the information directly.




**5) Click the button "Verify Inputs and Convert GIS Coordinates" to verify all the input in the Data Tab, and project GIS into the new Cartesian system (in unit of meters) with the specified reference point**





**Example: Original GIS to Projected GIS**

![GTA 6](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic6.png)

Original GIS (in latitude and longitude)
 
![GTA 7](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic7.png)

Projected GIS (in meters)




***Road Tab***


**Road Tab takes projected GIS and generate geometry for AERMOD source of interest. The geometry information will be stored as .CSV**

![GTA 9](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic9.png)




Users can choose to generate the AERMOD surce type they are interested in:

    • Line (LINE, RLINE, RLINEXT) – ‘Line.csv’

    • AREA – ‘AREA.csv’

    • VOLUME – ‘VOLUME_XX.csv’, XX refers to aximum parcel size




**Line Source** includes:
    • A written description of the line source
    • A graphic description of the line source in the "graphic example" button
    • The "LINE columns" button generates columns of line geometry as "Line.csv"
    • The "Generate Line" button generates the Line source geometry, and also stores as "Line.csv"
    • The "Visualize Line" button to allows you to view the geometry of roadways in Line geometry



**AREA Source** includes:
    • A written description of the area source
    • A graphic description of the area source in the "graphic example" button
    • The "AREA coluumns" button generates columns of area geometry as "AREA.csv"
    • The "Generate Area" button generates area source geometry as "AREA.csv"
    • The "Visualize AREA" button allows you to view the geometry of roadways in AREA geometry
     
     
     
**VOLUME Source** includes:
    • A written description of the area source
    • A graphic description of the volume source in the "graphic example" button
    • The "VOLUME columns" button generates columns of volume geometry as "VOLUME_XX.csv"
    • The "Generate VOLUME" button generates area source geometry as "VOLUME_XX.csv"
    • The "Visualize VOLUME" button allows you to view the geometry of roadways in VOLUME geometry (it usually takes a long time to generate a volume graph)





***Receptors Tab***



Receptors Tab takes projected GIS, generate near-road receptors and gridded receptors with user specified layers and/or intervals





![GTA 11](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic11.png)



"Information for receptors":
    A description on how to prepare for receptors in this Tab
    
    
    
 "Graphic Example" button:
    A graphic description that displays a visualization of the receptors
    
    
![GTA 12](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic12.png)




**Near Road Receptors**

    • Users may choose to either upload csv of receptors configuration (1.1), 
    or directly type in box chart (1.2). In this example, we uploaded 
    ‘receptor\_layers.csv’

    • For road type 1 (freeway in example), generate 4 layers of receptors at 5, 
    15, 50, and 100 meters away from road edge, with receptors interval of 20, 
    30, 50 and 100 meters within each layer
`
    • For road type 2 (arterial in example), generate 3 layers of receptors at 5, 
    15, and 50 meters away from road edge, with receptors interval of 20, 30 and 
    50 meters within each layer




**Gridded Receptors**

    • Enter intervals of gridded receptors (meters)
    
    • 200 meters was entered in the example



**Receptors Elevation**

    • Enter elevation of receptors from ground (1.5 to 1.6 meters recommended)



• Click the "Visualize receptors" to view distribution of generated receptors


• Click "Generate receptors" to generate receptors.

Receptors coordinates will be stored at:

‘\DC_DupontCircle\results\receptors_list.csv’





**‘receptors_list.csv’:**

![GTA 13](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic13.png)


coord_aer field: ‘X Y Z’ in AERMOD format

rec_id field: Receptor ID





***Emissions Tab***

Emissions Tab takes the emission rate from GIS file and generate AERMOD emission rates for various AERMOD sources



![GTA 14](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic14.png)





**Information for emissions**:
• A description on how to generate emission files in this Tab. All the generated emission files will be stored in ‘\DC_DupontCircle\results\emission\\*’



• If emission rate is not available, select ‘skip’ and users can just create AERMOD input file without emission rate

• If emission rate is available, locate emission rate column in GIS, and identify the emission unit of this column

• Select source(s) to generate emission rate. For VOLUMN source, the road ‘VOLUME_XX.csv’ file needs to be uploaded.

• Click this button to generate emission rate. Store the emission rate (‘em_AREA.csv’, ‘em_LINE.csv’, ‘em_RLINEXT.csv’, and ‘em_VOLUME_XX.csv’) into “\DC_DupontCircle\results\emission\\*”






The generated emission rate csv files (‘em\_AREA.csv’, ‘em\_LINE.csv’, ‘em\_RLINEXT.csv’, and ‘em\_VOLUME\_XX.csv’) contain one column ‘em\_aer’ – AERMOD emission rate.

![GTA 15](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic15.PNG)





***Compilation Tab***

Compilation Tab takes generated geometry csv (from Road Tab) , receptors csv (from Receptors Tab) , and emissions csv (from Emission Tab) , compile to AERMOD input file, and conduct AERMOD runs (if emissions are available)


![GTA 16](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic16.png)




If you have emission csv files available from Emission Ta b, select ‘Run AERMOD’ and the tool will generate ‘.inp’ file, run AERMOD, and generate ‘.out’ file from AERMOD. If emissions are not available ( e.g., skipped the Emission Tab), select ‘Emission unavailable’, and the tool can still compile a ‘.inp’ file without emission information




Select pollutant type and modeling period. Depending on POLLUTID, the values of AVERTIME is consistent with NAAQS

![GTA 17](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic17.png)





Other information needed for AERMOD:
    • URBANOPT
    • FLAGPOLE


Click the SURFILE and PROFFILE buttons to locate surface meteorology (.SFC) and upper profile meteorology (.PFL) file. 1hr CO concentration is modeled in the example with meteorology file ‘test\_1h.SFC’ and ‘test\_1h.PFL’ uploaded



**Running AREA**

    • Compile and run AERMOD for various sources. Users can choose to run one or more sources as needed

    • Compile and run AERMOD for AREA Source

    • Upload ‘AREA.csv’ generated from Road Tab ‘\DC_DupontCircle\results\AREA.csv’

    • Upload ‘receptors_list.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\receptors_list.csv’

    • Upload ‘em_AREA.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\emission\em_AREA.csv’

    • Compile ‘.inp’, run AERMOD, and generate ‘.out’. Files stored in ‘\DC_DupontCircle\results\\*’ For this example running CO concentration in 1 hour, the files are named as:

        • ‘AREA_CO_1.inp’

        • ‘AREA_CO_1.out’

        • ‘[Source]_[Pollutant]_[Period]’





**Running VOLUME**

    • Compile and run AERMOD for VOLUME Source**

    • Upload ‘VOLUME_XX.csv’ generated from Road Tab ‘\DC_DupontCircle\results\VOLUME_XX.csv’
 
    • Upload ‘receptors_list.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\receptors_list.csv’

    • Upload ‘em_VOLUME_XX.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\emission\em_VOLUME_XX.csv'

    • Compile ‘.inp’, run AERMOD, and generate ‘.out’. Files stored in ‘\DC\_DupontCircle\results\\*’ For this example running CO concentration in 1 hour, the files are named as:

        • ‘VOLUME_CO_1.inp’

        • ‘VOLUME_CO_1.out’

        • ‘[Source]_[Pollutant]_[Period]’





**Running LINE**

    • Compile and run AERMOD for LINE Source**

    • Upload ‘Line.csv’ generated from Road Tab ‘\DC_DupontCircle\results\Line.csv’

    • Upload ‘receptors_list.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\receptors_list.csv’

    • Upload ‘em_LINE.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\emission\em_LINE.csv’

    • Compile ‘.inp’, run AERMOD, and generate ‘.out’. Files stored in ‘\DC\_DupontCircle\results\\*’ For this example running CO concentration in 1 hour, the files are named as:

        • ‘LINE_CO_1.inp’

        • ‘LINE_CO_1.out’

        • ‘[Source]_[Pollutant]_[Period]’





**Running RLINE**

    • Compile and run AERMOD for RLINE Source

    • Upload ‘Line.csv’ generated from Road Tab ‘\DC_DupontCircle\results\Line.csv’

    • Upload ‘receptors_list.csv’ generated from Receptors Tab ‘\DC\_DupontCircle\results\receptors_list.csv’

    • Upload ‘em_LINE.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\emission\em_LINE.csv’

    • Compile ‘.inp’, run AERMOD, and generate ‘.out’. Files stored in ‘\DC_DupontCircle\results\\*’ For this example running CO concentration in 1 hour, the files are named as:
        • ‘RLINE_CO_1.inp’

        • ‘RLINE_CO_1.out’

        • ‘[Source]_[Pollutant]_[Period]’





**Running RLINEXT**

    • Compile and run AERMOD for RLINEXT Source

    • Upload ‘Line.csv’ generated from Road Tab ‘\DC_DupontCircle\results\Line.csv’

    • Upload ‘receptors_list.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\receptors_list.csv’

    • Upload ‘em_RLINEXT.csv’ generated from Receptors Tab ‘\DC_DupontCircle\results\emission\em_RLINEXT.csv’

    • Compile ‘.inp’, run AERMOD, and generate ‘.out’. Files stored in ‘\DC\_DupontCircle\results\\*’ For this example running CO concentration in 1 hour, the files are named as:

        • ‘RLINEXT_CO_1.inp’

        • ‘RLINEXT_CO_1.out’

        • ‘[Source]_[Pollutant]_[Period]’





**Running AERMOD**

Reminder: running AERMOD may take seconds, minutes, hours, or even days, depending on the size of network, number of receptors, and modeling time period





***Results Tab***

Results Tab takes AERMOD output files ‘.out’, organize concentration results into csv files, and visualize concentration profile in heat map

![GTA 18](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic18.png)


• Click to upload AERMOD ‘.out’ and organize concentration into ‘.csv’ file. Takes seconds to minutes, depending on the number of receptor results. In the example, ‘RLINEXT_Line_CO_1.out’ was uploaded

‘RLINEXT_Line_CO_1.out’ in text format

![GTA 19](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic19.png)


‘RLINEXT_Line_CO_1.csv’

![GTA 20](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic20.png)





Users can type the concentration range to visualize (default as from 0 to maximum concentration value in the file) 
Then click the button to visualize concentration (range 0 - 2)

![GTA 21](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic21.png)




Users can type the concentration range to visualize (default as from 0 to maximum concentration value in the file)
Then click the button to visualize concentration (range 0 - 3)

![GTA 22](https://github.com/mitchdolby/GIS_AERMOD_Project/blob/main/pictures/GTA_Pic22.png)



