# Surface Biology and Geology (SBG) OTTER Thermal Infrared Data Product Algorithms

## Identification
This organization contains the data product algorithms for the Surface Biology and Geology Thermal Infrared (SBG-TIR) Orbiting Terrestrial Thermal Emission Radiometer (OTTER) sensor. 

This document will provide background information relevant to the SBG-TIR mission and data products. 

## SBG-TIR Data Product Algorithms

The SBG-TIR data product algorithms include:
- [Level 1 Radiance and Brightness Temperature (L1 BT)](https://github.com/sbg-tir/SBG-TIR-L1)
- [Level 2 Land-Surface Temperature and Emissivity (L2 LSTE)](https://github.com/sbg-tir/SBG-TIR-L2-LSTE)
- [Level 2 STARS NDVI and Albedo (L2 STARS)](https://github.com/sbg-tir/SBG-TIR-L2-STARS)
- [Level 3 Evapotranspiration (L3 ET)](https://github.com/sbg-tir/SBG-TIR-L3-ET)
  - [Level 4 Evapotranspiration (L4 ESI)](https://github.com/sbg-tir/SBG-TIR-L3-ET?tab=readme-ov-file#l4t-esi-and-wue-products)
  - [Level 4 Water Use Efficiency (L4 WUE)](https://github.com/sbg-tir/SBG-TIR-L3-ET?tab=readme-ov-file#l4t-esi-and-wue-products)
- [Level 3 Surface Mineralogy (L3 SM)](https://github.com/sbg-tir/SBG-TIR-L3-SM)
- [Level 3 Elevated Temperature Features (L3 ETF)](https://github.com/sbg-tir/SBG-TIR-L3-ETF)
- [Level 4 Volcanic Activity (L4 VA)](https://github.com/sbg-tir/SBG-TIR-L4-VA)

## Evapotranspiration Models

The evapotranspiration models for the level 3 and 4 ecosystem products are being developed in the [JPL-Evapotranspiration-Algorithms](https://github.com/JPL-Evapotranspiration-Algorithms) organization. These models include:
- [Surface Temperature Initiated Closure (STIC)](https://github.com/JPL-Evapotranspiration-Algorithms/STIC)
- [Breathing Earth System Simulator (BESS)](https://github.com/JPL-Evapotranspiration-Algorithms/BESS)
- [Priestley Taylor Jet Propulsion Laboratory (PT-JPL)](https://github.com/JPL-Evapotranspiration-Algorithms/PT-JPL)
- [Priestley Taylor Jet Propulsion Laboratory Soil Moisture (PT-JPL-SM)](https://github.com/JPL-Evapotranspiration-Algorithms/PT-JPL-SM)

## STARS Data Fusion System

The STARS data fusion system supporting the auxiliary inputs for the ecosystem products is being developed in the [STARS-Data-Fusion](https://github.com/STARS-Data-Fusion) organization.

The Julia implementation for the STARS data fusion algorithm is in [STARS.jl](https://github.com/STARS-Data-Fusion/STARS.jl).

There are several supporting sub-components in generalized Julia packages, including:

- [SentinelTiles.jl](https://github.com/STARS-Data-Fusion/SentinelTiles.jl) for geo-referencing Sentinel UTM tiles
- [MODLAND.jl](https://github.com/STARS-Data-Fusion/MODLAND.jl) for geo-referencing MODIS/VIIRS sinusoidal tiles
- [CMR.jl](https://github.com/STARS-Data-Fusion/CMR.jl) for searching the Common Metadata Repository (CMR)
- [HLS.jl](https://github.com/STARS-Data-Fusion/HLS.jl) for searching and downloading the Harmonized Landsat Sentinel (HLS) dataset
- [VNP43NRT.jl](https://github.com/STARS-Data-Fusion/VNP43NRT.jl) for Bidirectional Reflectance Distribution Function (BRDF)

### Mission Background

The SBG mission has been divided into two separate satellite platforms, supporting 1) visible shortwave infrared (VSWIR) collections, and 2) multispectral thermal (TIR) collections. The algorithms for the VSWIR component of the SBG mission are in the [sbg-vswir](https://github.com/sbg-vswir) organization. 

The SGB-TIR mission is also a cooperative effort with the Italian Space Agency (Agenzia Spaziale Italiana; ASI), which provides SBG-TIR platform metadata and Visual and Near-Infrared (VNIR) products. 

The OTTER instrument consists of six spectral and two mid infrared bands with 60-m resolution and ~3 day revisit. OTTER will measure the emitted radiance of the Earth surface to better understand the dynamics of Earth’s changing surface geology and biology, focusing on ground/water temperature, snow reflectivity, active geologic processes, vegetation traits, and algal biomass; directly addressing the topics of interest identified in the National Academies of Sciences, Engineering and Medicine (NASEM) 2017 Decadal Survey. 

SBG-TIR Level 0 data include spacecraft packets that have been pre-processed by the Ground Data System (GDS). Level 1 products include spacecraft engineering data, the time-tagged raw sensor pixels appended with their radiometric calibration coefficients, the blackbody pixels used to generate the calibration coefficients, geolocated and radiometrically calibrated at-sensor radiances of each image pixel, the geolocation tags of each pixel, and the corrected spacecraft attitude data. Level 2 products include the visible near infrared top of atmosphere (VNIR TOA) reflectance, VNIR bottom of atmosphere (BOA) reflectance, the normalized difference vegetation index (NDVI), the surface temperature and emissivity of each spectral band retrieved from the at-sensor radiance data, and a cloud mask. The Ecosystems, Geology, Snow Physics, and Aquatic Biology/Geochemistry suites are comprised of Level 3 and 4 products. Level 3 products include evapotranspiration, elevated temperature features, and surface minerology data derived from Level 2 data. Level 4 products contain evaporative stress index, water use efficiency, and volcanic activity derived from Level 2 and 3 data.

| **Areas** | **Product** | **ShortName** | **File Format** | 
| --- | --- | --- | --- | 
| Fundamental (Level 1) | Radiance and Brightness Temperature | RAS | sw | NetCDF-4 |
| Fundamental | Surface Temperature and Emissivity | LSTE (WT, ST, and SGC) | COG |
| Fundamental | Cloud mask<br> Water mask | CM<br> WM | NetCDF-4 |
| Ecosystems Suite | Evapotranspiration<br> Water Use Efficiency<br> Evaporative Stress Index | ET<br> WUE<br> ESI | COG |
| Geology Suite | Surface Minerology (TIR only)<br> Elevated Technical Features<br> Volcanic Activity | SM<br> ETF<br> VA | COG |
| Snow Physics Suite | Snow Temperature (Use fundamental LST&E) | --- | COG |
| Aquatics Biology/Biogeochemistry Suite | Water Temperature (Use fundamental LST&E) | --- | COG |

*Table 1. SBG-TIR products*


### Band characteristics

The TIR instrument will acquire data from a sun-synchronous orbit of ~700 km with 60m spatial resolution in eight spectral bands with two of those located in the MIR and six in the TIR region of the electromagnetic spectrum between 3 and 13 µm. The center position and width of each band is provided in Table 2. The positions of the first three TIR bands closely match those of the ASTER sensor (ASTER bands 10 – 12), whereas the longest two TIR bands match those of the MODIS sensor (MODIS bands 31-32), which are typically used for “split-window” type temperature applications (REFS). The OTTER band centered at 10.3 µm detects surface mineralogy more accurately (e.g., distinguishing between silicate feldspars and quartz) as well as sulfate aerosols conversion in volcanic plumes. The two MIR bands are present to detect a larger range of high surface temperatures without saturating (e.g., 500 – 1200 K) as well as the potential of elevated CO2 emission sources using the 4.8 µm band.

It is expected that small adjustments to the band positions, widths, and transmission will be made based on ongoing engineering filter performance capabilities and finalized once the filters are fabricated.

| **Band #** | **Center Wavelength (µm)** | **Spectral Width (FWHM) (nm)** | **Tolerance Center Wavelength (± nm)** | **Tolerance Spectral Width (±nm)** | **Knowledge Center Wavelength (±nm)** | **Knowledge Spectral Width (±nm)** | **Accuracy (K)** | **NEΔT (K)** | **Range (K)** |
| --- | --- | --- | --- | --- | --- | --- | --- |--- | --- |
| MIR-1 | 3.98 | 20 | 50 | 10 | 10 | 10 | ≤3@750 | ≤0.3@750 | 700-1200 |
| MIR-2 | 4.8 | 150 | 100 | 50 | 20 | 20 | ≤1@450 | ≤0.2@450 | 400-800 |
| TIR-1 | 8.32 | 300 | 100 | 50 | 20 | 20 | ≤0.5@275 | ≤0.2@275 | 200-500 |
| TIR-2 | 8.63 | 300 | 100 | 50 | 20 | 20 | ≤0.5@275 | ≤0.2@275 | 200-500 |
| TIR-3 | 9.07 | 300 | 100 | 50 | 20 | 20 | ≤0.5@275 | ≤0.2@275 | 200-500 |
| TIR-4 | 10.30 | 300 | 50 | 50 | 20 | 20 | ≤0.5@275 | ≤0.2@275 | 200-500 |
| TIR-5 | 11.35 | 300 | 100 | 50 | 20 | 20 | ≤0.5@275 | ≤0.2@275 | 200-500 |
| TIR-6 | 12.05 | 300 | 100 | 50 | 20 | 20 | ≤0.5@275 | ≤0.2@275 | 200-500 |

*Table 2: SBG final band positions and characteristics.*

### Product File Name Format

Product file names will have the form (TBD):
<SBG_Name>_<PROD_TYPE>_<OOOOO>_<SSS>_<YYYYMMDD>T<hhmmss>_<BBbb>_<VV>.<TYPE>

Where:
SBG_Name: SBG-TIR name designation (TBD)
PROD_TYPE:  L1A/L1B products; Example=L1B_RAD
OOOOO:  Orbit number; starting at start of mission, ascending equatorial crossing
SSS:  Scene ID; starting at first scene of each orbit
YYYYMMDD:  Year, month, day of scene start time
hhmmss:  Hour, minute, second of scene start time
BBbb:  Build ID of software that generated product, Major+Minor (2+2 digits)
VV:  Product version number (2 digits)
TYPE:  File type extension=
nc or tif for the data file
nc.met or tif.met for the metadata file.

To provide an analysis-ready format, the SBG products are distributed in a tiled form and using the COG format:

#### NetCDF-4 File Format

The Network Common Data Form 4 (NetCDF-4) format will be used to distribute SBG granules at the orbit/scene level. These product files have a .nc file extension and are internally organized using the NetCDF-4 data standard. The NetCDF-4 format is utilized here for long-term archiving, and is not recommended for end-user analysis. These NetCDF-4 files are compatible with NetCDF Viewer, Panoply, and the NetCDF4 package in Python.

Each SBG swath product in NetCDF format will contain at least 3 groups of data:  A standard metadata group that specifies the same type of contents for all products, a product specific metadata group that specifies those metadata elements that are useful for defining attributes of the product data, and the group(s) containing the product data.  

Information on Network Common Data Form (NetCDF-4) may be found at https://www.unidata.ucar.edu/software/netcdf/. 

#### Cloud-Optimized GeoTIFF Orbit/Scene/Tile Format
All SBG-TIR standard products are stored in the Geographic Tagged Image File Format (GeoTIFF). GeoTIFF is a general purpose file format and programming library for storing scientific data. The GeoTIFF format was originally created by Dr. Niles Ritter with the Open Geospatial Consortium publishing the OGC GeoTIFF standard, which defines the GeoTIFF by specifying requirements and encoding rules for using the Tagged Image File Format (TIFF) for the exchange of georeferenced or geocoded image data. The following sections provide some key elements of GeoTIFF that will be employed in SBG-TIR data products. 


The tiled products include the letter T in their level identifiers: L1CT, L2T, L3T, and L4T. The tiling system used for SBG is borrowed from the modified Military Grid Reference System (MGRS) tiling scheme used by Sentinel 2. These tiles divide the Universal Transverse Mercator (UTM) zones into square tiles 109800 m across. SBG uses a 60 m cell size with 1830 rows by 1830 columns in each tile, totaling 3.35 million pixels per tile. This allows the end user to assume that each 60 m SBG pixel will remain in the same location at each timestep observed in analysis. The COG format also facilitates end-user analysis as a universally recognized and supported format, compatible with open-source software, including QGIS, ArcGIS, GDAL, the Raster package in R, `rioxarray` in Python,and `Rasters.jl` in Julia.

Each `float32` data layer occupies 4 bytes of storage per pixel, which amounts to an uncompressed size of 13.4 mb for each tiled data layer. The `uint8` quality flag layers occupy a single byte per pixel, which amounts to an uncompressed size of 3.35 mb per tiled data quality layer.

Each `.tif` COG data layer in each L2T/L3T/L4T product additionally contains a rendered browse image in GeoJPEG format with a `.jpeg` extension. This image format is universally recognized and supported, and these files are compatible with Google Earth. Each L2T/L3T/L4T tile granule includes a `.json` file containing the Product Metadata and Standard Metadata in JSON format.

Each SBG tiled product in COG format will contain a standard metadata group that specifies the same type of contents for all products, and a product specific metadata group that specifies those metadata elements that are useful for defining attributes of the product data.  

Complete documentation of the GeoTIFF structure and application software can be found at https://www.ogc.org/standard/geotiff/.

### Quality Flags

Two high-level quality flags are provided in all gridded and tiled products as thematic/binary masks encoded to zero and one in unsigned 8-bit integer layers. The cloud layer represents the final cloud test from L2 CLOUD. The water layer represents the surface water body in the Shuttle Radar Topography Mission (SRTM) Digital Elevation Model. For both layers, zero means absence, and one means presence. Pixels with the value 1 in the cloud layer represent detection of cloud in that pixel. Pixels with the value 1 in the water layer represent open water surface in that pixel. All tiled product data layers written in `float32` contain a standard not-a-number (`NaN`) value at each pixel that could not be retrieved. The cloud and water layers are provided to explain these missing values.

### Standard Metadata 

| **Name** | **Type** | **Size** | **Example** |
| --- | --- | --- | --- |
| AncillaryInputPointer | String | variable | Group name of ancillary file list | 
| AutomaticQualityFlag | String | variable | PASS/FAIL (of product data) |
| BuildId | String | variable | |
| CollectionLabel | String | variable | |
| DataFormatType | String | variable | NCSAHDF5 |
| DayNightFlag | String | variable | |
| EastBoundingCoordinate | LongFloat | 8 | |
| HDFVersionId | String | variable | 1.8.16 |
| ImageLines | Int32 | 4 | 5632 |
| ImageLineSpacing | Float32 | 4 | 68.754 | 
| ImagePixels | Int32 | 4 | 5400 |
| ImagePixelSpacing | Float32 | 4 | 65.536 |
| InputPointer | String | variable | |
| InstrumentShortName | String | variable | SBG |
| LocalGranuleID | String | variable | --- |
| LongName | String | variable | SBG |
| InstrumentShortName | String | variable | --- |
| LocalGranuleID | String | variable | --- |
| LongName | String | variable | SBG |
| NorthBoundingCoordinate | LongFloat | 8 | --- |
| PGEName | String | variable | L2_LSTE (L2_CLOUD) |
| PGEVersion | String | variable | |
| PlatformLongName | String | variable | |
| PlatformShortName | String | variable | |
| PlatformType | String | variable | Spacecraft |
| ProcessingLevelID | String | variable | 1 |
| ProcessingLevelDescription | String | variable | Level 2 Land Surface Temperatures and Emissivity (Level 2 Cloud mask) |
| ProducerAgency | String | variable | JPL |
| ProducerInstitution | String | variable | Caltech |
| ProductionDateTime | String | variable | |
| ProductionLocation | String | variable | |
| CampaignShortName | String | variable | Primary |
| RangeBeginningDate | String | variable | |
| CampaignShortName | String | variable | |
| RangeBeginningDate | String | variable | |
| RangeBeginningTime | String | variable | |
| RangeEndingDate | String | variable | |
| RangeEndingTime | String | variable | |
| SceneID | String | variable | |
| ShortName | String | variable | L2_LSTE (L2_CLOUD) |
| SceneID | String | variable | |
| ShortName | String | variable | |
| SISName | String | variable | |
| SISVersion | String | variable | |
| SouthBoundingCoordinate | LongFloat | 8 | |
| StartOrbitNumber | String | variable | |
| StartOrbitNumber | String | variable | |
| WestBoundingCoordinate | LongFloat | 8 | |

*Table 3. Standard metadata included in SBG-TIR product files*

### Appendix of Abbreviations and Acronyms

| **Abbreviatios** | **Description** |
| --- | --- |
| ALEXI	| Atmospheric-Land Exchange Inversion |
| ARS	| Agricultural Research Service |
| ASD	| Algorithm Specifications Document |
| ATBD	| Algorithm Theoretical Basis Document |
| BESS | Breathing Earth System Simulator |
| C | Celsius |
| CCB	| Change Control Board |
| CDR	| Critical Design Review |
| CF	| Climate and Forecast (metadata convention) |
| CM	| Configuration Management |
| CONUS	| Continental United States |
| COTS	| Commercial Off The Shelf |
| DAAC	| Distributed Active Archive Center |
| BOA | Bottom of Atmosphere
| dB	| DeciBel |
| DCN	| Document Change Notice |
| deg	| Degrees |
| deg/sec	| Degrees per Second |
| DEM	| Digital Elevation Model |
| DisALEXI	| ALEXI Disaggregation algorithm |
| DN	| Data Number |
| EASE	| Equal Area Scalable Earth |
| ECI	| Earth Centered Inertial coordinate system |
| ECR	| Earth Centered Rotating coordinate system |
| ECS	| EOSDIS Core System |
| EOS	| Earth Observing System |
| EOSDIS	| EOS Data and Information System |
| ESDIS	| Earth Science Data and Information System |
| ESDT	| Earth Science Data Type |
| FOV	| Field of View |
| FSW	| Flight Software |
| GB	| gigabytes, 109 bytes |
| GDS	| Ground Data System |
| GHA	| Greenwich Hour Angle |
| GHz	| $$\text{Gigahertz, 10}^9$$ hertz |
| GMAO	| Global Modeling and Assimilation Office |
| GMT	| Greenwich Mean Time |
| GPP	| Gross Primary Production |
| GSE	| Ground Support Equipment |
| GSFC	| Goddard Space Flight Center |
| HDF	| Hierarchical Data Format |
| HK	| Housekeeping (telemetry) |
| HRSL	| Hydrology and Remote Sensing Laboratory |
| Hz	| Hertz |
| HSD	| Health and Status Data |
| I&T	| Integration and Test |
| ICD	| Interface Control Document |
| I/O	| Input/Output |
| IOC	| In-Orbit Checkout |
| IPA	| Inter-Project Agreement |
| ITAR	| International Traffic in Arms Regulation |
| JPL	| Jet Propulsion Laboratory |
| K	| Kelvin |
| KHz	| Kilohertz |
| Km	| Kilometer, 1000 meters |
| L0 – L4	| Level 0 through Level 4 |
| LAN	| Local Area Network |
| LEO	| Low Earth Orbit |
| LOE	| Level of Effort |
| LOM	| Life of Mission |
| LP	| Land Processes |
| LSTE	| Land Surface Temperature and Emissivity |
| m	| Meter |
| MB	| Megabytes, 106 bytes |
| Mbps	| Mega bits per second |
| MHz	| Megahertz |
| MMR	| Monthly Management Review |
| MOA	| Memorandum of Agreement |
| MOD16 | MODIS Global evapotranspiration algorithm |
| MODIS	| Moderate Resolution Imaging Spectroradiometer |
| MOS	| Mission Operations System |
| m/s	| Meters per second |
| ms	| Milliseconds |
| MS	| Mission System |
| NASA	| National Aeronautics and Space Administration  |
| NCEP	| National Centers for Environmental Protection |
| NCSA	| National Center for Supercomputing Applications |
| netCDF	| Network Common Data Format |
| NISN	| NASA Integrated Services Network |
| NOAA	| National Oceanic and Atmospheric Administration |
| OA	| Operations Agreement |
| ODL	| Object Description Language |
| OODT	| Object Oriented Data Technology |
| ORR	| Operational Readiness Review |
| ORT	| Operational Readiness Test |
| PDR	| Preliminary Design Review |
| percent	% | Parts per hundred |
| PR	| Problem Report |
| PSD	| Product Specifications Document |
| PT-JPL	| Priestly-Taylor-JPL |
| PT-JPL-SM | Priestly-Taylor-JPL-Soil Moisture |
| QA	| Quality Assurance |
| rad	| radians |
| RDD	| Release Description Document |
| RFA	| Request For Action |
| SBG	| ECOsystem Spaceborne Thermal Radiometer on Space Station |
| S/C	| Spacecraft |
| SCP	| Secure Copy |
| SDP	| Software Development Plan |
| SDS	| Science Data System |
| sec, s	| Seconds |
| SITP	| System Integration and Test Plan |
| SMP	| Software Management Plan |
| SOM	| Software Operators Manual |
| STIC | Surface Temperature Initiated Closure model | 
| TAI	| International Atomic Clock |
| Tb	| Brightness Temperature |
| TBD	| To Be Determined |
| TBS	| To Be Specified |
| TOA	| Top of Atmosphere |
| TPS	| Third Party Software |
| USDA	| United State Department of Agriculture |
| USGS	| United States Geological Society |
| UTC	| Coordinated Universal Time |
| V&V	| Verification and Validation |
| XML	| Extensible Markup Language |

*Table 4. Abbreviations and acronyms used in SBG-TIR documentation and products*

