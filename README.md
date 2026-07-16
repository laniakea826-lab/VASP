# PROCAR parser
Manufacture output files from VASP calculation; band structure.

Saves PROCAR data into `.npz` format. 
Below are the descriptions of the variables saved in the output file.

---

## 1. ISPIN = 1 (Non-magnetic system)

* `procar`: A dictionary containing projection data for each orbital.
    * **Key (`n`)**: Atom index. Atom 1 of `POSCAR` corresponds to key `1` of `procar`. 
    * **Value**: A 3D numpy array with the shape `(nkpts, nbands, norbitals)`.
    * *Note: The atom index starts from 1, not 0!*
* `eigenval`: Energy eigenvalues. Can be used to plot a standard band structure along with the `k_path` variable.
* `k_path`: High-symmetry $k$-path coordinates.
* `infos`: Metadata of the calculation in the format `[nkpts, nbands, nions]`.

---

## 2. ISPIN = 2; LNONCOLLINEAR = TRUE (Non-collinear magnetic system)

* `procar`: Total projection data (same structure as in the `ISPIN = 1` system).
* `procar_x`, `procar_y`, `procar_z`: Projection data for each magnetic direction ($m_x$, $m_y$, $m_z$). Same structure as the `procar` variable.
* `eigenval`: Same as in the `ISPIN = 1` system.
* `k_path`: Same as in the `ISPIN = 1` system.
* `infos`: Same as in the `ISPIN = 1` system.

---

## 3. ISPIN = 2; LNONCOLLINEAR = FALSE (Collinear spin-polarized system)

* `procar_up`: Spin-up projection data (same structure as `procar` in the `ISPIN = 1` system).
* `procar_down`: Spin-down projection data (same structure as `procar` in the `ISPIN = 1` system).
* `eigenval`: Same as in the `ISPIN = 1` system.
* `k_path`: Same as in the `ISPIN = 1` system.
* `infos`: Same as in the `ISPIN = 1` system.
