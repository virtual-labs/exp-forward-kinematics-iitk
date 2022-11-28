<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>

# Introduction

The PUMA 560 is a industrial robot arm with six degrees of freedom and all rotational joints. In this experiment at first a brief theory about PUMA 560 robot is presented in the theory section. The theory for mathematical computations was obtained from a wide variety of sources encompassing books, papers and internet. In simulation section a virtual model is developed in javascript program which is used to investigate the forward kinematics problem. For more information on other aspects of PUMA 560 and robotics visitors are advised to follow the references.
<center>
<img src="./images/PUMA560.jpg">

***Figure 1: PUMA 560***
</center>

# Theory
- Programmable Universal Machine for Assembly, more popularly known as PUMA is an industrial robot arm developed by Victor Scheinman at Unimation, in the year 1978. PUMA comes in various makes viz. PUMA 260, PUMA 560, PUMA 761 etc. Figure 2 shows link-frame assignments in the position corresponding to all joint angles equal to zero. Here the frame {0} (not shown) is coincident with frame [1} when is zero. Note also that, for this robot, as for many industrial robots, the joint axes of joints 4, 5, and 6 all intersect at a common point, and this point of intersection coincides with the origin of frames {4}, {5}, and {6}. Furthermore, the joint axes 4, 5, and 6 are mutually orthogonal. This wrist mechanism is illustrated schematically in Fig.4. In this experiment forward kinematics of PUMA 560 is described through a virtual model. The forward kinematics problem is concerned with the relationship between the individual joints of the robot manipulator and the position and orientation of the tool or end effector. 


## General Terminology in Robotics:

### Workspace:

The reachable workspace of a robot's end-effector is the manifold of reachable frames.

### Accuracy:

Accuracy refers to a robot's ability to position its wrist end at a desired target point within the work volume, and it is defined in terms of spatial resolution. It depends on the technology and the control increments.

### Repeatability:

Repeatability is a statistical term associated with accuracy. If a robot joint moves by the same angle from a certain point a number of times, all with equal environmental conditions, the target is always missed by a large margin. If the same error is repeated, then we say that the repeatability is high and the accuracy is poor.

### Safety:

The ability to reduce the human-robot impact force and ensure human safety is a fundamental requirement for human-friendly robots.

### Forward Kinematics :

Forward kinematics (FK) mainly deals with constructing a Denavit-Hartenberg (D-H) transformation matrix with Puma's parameters obtained from a D-H parameter table shown below: 

<center>
<img src="./images/puma560-kM.jpg">

***Figure 2: Kinematic parameters and frame assignments for the PUMA 560 manipulator.***
</center>

<center>
<img src="./images/puma560-kM1.jpg">

***Figure 3: Kinematic parameters and frame assignments for the forearm of the PUMA 560 manipulator.***
</center>

<center>
<img src="./images/puma560-kM2.jpg">

***Figure 4: Schematic of a 3R wrist in which all three axes intersect at a point and are mutually orthogonal.***
</center>


<center>

***Table 1. Puma 560 D-H parameter table***

| $$ Link_i $$ | $$	\\alpha_{i-1} $$ | $$ a_{i-1}(m) $$ | $$ d_i (m) $$ | $$ \\theta_i $$ |
| :-- | :-- | :-- | :-- | :-- |
| $$ 1 $$ | $$ 0 $$ | $$ 0 $$ | $$ 0 $$ | $$ \\theta_1 $$ |
| $$ 2 $$ | $$ -90 $$ | $$ 0 $$ | $$ 0 $$ | $$ \\theta_2 $$ |
| $$ 3 $$ | $$ 0 $$ | $$ a_2 $$ | $$ d_2 $$ | $$ \\theta_3 $$ |
| $$ 4 $$ | $$ -90 $$ | $$ a_3 $$ | $$ d_3 $$ | $$ \\theta_4 $$ |
| $$ 5 $$ | $$ 90 $$ | $$ 0 $$ | $$ 0 $$ | $$ \\theta_5 $$ |
| $$ 6 $$ | $$ -90 $$ | $$ 0 $$ | $$ 0 $$ | $$ \\theta_6 $$ |

</center>

**Transformation matrices of six joints for Puma 560 robot**

$$ T_1= \\begin{bmatrix} 
cos(\\theta_1) & -sin(\\theta_1) & 0 & 0 \\
sin(\\theta_1) & cos(\\theta_1) & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
\\end{bmatrix}
$$