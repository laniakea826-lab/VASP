# VASP PROCAR PASER
Saving data as npz format.
Check the variable below

## ISPIN = 1 system
procar:     data corresponds to each orbitals. DICT itself.
            Atom 1 of POSCAR corresponds to Atom 1 of 'procar'.
            procar[n] is 3D array itself with shape (number of k points, NBANDS, number of orbitals)
        NOTE. it's index does not start from 0!!!
        
eigenval:   Energy eigenvalues.
            Can be draw normal energy band structure with 'k_path' variable.
            
k_path:     k_path coordinates.

infos:      Information of the calculation.
            Form of [nkpts, NBANDSM nions]



## ISPIN = 2; LNONCOLLINEAR = TRUE system
procar:     Similar to adressed in ISPIN = 1 system; represents total magnetic direction data.

procar_x, procar_y, procar_z: Simliar to variable 'procar'. They represent each magnetic direction.
        
eigenval:   Adressed in ISPIN = 1 system
k_path:     Adressed in ISPIN = 1 system
infos:      Adressed in ISPIN = 1 system



## ISPIN = 2; LNONCOLLINEAR = FALSE system
procar_up:    Similar to adressed in ISPIN = 1 system; represents spin up data
procar_down:  Similar to adressed in ISPIN = 1 system; represents spin down data
        
eigenval:   Adressed in ISPIN = 1 system
k_path:     Adressed in ISPIN = 1 system
infos:      Adressed in ISPIN = 1 system
