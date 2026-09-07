computing temperature of the aux CV from PLUMED
This is a Fortran file, that will read the velocity of the auxiliary degrees of freedom from an output of PLUMED, and compute the Temperature. To print the velocities of CV, use the following in the PLUMED input:
PRINT STRIDE=100  ex.dis_vfct ….FILE=COLVAR_VEL
where ex.xxx_vfct is the velocity of the fictitious variable corresponding to the CV named as "xxx" in the PLUMED input.

The code reads velocities as follows:
 read(1,*,IOSTAT=ios)temp,vfict(1:ncv) 
Here, temp is dummy variable (i.e. the first column of the file is not used), and vfict is the velocity in d/ps units

Temperature is computed as temp=mass*dot_product(vfict(1:ncv),vfict(1:ncv))/gasconst*convert_to_K/dfloat(ncv). 
Here, mass is "mass in amu Ang.^-2  u_cv^-2 : " where u_cv is the units of CV.
