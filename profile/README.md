# Surface Biology and Geology (SBG) OTTER Thermal Infrared Data Product Algorithms

This organization contains the data product algorithms for the Surface Biology and Geology Thermal Infrared (SBG-TIR) Orbiting Terrestrial Thermal Emission Radiometer (OTTER) sensor.

NASA's SBG mission was a Designated Observable (DO) identified in the National Academies of Sciences, Engineering and Medicine (NASEM) 2017 Decadal Survey. The Decadal Survey document presented a clear vision for the combined roles of visible to shortwave infrared imaging spectroscopy and multispectral or hyperspectral thermal infrared image data in addressing terrestrial and aquatic ecosystems and other elements of biodiversity, geology, natural hazards, the water cycle, and applied sciences topics relevant to many areas with societal benefits. 

The SBG-TIR portion of the mission develops the TIR multispectral instrument. The SBG-TIR instrument measures the emitted radiance of the Earth surface and uses that information to better understand the dynamics of Earth's changing surface geology and biology, ground/water temperature, snow reflectivity, active geologic processes, vegetation traits, and algal biomass. The SGB-TIR mission is also a cooperative effort with the Italian Space Agency (Agenzia Spaziale Italiana; ASI), which provides SBG-TIR platform metadata and Visual and Near-Infrared (VNIR) products. Descriptions of partner products are covered in separate documents.

| **Areas** | **Product** | **ShortName** | 
| --- | --- | --- |
| Fundamental (Level 1) | Radiance at Sensor | RAS |
| Fundamental | Surface Temperature and Emissivity | LSTE (incl WT, ST, and SGC) |
| Fundamental | Cloud mask | CM |
| Plant Functional Traits Suite | Evapotranspiration<br> Water Use Efficiency<br> Evaporative Stress Index | ET<br> WUE<br> ESI |
| Geology Suite | Surface Minerology (TIR only)<br> Elevated Technical Features<br> Volcanic Activity | SM<br> ETF<br> VA |
| Snow Physics Suite | Snow Temperature (Use fundamental LST&E) | --- |
| Aquatics Biology/Biogeochemistry Suite | Water Temperature (Use fundamental LST&E) | --- |

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

## SBG-VSWIR

The algorithms for the visible shortwave infrared (VSWIR) component of the SBG mission are in the [sbg-vswir](https://github.com/sbg-vswir) organization.


## Standard Metadata

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

## Appendix of Abbreviations and Acronyms

| **Abbreviatios** | **Description** |
| --- | --- |
| ALEXI	| Atmospheric-Land Exchange Inversion |
| ARS	| Agricultural Research Service |
| ASD	| Algorithm Specifications Document |
| ATBD	| Algorithm Theoretical Basis Document |
| CCB	| Change Control Board |
| CDR	| Critical Design Review |
| CF	| Climate and Forecast (metadata convention) |
| CM	| Configuration Management |
| CONUS	| Continental United States |
| COTS	| Commercial Off The Shelf |
| DAAC	| Distributed Active Archive Center |
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
| SBG	| ECOsystem Spaceborne Thermal Radiometer on Space Station |
| EOS	| Earth Observing System |
| EOSDIS	| EOS Data and Information System |
| ESDIS	| Earth Science Data and Information System |
| ESDT	| Earth Science Data Type |
| FOV	| Field of View |
| FSW	| Flight Software |
| GB	| gigabytes, 109 bytes |
| GDS	| Ground Data System |
| GHA	| Greenwich Hour Angle |
| GHz	| Gigahertz, 109 hertz |
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
| Km	| kilometer, 1000 meters |
| L0 – L4	| Level 0 through Level 4 |
| LAN	| Local Area Network |
| LEO	| Low Earth Orbit |
| LOE	| Level of Effort |
| LOM	| Life of Mission |
| LP	| Land Processes |
| LSTE	| Land Surface Temperature and Emissivity |
| m	| meter |
| MB	| megabytes, 106 bytes |
| Mbps	| Mega bits per second |
| MHz	| Megahertz |
| MMR	| Monthly Management Review |
| MOA	| Memorandum of Agreement |
| MODIS	| Moderate Resolution Imaging Spectroradiometer |
| MOS	| Mission Operations System |
| m/s	| meters per second |
| ms	| milliseconds |
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
| percent	% | parts per hundred |
| PR	| Problem Report |
| PSD	| Product Specifications Document |
| PT-JPL	| Priestly-Taylor-JPL |
| PT-JPL-SM | Priestly-Taylor-JPL-Soil Moisutre |
| QA	| Quality Assurance |
| rad	| radians |
| RDD	| Release Description Document |
| RFA	| Request For Action |
| S/C	| Spacecraft |
| SCP	| Secure Copy |
| SDP	| Software Development Plan |
| SDS	| Science Data System |
| sec, s	| seconds |
| SITP	| System Integration and Test Plan |
| SMP	| Software Management Plan |
| SOM	| Software Operators Manual |
| TAI	| International Atomic Clock |
| Tb	| Brightness Temperature |
| TBD	| To Be Determined |
| TBS	| To Be Specified |
| TOA	| Time of Arrival |
| TPS	| Third Party Software |
| USDA	| United State Department of Agriculture |
| USGS	| United States Geological Society |
| UTC	| Coordinated Universal Time |
| V&V	| Verification and Validation |
| XML	| Extensible Markup Language |
