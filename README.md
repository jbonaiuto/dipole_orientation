MEG dipole orientations
=======================

Simulation and analysis code for estimating cortical column orientations to constrain dipole orientations in MEG source inversion.

> JJ Bonaiuto, F Afdideh, M Ferez, K Wagstyl, J Mattout, M Bonnefond, GR Barnes, S Bestmann<br>
> **Estimates of cortical column orientation improve MEG source inversion**<br>
> NeuroImage 2020, https://www.sciencedirect.com/science/article/pii/S1053811920303487?via%3Dihub<br>
> (bioRxiv link: https://www.biorxiv.org/content/10.1101/810267v1)

## Requirements:

* SPM12 (replace spm_eeg_lgainmat.m, spm_cfg_eeg_inv_headmodel.m, spm_cfg_eeg_inv_invertiter.m, spm_eeg_inv_results_display.m, spm_eeg_invert_classic.m, spm_eeg_invert_display.m, spm_eeg_invertiter.m, and spm_eeg_simulate.m): https://www.fil.ion.ucl.ac.uk/spm/software/spm12/
* shadedErrorBar: https://fr.mathworks.com/matlabcentral/fileexchange/26311-raacampbell-shadederrorbar?
* dict: http://uk.mathworks.com/matlabcentral/fileexchange/19381-lookuptable
* rodrigues_rot: https://fr.mathworks.com/matlabcentral/fileexchange/34426-rotate-vector-s-about-axis

For variational vector field:

* nibabel
* freesurfer - dev version


## Usage

    normals=compute_surface_normals(subjects_dir, subj_id, surface, method)
where surface is 'pial', 'white', or 'white-pial' (combined surface), and method is 'ds_surf_norm', 'orig_surf_norm', 'link_vector', or 'variational'.

Then set the 'normals' attribute of the gifti surface you want to use for inversion using the result. spm_eeg_lgainmat.m will use this attribute if it exists, rather than computing surface normals. If it does not exist, normals will be computed as usual using spm_mesh_normals.m
