# elastic
Elastic is a finite element solver for linear elasticity problems in two and three dimensions.

#### Installation
1. you will need to install the [ICS Commons Library](https://github.com/ICStoolbox/Commons) on your system. 
Please refer to the instructions provided on the ICS Commons Library page in order to install this library.

2. clone this repository and build elastic:

   ` git clone https://github.com/ICStoolbox/LinearElasticity.git `

   go to LinearElasticity directory

   ` cd LinearElasticity `

   then create build directory and create Makefile
   ```
   mkdir build
   cd build
   cmake ..
   make
   ```

   if no errors are produced, install the binary and library

   ` make install ` 

you can test the installation and look at examples by entering the [demos](demos) directory.

#####Usage
elastic program is called in command line. Open a terminal and type

    elastic --help

or

    elastic -h

to know the list of options and flags. The square braces indicate optional arguments. Some commands have flags, some others do no. Some flags are optional, some are mandatory. The help output looks like this:

    usage: elastic [+/-v | -h] [-n nit] [-r res] [-t typ] source_file[.mesh] [-s data_file[.sol]] [-o output_file[.sol]]
 
The options and flags are:

    --help       show the syntax and exit.
    --version    show the version and date of release and exit.

    -n nit       number of iterations max for convergence 
    -r res       value of the residual (Krylov space) for convergence
    -t typ       specify the type of FE space: 1: P1, 2: P2
    -v           suppress any message (for use with function call).
    +v           increase the verbosity level for output.

    source_file.mesh      name of the mesh file
    data_file.sol         name of file containing the initial solution or boundary conditions
    output_file.sol       name of the output file (displacement field)


#### Usage
After compiling elastic as described above, you should have an executable file in your $HOME/bin directory. If your PATH variable is correctly set to this directory, elastic can be called as follows:

    elastic mesh_file[.mesh]
 
A full description of all parameters and options that can be specified in the command line or in a parameter file [file.elas] can be found in the project [wiki](https://github.com/ICStoolbox/LinearElasticity/wiki).

Running elastic with the input file 'carre.mesh' will produce an output that will look like:

    user:~/code/LinearElasticity/demos/2d$ elastic carre 
     - ELASTIC, Release 5.0c, Jan.19, 2016
       (C) Copyright 2006- , ICS-SU
    
     - LOADING DATA
        carre.mesh: 5663 vertices, 257 edges, 11067 triangles
        carre.elas: 4 conditions
     - COMPLETED: 0.024s

     ** MODULE ELASTIC: 5.0c
        Matrix and right-hand side assembly
        Solving linear system: 9.236327E-07 in 2983 iterations
     ** COMPLETED: 6.954s

     - WRITING DATA
        carre.sol: 5663 data vectors
     - COMPLETED: 0.012s

     ** Cumulative time: 6.990s.

This output was produced by the parameter file 'carre.elas' which contains the specifications of the problem (boundary conditions, surface load and body forces, elastic properties of the domain).

#### Authors & contributors
* elastic has been initiated by Maya de Buhan (Université Paris Descartes) and Pascal Frey (Université Pierre et Marie Curie). Current team includes Charles Dapogny (Université Joseph Fourier), Chiara Nardoni (Université Pierre et Marie Curie) and Loic Norgeot (Université Pierre et Marie Curie).
* Contributors to this project are warmly welcomed. 

#### License
elastic is given under the [terms of the GNU Lesser General Public License] (LICENSE.md).
