# BDML/BD5
an open format for representing quantitative data of biological dynamics

## Motivation
Rapid advances in live-cell imaging and modeling techniques enable many research groups to obtain a huge amount of quantitative biological dynamics data on spatiotemporal dynamics of biological objects such as molecules, cells, and organisms. However, their data cannot often be compared and analyzed by the same software tools because of different data formats. BDML (Biological Dynamics Markup Language) aims to facilitate data exchange and development of software tools for data visualization and analysis.

## Overview of BDML/BD5
BDML is an open format for representing quantitative biological dynamics data. It is based on Extensible Markup Language (XML). By using BDML, a wide variety of quantitative biological dynamics data from molecules to cells to organisms can be described. To describe a large size of quantitative biological dynamics data, we developed BD5, an HDF5-based data format to support BDML for storing quantitative biological dynamics data.

BDML schema and specification: <http://ssbd.qbic.riken.jp/bdml/>  
BD5 specification:

 BD5 has one container named *data* group. It includes
  * *scaleUnit* dataset for the definition of spatial and time scale and unit,
  * *objectDef* dataset for the definition of biological objects,
  * *featureDef* dataset for features of interest,
  * numbered groups (0, 1, ..., n) corresponding to the number in time series,
  * *trackInfo* dataset for the information of tracking of one object to another.

![Overview of BD5 data format](BD5Overview.png)

In *scaleUnit*, spatial and time scale and unit is defined. *dimension* should be described by "0D", "1D", "2D", "3D", "0D+T", "1D+T", "2D+T" or "3D+T". Followed by *dimension*, *xScale*, *yScale*, *zScale* and *sUnit* should be described. In the case of time series data, *tScale* and *tUnit* should be described.

|dimension |xScale |yScale |zScale |sUnit      |tScale |tUnit  |
|:---------|-------|-------|-------|-----------|-------|-------|
|3D+T      |0.5    |0.5    |1.0    |micrometer |1.0    |second |

Each numbered group has *object* and *feature* groups. Each *object* group has numbered dataset(s) corresponding to the reference number of the biological object predefined in the *objectDef* dataset. Each row of a numbered object includes the ID of the object and the spatiotemporal information of the object. In the current version of BD5, we prepared five entities, "point, "circle", "sphere", "line" and "face". In the case of "point" entity, each row of a numbered object includes time and xyz (or xy or x) coordinates. In the case of "circle" or "sphere" entity, each row includes time and xyz (or xy) coordinates. In the case of "line" or "face" entity, each row includes time, xyz (or xy) coordinates, and *seqID*. The *seqID* represents the ID of sequence of xyz coordinates. A set of regions or surfaces each of which is connected by xyz coordinates described beginning at the top represents the spatial information of the object.

## Program codes
Some software tools for data visualization and analysis are available at <http://ssbd.qbic.riken.jp/software/>.

Some programs of Jupyter Notebook for BD5 format are also available as follows:

1. <https://github.com/openssbd/BDML-BD5/blob/master/BD5_Displacement.ipynb>  
2. <https://github.com/openssbd/BDML-BD5/blob/master/BD5_ProliferationCurve.ipynb>

## Reference
Koji Kyoda, Yukako Tohsato, Kenneth H.L. Ho, Shuichi Onami (2015) Biological Dynamics Markup Language (BDML): an open format for representing quantitative biological dynamics data. *Bioinformatics* **31**, 1044-1052.
