# Improved quasi-static method solver based on OpenFOAM - KaiyangIQS.

This is a neutron space-time kinetics solver with improved quasi-static method based on OpenFOAM. This solver is named as KaiyangIQS, which will be a toolkit of Kaiyang Code (北斗第六 - 开阳). The algorithm, numerical methods, and validated cases can be referred from: *Development of a neutron space-time kinetics solver with improved quasi-static method based on OpenFOAM, Nuclear Engineering and Design (under review)*

## Authors' infomation
Tutor: Dalin Zhang (张大林), Professor, Xi'an Jiaotong University, China, <dlzhang@mail.xjtu.edu.cn>, personal page: <https://gr.xjtu.edu.cn/en/web/dlzhang>

Author: Xingguang Zhou (周星光), Doctor of Engineering (student), Xi'an Jiaotong University, China, <zxg818@stu.xjtu.edu.cn>

Author: Xinyu Li (李新宇), Doctor of Philosophy (student), Xi'an Jiaotong University, China, <lixinyu0031@stu.xjtu.edu.cn>

Lab: Nuclear Thermal-hydraulic Laboratory, Xi'an Jiaotong University (XJTU-NuTHeL), lab page: <http://nuthel.xjtu.edu.cn/index.htm>

## OpenFOAM version
The improved quasi-static method solver, KaiyangIQS, developed in this study is based on OpenFOAM-v2006, and the website is: <https://www.openfoam.com/news/main-news/openfoam-v20-06>

## Description
There are three benchmark problems in this repository. *Unidimensional-rod-ejection*, *TWIGL-2D*, and *3D-rod-ejection* are the cases which have been validated in the paper. 

### Improved quasi-static solver
1. In each case, the directory **neutronKineticsSolver** is the solver with improved quasi-static method.
2. In the directory neutronKineticsSolver, **adjointDiffusionFoam** is the solver of adjoint scalar flux diffusion equation, and **iqsNeutronicsFoam** is the solver with improved quasi-statics method.
3. In the directory of iqsNeutronicsFoam, **pointKinetics** is the module of amplitude function, **shapeDiffusion** is the module of shape function. **iqsNeutronicsFoam.C** is the main control of the whole algorithm.
4. Users will change the group constants over time at **shapeDiffusion/ChangeGroupConstant.H**, and calculate the kinetics parameters at **shapeDiffusion/KineticEffectiveCalc.H**. 

### Benchmark validation
For each benchmark validation, the name of the dictionary usually contains the keyword **Problem**. The benchmark validation directory is in the same level of directory **neutronKineticsSolver**.

### Compile the solver and run the cases
1. Open the terminal at the directory of iqsNeutronicsFoam, make sure to use the OpenFOAM-v2006 environment. Then, enter ```wclean``` and ```wmake```.
2. Swith the terminal to ***xxxProblem/Problem*** directory. Make sure to use the OpenFOAM-v2006 environment. Then enter ```testIQS >log``` in terminal.
3. After completing step 2, we can see that there is a **log** file occurs, and the results are in this file.
4. When calculation has done, we open the **log** file and use a text editor (such as Microsoft VScode: <https://code.visualstudio.com/>) to search and extract the target strings like ```n/n0 = 7(result a b c d e f)```.

## Notes 
1. Initial fields at ```t = 0s``` of shape function and DNPs are obtained from the diffusion solver **sp3Foam**. sp3Foam is a low-order neutron transport equation solver with SP3 method, and this solver also can solve the neutron diffusion equation. sp3Foam is under reviewing at *Development and validation of a low-order neutron transport solver with SP3 method based on OpenFOAM, Progress in Nuclear Energy (under review)*. We will open-source this solver while the under reivew has done.
2. KaiyangIQS has hard-coded the change of group constants and kinetics parameter calculation. Therefore, users need to manually modify the **shapeDiffusion/ChangeGroupConstant.H** and **shapeDiffusion/KineticEffectiveCalc.H**. For the verification of the three benchmark problems in this paper, we have made all code modifications. Users only need to recompile the solvers in the corresponding folders before running different benchmark problem.
3. Point kinetics solver and adjoint scalar flux diffusion equation solver in this paper also can both run independently and be validated.
4. For TWIGL benchmark problem, there are two cases: ramp perturbation and linear perturbation. This repo only uploads the linear perturbation. If the user want to run the ramp perturbation case, only need to modify the read group constant file ```iqsNeutronicsFoam/shapeDiffusion/readGroupConstants.H``` in the ```TWIGL-2D/neutronKineticsSolver``` folder, and it is easy. 
5. At present, this version of KaiyangIQS is still an alpha version (in the debugging state), and further optimization of its code architecture will be carried out, including but not limited to group constants input optimization, post-processing optimization, parallel computing, etc.

## License 
KaiyangIQS is complied with GPLv3 license: <https://www.gnu.org/licenses/gpl-3.0.en.html>. 
