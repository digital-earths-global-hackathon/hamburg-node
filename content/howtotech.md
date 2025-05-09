---
title: First steps - How to hack
---


During the Hackathon climate data from [km-scale simulations](https://digital-earths-global-hackathon.github.io/hk25/simulations/) with ICON, IFS-FESOM and other models will be provided in a [**Healpix format**](https://easy.gems.dkrz.de/Processing/healpix/index.html) at different zoom levels. Jupyter Notebooks will be provided to explain the basics of the data handling. First examples can already be found on [**easy.gems**](https://easy.gems.dkrz.de/Processing/healpix/healpix_starter.html). Participants can then develop their own Jupyter Notebooks or python scripts to analyze and plot the data.

To make the most of your time analyzing data and minimize technical hiccups along the way, it's key to begin with a solid setup. This guide lays out first steps and to-dos to help you set up everything properly and get started quickly.

In this documentation, we’ll walk you through the basic setup and essential technical preparations. For more detailed explanations or deeper dives, we’ll point you to relevant additional resources. Take a moment to read through everything carefully—it’ll save you time and effort later on!

---

## 1. Check your access to the [HPC system Levante](https://www.dkrz.de/en/systems/hpc/hlre-4-levante?set_language=en)

To get access to the data you will need to get an [**DKRZ user account**](https://docs.dkrz.de/doc/getting_started/getting-a-user-account/dkrz-user-account.html#dkrz-user-account).
You need to [register](https://docs.dkrz.de/doc/getting_started/getting-a-user-account/dkrz-user-account.html#creating-a-new-account-from-scratch) here. Mention, that you are part of the global hackathon and [join an existing project](https://docs.dkrz.de/doc/getting_started/getting-a-user-account/dkrz-user-account.html#join-existing-project). The ID for the project is *bb1153*.

**If you are associated with any other project at DKRZ (e.g. because you are working at MPI-M), please use that project for your work. *bb1153* is there to provide access to outside users and the resources are shared by several hundred users.**

## 2. Log in

Once you are registered, use either https://jupyterhub.dkrz.de or `ssh -Y <userid>@levante.dkrz.de` for *shell logins*.

Levante uses the queuing system [SLURM](https://docs.dkrz.de/doc/levante/running-jobs/index.html) for submission, scheduling, execution, and monitoring of jobs. Choose the **interactive** partition for interactive data analysis.

Information about the file system or **where to store what on Levante**
* /home/ for scripts. Backuped, max 30 GB/user
* /work/ for data you need more than 2 weeks (model output/…), project quota, NO BACKUP
* /scratch/ for temporary files, 15 TB quota - DELETION AFTER TWO WEEKS, NO BACKUP

## 3. Set up your python environment

We have curated an *official* Python environment for the hackathon, which should provide a good working stack. We do not provide a central installation, as this is incompatible with self-installing packages (`pip install ...`), and often leads to conflicts.

Get the **environment.yaml** file:

`wget "https://raw.githubusercontent.com/digital-earths-global-hackathon/tools/refs/heads/main/python_envs/environment.yaml"`

You can either use your own conda/mamba installation, e.g. [micromamba](http://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html) to create and install the environment, or use one of the system's conda environments. In the following we will assume your conda/mamba/micromamba to be called `mamba`. This works for the system's environment. If you are already using another variant, please adjust accordingly.

### To load one of the system's conda environments:

If you don't have your own mamba installation, you can use the system's python environment, which secretly is a conda installation with mamba in it.

```bash
module purge
module load python3/unstable
```

### Create the environment from the environment.yaml file

Create the software environment (this takes some time):

`mamba env create -f environment.yaml`

Activate the environment:

`mamba activate easy`

This might print an error message telling you to first run `mamba init` (or similar). In that case, follow the instructions, and then try again.

Now `mamba env list` should display `easy` as activated environment (*)

After activating the "easy" environment you can create an [IPython kernel](https://ipython.readthedocs.io/en/latest/install/kernel_install.html) 
to conveniently use the environment in [DKRZ JupyerHub](https://jupyterhub.dkrz.de):

`python3 -m ipykernel install --name global-hackathon-easy --user`

Now you can select the "global-hackathon-easy" kernel in JupyterHub. If you can't see the kernel in the kernel list, press the _refresh the file browser_ button (round arrow) on the left panel of jupyterhub.

#### If you are running into issues with the quota in your home directory

If your home is pretty full, the environment might break your home quota. If this is an issue, you can place it in the work area of your project. Python will then load substantially slower, though. 

`mamba env create -f environment.yaml -p <path-to-your-environment-folder>`

Note: `<path-to-your-environment-folder>` means something like `/work/bb1153/${USER}/easy`. You might now need to provide the full path to the environment folder in the `mamba activate` command. 

 `mamba activate <path-to-your-environment-folder>`

## Simulation

We are using the [Intake](https://easy.gems.dkrz.de/Processing/Intake/index.html) catalog to store a diversity of data lists. Intake uses xarray for easy data access in python and allows for powerful searches.

See https://digital-earths-global-hackathon.github.io/catalog/ for the landing page of the catalog and links to usage examples.

## 4. Start your analysis!

Whether to create your own or built up on existing [notebooks](https://github.com/digital-earths-global-hackathon/hk25-teams), everything should be set to start your analysis!

Enjoy the hacking!

---

## [easy.gems](https://easy.gems.dkrz.de/index.html)

For further tutorials or information about high-resolution climate simulations, check out the user-driven site [**easy.gems**](https://easy.gems.dkrz.de/index.html).

Some entries are highlighted here:
* [Hierarchical HEALPix output](https://easy.gems.dkrz.de/Processing/healpix/index.html)
* [Resampling to lon-lat grid](https://easy.gems.dkrz.de/Processing/healpix/index.html)


