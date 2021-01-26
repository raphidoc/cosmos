# Disclaimer

What is described here can be pertinent and useful in any case. But to truly unleash the potential of the concepts presented here, to accomplish the specific goal of improving the practice of science requiring a good amount of complex data with [interwingled](https://en.wikipedia.org/wiki/Intertwingularity) relationships, one must consider the metadata as a primary key. This data about data is critical to properly explore, explain and analyze a database. Nothing can replace the absence of it's collection on filed.

# Directory tree

The directory tree is the basis of the data architecture. This piece is critical to the integrity of the database as it is the main storage for raw and process data files as well as metadata in the form of log-field and log-processing.
Any change made to it after it's creation would be tricky, and it become trickier with time and project completion ...
Therefore this part should not change in the future even with modification of the acquisition methods. So the difficulty here is to create a structure specific enough to ensure integrity and efficiency as well as being able to ingest changes. This is the tradeoff between specificity and generality.

![directory_tree](/images/directory_tree.png)

Under is the tree of the directory-tree example. It contain data that have been acquired and stored but not processed or organized in a convenient way. From this stage, the call to some basic function (l2_*_gen) should conveniently create and fill the L2 of the structure. This L2 is based on the synthesis_data where key -> {Latitude, Longitude, DateTime}. Notably, the Z dimension of synthesis_water-sample where key -> {Latitude, Longitude, Zsample, DateTime} is "compressed".

This data can be downloaded to test and improve the [lighthouse](https://srscm03.uqar.ca/mabr0002/lighthouse) package

```bash
└── CHONe
    ├── CHONe_data_synthesis.csv
    ├── L1
    │   ├── bathymetry
    │   ├── diving
    │   │   ├── asd
    │   │   ├── lai
    │   │   └── quadra
    │   ├── fun-exp
    │   ├── Intertidal
    │   │   ├── asd
    │   │   ├── lai
    │   │   └── quadra
    │   └── water-column
    │       ├── cops
    │       │   ├── 20170504
    │       │   │   ├── BSI_CAST_004_170504_195653_URC.csv
    │       │   │   ├── BSI_CAST_005_170504_195846_URC.csv
    │       │   │   ├── BSI_CAST_006_170504_200025_URC.csv
    │       │   │   ├── BSI_CAST_007_170504_200209_URC.csv
    │       │   │   └── GPS_170504.csv
    │       │   ├── 20170521
    │       │   │   ├── BSI_CAST_002_170521_125701_URC.csv
    │       │   │   ├── BSI_CAST_003_170521_130018_URC.csv
    │       │   │   ├── BSI_CAST_004_170521_130415_URC.csv
    │       │   │   └── GPS_170521.csv
    │       │   └── 20190601
    │       │       ├── BSI_CAST_008_190601_133150_URC.csv
    │       │       ├── BSI_CAST_009_190601_133725_URC.csv
    │       │       ├── BSI_CAST_010_190601_134524_URC.csv
    │       │       └── GPS_190601.csv
    │       ├── iop
    │       │   ├── 20170504
    │       │   │   ├── ASPH023.txt
    │       │   │   ├── CTD023.TXT
    │       │   │   ├── FL023.TXT
    │       │   │   └── HS6023.dat
    │       │   ├── 20170521
    │       │   │   ├── ASPH035.txt
    │       │   │   ├── CTD035.TXT
    │       │   │   ├── FL035.TXT
    │       │   │   └── HS6035.dat
    │       │   └── 20190601
    │       │       └── HS6127.dat
    │       └── water-sample
    │           ├── Ag
    │           │   ├── Ag_processing_log_CHONe.csv
    │           │   └── raw
    │           │       ├── 030.Sample.Raw.csv
    │           │       ├── 035.Sample.Raw.csv
    │           │       ├── 036.Sample.Raw.csv
    │           │       ├── 136A.Sample.Raw.csv
    │           │       └── 136B.Sample.Raw.csv
    │           ├── Ap
    │           │   ├── Ap_processing_log_CHONe.csv
    │           │   └── raw
    │           │       ├── 023_A_Ap.Sample.Raw.csv
    │           │       ├── 023_A_NAp.Sample.Raw.csv
    │           │       ├── 023_B_Ap.Sample.Raw.csv
    │           │       ├── 023_B_NAp.Sample.Raw.csv
    │           │       ├── 035_A_Ap.Sample.Raw.csv
    │           │       ├── 035_A_NAp.Sample.Raw.csv
    │           │       ├── 035_B_Ap.Sample.Raw.csv
    │           │       ├── 035_B_NAp.Sample.Raw.csv
    │           │       ├── 036_A_Ap.Sample.Raw.csv
    │           │       ├── 036_A_NAp.Sample.Raw.csv
    │           │       ├── 036_B_Ap.Sample.Raw.csv
    │           │       ├── 036_B_NAp.Sample.Raw.csv
    │           │       ├── 136_A_Ap.Sample.Raw.csv
    │           │       ├── 136_A_NAp.Sample.Raw.csv
    │           │       ├── 136_B_Ap.Sample.Raw.csv
    │           │       └── 136_B_NAp.Sample.Raw.csv
    │           ├── CHONe_water-sample_synthesis.csv
    │           └── SPM
    │               └── SPM_CHONe.csv
    ├── L2
    ├── L3
    ├── log-field
    ├── log-processing
    └── TEMP
        └── raphael

33 directories, 48 files

```


# RDBMS

First of all, a thorough investigation should be performed to asses the normalization level required for our database, considering the tradeoff between integrity and performance under normal usage condition. The data lifecycle make it subject to reanalysis and hence to several [CRUD](https://fr.wikipedia.org/wiki/CRUD) operation.

## Data lifecycle and normal usage condition

1. Acquisition
    1. Methods

2. Processing
    1. Quality Check
    2. Reprocessing

3. Distribution


# In between

Beside the directory tree and the RDBMS, several html dashboard are online:
1. [Database dashboard](https://base-dashboard.netlify.app), built from SQLite database. (faster in chrome)
2. [QC SPM dashboard](https://chone-qc-spm.netlify.app), built from SPM 'L2' by L3 function.

The link between the directory tree and the RDBMS should be [ACID](https://fr.wikipedia.org/wiki/Propri%C3%A9t%C3%A9s_ACID) compliant.
