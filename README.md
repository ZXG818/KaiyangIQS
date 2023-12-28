# Improved quasi-static method solver based on OpenFOAM - KaiyangIQS.

This is a neutron space-time kinetics solver with improved quasi-static method based on OpenFOAM. This solver is named as KaiyangIQS, which will be a toolkit of Kaiyang Code (北斗第六 - 开阳). The algorithm, numerical methods, and validated cases can be referred from: *Development of a neutron space-time kinetics solver with improved quasi-static method based on OpenFOAM, Nuclear Engineering and Design (under review)*

## Authors' infomation
Tutor: Prof. Dalin Zhang (张大林), Xi'an Jiaotong University, China, <dlzhang@mail.xjtu.edu.cn>, personal page: <https://gr.xjtu.edu.cn/en/web/dlzhang>

Author: Xingguang Zhou (周星光), Doctor of Engineering (student) at Xi'an Jiaotong University, China, <zxg818@stu.xjtu.edu.cn>

Author: Xinyu Li (李新宇), Doctor of Philosophy (student) at Xi'an Jiaotong University, China, <lixinyu0031@stu.xjtu.edu.cn>

Lab: Nuclear Thermal-hydraulic Laboratory at Xi'an Jiaotong University (XJTU-NuTHeL), website: <http://nuthel.xjtu.edu.cn/index.htm>

## OpenFOAM version
The improved quasi-static method solver, KaiyangIQS, developed in this study is based on OpenFOAM-v2006, and the website is <https://www.openfoam.com/news/main-news/openfoam-v20-06>

## Description
There are three cases in this repository. *Unidimensional-rod-ejection*, *TWIGL-2D*, and *3D-rod-ejection* are the cases which has been validated in the paper. 
### Improved quasi-static solver
In each case, the dictionary **neutronKineticsSolver** is the solver with improved quasi-static method. In the dictionary neutronKineticsSolver, **adjointDiffusionFoam** is the solver of adjoint scalar flux diffusion equation, and **iqsNeutronicsFoam** is the solver with improved quasi-statics method. In the dictionary of iqsNeutronicsFoam, **pointKinetics** is the module of amplitude function, **shapeDiffusion** is the module of shape function. **iqsNeutronicsFoam.C** is the main control of the whole algorithm. 

