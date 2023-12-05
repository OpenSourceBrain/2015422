# Simulation and plotting scripts for (Soplata et al., 2023)

These are the simulation and plotting runscripts for all simulations in the
publication below. See below for instructions. All parameters relevant to the work
that not in this repo are contained here:
https://github.com/asoplata/dynasim-extended-benita-model which is where the
main mechanism files exist (these are also located in this zip file in a
directory of the same name as the repo).

### Citation

Soplata, Austin E., Elie Adam, Emery N. Brown, Patrick L. Purdon, Michelle M. McCarthy, and Nancy Kopell. 2023. "Rapid Thalamocortical Network Switching Mediated by Cortical Synchronization Underlies Propofol-Induced EEG Signatures: A Biophysical Model." Journal of Neurophysiology 130 (1): 86–103. https://doi.org/10.1152/jn.00068.2022.

### Hardware Requirements

1. Most of the simulations were run on a computing cluster with RAM anywhere
   from 12GB - 64GB. Running individual simulations on your desktop may be
   possible depending on its RAM.
2. Each simulation that saves simulation data, as opposed to simply output
   plots, requires around 15GB of space each.
3. All simulations were run on nodes using Intel "Skylake" architecture. Since
   Matlab appears to generate different random seeds depending on the CPU
   architecture (UGH), the only way you'll get "bit-perfect" reproducible
   simulations similar to what I got is to use the same architecture. However,
   this shouldn't really matter, since the behavior of what we found doesn't
   depend on exact starting conditions or floating-point error.

### Software Dependencies

1. You must have a "recent" version of MATLAB installed; the simulations were
   run using version 2022a. The code is not guaranteed to work on different
   versions of MATLAB, but I can provide help if you ask.
2. You must then install the "dev" branch of DynaSim:
   https://github.com/DynaSim/DynaSim/tree/dev . All simulations were last run
   using this commit:
   https://github.com/DynaSim/DynaSim/commit/b1aa46d29bd96a4383f5831211fbae73a0ff709f
   . Instructions for how to install it are available on its wiki here:
   https://github.com/DynaSim/DynaSim/wiki/Installation .
3. You must then install the model itself, which is available here
   https://github.com/asoplata/dynasim-extended-benita-model . This should be as
   easy as copying those files into
   `<YOUR_DYNASIM_INSTALL_FOLDER>/models/personal`, which you may have to create
   if it doesn't exist.

### Simulation running and plotting instructions

After you've installed the dependencies, run the simulation file for the figure
you're interested in. The simulation files are all the Matlab script files in
the top-level of each figure directory which do NOT contain "ans" in the
filename (indicating "analysis" script) and which are not single-function
files. Note that you should replace the variable `output_dir` with where you
want the data saved in every script. You can ignore Matlab files in lower
directories that start with "solve"; these are solve files that will be
automatically generated by DynaSim when you run your simulation script. If
you're going to run a lot of the simulations, I recommend using a combination
of `grep` and `sed` to change your output directory, as shown here
https://github.com/asoplata/bin/blob/master/grsed .

After you've run the simulation runscript and generated any output data
necessary, run the "ans" (analysis) script for that runscript to produce the
PNG plots which were used to create the final figures.

If you need any help with this, feel free to reach out and contact me using the
email on my GitHub profile page!

