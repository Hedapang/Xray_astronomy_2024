# Xray_astronomy_2024

* * *
### Software Installation 
#### 1. Install HEASoft (Need Linux or macOS system)
**1.1 Downolad HEASoft source code suitbale for your system (e.g. macOS, Ubuntu, etc) at:**
[https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/download.html](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/download.html)

★ Current version is 6.33.1! If you have an older one, just use it.

<ins>Do not choose the Pre-Compiled Binary type!</ins>

<ins>Choose "All" in STEP2 and click 'Submit' only once. </ins>

<ins>Ensure you have enough memory (> 10 GB) to download and install heasoft successfully!</ins>

**1.2 Install the prerequisite packages (X11, Compilers: C, C++, Perl & Fortran, Python)**

For Mac users (Intel/M1/M2 chip):

following: [https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/ macos.html](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/ macos.html)

    install [XQuartz](https://www.xquartz.org)
    xcode-select --install
    brew install gcc@12
    brew install perl
    brew install libpng
    conda install astropy numpy scipy matplotlib pip

For Ubuntu users:

following: [https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/ linux.html](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/ linux.html)

    sudo apt-get -y install libreadline-dev
    sudo apt-get -y install libncurses5-dev
    sudo apt-get -y install ncurses-dev
    sudo apt-get -y install curl
    sudo apt-get -y install libcurl4
    sudo apt-get -y install libcurl4-gnutls-dev
    sudo apt-get -y install xorg-dev
    sudo apt-get -y install make
    sudo apt-get -y install gcc g++ gfortran
    sudo apt-get -y install perl-modules
    sudo apt-get -y install python3-dev [or python-dev]
    sudo apt-get -y install python3-pip
    sudo apt-get -y install python3-setuptools
    sudo apt-get -y install numpy
    sudo apt-get -y install python3-astropy
    sudo apt-get -y install python3-scipy

**1.3 Configure the software**

(1) Unpack the downloaded file in a clean directory (your home directory is highly recommended)

    cd /usr/local/  # or any other directory you prefer
    sudo tar zxvf /path/to/the/downloaded/file/heasoft-6.33src.tar.gz # change according to your path and filename 

(2) Build the environment --

Set the relevant environment variables to point to the compatible compiler. It is recommended to simply add the following commands in your profile (.zshrc, .bashrc or .cshrc file, normally in your home directory). 

For users of Bourne Shell (sh, zsh and bash):

    export CC=/usr/bin/clang
    export CXX=/usr/bin/clang++ 
    export FC=/usr/local/bin/gfortran-12 
    export PERL=/usr/bin/perl
    
For users of C Shell variants (csh, tcsh):

    setenv CC /usr/bin/clang
    setenv CXX /usr/bin/clang++ 
    setenv FC /usr/local/bin/gfortran-12 
    setenv PERL /usr/bin/perl
    
(3) Go to the heasoft-6.33/BUILD_DIR directory and configure the software for your platform.

For users of Bourne Shell (sh, zsh and bash):

    cd heasoft-6.33/BUILD_DIR/
    ./configure > config.txt 2>&1             
    make > build.log 2>&1                     
    make install > install.log 2>&1   

For users of C Shell variants (csh, tcsh):

    cd heasoft-6.33/BUILD_DIR/
    ./configure >& config.txt
    make >& build.log
    make install >& install.log
    
This step will capture the screen outputs to text files, and if you want to see the outputs instantaneously, just ./configure, make and make install.

<ins> At the configure step -- only if you see "Finished" at the end of the output, it means the configuration is successful. If errors occur, be patient to solve them step by step. </ins>

<ins> The make step may take a long time (~ 1 hour, just let it run and do your things). If your process finished in a few minutes, check if there are any errors. </ins>

**1.4 Initialization**

Add the following commands in your profile --

For users of Bourne Shell (sh, zsh and bash):

    export HEADAS=/path/to/your/installed/heasoft-6.33/(PLATFORM)
    alias heainit=". $HEADAS/headas-init.sh"
    
For users of C Shell variants (csh, tcsh):

    setenv HEADAS /path/to/your/installed/heasoft-6.33/(PLATFORM)
    source $HEADAS/headas-init.csh

where (PLATFORM) is a placeholder for the platform-specific string denoting your machine's architecture, for example:

aarch64-apple-darwin22.6.0

<ins>You can always find your PLATFORM in the heasoft-6.33/ directory (i.e. the name of a sub-directory)</ins>

Once you finish this step, open a new terminal and try:

    heainit
    xspec
    
If you enter the Xspec environment without any error, the initialization is done! Now you can have a break and dive into the X-ray data analysis!


For more details about the HEASoft installation, it is highly recommend to refer to the instructions in STEP 3 at:
[https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/download.html](https://heasarc.gsfc.nasa.gov/docs/software/lheasoft/download.html)

You can always find some useful information in these official guide.


#### 2. Install eSASS

For reference, see:
[https://erosita.mpe.mpg.de/edr/DataAnalysis/esassinstall.html](https://erosita.mpe.mpg.de/edr/DataAnalysis/esassinstall.html)

**2.1 Download eSASS and CALDB**

Minimum requirements:
✓ CPU: x86-64 CPU (Intel, AMD or equivalent) , Apple Silicon M1/M2
✓ Memory: 8 GB
✓ Disk space: 3 GB (including CALDB)

* The eSASS4DR1 package can be downloaded as a unique archive tarball from the following link:
[https://erosita.mpe.mpg.de/dr1/eSASS4DR1/eSASS4DR1_installation/ eSASS4DR1.tgz](https://erosita.mpe.mpg.de/dr1/eSASS4DR1/eSASS4DR1_installation/ eSASS4DR1.tgz)

Move this script to a clean directory (e.g. create a new sub-directory named as "esass" in your home directory) and make the script executable by typing:

    chmod +x eSASS4EDRmirror.sh

* The CALDB is also available as a unique tarball. You can download it via the following link:
[https://erosita.mpe.mpg.de/dr1/eSASS4DR1/eSASS4DR1_installation/ caldb4DR1.tgz](https://erosita.mpe.mpg.de/dr1/eSASS4DR1/eSASS4DR1_installation/ caldb4DR1.tgz)


**2.2 Install eSASS4DR1 on Linux (Ubuntu systems) and macOS**

(1) After downloading the eSASS4DR1 package and CALDB, move the files to an installation folder (/<my eSASS path>/) and extract the content:

    tar zxf **.tgz

(2) Configure healpix:

    cd /<your eSASS path>/external/Healpix_3.50 
    ./configure
    
and launch the configure script there:
    1. Choose option "3": configure Healpix F90 package.
    2. Enter the name of your F90 compiler (e.g., gfortran).
    3. Accept all default flags.
    4. Enter the name of your C compiler (e.g., gcc).
    5. Accept all default flags.
    6. Accept for the libcfitsio.a library.
    7. Point to your CFITSIO library (the command locate can be used to find the directory ~/
    lib/ where libcfitsio.a is placed, which comes with the HEASOFT installation). It is advisable to
    give the full path.
    8. Enabling the PGPLOT is optional.
    9. Choose the standard serial implementation, i.e. option "0".
    10. Accept the Position Independent Compilation.
    11. Choosing a shared/dynamic library is optional.
    12. Choose option "0": exit.
    
***NOTE!***   
<ins>***1. Press enter to accept all default flags.*** </ins>  
<ins>***2. Type y (yes) for all optional settings.*** </ins>    
<ins>***3. The full name and the location of your cfitsio library can be find using the command "locate libcfitsio.a" (the libcfitsio.a file is placed in ~/lib/ directory).*** </ins>

***When the configure step is done, you will see a "Good Bye". Then you should run the command:***

    make


(3) Install eSASS

Note:
• The eSASS software also requires the fftw library installed in your system. In Ubuntu systems, it can be installed by typing sudo apt-get install fftw3 and sudo apt-get install libfftw3-dev in a terminal. This process requires administrator privileges,
i.e., sudo password. In macOS systems, please install the fftw-3, fftw-3-long, and fftw-3- single, either using MacPorts or Brew.
• macOS systems also require:
autoconf, automake, coreutils, libtool, ncurses, readline, realpath, libpng, and perl.

From this point on, it is assumed that:
• You have a HEASOFT installation, and the path of this installation is stored in the environment variable HEADAS.
• You have access to a HEALPix 3.50 installation.
• You have a fftw library installed on your computer.

You can proceed with the eSASS installation as described in the following.

    cd /<my eSASS path>/eSASS4DR1/eSASS/autoconf
    heainit
    
    export CC=/path/to/gcc 
    export CXX=/path/to/g++ 
    export FC=/path/to/gfortran 
    export F77=/path/to/gfortran
    
    aclocal

    autoreconf -fi -v
    
    ./configure --with-caldb=/<my CALDB path>/ --with-healpix=/<my HEALPix path> --with-headas=$HEADAS --with-gsl=compile --with-lapack=system
    

For **Ubuntu** users, there may be errors like "No ** library found!", which means you are missing some required packages. You can easily solve this problem by installing the missing libraries (more and more packages you install > ~ <):

First, search the library with the name of "xxx" (e.g. readline):

    apt-cache search readline # change as you need

There may be a lot of outputs, choose the one named like lib*-dev (e.g. lib64readline-dev) and install it in your home directory:

    sudo apt-get -y install lib64readline-dev
    
★ To identify if the eSASS4DR1 configuration succeeded, the end of the configure command output must look like this:

  ### CALDB SETUP ###
  configure: Using caldb directory /full.path/to/caldb as you provided for setup ### Installation location: /<my eSASS path>/eSASS4DR1/eSASS ###

If no more errors occur when configuring, continue to run make:

    make
    make install

Hopefully, you will see "Congratulations! The installation succeeded" after tens of minutes~

Finally, run make clean to remove those unnecessary files and enable the eSASS environment:

    source /<your eSASS path>/eSASS4EDR/bin/esass-init.sh 

<u>It is recommended to add this line to your profile (.bashrc, zshrc or cshrc) for automatic initialisation.</u>


* * *

<ins>If you have more questions about the installation, please feel free to contact me.</ins>

My email: helin@smail.nju.edu.cn

or find me in Wechat group.

#### 完结！撒花！o(≧v≦)o
