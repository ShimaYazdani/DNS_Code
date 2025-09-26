# DNS_Code
- This FORTRAN code includes a Direct Numerical Simulation (DNS) solver for simulating turbulent flows in Cartesian coordinates, such as cavity and channel flow.
- The present numerical method combines a collocated grid approach with the Pressure-Weighted Interpolation Method (PWIM) to mitigate pressure-velocity coupling issues, enhancing the stability and convergence of simulations. 
- Additionally, a combination of explicit SIMPLE-family and symmetry-preserving schemes is incorporated to enhance computational efficiency, particularly in reducing computational time. 
- The numerical solution procedure is presented in sufficient detail for both temporal and spatial discretization with 2nd- and 4th-order accuracy. The details of the numerical solution and the discretization of equations are fully described in the article. 
- Additionally, statistical calculations, including turbulent kinetic energy, turbulent energy dissipation rate, and Kolmogorov length scales, are carried out.
- Moreover, an Open-MP feature embedded in the Intel compiler is used to parallelize loop structures in the code. Therefore, to compile the code, a compiler that supports this feature is required;  for example, the Intel compiler.
- The inputs for the desired flow are set through an input file called input.ini, which includes the number of grid points, geometry length, Reynolds number, CFL, and number of cores as below:
- 
********************************************************************************************************************************************
50       50        M_I  ,  N_J --------------->/M_I: Number of grid points in x-direction  ,  N_I: Number of grid points in y-direction/

50     1.D0        L_K  ,  Length------------->/L_k: Number of grid points in z-direction  ,  Length: Geometry length in z-direction/

0                  0 = Restart  , 1 = Resume-->/0: Running program from t=0  ,  1: Resuming stopped program/

10000.0            Reynolds------------------->/Reynolds: Reynolds number/

10.0   1000        CFL   ,  Writing Step------>/Courant-Friedrichs-Lewy  ,  Writing Step: Writung data every 1000 time steps/

3                  Number of CPU Cores-------->/Number of CPU cores used for parallel solving/
********************************************************************************************************************************************

- All the required inputs are embedded in the input.ini file. The user only needs to run the executable file Console1.exe and does not need to make any settings inside the Fortran code. These files are located in the following path:
  \x64\Release
- Note: If necessary, the user can change the algorithms used in the code to their liking. In this case, an IDE environment such as Visual Studio, which includes a Fortran compiler, is required.
- The simulation output is in the form of files, including the instantaneous flow field, the time-averaged flow field, and a file containing the velocity fluctuations over time. 
Several ready-made layouts with the ".lay" extension have been prepared for output in Tecplot software, allowing the results to be easily viewed.
The proposed solver is validated through a series of benchmark simulations, including laminar and turbulent flow cases, with excellent agreement observed with experimental and other numerical data.
