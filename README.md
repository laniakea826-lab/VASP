### VASP
PROCAR paser . following band structure plot

Saving data as npz format.
Each variable 

# ISPIN = 1 system




if ispin == 1:
    np.savez_compressed('procar_results.npz', 
                            procar=orb_data,
                            eigenval=ene_data, 
                            kpath=k_path,
                            infos=[nkpts, nbands, nions])
elif lnonco == 'T':
    np.savez_compressed('procar_results.npz', 
                            procar=orb_tot_data, 
                            procar_x=orb_magx_data, 
                            procar_y=orb_magy_data, 
                            procar_z=orb_magz_data, 
                            eigenval=ene_data, 
                            kpath=k_path,
                            infos=[nkpts, nbands, nions])
else:
    np.savez_compressed('procar_results.npz', 
                            procar_up=orb_up_data, 
                            procar_down=orb_down_data, 
                            eigenval=ene_data, 
                            kpath=k_path,
                            infos=[nkpts, nbands, nions])
