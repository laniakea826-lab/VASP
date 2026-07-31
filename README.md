# PROCAR parser
Manufacture output files from VASP calculation; band structure.

Saves PROCAR data into `.npz` (binary) format.  
It is easily imported and plotted, with about 5% of the original PROCAR size.  
*NOTE. Unreadable for human!*

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

---

## 4. Optional: kpts_infos.npz

* `klabel`: Labels of high-symmetry points along the $k$-path.
* `ticks`: Coordinates along the $k$-path corresponding to each label in `klabel`.
* *Note: These variables are always printed in your terminal regardless of your input choice (Y/N).*

---

### Usage Example (detailed guide inside the code)
python3 filename.py
```python
ISPIN ( 1 / 2 ) :                          # insert your option

parsing PROCAR start
parsing PROCAR done

saving data into binary format...
saved!

parsing KPOITNS start
parsing KPOINTS done

saving data into binary format...

saved!

orbitals:  ['s', 'py', 'pz', 'px', 'dxy', 'dyz', 'dz2', 'dxz', 'x2-y2', 'fy3x2', 'fxyz', 'fyz2', 'fz3', 'fxz2', 'fzx2', 'fx3', 'tot']
high symmetry points:  ['Γ', 'X', 'M', 'Γ', 'Z', 'X', 'R', 'M', 'A']
positons:  [0.0, 0.5, 1.0000000000000002, 1.707106781186545, 2.2071067811865466, 2.914213562373094, 3.414213562373096, 4.121320343559644, 4.6213203435596455]

save k-path information ( Y / N ) :                          # insert your choice
```
