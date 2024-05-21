# Graetz
Graetz model
README

#â€”â€”â€”â€”â€”#
#Unidimensionnal forced convection generalized Graetz solutions#
#â€”â€”â€”â€”â€”#

This Maple code implements the generalized Graetz modes decomposition of the temperature field. It enables the determination of the temperature field solution to the stationary energy convection-diffusion equation, see (1). The code is divided in five sections: configuration and setup,  Spectrum and eigenmodes computation, alpha_i and c_i(z) evalutation, cost function minimization and Temperature field assembly. 

Three representative examples are given. A .mw file is associated to each example (Gaussian_Inlet_Temperature.mw, Solid_Wall_Thermal_Conductivity.mw and Efficiency_Co-current_Heat_Exchanger.mw). Those files can use two packages (Eigenmodes_Radial_Geometry_Dirichlet.mpl, Eigenmodes_Planar_Geometry_Neumann.mpl files) according to the nature of the lateral boundary conditions and the geometry of the domain. Those packages determine the eigenvalues and build the eigenmodes.

To execute one of the illustrative examples:
- open the selected .mw file
fill in the path to the package in the Importation Section
Then run the .mw file.
Maple command line is also possible. Both need the path to the the Importation Section.

#â€”â€”â€”â€”â€”#
#Input Parameters#
#â€”â€”â€”â€”â€”#

###Numerical parameters
They control the number of digits and the order of the Generalized Graetz modes method.

#Number of digits of the computations: Integer digit (for N_meth>50, digit need to be improved for taking care of accuracy)
Method's order, i.e Generalized Graetz eingen-function polynomial order in lambda (Generalized Graetz eingen-function are analytical functions of lambda): Integer N_meth

###Geometric parameters
The domain is be decomposed radially in several compartments and longitudinally in several sections. The boundaries of the latter are stored in two arrays.

#Number of compartments: Integer
N_comp
#Compartments' limits:  i-th compartment by for Bounds[i]&lt;r&lt;Bounds[i+1]: Array of floats
Bounds
#Number of longitudinal sections: Integer
N_Section
#Boundaries' sections: Array of floats
Sections

###Physical parameters
They describe the properties of the solids or the fluids in the studied domain.
They include the velocity profiles (array), the thermal conductivities (array) and the Peclet numbers.

#Dimensional Fluid's thermal conductivity: Rational number
kF_dim
#Non dimensional Fluid's thermal conductivity: Rational number
kF
#Thermal conductivities for each compartments: Array of rational numbers
K
#Péclet Number: Rational number
Pe
#Velocity's field for each compartment: Array of functions
V

#â€”â€”â€”â€”â€”#
#Output Parameters and Postprocessings#
#â€”â€”â€”â€”â€”#

The solved temperature field is stored in a Matrix according to the division of the
