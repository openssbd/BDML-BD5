# BDML/BD5
an open format for representing quantitative data of biological dynamics

## Motivation
Rapid advances in live-cell imaging and modeling techniques enable many research groups to obtain a huge amount of quantitative biological dynamics data on spatiotemporal dynamics of biological objects such as molecules, cells, and organisms. However, their data cannot often be compared and analyzed by the same software tools because of different data formats. BDML (Biological Dynamics Markup Language) aims to facilitate data exchange and development of software tools for data visualization and analysis.

## Overview of BDML/BD5
BDML is an open format for representing quantitative biological dynamics data. It is based on Extensible Markup Language (XML). By using BDML, a wide variety of quantitative biological dynamics data from molecules to cells to organisms can be described. To describe a large size of quantitative biological dynamics data, we developed BD5, an HDF5-based data format to support BDML for storing quantitative biological dynamics data.

BDML schema and specification: <http://ssbd.qbic.riken.jp/bdml/>  
BD5 specification: will be available soon.
 BD5 has one container named *data* group. It includes
  * *scaleUnit* dataset for the definition of spatial and time scale and unit,
  * *objectDef* dataset for the definition of biological objects,
  * *featureDef* dataset for features of interest,
  * numbered groups (0, 1, ..., n) corresponding to the number in time series,
  * *trackInfo* dataset for the information of tracking of one object to another.


## Program codes
Some software tools for data visualization and analysis are available at <http://ssbd.qbic.riken.jp/software/>.

Some programs of Jupyter Notebook for BD5 format are also available as follows:

1. <https://github.com/openssbd/BDML-BD5/blob/master/BD5_Displacement.ipynb>  
2. <https://github.com/openssbd/BDML-BD5/blob/master/BD5_ProliferationCurve.ipynb>

## Reference
Koji Kyoda, Yukako Tohsato, Kenneth H.L. Ho, Shuichi Onami (2015) Biological Dynamics Markup Language (BDML): an open format for representing quantitative biological dynamics data. *Bioinformatics* **31**, 1044-1052.
