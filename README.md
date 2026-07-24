# Examples-mapdl
This repo is a collection of mapdl examples showing the modeling capabilities that complement Ansys Maxwell, particularly on the multiphysics perspective.

# Types of Coupled-Field Analysis or Multiphysics Analysis

A *coupled-field analysis*, also known as a *multiphysics analysis*, is a combination of analyses from different engineering disciplines (physics fields) that interact to solve a global engineering problem. When the input of one field analysis depends on the results from another analysis, the analyses are *coupled*.

Some analyses can have *one-way coupling*. For example, in a thermal stress problem, the temperature field introduces thermal strains in the structural field, but the structural strains generally do not affect the temperature distribution; therefore, there is no need to iterate between the two field solutions.

More complicated cases involce *two-way coupling*. For example, a piezoelectric analysis handles the interaction between the structural and electric fields; that is, it solves the voltage distribution due to applied displacements, or vice versa. In a fluid-structure interaction problem, the fluid pressure causes the structure to deform, in turn causing the fluid solution to change; such a problem requires interactions between the two physics fields for convergence.

Coupling between fields occurs either by *direct* or *load-transfer* coupling. Coupling across fields can be complicated because different fields may be solving for different types of analyses during a simulation. For example, in an induction heating problem, a harmonic electromagnetic analysis calculates Joule heating, used in a transient thermal analysis to predict a time-dependent temperature solution. The induction heating problem is complicated further because the material properties in both physics simulations are highly temperature-dependent.

Some applications in which coupled-field analysis are often required are pressure vessels (thermal-stress analysis), fluid-floe constrictions (fluid-structure analysis), induction heating (magnetic-thermal analysis), ultrasonic transducers (piezoelectric analysis), magnetic forming (magneto-structural analysis), and microelectromechanical systems (MEMS).

# Types of Coulping Methods

There are basically two methods of coupling distinguished by the finite element formulation techniques used to develop the matrix equations. These are illustrated here with two types of degrees of freedom $\{{X_1}, {X_2}\}$:

1. *Strong Coupling*, also called matrix, simultaneous, or full coupling -- where the matrix equation is of the form:

$$ \begin{bmatrix}
[K_{11}] & [K_{12}] \\
[K_{21}] & [K_{22}]
\end{bmatrix} 
\begin{bmatrix} X_1 \\ X_2
\end{bmatrix} 
= \begin{bmatrix} F_1 \\ F_2
\end{bmatrix}$$

and the coupling effect is accounted for by the presence of the off-diagonal submatrices $[K_{12}]$ and $[K_{21}]$. This method provides for a coupled response in the solution after one iteration.

2. *Weak Coupling*, also called load vector or sequential coupling -- where the coupling in the matrix equation is shown in the most general form:

$$ \begin{bmatrix}
K_{11}(X_1, X_2) & [0]\\
[0] & K_{22}(X_1, X_2)
\end{bmatrix}
\begin{bmatrix}
X_1 \\ 
X_2
\end{bmatrix}
=\begin{bmatrix}
F_1 (X_1, X_2) \\
F_2 (X_1, X_2)
\end{bmatrix}$$

and the coupling effect is accounted for in the dependency of $[K_{11}]$ and $F_1$ on $X_2$ as well as $[K_{22}]$ and $F_2$ on $X_1$. At least two iterations are required to achieve a coupled response.



[1] Ansys Mechanical APDL Theory Reference.pdf

[2] Ansys Mechanical APDL Coupled-Field Analysis Guide.pdf
