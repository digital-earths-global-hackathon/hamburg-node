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


## 2. Log in

Once you are registered, use either https://jupyterhub.dkrz.de or `ssh -Y <userid>@levante.dkrz.de` for *shell logins*.

Levante uses the queuing system [SLURM](https://docs.dkrz.de/doc/levante/running-jobs/index.html) for submission, scheduling, execution, and monitoring of jobs. Choose the **interactive** partition for interactive data analysis.

Information about the file system or **where to store what on Levante**
* /home/ for scripts. Backuped, max 30 GB/user
* /work/ for data you need more than 2 weeks (model output/…), project quota, NO BACKUP
* /scratch/ for temporary files, 15 TB quota - DELETION AFTER TWO WEEKS, NO BACKUP


## 3. Set up your python environment

We have curated an "official" Python environment for the hackathon, which should provide all the necessary packages.

Get the **environment.yaml** file:

`wget "https://raw.githubusercontent.com/digital-earths-global-hackathon/tools/refs/heads/main/python_envs/environment.yaml"`

Make sure that no other modules are loaded:

`module purge`

Load the **python3/unstable** module:

`module load python3/unstable`

We recommend using [`micromamba`](http://mamba.readthedocs.io/en/latest/installation/micromamba-installation.html) 
to create and install the environment. mamba and micromamba are the same code base, only build options vary.

As the environment is quite large at 4GB, it is recommended that you place it in the work area of your project. Note: <path-to-your-environment-folder> means e.g. /work/xy2222/z123456/easy

Create the software environment (this takes some time):

`mamba env create -p <path-to-your-environment-folder> -f environment.yaml`

Activate the environment:

`mamba activate easy`

If the activation doesn't work use: `mamba activate <path-to-your-environment-folder>`

Now 'mamba env list' should display 'easy' as activated environment (*)

After activating the "easy" environment you can create an [IPython kernel](https://ipython.readthedocs.io/en/latest/install/kernel_install.html) 
to conveniently use the environment in [DKRZ JupyerHub](https://jupyterhub.dkrz.de):

`python3 -m ipykernel install --name global-hackathon-easy --user`

Now you can select the "global-hackathon-easy" kernel in JupyerHub. If you can't see the kernel in the kernel list press the _"refresh the file browser"_ button (round arrow) on the left panel of jupyterhub.


### Simulation

We are using the [Intake](https://easy.gems.dkrz.de/Processing/Intake/index.html) catalog to store a diversity of data lists. Intake uses xarray for easy data access in python and allows for powerful searches.

**The url to the catalog and usage examples will follow shortly before the hackathon.**

## 4. Start your analysis!

Whether to create your own or built up on existing [notebooks](https://github.com/digital-earths-global-hackathon/hk25-teams), everything should be set to start your analysis!


Enjoy the hacking!

---

## [easy.gems](https://easy.gems.dkrz.de/index.html)

For further tutorials or information about high-resolution climate simulations, check out the user-driven site [**easy.gems**](https://easy.gems.dkrz.de/index.html).

Some entries are highlighted here:
* [Hierarchical HEALPix output](https://easy.gems.dkrz.de/Processing/healpix/index.html)
* [Resampling to lon-lat grid](https://easy.gems.dkrz.de/Processing/healpix/index.html)


