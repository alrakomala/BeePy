# BeePy

#### ¡Hola! En este taller vamos a utilizar datos públicos de la NASA sobre exoplanetas para aplicar técnicas de análisis de datos (limpieza, visualización, análisis descriptivo, machine learning).

## Introducción

El primer exoplaneta fue descubierto en 1990 y desde entonces se han identificado miles utilizando diversas técnicas como: tránsito, velocidad radial, imagen directa, microlentes, entre otros [$^1$](https://exoplanetarchive.ipac.caltech.edu/docs/counts_detail.html). La misión que ha descubierto más exoplanetas ha sido [**Kepler**](https://www.nasa.gov/mission_pages/kepler/overview/index.html), telescopio espacial que estuvo dedicado cerca de 10 años a la búsqueda de planetas extrasolares, especialmente aquellos de tamaño similar a la Tierra y que se encuentran en la zona de habitabilidad de su estrella.

Gracias a la Misión Kepler ahora sabemos que hay más planetas que estrellas en la galaxia. La técnica de detección con Kepler es la de tránsito, consiste en medir la luminosidad de la estrella como función del tiempo para identificar pequeñas disminuciones como consecuencia del paso del planeta entre la estrella y el observador (un mini mini eclipse).

Analizando la curva de luz es posible determinar el tamaño del planeta. 

## Objetivo

Analizar los datos disponibles para: 

- Familiarizarse con las propiedades y escalas de los exoplanetas y de su estrella anfitriona.
- Identificar sistemas planetarios.
- Determinar si la tercera ley de Kepler es válida para exoplanetas.
- Construir un modelo de aprendizaje automatizado que sea capaz de identificar futuros candidatos. 


## Datos

[NASA exoplanet archive](https://exoplanetarchive.ipac.caltech.edu)

-> 'Data', 'KOI_Table (Cumulative list)'



> COLUMN kepid:          KepID
> COLUMN kepoi_name:     KOI Name
> COLUMN kepler_name:    Kepler Name
> COLUMN koi_disposition: Exoplanet Archive Disposition
> COLUMN koi_vet_stat:   Vetting Status
> COLUMN koi_vet_date:   Date of Last Parameter Update
> COLUMN koi_pdisposition: Disposition Using Kepler Data
> COLUMN koi_score:      Disposition Score
> COLUMN koi_fpflag_nt:  Not Transit-Like False Positive Flag
> COLUMN koi_fpflag_ss:  Stellar Eclipse False Positive Flag
> COLUMN koi_fpflag_co:  Centroid Offset False Positive Flag
> COLUMN koi_fpflag_ec:  Ephemeris Match Indicates Contamination False Positive Flag
> COLUMN koi_disp_prov:  Disposition Provenance
> COLUMN koi_comment:    Comment
> COLUMN koi_period:     Orbital Period [days]
> COLUMN koi_time0bk:    Transit Epoch [BKJD]
> COLUMN koi_time0:      Transit Epoch [BJD]
> COLUMN koi_eccen:      Eccentricity
> COLUMN koi_longp:      Long. of Periastron [deg]
> COLUMN koi_impact:     Impact Parameter
> COLUMN koi_duration:   Transit Duration [hrs]
> COLUMN koi_ingress:    Ingress Duration [hrs]
> COLUMN koi_depth:      Transit Depth [ppm]
> COLUMN koi_ror:        Planet-Star Radius Ratio
> COLUMN koi_srho:       Fitted Stellar Density [g/cm**3]
> COLUMN koi_fittype:    Planetary Fit Type
> COLUMN koi_prad:       Planetary Radius [Earth radii]
> COLUMN koi_sma:        Orbit Semi-Major Axis [au]
> COLUMN koi_incl:       Inclination [deg]
> COLUMN koi_teq:        Equilibrium Temperature [K]
> COLUMN koi_insol:      Insolation Flux [Earth flux]
> COLUMN koi_dor:        Planet-Star Distance over Star Radius
> COLUMN koi_limbdark_mod: Limb Darkening Model
> COLUMN koi_ldm_coeff4: Limb Darkening Coeff. 4
> COLUMN koi_ldm_coeff3: Limb Darkening Coeff. 3
> COLUMN koi_ldm_coeff2: Limb Darkening Coeff. 2
> COLUMN koi_ldm_coeff1: Limb Darkening Coeff. 1
> COLUMN koi_parm_prov:  Parameters Provenance
> COLUMN koi_max_sngle_ev: Maximum Single Event Statistic
> COLUMN koi_max_mult_ev: Maximum Multiple Event Statistic
> COLUMN koi_model_snr:  Transit Signal-to-Noise
> COLUMN koi_count:      Number of Planets
> COLUMN koi_num_transits: Number of Transits
> COLUMN koi_tce_plnt_num: TCE Planet Number
> COLUMN koi_tce_delivname: TCE Delivery
> COLUMN koi_quarters:   Quarters
> COLUMN koi_bin_oedp_sig: Odd-Even Depth Comparision Statistic
> COLUMN koi_trans_mod:  Transit Model
> COLUMN koi_model_dof:  Degrees of Freedom
> COLUMN koi_model_chisq: Chi-Square
> COLUMN koi_datalink_dvr: Link to DV Report
> COLUMN koi_datalink_dvs: Link to DV Summary
> COLUMN koi_steff:      Stellar Effective Temperature [K]
> COLUMN koi_slogg:      Stellar Surface Gravity [log10(cm/s**2)]
> COLUMN koi_smet:       Stellar Metallicity [dex]
> COLUMN koi_srad:       Stellar Radius [Solar radii]
> COLUMN koi_smass:      Stellar Mass [Solar mass]
> COLUMN koi_sage:       Stellar Age [Gyr]
> COLUMN koi_sparprov:   Stellar Parameter Provenance
> COLUMN ra:             RA [decimal degrees]
> COLUMN dec:            Dec [decimal degrees]
> COLUMN koi_kepmag:     Kepler-band [mag]
> COLUMN koi_gmag:       g'-band [mag]
> COLUMN koi_rmag:       r'-band [mag]
> COLUMN koi_imag:       i'-band [mag]
> COLUMN koi_zmag:       z'-band [mag]
> COLUMN koi_jmag:       J-band [mag]
> COLUMN koi_hmag:       H-band [mag]
> COLUMN koi_kmag:       K-band [mag]
> COLUMN koi_fwm_stat_sig: FW Offset Significance [percent]
> COLUMN koi_fwm_sra:    FW Source &alpha;(OOT) [hrs]
> COLUMN koi_fwm_sdec:   FW Source &delta;(OOT) [deg]
> COLUMN koi_fwm_srao:   FW Source &Delta;&alpha;(OOT) [sec]
> COLUMN koi_fwm_sdeco:  FW Source &Delta;&delta;(OOT) [arcsec]
> COLUMN koi_fwm_prao:   FW &Delta;&alpha;(OOT) [sec]
> COLUMN koi_fwm_pdeco:  FW &Delta;&delta;(OOT) [arcsec]
> COLUMN koi_dicco_mra:  PRF &Delta;&alpha;<sub>SQ</sub>(OOT) [arcsec]
> COLUMN koi_dicco_mdec: PRF &Delta;&delta;<sub>SQ</sub>(OOT) [arcsec]
> COLUMN koi_dicco_msky: PRF &Delta;&theta;<sub>SQ</sub>(OOT) [arcsec]
> COLUMN koi_dikco_mra:  PRF &Delta;&alpha;<sub>SQ</sub>(KIC) [arcsec]
> COLUMN koi_dikco_mdec: PRF &Delta;&delta;<sub>SQ</sub>(KIC) [arcsec]
> COLUMN koi_dikco_msky: PRF &Delta;&theta;<sub>SQ</sub>(KIC) [arcsec]